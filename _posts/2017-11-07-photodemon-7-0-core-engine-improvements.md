---
author: tanner_h
date: 2017-11-07 20:51:44+00:00
layout: post
slug: photodemon-7-0-core-engine-improvements
title: 'PhotoDemon 7.0: core engine improvements'
excerpt: While engine improvements don't always make for pretty pictures (because they exist "behind-the-scenes"), they're the foundation on which the entire program rests, so let's talk about some of the core engine changes that make this 7.0 release possible.  (And perhaps most importantly - let's talk about how these changes will make future releases possible.)
redirect_from:
  - /1678/photodemon-7-0-core-engine-improvements/
---

*(This is part of a series about PhotoDemon 7.0.  For the full 7.0 article collection, visit [this page](2017/11/28/photodemon-7-0-release).)*

PhotoDemon 7.0 is one of the rare releases where it's not an exaggeration to claim the program has been almost completely "rewritten".  There were so many major changes in this release - a new UI engine, new paint engine, new tool engine, new viewport engine, new Undo/Redo engine - that whole swaths of the program had to be reworked not just on their own, but in how they interact with each other.

While engine improvements don't always make for pretty pictures (because they exist "behind-the-scenes"), they're the foundation on which the entire program rests, so let's talk about some of the core engine changes that make this 7.0 release possible.  (And perhaps most importantly - let's talk about how these changes will make _future_ releases possible.)

## A paint-enabled viewport

In previous releases, PhotoDemon's primary interface was just for viewing images.  Sure, you could scroll and zoom and make minor adjustments, like moving or resizing layers, but most program operations took place in separate dialogs.  This meant that the viewport was not well-designed for interactive operations.

But with the addition of paint tools, that needed to change.  Drastically.  Paint tools aren't useful if there are large stutters between strokes, or significant lag during continuous mouse movements.

Viewport responsiveness is a pain point for many photo editors, and over the years, different mitigation strategies have emerged.  Many programs ultimately fall back on [multithreading](https://en.wikipedia.org/wiki/Thread_(computing)#Multithreading) to help, but this leads to problems of its own.  Let me demonstrate with a five-layer testing image I use to compare performance across programs:

![media/images/import/pdn_layer_move-570x397.gif](media/images/import/pdn_layer_move.gif)  

This is an example of moving a small layer in Paint.NET.  Notice the visible "chunking" as the layer is moved around.

![media/images/import/gimp_layer_move-570x397.gif](media/images/import/gimp_layer_move.gif)  

Here is the same thing in GIMP.  Notice how GIMP doesn't do anything at all, and then the layer will suddenly "jump" into place.  Sometimes the image leaves trails behind as it is dragged, too.

Visual artifacts like "smearing" and "chunking" drive me _crazy_.

In PhotoDemon 7.0, I put a lot of work into creating a responsive viewport that avoids these rendering issues.  Here's how PhotoDemon handles the same image:

![media/images/import/pd_layer_move-570x397.gif](media/images/import/pd_layer_move.gif)  

Notice how PhotoDemon keeps perfect pace with the mouse, with no "chunking" or other artifacts.

No matter how fast or slow the mouse moves, PhotoDemon fully synchronizes the viewport.  Note that this animated GIF only plays at 8 frames per second, so the actual viewport is even _more_ fluid than this shows.

Similar optimizations extend to PhotoDemon's new paintbrush engine.  Regardless of the age of your PC, I hope you will experience a fluid, responsive viewport across a wide range of brush and image conditions.  

Another neat feature enabled by PhotoDemon's ultra-responsive viewport is non-destructive layer rotation and skew.  All layer types - including text layers! - can be freely rotated and skewed in real-time, without harming the underlying pixel and vector data.  (Text layers are especially neat, because a rotated text layer still allows text and font editing.)

For a full look at PhotoDemon's new non-destructive layer transforms, visit the option panels of the Move/Size tool.

## Smarter Undo/Redo engine

Improving PhotoDemon's viewport required many long nights of performance profiling, and I was surprised to discover that one of the biggest culprits of random slowdowns was the Undo/Redo engine.  I'd previously put a lot of work into this engine, but painting makes tiny delays much more noticeable.

To solve this problem, I turned to outside help.  PhotoDemon 7.0 now ships with two state-of-the-art compression libraries: [Lz4](http://lz4.github.io/lz4/) and [Zstandard](http://facebook.github.io/zstd/).  These two libraries approach compression from different standpoints.  Lz4 attempts to compress and decompress data as fast as possible, while Zstandard strives for an ideal saddle-point between compression ratio and performance.

PhotoDemon's Undo engine juggles between these compression libraries to find the ideal trade-off between faster compression and larger Undo files, or slower compression and smaller Undo files.  Each hard drive is different (e.g. SSDs can write data very fast, but tend to have less free space, while traditional HDDs are slow but with lots of free space), and since PhotoDemon can't predict an ideal ratio in advance, it instead adjusts its settings in response to a variety of real-time parameters.

The end result is Undo/Redo operations that are both much faster than previous releases, while also taking up less hard drive space.  And, if you're extremely crunched for free space, you can still manually crank up Undo/Redo settings to reduce storage requirements even further.

## More control when saving images

When developing PhotoDemon, my guiding mantra is "simple but powerful."  Unfortunately, I sometimes screw up and drift too far to one extreme or the other.

One screw-up in past releases involved file format settings when saving images.  In an attempt to be helpful, I hid most export settings, and instead let PhotoDemon calculate appropriate settings for you.  This worked well for beginners, but developers have since told me that they _need_ those detailed settings, especially during tasks like batch processing.

In response, I've completely rewritten PhotoDemon's image export engine for this release.  The "auto-detect best settings" feature is still present, but if you want detailed settings, you now get a whole bunch of 'em!

Let's talk about PNG export in particular, as it's a critical one for web development:

![media/images/import/png_export_standard-570x391.png](media/images/import/png_export_standard.png) 

The PNG export dialog now supports two different modes: "traditional" PNGs, and web-optimized PNGs.  Most users will probably stick to traditional PNG mode, and this mode now exposes a wide range of traditional PNG settings.

The newly available "advanced settings" panel provides detailed control over the exported PNG's color depth.  PNGs support a wide range of color formats, depths, and transparency handling, and PhotoDemon supports as many as it can.  For example, if you want to specifically write high bit-depth grayscale PNGs without transparency, or paletted 8-bpp RGBA PNGs with special alpha channels, such combinations are now supported:

![media/images/import/png_export_colordepth-570x391.png](media/images/import/png_export_colordepth.png) *Exporting an 8-bpp PNG with binary (on/off) transparency*

For web-developers, PD now supports two 3rd-party open-source PNG optimization libraries: [OptiPNG](http://optipng.sourceforge.net/) for lossless optimizations, and [pngquant](https://pngquant.org/) for lossy optimizations.

![media/images/import/png_export_web-570x391.png](media/images/import/png_export_web.png) *The new "Export Web-Optimized PNG" settings panel*

Together, these two libraries can greatly reduce PNG size.  You can choose to use one library, or the other, or both simultaneously.  The results are [far superior to Photoshop's "Save for Web" feature](https://pngquant.org/vsphotoshop.html), and the web-optimization feature is also supported by PhotoDemon's batch processor - so you can now web-optimize whole folders of images in one go.

Other image formats have received similar export dialogs, with support for new features where applicable.  For example, multi-layer images can now be exported as multi-page TIFFs:

![media/images/import/tiff_export-570x317.png](media/images/import/tiff_export.png) 

I hope this makes it easier to use PhotoDemon for both casual and professional editing tasks.

## New clipboard engine

You would not _believe_ how complicated it is to trade image data with other programs over the Windows clipboard.  Windows places very few restrictions on clipboard data, which means that developers can shove any kind of data they want on there.  This works great for copy+paste capabilities inside the same program, but if you want to copy image data from one program to another?  Utter chaos!

In PhotoDemon 7.0, I've gone to great strides to solve this problem.  Copy+paste capabilities should now work with all major open-source photo editors, most proprietary ones, and a wide range of unrelated programs, like web browsers and office software.  If one of your programs *doesn't* work with PhotoDemon's copy+paste feature, please let me know so I can take a deeper look.

While I was here, I took the opportunity to implement a cool clipboard feature called _delayed rendering_.

When you click "copy" inside a program, the program must upload a large list of images to the clipboard, one for each format it wants to support.  Common formats include BMP, JPEG, PNG, and internal developer formats like DIB, DIBv5, and DDBs.  Each of these formats takes a lot of time to generate - think of it as saving an image file 6x in a row - and if the source image is large, these six copies can be big enough to crash a 32-bit program.

To work around this, most programs compromise and only place a few formats on the clipboard.  This is the least of many evils, as it's faster and consumes less memory, but it limits the number of programs you can trade data with.

In PhotoDemon 7.0, we use a new strategy called "delayed rendering".  With delayed rendering, when a user copies data inside PhotoDemon, we don't actually copy data to the clipboard.  Instead, we notify the clipboard of the full list of formats we support - a rather large list! - and then we wait.  If (and when) a user eventually clicks paste - in any program - the clipboard rushes back to us and says, "*paste* was just clicked, and this is the format the target program wants."  We then generate that specific format on-the-fly, and the entire process happens seamlessly, without any work on your part.

This strategy consumes very little memory (just enough for that one format, and only when it's actually requested), and it allows us to support many more clipboard formats than we otherwise could.

So why don't more programs do this?  Because like most nice things, it's surprisingly nasty to implement.  There are a ton of hurdles that must be dealt with, and a lot of weird edge-cases that require special attention.  If I had to do it all over again... well, let's just say that I'm grateful I don't have to.  In the meantime, enjoy a much faster, lighter, and more compatible clipboard engine!

## Updated metadata engine

As I've mentioned in the past, image metadata is an absolute nightmare.  Every camera manufacturer uses different metadata formats, many of which aren't publicly documented, and trying to process this information will drive even the most dedicated developers to insanity.

To combat this issue, PhotoDemon leans on the 3rd-party [ExifTool library](https://sno.phy.queensu.ca/~phil/exiftool/) for help.  ExifTool is an amazing piece of software (and significantly larger than PhotoDemon, if you can believe it), and it handles all that messy metadata processing so I don't have to.

In PhotoDemon 7.0, many more of ExifTool's features are available to users.  An overhauled metadata browser now presents every last bit of information that ExifTool was able to retrieve.  Existing metadata entries can also be modified or removed.  (Unfortunately, adding brand-new tags to an image is not yet supported; this is coming in a future release.)

![media/images/import/metadata_sample-570x340.png](media/images/import/metadata_sample.png) *Examining metadata from a Photoshop-processed image.  Look how many metadata groups Adobe adds to the file!*

As part of this overhaul, PhotoDemon's connection to the ExifTool engine has been further optimized for performance.  Even on images with extremely dense metadata collections, there is no performance penalty from these new metadata features.

## Many new engines related to tools, adjustments, and effects

One of the things that hindered previous PhotoDemon versions was a lack of fundamental libraries in the (very old, but very portable) toolkit used to develop the program.  This led to many "quick-and-dirty" hacks to get various tools up and running in a short timeframe.  

Unfortunately, quick-and-dirty hacks eventually catch up with you, and that's what happened after the last stable release.  It had become apparent to me that large changes were required to reduce problematic functions, cut down on code duplication, and improve program performance.

As such, many new libraries and engines were developed over the course of 7.0.  Many of these are tedious ones only relevant to developers, but let me spotlight a few of the ones that power new tools, adjustments, and effects.

![media/images/import/pdRandomize-570x329.png](media/images/import/pdRandomize.png)

All effects that use random number generation (like the Stained Glass filter, above) now use a shared [randomization engine](https://github.com/tannerhelland/PhotoDemon/blob/main/Classes/pdRandomize.cls), with support for several different random number generation methods, and highly optimized functions for special features like gaussian-distributed random numbers.

![media/images/import/pdFloodFill-570x397.png](media/images/import/pdFloodFill.png)

A [high-speed region analyzer](https://github.com/tannerhelland/PhotoDemon/blob/main/Classes/pdFloodFill.cls) provides the backbone of two different on-canvas tools: the bucket fill and magic wand tools.  This engine made it possible to finally add a traditional "marching ants" outline mode to PhotoDemon's selection tools.

![media/images/import/pdNoise-570x327.png](media/images/import/pdNoise.png)

Noise generation is the backbone of a wide variety of filters, including everything from the "Artistic > Figured Glass" effect to the new "Nature > Lava" effect shown above.  PhotoDemon now has a powerful [noise engine](https://github.com/tannerhelland/PhotoDemon/blob/main/Classes/pdNoise.cls) capable of producing [Perlin Noise](https://en.wikipedia.org/wiki/Perlin_noise), [Simplex Noise](https://en.wikipedia.org/wiki/Simplex_noise), and [OpenSimplex Noise](https://en.wikipedia.org/wiki/OpenSimplex_noise).  Performance improvements to the noise generator allowed me to speed up filters like the "Nature > Fog" effect by more than 400%. 

![media/images/import/pdPixelIterator-570x328.png](media/images/import/pdPixelIterator.png)

Sliding-window pixel iteration is required by many tools that support a "radius" parameter, like median filtering.  A new [pixel iterator class](https://github.com/tannerhelland/PhotoDemon/blob/main/Classes/pdPixelIterator.cls) allowed me to cut a ton of redundant code from the project, while also improving performance and adding support for "circular" windows.  If you encounter a tool that offers "square" vs "circular" radius options, the new iterator engine is the one handling this.

These are just a handful of the 20+ engines written for various PhotoDemon features in the 7.0 release.  Many of these engines are already being used to develop exciting new paint tools and effects, and thanks to them, the wait for a post-7.0 release will be _much_ shorter.

(Also, because PhotoDemon is 100% open-source, other developers are welcome to use these engines in their own projects.  I hope they help someone!)

## 80% of a new selection engine

PhotoDemon still lacks the ability to merge multiple selections together.  I am ~80% of the way toward finishing this feature, but the last 20% is especially messy, so I have postponed this feature until the next release.  Sorry about that.  (When released, it will use the same engine that powers a forthcoming Shape tool, which should allow any shape to be turned into selection, and vice-versa.)

So why do I mention selections here?  Because the ~80% finished selection engine still brings many benefits to this release.  Animated Marching Ant outlines are now available for all selection types, for example, and many selection operations are much faster than previous releases.  (Magic wand in particular has seen great performance improvements.)  Selections also play much more nicely with the Undo/Redo engine, and they are much more responsive on large images.

![media/images/import/selection_zoom_accuracy-570x397.jpg](media/images/import/selection_zoom_accuracy.jpg)

A number of accuracy enhancements have also been made - for example, when deeply zoomed in, selection outlines now outline individual pixel boundaries, as shown in the image above.  Best of all, this feature works on all selection shapes, not just ones with rectangular boundaries.

## New color-management engine

In this release, I have finally migrated PhotoDemon's color management chain to the 3rd-party [LittleCMS library](http://www.littlecms.com/).  LittleCMS is much more powerful than the built-in Windows color management engine, and it is also *much* faster.  So much faster, in fact, that I've been able to color-manage many small items that were not previously color-managed for performance reasons (like the image thumbnails used as taskbar icons).

(This is time for a good reminder: if you're running a multi-display system, be sure to visit the Tools > Options > Color-management window to confirm your color management settings across each display.)

## Conclusion

PhotoDemon 7.0 took a long time to release, but its delay allowed me to build a much more solid foundation for future releases.  As part of this work, I was also able to contribute some nice new code libraries to the broader open-source world.  (And a big thank you goes out to the open-source libraries that make PhotoDemon possible!)

[Return to the main PhotoDemon 7.0 release announcement](2017/11/28/photodemon-7-0-release)



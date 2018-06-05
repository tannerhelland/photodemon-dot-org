---
author: tanner_h
date: 2015-03-12 19:24:53+00:00
layout: post
slug: photodemon-6-6-beta-is-live
title: PhotoDemon 6.6 beta is live
excerpt: Version 6.6 is a little different from past releases.  I'm making great progress on adding on-canvas paint tools (and related tools, like text and shapes), but due to their complexity, the new tools still need a few more months of work.  I don't want to wait that long to release an update, so I've back-ported as many non-paint-tool upgrades and improvements as I can - that's what you'll find in version 6.6.
redirect_from:
  - /1042/photodemon-6-6-beta-is-live/
---

## Update 19 March 2015

Thank you to everyone helping to test the 6.6 beta.  I've just uploaded beta 3, which includes many bug-fixes relative to betas 1 and 2.  (Users of the previous beta will be automatically notified of the update.)

Barring any surprises, this will be the last beta for version 6.6.  

## Overview

It's that time again: PhotoDemon 6.6 is nearing release, and it's time for beta testing.  A few minor items still need addressing, and some language files are incomplete, but the core program is 99% ready for release - so anyone who can give it a whirl is greatly appreciated.

Version 6.6 is a little different from past releases.  I'm making great progress on adding on-canvas paint tools (and related tools, like text and shapes), but due to their complexity, the new tools still need a few more months of work.  I don't want to wait that long to release an update, so I've back-ported as many non-paint-tool upgrades and improvements as I can - that's what you'll find in version 6.6.

As such, this release is more about refinement than epic new features (although there are still some great new tools, like [polygon, lasso, and magic wand selections](2015/01/12/photodemon-6-6-preview-new-selection-tools)).  Some of the other new features, like automatic updates, should greatly reduce the "annoyance factor" of using PD on a regular basis.

While I expect this beta to be pretty stable, let me include my standard disclaimer, just to be safe: please don't do any serious photo editing work with the beta, and please don't test it on any photos you can't afford to lose.  I strongly recommend copying some test images to their own folder, and trying the beta on those copies.

As always, [I'd love to hear your thoughts](about/contact/) on the new release!

Now, for the good stuff.  For users upgrading from 6.4, here are some of the improvements you'll find in version 6.6.

### New selection tools

![media/images/import/PD_magic_wand_comparison_modes-570x372.jpg](media/images/import/PD_magic_wand_comparison_modes.jpg)

I've already talked about these tools in [a past article](2015/01/12/photodemon-6-6-preview-new-selection-tools), but let's do a quick recap for newcomers:

**Magic Wand selections**
	
  * You can click-drag the magic wand point in real-time to see changes
  * Arrow keys can be used for fine-tuned movement
  * Contiguous and global capture modes are supported
  * Selections can be made using the active layer, or the composite image (no flattening required!)
  * Full support for lossless, real-time antialiasing and feathering
  * Seven pixel matching modes, including Composite (color+alpha), Colors only (no alpha), Luminance only, or any individual channel

![media/images/import/PD_polygon_selection_edit-570x372.jpg](media/images/import/PD_polygon_selection_edit.jpg)

**Polygon selections**
	
  * Polygon selection points are non-destructive, meaning you can move the points _even after placing them_
  * The polygon as a whole can also be moved non-destructively
  * Support for curvature, so you can round polygon shapes as necessary
  * New optional "outline" mode allows you to see more of the image while creating the selection

**Lasso selections**
	
  * Once created, the lasso can be moved non-destructively
  * The Backspace key be used while drawing, so you can "retreat" the lasso to correct small mistakes
  * As with polygon selections, the new "outline" mode allows you to see more of the image while creating the selection

Some of the new features (like Outline mode) have also been added to the standard selection tools, and the Highlight mode now allows you to pick your own highlight color.

Many thanks to all those who helped test the new selection tools.  I hope you enjoy them!

![media/images/import/PD_66_Update_Preferences-570x395.jpg](media/images/import/PD_66_Update_Preferences.jpg)

### Automatic Updates

This is another feature that already received [its own article](2015/02/19/coming-in-photodemon-6-6-automatic-updates), but here's a quick overview:
	
  * PhotoDemon can now automatically update itself, with no work on your part
  * Three update tracks are supported: stable, stable+beta, and stable+beta+developer builds.  You can switch between these at any time.
  * Some program aspects - like language files - support delta patches, so only the latest changes are downloaded
  * For those who may dislike updates, you can still turn off or customize update checks to your liking
  * For additional transparency, PD now displays a network icon in the status bar whenever it's downloading update information

I'm not aware of another portable application that supports seamless, silent updates, so I think this is a pretty exciting feature.  (Many thanks to everyone who helped test this.)

### Numerous interface improvements

The end goal for PD's interface is supporting fully customizable visual themes.  I personally like dark interfaces when working on images, as it helps me focus on the image itself instead of the program surrounding it.

Windows provides no inherent support for customized application themes, so any developer who wants this feature must manage all of their interface rendering.  It's a massive undertaking.

Fortunately, PD is already some 75% of the way there.  Sliders, drop-downs, edit boxes, check and option buttons, and many more controls have been custom-built for the new theming engine.  A few holdouts remain (list boxes and command buttons, in particular), but they are on the to-do list.

These new custom-drawn controls allow for a lot of nice things.  As a random example, one thing I've already implemented is support for divider lines in complicated drop-downs, like Blend Modes:

![media/images/import/PD_66_drop_down_separators.jpg](media/images/import/PD_66_drop_down_separators.jpg)

It's really nice to have control over little things like this, so I think the work involved is worth the effort.  PD 6.6 is a little strange because some tool dialogs have been converted to the new controls while others have not, but one of the things I'll continue doing prior to the official release is replacing old controls with the new themable ones.

Unfortunately, changing themes will not be possible until a future release, but since I get a lot of questions about this, I wanted to mention that theming is well on its way toward completion.  The main PD window in particular has been fully converted to the new controls, so feel free to give 'em a whirl!

![media/images/import/PD_66_Unicode_layers-570x337.jpg](media/images/import/PD_66_Unicode_layers.jpg)

### Improved Unicode support

As with theming, full Unicode support will not land until the next release, but PD 6.6 includes a great deal of progress toward supporting all possible languages.  Unicode metadata and layer names are now supported, and the screenshot above shows how Unicode support is already enabled for the text tool prototype.  Internally, all PD text handling has also been moved from ANSI to UTF-8.

Even though it's not necessarily a "new tool", Unicode support has been one of the biggest emphases of this development cycle.  (A portable application isn't really portable if it doesn't work with Unicode, right?)  I'm very excited for the next release to include a text tool that is 100% Unicode-compatible from Day 1.

### Improved file format support, (especially RAW and HDR)

Because Windows itself provides very poor image format support, PD relies on the open-source FreeImage library for supporting anything beyond JPEG and PNG images.  This release, PD developers contributed [a bunch of patches](http://freeimage.cvs.sourceforge.net/viewvc/freeimage/FreeImage/Whatsnew.txt?revision=1.471&view=markup) to FreeImage in hopes of improving the library for not just PD, but everyone else who uses the library.  In particular, we worked with FreeImage to enable full support for one of the most popular [PNG transparency test libraries](http://entropymine.com/jason/testbed/pngtrans/).

Alongside our patches, the FreeImage team has integrated the latest LibRaw update, which adds support for [200 new camera models](http://www.libraw.org/news/libraw-0-17-alpha1).  I've also started custom-building FreeImage for PD so I can enable additional optimizations, so image loading and saving should be better than ever.

Many thanks to the FreeImage and LibRaw teams for their contributions to open-source tools like PD.

Inside PD itself, many new format-related features have been added.  For example, PNGs with sRGB, cHRM, or standalone gAMA chunks now receive full processing.  This makes PD one of the few photo editors that provides identical rendering to a fully compliant web browser.  (Test for yourself using [this helpful page from the libpng team](http://libpng.org/pub/png/png-colortest.html).)  

Many improvements have also been made to image metadata handling, particularly when moving images between formats with incompatible metadata types (e.g. EXIF in JPEGs and XMP in PNGs).  PhotoDemon is now smart enough to convert as many tags as it can to a supported metadata format (rather than just dropping the tags), so image metadata can even be preserved when moving images between formats.  (As always, many thanks to the excellent [ExifTool program](http://www.sno.phy.queensu.ca/~phil/exiftool/) that makes this possible.)

![media/images/import/PD_66_EMF_vs_EMFPlus-570x264.jpg](media/images/import/PD_66_EMF_vs_EMFPlus.jpg)

Finally, support has been added for importing EMF and WMF vector images.  EMFs are automatically up-sampled to the new EMF+ format while editing, which enables support for high-quality antialiasing and transparency, among other things.  Thank you to GioRock for his help with supporting these image formats.

![media/images/import/PD_66_HDR_Import-570x344.jpg](media/images/import/PD_66_HDR_Import.jpg)

### Tone-mapping dialog for HDR and RAW images

Working on HDR and RAW images is tough, because these file formats capture color and lighting values that exceed the range of PC displays.  As such, it is necessary to apply a tone-mapping operation to these images before displaying them on a screen.  Otherwise, values outside the range of the PC display will simply disappear.

In past versions, PD applied tone-mapping automatically to high bit-depth images, but this solution wasn't ideal.  Different images have different tone-mapping needs; some require drastic manipulation, while others can almost be taken "as-is".

To that end, PD now gives you full control over incoming HDR and RAW images.  (This includes high bit-depth variants of normal formats, like 48 or 64-bpp PNGs.)  Multiple tone-mapping operations are available, and if you were happy with PD's old approach to tone-mapping, you can use the "automatically apply these settings" toggle to restore the old behavior.

Many thanks to [Hans Nolte](https://github.com/hansnolte) for his help building and testing this tool.

### Supersampling support

PhotoDemon provides a lot of Distort and Transformation tools.  These tools have some unique concerns, because they physically remap an image between different coordinate spaces.  PD already provided support for subpixel positioning on such tools, which improves output considerably, but there's still room for additional improvements via an opposite technique, called [supersampling](http://en.wikipedia.org/wiki/Supersampling).

In honor of the TV show Community [returning to the air](https://screen.yahoo.com/community/), let me demonstrate these new improvements on an image of the lovely Alison Brie.

![media/images/import/Alison-Brie-321x570.jpg](media/images/import/Alison-Brie.jpg)

First up, we're going to apply PD's Pan and Zoom tool to the base image:

![media/images/import/1-subpixel-AA-at-1x-size-321x570.jpg](media/images/import/1-subpixel-AA-at-1x-size.jpg)

This is the output of the tool in PD 6.4.  Even though subpixel sampling is used, the "shrinking" effect of the tool causes each pixel in the new image to represent more than 100 pixels in the source image.  Subpixel sampling is great when distortions **enlarge** image regions (because it intelligently estimates the value of subpixels between existing pixels), but it can't do much for distorts that **shrink** image regions.

Supersampling is the exact opposite.  It's useless when enlarging, but immensely helpful when shrinking.  Supersampling works by sampling a whole bunch of pixels from the original image, then averaging them together to produce a composite pixel in the new image.  Because that probably makes very little sense, here's the same image, but produced with 12x supersampling:

![media/images/import/5-supersampling-with-12-offsets-321x570.jpg](media/images/import/5-supersampling-with-12-offsets.jpg)

Notice how much clearer this new image is?  Instead of a 1:1 mapping between the old and new images, PD's supersampling engine has intelligently sampled up to a dozen source pixels for each destination pixel, causing the new image to reflect a true pan and zoom function much more accurately.

Here is another comparison using PD's Perspective Tool, which has also received supersampling support:

![media/images/import/1-no-subpixel-no-supersample-321x570.jpg](media/images/import/1-no-subpixel-no-supersample.jpg)

![media/images/import/3-yes-subpixel-yes-supersample-321x570.jpg](media/images/import/3-yes-subpixel-yes-supersample.jpg)

Notice in particular the extreme improvements in the top-left, where the "shrinking" is most severe.

The main issue with supersampling is that it can be crazy slow, because for 12x supersampling, the program needs to do 12x more work.  To work around this limitation, PhotoDemon uses a technique called _adaptive supersampling_.  Basically, PD performs some pre-analysis on each pixel, sampling only one or two source pixels using the distort transform and seeing if the resulting colors differ.  If they do, the program proceeds with full supersampling, but if they don't, the program assumes the pixel is either from a region of smooth color (so there's no variation anyway), or that it's being mapped to a region of normal or enlarged size, so supersampling won't improve the output.

Adaptive supersampling greatly improves performance by only activating when necessary.  As an additional optimization, updated tools now expose a Quality slider, which allows you to choose a level between 1 (no super- or sub-sampling) and 5 (max super- and sub-sampling).  In most cases, the median value of 3 should produce excellent results while maintaining good performance.

### New and Improved Tools

Even though most my work has been focused on the items mentioned above, there's still been some time for performance, quality, and other improvements to existing tools - and maybe even adding a few new ones!  Some of the notable updates include:

  * New Cross-Screen tool

![media/images/import/PD_66_Cross_Screen-570x328.jpg](media/images/import/PD_66_Cross_Screen.jpg)

[Cross-screen](http://en.wikipedia.org/wiki/Photographic_filter#Cross_screen) produces "stars" from bright regions in an image.

  * Overhauled Lens Flare tool

  ![media/images/import/PD_66_Lens_Flare-570x336.jpg](media/images/import/PD_66_Lens_Flare.jpg)

Lens flare now supports many more options, so you can reproduce that [JJ Abrams feeling](http://io9.com/5230278/jj-abrams-admits-star-trek-lens-flares-are-ridiculous) _just right_.

  * Rewritten single-shot HDR tool

![media/images/import/PD_66_HDR-570x328.jpg](media/images/import/PD_66_HDR.jpg)

PD's old HDR tool could produce some neat results, but boy, was it slow.  On a large RAW image, it could take more than a minute to render its full effect.

With help from [Frans van Beers](https://plus.google.com/+FransvanBeers/), an entirely new single-shot HDR system was developed.  On large images and at maximum quality, the new tool is as much as 2000% faster than the old tool.  (No, that is not a typo - it really is that much faster.)  The HDR result is also a bit more flexible, so I consider this a win in more ways than one.

  * Unsharp Mask overhaul

![media/images/import/PD_66_Unsharp_Mask-570x328.jpg](media/images/import/PD_66_Unsharp_Mask.jpg)

Another one of Frans's contributions involved improvements to the Unsharp Masking tool.  Unsharp masking is indispensable, but unfortunately, PD's old version was pretty slow.  

The new version of the tool provides optional quality settings, which can greatly improve performance with only a small trade-off to overall quality.  As an example, on a 1920x1200 image and 200px sharpen radius, the old tool would take 24 seconds to render on my development PC.  The new one takes less than 1.5 seconds.

  * Improved Channel Mixer

![media/images/import/PD_66_Channel_Mixer-570x384.jpg](media/images/import/PD_66_Channel_Mixer.jpg)

PD's Channel Mixer provides a quick way to make very complex color adjustments.

  * Many other tool improvements

Other tools that saw work this release include Curves, Levels, Green Screen (Chroma Key), Color Balance, Kaleidoscope, Zoom Blur, Motion Blur, and probably others I forgot to add to my notes.  Many incidental bugs and performance issues have also been addressed across the program, so I hope you find everything working faster and better than it did in 6.4.

### Long-requested features from Raj Chaudhuri

I want to call special attention to some great 6.6 contributions from [Raj Chaudhuri](https://github.com/rajch).  

Raj was kind enough to sit down and deal with some of the oldest feature requests I had for PD, ones that had fallen off my radar despite being reported months or even years (!!!) ago.  While Raj helped with a great many things, I'd like to mention a few specifics:

![media/images/import/PD_66_Quick_Close.jpg](media/images/import/PD_66_Quick_Close.jpg)

New quick-close buttons in the image tabstrip (note the little red X in the corner, which appears when hovering with the mouse).

![media/images/import/PD_66_Image_Tabstrip_Context_Menu.jpg](media/images/import/PD_66_Image_Tabstrip_Context_Menu.jpg)

A new right-click context menu for the image tabstrip.

![media/images/import/PD_66_Recent_Macros-570x199.jpg](media/images/import/PD_66_Recent_Macros.jpg)

A new Recent Macros menu, which updates itself automatically as you use and record program macros.

Little additions like this are the kinds of things I often overlook, but they make a big difference in usability and convenience.  Many thanks to Raj for his contributions to this release.



### Third-party code review from Will Stamper



Another contributor I'd like to call out is [Will Stamper](https://github.com/epmatsw).  Will was kind enough to do an extensive review of PhotoDemon's source code, and he not only fixed many obnoxious things like typos, he also found a number of new bugs and program inefficiencies, especially in corners of the program that haven't been revisited in some time.

This kind of work is often thankless, especially when doing it to a codebase as large as PhotoDemon's, so many thanks to Will for such a helpful and much-needed contribution.



### Various performance improvements



While I was limited on how many new features I could back-port to this release (though looking at the length of this article, I guess there was more than I thought), one thing that's been easier to back-port is a lot of performance enhancements.  Because these changes often take place under-the-hood, I don't have to deal with things like language translations or user interface concerns, so PD 6.6 actually includes a number of performance improvements over 6.4.

A few highlights include:

**Updated Viewport and Canvas Pipeline**

Most of the rewritten viewport pipeline from the current paint tool work is included in this release.  Paint tools required me to redesign the way PhotoDemon manages the current image canvas, particularly when a lot of layers are active, so this was a good chance to better optimize the entire viewport pipeline.

Among other things, the new pipeline now supports sub-pixel positioning for both layers and selections.  This means that even when zoomed way out from a large image, the on-screen representation will still reflect the actual image very closely.

PD's central compositor - which handles layer blending - also saw many improvements.  When I added layers to version 6.4, a lot of performance enhancements had to be dropped because it was too much work to integrate them with layers.  Now that layer support is stable, I was finally able to add a lot of those old performance tweaks back in.

Note too that if you're stuck using PD on a very old PC, you can always modify the performance settings in the Tools > Options dialog to eke a bit more performance out of the program.

**Greatly reduced memory churn**
 
Photo editing software needs to generate a lot of temporary images.  Many effects require multiple image copies during processing, additional copies are required whenever we render images to the screen, and all the new custom-built buttons and sliders and other controls have to generate a lot of their own interface images.

In version 6.6, these temporary image copies are now managed much more intelligently.  Instead of PD's memory usage spiking all over the place, it tries to reuse existing temporary images whenever possible.  Additional optimizations kick in when generating image copies; instead of always relying on expensive copy operations that ensure things like image color depth and sizes match, we now bypass those entirely if we know images have equivalent parameters.

This should result in much smoother performance, particularly when previewing intensive effects and adjustments.

**Many performance improvements to the language translation engine**

Because PD allows users to change their active language at run-time, it has to manage a lot of translation stuff behind the scenes.  This was always cumbersome when working with the default Windows controls, because they were not designed for frequent, rapid caption changes.

PD's new user interface controls support translation features internally, so they are able to update themselves much more quickly when non-English languages are in use.  This should provide a much smoother experience for anyone who uses PD's growing body of non-English localizations.



### Interface improvements



As part of implementing paint tools, it was finally time to rework some of the more obnoxious elements of PD's main interface.  Many of these improvements have been backported to 6.6, including:

**Resizable and customizable left-hand tool pane**

The main toolbox on the left side of PD's screen can now be resized to your liking.  Buttons will automatically reflow as necessary, so you can shrink it down as much (or as little) as you like.

People who want to maximize canvas space can also shrink button size and remove group labels entirely, as in this screenshot:

![media/images/import/PD_66_Tiny_Toolbox-570x317.jpg](media/images/import/PD_66_Tiny_Toolbox.jpg)

These new customization options are available in the Window menu.

**New toolbox buttons for Save Lossless Copy and Fade Last Effect**

If you aren't accustomed to these two tools, you might not realize what a lifesaver they can be.  Easy access from the main toolbox should help more users discover them.

**Auto-hide bottom options box**

Some tools (like the pan/zoom hand) do not require extra options.  When these tools are selected, the bottom options box will now automatically hide itself.

**Fit Image, Fit Width, and Fit Height zoom options**

To make the best use of the available viewport space, PD now defaults to a "fit image" zoom option.  This automatically fits the image to the full available viewport, and if the viewport size changes (due to resizing the window or resizing toolbars or anything else), the image will automatically adjust to match.  

This behavior is so convenient that it now has a built-in toggle right there in the status bar.

As an additional convenience, I have also added options for fitting the image by width or height alone, similar to how users use Office software. 



### Many other bug-fixes, improvements, and enhancements



Rather than bore you with an additional list of updates, let me just refer curious individuals to [PhotoDemon's commit log](https://github.com/tannerhelland/PhotoDemon/commits/master).  That link provides an excruciatingly detailed look at everything that's been updated.



## Known bugs



As of 19 March 2015, none!  



## Official release timeline



I expect Beta 3 (uploaded on 19 March) to be the final beta before 6.6 releases.  Barring any surprises, 6.6 final should be available sometime next week.  Automatic update notifications for existing PhotoDemon installs will also go live at that point.

If you find any bugs, or if you have suggestions to improve version 6.6 before it releases, [please let me know](about/contact/)!  Once version 6.6 is released, any additional updates will be postponed to version 6.8... which may actually get renamed to version 7.0, since it will be a huge update with paint tools, a text tool, and so much more.

Thank you again to everyone who helped with version 6.6's development, and thank you to everyone who can help test this beta.  I especially appreciate your patience as I continue work on paint and text tools.  If nothing else, I hope this somewhat unconventional release helps make up for the delay.

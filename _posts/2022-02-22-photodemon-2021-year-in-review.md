---
author: tanner_h
date: 2022-02-23 13:23:19
layout: post
slug: photodemon-2021-year-in-review
title: 'PhotoDemon Year In Review: 2021'
excerpt: 2021 was an exciting year for PhotoDemon.  Here's a list of all the new features and improvements that made their way into nightly builds over the past year...
---

Hello, friends.  You haven't heard much from me during the past year, but that's only because I was hard at work on the next version of PhotoDemon!  

I thought it might be fun to share all the new features that arrived in PhotoDemon during 2021.  You may have seen some of these improvements if you [follow PhotoDemon's development over at GitHub](https://github.com/tannerhelland/PhotoDemon/commits/main), but if not, you're in for a treat.

As always, you can play with these new features today by [downloading the latest PhotoDemon nightly build](download/#nightly).  Otherwise, these features will be available in a 9.0 stable release sometime later this year.

## Major new features that arrived in 2021 

### New toolpanel design

![screen capture old version](media/images/interface_8.4.png)

![screen capture new version](media/images/interface_9.0.png)

PhotoDemon's new [top-aligned toolpanel UX](https://github.com/tannerhelland/PhotoDemon/commit/471070d3b01b44261ba2289dc32095a9346990a0) takes up 50% less screen space, while still providing one-click access to all advanced tool features.  Options are grouped into logical categories, with the most common settings accessible directly from the toolpanel.

Advanced options can be accessed from category-specific drop-down panels - just click on a category titlebar to "drop" its corresponding panel, or use the tab key to navigate through each setting using only the keyboard.

![new toolpanels](media/images/new_toolpanels.webp)

Panels automatically hide when you switch away from them, or you can use the "pin" button in a panel's lower corner to "pin" it open.  On larger displays, the new toolpanel engine can even slide some options out of panels and directly into the toolpanel (if enough horizontal space is available).

My goal with this new design was three-fold:
1. Giving your images even more space on-screen.
2. Making it easier for users of other popular photo editors to acclimate to PhotoDemon.
3. Keeping the interface highly readable and "discoverable", especially for beginners.

I hope you enjoy the new toolpanel design.  Please let me know if you have any ideas for improving it further.

### New selection tool features, including combined selections

![screen-capture](media/images/combine_selections.webp)

This feature took me most of 2021 (and a bit of 2022) to implement, but yes - PhotoDemon now supports multiple selections.  You can combine selections of any shape using "add", "subtract", and "intersect" combine modes.  (And of course, the old "replace" mode is still available!)

The new "combine selections" feature works across all selection tools, and PhotoDemon's version is especially cool because you can *still edit your current selection* even *after* a merge!  (You can see this in the animation above - watch as the "lasso" selection moves around, and the merged selection updates in real-time.)  

This brings incredible flexibility because unlike other photo editors, you don't lose the ability to modify a selection once it is merged.  PhotoDemon allows you to move, resize, and transform that last selection over and over to get it "just right".

The new selection engine also provides new rendering features.  The new renderer will automatically highlight the interior region formed when merging selections, which is very helpful with the "subtract" and "intersect" combine modes, especially when the underlying selections are complex.  You can also choose to fade-out the area outside the selection, or disable outline animations completely.  (These settings are accessible from the new "appearance" panel on all selection tools.)

### New image format support

I may have gone a little overboard with new image format support in this release, but I can't help it - I love it when PhotoDemon helps a user "unlock" images stuck in proprietary or poorly supported formats.

That's why I am incredibly excited to announce that PhotoDemon 9.0 will ship with support for a very popular (and very complex) image format: Paintshop Pro (PSP) images.  PhotoDemon's Paintshop Pro engine is 100% custom-built, and it provides native support for many advanced Paintshop Pro features, including both vector layers and editable text!

For example, here is a screenshot from [the PhotoDemon forums](https://github.com/tannerhelland/PhotoDemon/discussions/347) showing an image with hundreds of vector layers as it appears in Paintshop Pro...

![screen-capture](https://user-images.githubusercontent.com/142650/103448820-bd51eb80-4c96-11eb-9bef-30a70de1e504.png)

...and here is the same image, loaded into PhotoDemon:

![screen-capture](https://user-images.githubusercontent.com/1930029/104645217-05e0b000-566c-11eb-9e2a-a6fa978b8a6c.png)

Here is an additional debug screenshot marking all the vector objects (e.g. shapes defined purely by mathematical formulas) in the image:

![screen-capture](https://user-images.githubusercontent.com/1930029/104645954-0b8ac580-566d-11eb-9fa5-5b858d91ffd9.png)

PhotoDemon has to solve all of these vector equations on-the-fly and attempt to render them the same as Paintshop Pro.  The results look pretty darn close, and PhotoDemon will do all that while loading the file 3-4x faster than the latest version of Paintshop Pro!

Besides Paintshop Pro images, nightly builds also add support for the following image formats:

- Import and export support for the brand-new [AVIF file format](https://en.wikipedia.org/wiki/AV1#AV1_Image_File_Format_(AVIF)), c/o the [open-source libavif library](https://github.com/AOMediaCodec/libavif).  AVIF file support is incredibly complex (the stock encoder+decoder apps are almost 3x larger than PhotoDemon!) and they are only available for 64-bit systems, so PhotoDemon does not ship these libraries by default.  If you attempt to open or save an AVIF file, PhotoDemon will offer to download a local copy of libavif for you.  
- Comprehensive import and export support for [animated WebP images](https://developers.google.com/speed/webp), including direct export to animated WebP from PhotoDemon's screen recorder tool (`Tools > Animated screen capture`).  All of the animations on this page were generated using this feature!
- All-new [GIF import and export engines](https://github.com/tannerhelland/PhotoDemon/commit/cfee72e569721a71efe4a5bc8b8858a5f8501517), including a new [best-in-class animated GIF optimizer](https://github.com/tannerhelland/PhotoDemon/commit/aaab70c06a0697b56d0336e22477782b9af59093).
- Import support for [lossless JPEG (JPEG-LS) images](https://en.wikipedia.org/wiki/Lossless_JPEG), c/o the [CharLS library](https://github.com/team-charls/charls)
- Import support for [Comic Book Archive (CBZ) images](https://en.wikipedia.org/wiki/Comic_book_archive).
- Import support for old [Symbian (mbm, aif) images](https://en.wikipedia.org/wiki/MBM_(file_format))

### New best-in-class Image > Resize tool

The `Image > Resize` tool might be the tool I use most often.  I've really tried to make PhotoDemon's implementation a great one, but Photoshop's version has an additional feature that makes me extremely jealous: live previews right there in the Resize tool window.  

Why?  There are many different algorithms for resizing pixel data, with all sorts of trade-offs depending on an image's size and contents.  Unfortunately, there's no "always the best choice" algorithm, so when quality is paramount, some trial-and-error is necessary to figure out which algorithm will work best.  

And anything involving trial-and-error benefits greatly from live previews.

So why don't more photo editors provide live previews for this ubiquitous tool?  Well, because it's horrifically complicated to generate a real-time preview that accurately reflects a "full" resize.  (Preview windows typically take shortcuts to produce a preview as quickly as possible, but resizing algorithms need to examine huge numbers of pixels, which makes reliable previews a daunting task.)

Against my better judgment, [I've finally tackled a similar feature in PhotoDemon](https://github.com/tannerhelland/PhotoDemon/pull/361).  I'm proud to say that PhotoDemon will be (to my knowledge) the first open-source photo editor to provide live image resize previews, and it offers this for not one, or two, but **twelve** different resize strategies.  (Thirteen, I suppose, if you include the "automatic" option that attempts to choose a good algorithm for you.)

![screen-capture](media/images/image_resize_new.png)

Supported interpolation models include nearest-neighbor, bilinear, cosine, Hermite, bell, quadratic, b-spline, bicubic, Catmull-Rom, Mitchell-Netravali, cubic convolution and variable-radius Lanczos (sinc) filtering.  All algorithms are provided in two forms: speed-optimized integer-only calculations, and slower but theoretically "perfect" floating-point versions.  You can toggle between these via the new "optimize for speed" toggle.

The new resize engine has very low memory requirements and excellent performance, and it also brings new niceties like memory-size estimation, a user-resizable dialog, and progress bar updates after you hit OK.  (And as an added bonus, the `Layer > Resize` tool gains all of these same benefits!)

### Support for Photoshop effect plugins (8bf)

PhotoDemon now attempts to support [Photoshop effect plugins](https://en.wikipedia.org/wiki/Photoshop_plugin) ("8bf", 32-bit only).  This feature is made possible thanks to [spetric's Photoshop-Plugin-Host library](https://github.com/spetric/Photoshop-Plugin-Host).

This is an area where I lack expertise, but I've tested it against filters that ship with old versions of Photoshop, and the results are encouraging.  For example, here is Photoshop 5.0's "Texturize" filter running natively within PhotoDemon:

![screen-capture](media/images/8bf_filter.png)

Unfortunately, Photoshop plugins vary widely in quality and reliability, so you may encounter plugins that misbehave or fail to load at all.  If you do, please [create an issue on GitHub](https://github.com/tannerhelland/PhotoDemon/issues/new/choose) so I can investigate.

### New and Improved Effects

- A new [neural-network color quantizer](https://github.com/tannerhelland/PhotoDemon/commit/fc27cfc6a5ce7ab42a7d929e80e220281c818bb6) provides extremely high-quality results when saving to 256-color image formats, like GIF or web-optimized PNGs.  The new quantizer is also directly accessible as an effect via the `Effects > Stylize > Palettize` menu.
- A new [`Effects > Distort > Droste`](https://github.com/tannerhelland/PhotoDemon/pull/364) tool helps you channel your inner [M.C. Escher](https://en.wikipedia.org/wiki/Print_Gallery_(M._C._Escher)).  (Thank you to the author(s) of [the Paint.NET Droste plugin](https://forums.getpaint.net/topic/32240-droste-v11-may-8-2019/) that inspired it.)  This effect takes an image like this...

![clock](media/images/clock.png)

...and produces a result like this:

![clock](media/images/clock_droste.png)

- A new [`Effects > Render > Truchet Tiles`](https://github.com/tannerhelland/PhotoDemon/pull/358) tool can automatically produce a variety of geometric patterns for you:

![Truchet tiles](media/images/truchet.png)

- A new `Effects > Animation` menu adds support for [Foreground and Background effects](https://github.com/tannerhelland/PhotoDemon/commit/06a4f1df3a5231eb0cac17dd7f426a049e44f7e7), so you can easily add a new background or foreground layer to your favorite animated images
- A new [`Effects > Edge > Gradient flow`](https://github.com/tannerhelland/PhotoDemon/commit/f7e28487c087f1483dac435290ab3c30f7c18ac0) tool analyzes directionality in an image, which is useful in scientific analysis... or, you know, for making weird images like this:

![clock](media/images/gradient_flow.png)

- Greatly improved and accelerated [`Effects > Artistic > Stained Glass`](https://github.com/tannerhelland/PhotoDemon/commit/02f60a5c6807cec763fcfb7628332b9b6de897f2) and [`Effects > Pixelate > Crystallize`](https://github.com/tannerhelland/PhotoDemon/commit/ac2772d145a30b5e1a4bccd334c642062f63708c) tools, including new pattern features:

![clock](media/images/stained_glass_new.png)

### New and Improved Adjustments

- New [`Adjustments > Color > Color lookup`](https://github.com/tannerhelland/PhotoDemon/commit/5739253c850fbeb86af85f2ba4020da0ce1262d7) tool, with built-in support for [all 3D LUT formats that ship with Photoshop](https://helpx.adobe.com/photoshop/how-to/edit-photo-color-lookup-adjustment.html) (cube, look, 3dl) and [high-performance tetrahedral interpolation](https://www.nvidia.com/content/GTC/posters/2010/V01-Real-Time-Color-Space-Conversion-for-High-Resolution-Video.pdf) for best-in-class quality  
- New [`Adjustments > Lighting > Dehaze`](https://github.com/tannerhelland/PhotoDemon/commit/dde19d0c6e45b41f9c0d88d6d7c62a4651595836) tool, for recovering images marred by haze or fog
- Overhauled [`Adjustments > Curves`](https://github.com/tannerhelland/PhotoDemon/commit/989f861d8cf4b32e5a49c10cc87c094cc7f38b33) tool, with improved performance and a new UI
- Completely redesigned [`Adjustments > Color > Photo filter`](https://github.com/tannerhelland/PhotoDemon/commit/f142633977c1eed9f627f6ab6ab84053960914a1) tool, to better match the equivalent feature in Photoshop 
- [Otsu's method](https://en.wikipedia.org/wiki/Otsu%27s_method) is now used by [the `Adjustments > Monochrome` tool](https://github.com/tannerhelland/PhotoDemon/commit/4286395b520ec84b4c047eb37092a91532e7d500), for improved contrast when reducing an image to two colors.

### Image and Layer tools

- New [`Layer > Replace` tools](https://github.com/tannerhelland/PhotoDemon/commit/24f50821c1fd665494d72fd4e4e75fc29e8c3a0e), for quickly replacing an existing layer with data from the clipboard or an arbitrary image file.
- Overhauled [`Image > Crop` tool](https://github.com/tannerhelland/PhotoDemon/commit/6bfe841f282ae9ec9d75b4cd29065eee11c7e9f2), with new support for preserving editable text layers after a crop (instead of rasterizing them).
- New [lock aspect ratio](https://github.com/tannerhelland/PhotoDemon/commit/3b74576eb425c5ff80a4b05615f94a86faabf261) toggles on the `Move/Size` tool

### Batch processor

- New support for [preserving folder structure](https://github.com/tannerhelland/PhotoDemon/commit/4c6e7040440e5f2424485670d04d618a7fe211bd) when batch processing images from complex folder trees
- New support for batch processing [animated image formats (GIF, PNG, WebP)](https://github.com/tannerhelland/PhotoDemon/commit/647927e3130eaeaac4d58376c5b0f20463fbf57b)

### User interface 

- Adjustment and Effect dialogs are no longer fixed-size - [you can resize all of them at run-time](https://github.com/tannerhelland/PhotoDemon/commit/ab5363a885aec5529a81c28255defe77a516b285)!
- Adjustment and Effect tools now have [built-in Undo/Redo on each dialog](https://github.com/tannerhelland/PhotoDemon/commit/9d7adda0ab158f00d2f0ac393bc19ef800b31b30)
- [Faster app startup time](https://github.com/tannerhelland/PhotoDemon/commit/a56af482d262f6dab1ff016f111a0e909d9bfb98), particularly on Windows 10 and 11.
- PhotoDemon can now [automatically restore a previous session](https://github.com/tannerhelland/PhotoDemon/commit/735ba00b2f8da59356fab95c8486cda54b915939) when a system reboot interrupts.
- [Improved clipboard support](https://github.com/tannerhelland/PhotoDemon/commit/84f84be77b7a1f52cb1151eeef8e5df1bbec5fad) when copy/pasting to/from Google Chrome.
- New [background image compressor](https://github.com/tannerhelland/PhotoDemon/commit/dbac890b93ec10b36fd2e63aecf96d5e92904c6f) greatly reduces memory usage when working with multiple images.
- Similarly, a new [run-time resource minimizer](https://github.com/tannerhelland/PhotoDemon/commit/f00f0a81bf9f8fbff0a2c125b774884111de82e3) specifically designed for UI elements makes PhotoDemon - already among the lightest photo editors - even lighter on system resources.
- The `Window` menu now displays a [list of open images](https://github.com/tannerhelland/PhotoDemon/commit/009721ddc60246c803ee32ffe4c4376937a09bb4) for immediate access to any open image (even if you've disabled the image tabstrip).
- [Expanded "convenience" buttons in the Layer Toolbox](https://github.com/tannerhelland/PhotoDemon/commit/a421afaaddfee746e1769768503f300cf4849616), including new Shift+Click behavior (see button tooltips)

![clock](media/images/improved_layer_buttons.png)

- [Additional hotkeys have been implemented](https://github.com/tannerhelland/PhotoDemon/commit/08b2ad83e2e1fc89e2aa69f219a1da9d036098ce) to better match other photo editing software
- [Recent image and macro files](https://github.com/tannerhelland/PhotoDemon/commit/e2c17eaeda95abb2e27fd9bc036a6cf5047a184b) will now appear in search results from PhotoDemon's built-in search tool (Ctrl+F)

### That's still not everything, but I'm getting tired...

For a full list of changes, including many more minor improvements and bug-fixes, [visit the project's commit log at GitHub](https://github.com/tannerhelland/PhotoDemon/commits/main).

## Special thanks

Thank you to everyone who reported issues and shared feedback over the past year.  I am indebted to all of you.  ❤

And of course, an **extra-large thank you** to [all of PhotoDemon's Patreon supporters](https://www.patreon.com/photodemon) and [other contributors](contributors/), whose donations make this project possible.  If you find PhotoDemon useful, please consider [joining the Patreon campaign](https://www.patreon.com/photodemon) or [making a one-time donation](donate/).  Every little bit helps.

## When will PhotoDemon 9.0 release?

I honestly don't know.  Sometime in 2022?  Probably?  Hopefully?!

I'm about 2/3 of the way through my todo list for the 9.0 release, which would hypothetically put its release date sometime near autumn.  That said, I may get anxious and push out a 9.0 release sooner, and save some todo list items for a future 10.0 release... or I might get overly ambitious and add a few more things to the todo list, which would push 9.0's release back but make it even better.

What are your feelings?  Do you prefer giant releases with tons of new features?  Or smaller, more regular releases?

Or, do you happily use PhotoDemon's nightly builds and get every new feature as soon as it's available?

If you feel strongly one way or another, please **[share your feelings at the PhotoDemon forums](https://github.com/tannerhelland/PhotoDemon/discussions)**.  I'd love to hear your feedback on all the new features coming to version 9.0.

Finally, let me plug **[PhotoDemon's Patreon campaign](https://www.patreon.com/photodemon)** one more time.  Donations from generous users are the reason I can give away this software for free.  Patreon is a great way to help that happen.

If Patreon isn't a good fit for you, **[one-time donations](donate/)** are also a tremendous help.  Thank you so much for your generosity.  

As for me, it's time to get back to work on version 9.0.  I hope you'll get to experience it soon!
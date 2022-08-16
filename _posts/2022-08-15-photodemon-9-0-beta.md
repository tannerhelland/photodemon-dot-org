---
author: tanner_h
date: 2022-08-15 12:00:00+00:00
layout: post
slug: photodemon-9-0-beta
title: PhotoDemon 9.0 beta is now available
excerpt: After two years of work, a new PhotoDemon release is almost ready. New features include an improved user interface, multi-selection support, full support for new image formats (AVIF, PSP, SVG, XCF and more), content-aware fill, new filters and effects, and much more.
---

![screen-capture](media/images/photodemon_9.0.png)

## Overview

After two years of work, PhotoDemon 9.0 is almost ready. Highlights of this release include an improved user interface, new best-in-class selection tools (including support for multiple selections), support for many new image formats (AVIF, PSP, SVG, XCF), content-aware fill, new filters and effects, and much more.  

As with all previous PhotoDemon releases, PhotoDemon 9.0 supports any Windows PC sold in the past 20 years.  All modern versions of Windows (from Windows XP through the latest Windows 11 insider builds) are fully supported.

This release was a monumental effort and it would not be possible without many wonderful contributors who donated money, time, and feedback.  

**[Thank you to everyone who donates.](donate/)**  Your support makes this 100% free, 100% open-source project possible.

## Download the beta

If you already have a copy of PhotoDemon, you're good to go!  PhotoDemon will automatically update according to your preference in the `Tools > Options > Updates` menu.  (Just make sure you select updates for **stable and beta releases** or **stable, beta, and developer releases**; otherwise, PhotoDemon won't update until 9.0 formally releases.)

If you want to manually download the beta, [**click here**](https://github.com/tannerhelland/PhotoDemon/releases/download/v9.0-beta.1/PhotoDemon-9.0-beta.zip) or **[visit the download page](download/)**.

## Special thanks

**[Thank you to all of PhotoDemon's Patreon supporters](https://www.patreon.com/photodemon).**  Your donations make this project possible.

Thank you also to everyone who has made a [one-time donation](donate/).  

Finally, thank you to everyone who contributed bug reports, feature ideas, and feedback during this release cycle.  I am grateful to all of you.  ❤

## What's new and improved in this release

Some of these new features have already been discussed in greater detail in the [2021 year in review article](http://localhost:4000/2022/02/23/photodemon-2021-year-in-review.html), so head there for an even deeper dive.  

Otherwise, read on for a (very) long list of all the exciting changes available PhotoDemon 9.0.

### A quick mention, before we begin...

I know you're eager to see all the new features, but let me quickly share one *extra* exciting thing about version 9.0.

Despite providing more tools, adjustments, and effects than PhotoDemon 8.4, PhotoDemon 9.0 is actually *lighter* on system resources.  Take a look at this Windows Task Manager screenshot comparing the cold-start resource usage between the 9.0 beta release (highlighted) and the previous stable release:

![task manager screenshot](media/images/photodemon_9.0_resource_usage.png)

That's a 12% memory reduction, 21% [handle](https://en.wikipedia.org/wiki/Handle_(computing)) reduction, and 36% reduction in [graphics objects](https://en.wikipedia.org/wiki/Graphics_Device_Interface).  As you start working with images, the lower memory consumption of version 9.0 will be even more pronounced.

I just wanted to mention this up front because unlike other software, I try to make PhotoDemon **smaller** and **lighter** with each release, with even better support for ancient PCs.  So as you read about all the fun new features in version 9.0, remember that those improvements won't bog down your PC - and in fact, the PhotoDemon features you already enjoy will likely run even better than before.

### A revised and improved primary user interface

PhotoDemon's primary interface has been redesigned to give you more room to work.

![new-toolpanels](media/images/new-toolpanels.webp)

Tool options are now top-aligned against the menu bar, like other popular photo editors.  The most common options appear directly on the toolbar, and extended options have been moved to carefully organized flyout panels.

These flyout panels automatically disappear when you interact with the canvas.  You can also click the "pin" icon in the bottom-right of a panel to keep it open.

This new UI takes up less than half the vertical space of the old design, while still providing one-click access to all advanced tool options.

This new interface is designed to work all the way down to ancient display resolutions (like 1024x768), but if you have a modern display, some tools can automatically move advanced settings back into the toolbar itself as space allows.  This animation shows an "opacity" setting automatically moving between a flyout panel (below brush size) and the toolbar itself as the main PhotoDemon window is resized:

![toolpanel-autosize](media/images/toolpanel-autosize.webp)

### Best-in-class selection tools, including composite selections

PhotoDemon has always supported editable selections.  After you create a selection, you can continue to modify the selection by click-dragging on the selection's corners or sides, or using text boxes to make precise adjustments.

This feature has now been extended to multiple selections.  You can combine multiple selections using Add, Subtract, and Intersect modes, and your last selection remains editable **even when multiple selections are active**.  Here is a lasso selection being composited against previous rectangle and ellipse selections in real-time:

![multiple-selections](media/images/combine-selections-new.webp)

Honestly, this feature was a nightmare to develop, but I really wanted PhotoDemon to provide the best selection tool experience of any free photo editor.  I hope this release lives up to that goal.

### Content-aware fill for smart object removal

Building on these new selection tool features, PhotoDemon now ships with a powerful content-aware fill tool.  (This feature is also called "smart object removal" or "inpainting".)

Simply select one or more objects that you want to remove from a photo, and PhotoDemon will take care of the rest.  

![content-aware-fill](media/images/content-aware-fill.webp)

PhotoDemon's content-aware fill has no restrictions.  It works with all selection tools on any PC - yes, even on Windows XP.

The default settings work well in most conditions, but as you can see in the animation above, power users can further tweak the tool's behavior.  For example, in this panorama photo with missing pixels, I ask the inpainter to only sample pixels from certain directions.  This prevents the darker clouds on the left from bleeding into the lighter clouds on the right:

![content-aware-fill](media/images/content-aware-fill-panorama.webp)

Unlike other software, PhotoDemon's content-aware fill does not rely on "AI" or other silly buzzwords.  It does not require an internet connection or a large database of images to "learn" from.  Instead, it studies your current photo as-is, constructing different possible textures from nearby regions of the image, then refining the result until it arrives at a version it "likes".

I mention this because PhotoDemon's content-aware fill is deliberately [nondeterministic](https://en.wikipedia.org/wiki/Nondeterministic_algorithm).  If you don't like its results, no problem!  Just run the tool again and it will try a different approach.  Running it several times in quick succession can produce better results than running it once, and afterwards you can simply step through the different fill results using Undo/Redo.

For example, here's me using this strategy on the beach photo from before, but repeating the tool a few times to see different results:

![content-aware-fill](media/images/content-aware-fill-retry.webp)

### Full support for many new image formats

Expanded image format support was a large focus of this release.  PhotoDemon now provides:

- Import and export support for Corel Paintshop Pro (**PSP**) images.  The new importer can even preserve PSP text layers as editable text layers inside PhotoDemon!
- Import support for GIMP (**XCF**) images, including comprehensive coverage of layers in all color modes, integer and float precisions, and GIMP versions.
- Import and export support for the brand-new [**AVIF** file format](https://en.wikipedia.org/wiki/AV1#AV1_Image_File_Format_(AVIF)), c/o the [open-source libavif library](https://github.com/AOMediaCodec/libavif).  AVIF file support is incredibly complex (the stock encoder+decoder apps are ~3x larger than PhotoDemon) and they are only available for 64-bit systems, so PhotoDemon does not ship these libraries by default.  If you attempt to open or save an AVIF file on a compatible PC, PhotoDemon will offer to automatically download and configure a portable copy of libavif.
- Import and export support for **animated WebP** images.  Many of the screen capture animations on this page were created with this feature.
- Import support for [**SVG and SVGZ** images](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics), c/o the [open-source resvg library](https://github.com/RazrFalcon/resvg).

Other new formats supported by PhotoDemon include lossless JPEG (**JPEG-LS**), comic book archives (**CBZ**), old Symbian images (**MBM**, **AIF**), and lossless "quite OK" (**QOI**) images.  

In other image format news, PhotoDemon now includes a best-in-class [automatic GIF optimizer](https://github.com/tannerhelland/PhotoDemon/commit/aaab70c06a0697b56d0336e22477782b9af59093), and image formats that require palettes (like GIFs) benefit from a new [neural-network color quantizer](https://github.com/tannerhelland/PhotoDemon/commit/fc27cfc6a5ce7ab42a7d929e80e220281c818bb6) that constructs extremely high-quality palettes, even at low color counts.  

![neural_network_color_map](media/images/neural_network_color_map.png)

### Best-in-class Image Resize tool

PhotoDemon's `Image > Resize` tool now provides a dozen hand-tuned resampling modes.  Even better, all modes support live interactive previews:

![new-resize](media/images/new-resize.webp)

Live previews work with both upsampling and downsampling, and all resampling modes provide high-speed (integer) and high-precision (floating point) versions.  If you don't want to mess with any of these intricacies, a smart "automatic" mode automatically chooses reasonable settings for you.

With these improvements, I believe PhotoDemon provides the best image resize experience of any free photo editor.

### Built-in support for Adobe Photoshop plugins (8bf)

PhotoDemon now provides native support for [Photoshop effect plugins](https://en.wikipedia.org/wiki/Photoshop_plugin) ("8bf", 32-bit only).  This feature is possible thanks to [spetric's Photoshop-Plugin-Host library](https://github.com/spetric/Photoshop-Plugin-Host).

For example, here is Photoshop 5.0's "Texturize" filter running natively within PhotoDemon:

![screen-capture](media/images/8bf_filter.png)

### New Color Lookup adjustment, with import and export support for 3D Lookup Tables (LUTs)

Color lookup files (commonly called 3D LUTs, because they store **3**-**D**imensional **L**ook-**U**p **T**ables) are used extensively in film, photography, and game development.  These files encode any combination of color adjustments, including all the tools from PhotoDemon's (extensive) `Adjustments` menu.

PhotoDemon now provides full support for 3D LUTs in the new `Adjustments > Color > Color lookup` menu.  3DL, CUBE, and LOOK formats are supported at any complexity.  PhotoDemon also ships with a free set of color lookups that mimic your favorite one-click social media filters:

![color-lookup](media/images/color-lookup.webp)
*Bryce Canyon photo by [Daniel Lambson](https://www.flickr.com/photos/daniellambson/51490498024/in/pool-brycecanyonnps/)*

You can also make your own 3D LUT files.  Just load a photo and apply any combination of adjustments, then use the new `File > Export > Color lookup` tool to save those adjustments to 3DL, CUBE, or LOOK format.  All of your adjustments are now ready to use in Adobe Photoshop or any other LUT-capable photo editor - even if those photo editors don't provide the same adjustment tools as PhotoDemon!

You can also search online for "free 3D LUTs" to find more color adjustments than any human being could ever need or want.  (There are also many paid LUT offerings, if you're into that.)

I believe PhotoDemon is the first free, open-source photo editor to provide full coverage for all major 3D LUT formats.  This is also a relatively recent addition to Photoshop, so it's exciting to provide it here for free!

## Full list of changes by category

Those are some of the biggest improvements coming to PhotoDemon 9.0, but they are far from the only ones.  (I haven't even gotten to new effects yet!)

It would take too long to discuss every new feature at this same level of detail, so here is an abbreviated list of other highlights in the 9.0 beta.

### Effects

- New [`Effects > Light and shadow > Bump map`](https://github.com/tannerhelland/PhotoDemon/pull/399) tool.

![bump-map](media/images/bump-map.webp)

- New [`Effects > Distort > Droste`](https://github.com/tannerhelland/PhotoDemon/pull/364) tool, so you can channel your inner [M.C. Escher](https://en.wikipedia.org/wiki/Print_Gallery_(M._C._Escher)).

![effect_distort_droste](media/images/effect_distort_droste.png)

- New [`Effects > Render > Truchet Tiles` tool](https://github.com/tannerhelland/PhotoDemon/pull/358).

![effect_render_truchet](media/images/effect_render_truchet.png)

- New `Effects > Animation menu`, including new [Foreground and Background effects](https://github.com/tannerhelland/PhotoDemon/commit/06a4f1df3a5231eb0cac17dd7f426a049e44f7e7) (for automatically applying a background or foreground layer to an animated image) and an [Animation speed effect](https://github.com/tannerhelland/PhotoDemon/pull/400) (for permanently modifying playback speed).

![effects_animation_foreground](media/images/effects_animation_foreground.png)

- New [`Effects > Edge > Gradient flow`](https://github.com/tannerhelland/PhotoDemon/commit/f7e28487c087f1483dac435290ab3c30f7c18ac0) tool

![gradient_flow](media/images/gradient_flow.png)

- Greatly improved `Effects > Transform > Perspective` tool, with new live preview support and precision control for corner coordinates.

![effect_transform_perspective](media/images/effect_transform_perspective.webp)

- Greatly improved and accelerated [`Effects > Artistic > Stained Glass`](https://github.com/tannerhelland/PhotoDemon/commit/02f60a5c6807cec763fcfb7628332b9b6de897f2) and [`Effects > Pixelate > Crystallize`](https://github.com/tannerhelland/PhotoDemon/commit/ac2772d145a30b5e1a4bccd334c642062f63708c) tools

![effect_artistic_stained_glass](media/images/effect_artistic_stained_glass.webp)

- New support for [Photoshop effect plugins](https://en.wikipedia.org/wiki/Photoshop_plugin) ("8bf", 32-bit only), with thanks to [spetric's Photoshop-Plugin-Host library](https://github.com/spetric/Photoshop-Plugin-Host).

### Adjustments

- New [`Adjustments > Lighting > Dehaze` tool](https://github.com/tannerhelland/PhotoDemon/commit/dde19d0c6e45b41f9c0d88d6d7c62a4651595836).

![adjustments_lighting_dehaze](media/images/adjustments_lighting_dehaze.png)

- Overhauled [`Adjustments > Curves` tool](https://github.com/tannerhelland/PhotoDemon/commit/989f861d8cf4b32e5a49c10cc87c094cc7f38b33), with improved performance and a new UI.

![adjustments_curves](media/images/adjustments_curves.png)

- Completely redesigned [`Adjustments > Color > Photo filter`](https://github.com/tannerhelland/PhotoDemon/commit/f142633977c1eed9f627f6ab6ab84053960914a1) tool, to better match the identical tool in Photoshop.

![adjustments_photo_filter](media/images/adjustments_photo_filter.png)

- [Otsu's method](https://en.wikipedia.org/wiki/Otsu%27s_method) is now used by [the `Adjustments > Monochrome` tool](https://github.com/tannerhelland/PhotoDemon/commit/4286395b520ec84b4c047eb37092a91532e7d500), for improved contrast when reducing an image to two colors.

- New [`Adjustments > Color > Color lookup`](https://github.com/tannerhelland/PhotoDemon/commit/5739253c850fbeb86af85f2ba4020da0ce1262d7) tool, with built-in support for [all 3D LUT formats that ship with Photoshop](https://helpx.adobe.com/photoshop/how-to/edit-photo-color-lookup-adjustment.html) (cube, look, 3dl) and [high-performance tetrahedral interpolation](https://www.nvidia.com/content/GTC/posters/2010/V01-Real-Time-Color-Space-Conversion-for-High-Resolution-Video.pdf) for best-in-class quality.
- All photo adjustments (in any combination) can now be exported to [standalone 3D LUT files](https://github.com/tannerhelland/PhotoDemon/pull/415), enabling use of your favorite PhotoDemon adjustments in other software.
- PhotoDemon now ships with [a default set of public-domain 3D LUTs](https://github.com/tannerhelland/PhotoDemon/commit/6b769ea70b134fc1190d98f7272aedb6b7dcc510).

### File formats

- Comprehensive import and export support for [Corel Paintshop Pro (psp, pspimage) images](https://en.wikipedia.org/wiki/PaintShop_Pro), including many text and vector layer features.
- Comprehensive import support for [GIMP XCF images](https://en.wikipedia.org/wiki/GIMP), including full coverage for all color modes, precisions (integer and float), and XCF versions.  GZ-compressed XCF files are also supported.
- Comprehensive import and export support for the brand-new [AVIF file format](https://en.wikipedia.org/wiki/AV1#AV1_Image_File_Format_(AVIF)), c/o the [open-source libavif library](https://github.com/AOMediaCodec/libavif).  AVIF file support is incredibly complex (the stock encoder+decoder apps are almost 3x larger than PhotoDemon!) and they are only available for 64-bit systems, so PhotoDemon does not ship these libraries by default.  If you attempt to open or save an AVIF file, PhotoDemon will offer to download a local copy of libavif.  
- Comprehensive import and export support for [animated WebP images](https://developers.google.com/speed/webp), including direct export from PhotoDemon's built-in screen recording tool (`Tools > Animated screen capture`).

![animated-screen-capture](media/images/animated-screen-capture.png)

- Comprehensive import and export support for [lossless QOI ("quite OK image") files](https://qoiformat.org/).
- Comprehensive import support for [SVG and SVGZ images](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics), c/o the [open-source resvg library](https://github.com/RazrFalcon/resvg)
- Comprehensive import support for [lossless JPEG (JPEG-LS) images](https://en.wikipedia.org/wiki/Lossless_JPEG), c/o the [open-source CharLS library](https://github.com/team-charls/charls)
- Comprehensive import support for [Comic Book Archive (CBZ) images](https://en.wikipedia.org/wiki/Comic_book_archive).
- Comprehensive import support for [Symbian (mbm, aif) images](https://en.wikipedia.org/wiki/MBM_(file_format))
- All-new [GIF import and export engines](https://github.com/tannerhelland/PhotoDemon/commit/cfee72e569721a71efe4a5bc8b8858a5f8501517), including a new [best-in-class GIF optimizer](https://github.com/tannerhelland/PhotoDemon/commit/aaab70c06a0697b56d0336e22477782b9af59093).
- New [neural-network color quantizer](https://github.com/tannerhelland/PhotoDemon/commit/fc27cfc6a5ce7ab42a7d929e80e220281c818bb6) for maximum-quality results when saving to 256-color image formats, like GIF or web-optimized PNGs.  (The new quantizer is also directly accessible from the `Effects > Stylize > Palettize` tool.)
- [Safe overwrite behavior](https://github.com/tannerhelland/PhotoDemon/commit/18a6a152f0923ab0ad737e6f46ea54e6aa28b1b7) is now the default for all file formats.  (When saving over a file that already exists, PhotoDemon will save to a temporary file, validate the temporary file's correctness after the save completes, and only *then* will it replace the old copy with the new one.)

### Image and Layer tools

- [All-new selection tool engine](https://github.com/tannerhelland/PhotoDemon/pull/387), including full support for merging selections.  All selection tools support new "Add", "Subtract", and "Intersect" combine modes.  In addition, a new canvas selection renderer automatically highlights the merged region of composite selections.  (Other new rendering UI features are available on each selection toolpanel).
- New [`Edit > Content-aware fill` (and corresponding `Select > Heal selected area`) tools](https://github.com/tannerhelland/PhotoDemon/pull/403) can intelligently remove objects from photos.  Just select the object you want to remove, then click the menu to remove it!
- Completely redesigned [`Image > Resize` tool](https://github.com/tannerhelland/PhotoDemon/pull/361), with real-time interactive previews, 12 different resampling filters, memory size estimations, a user-resizable dialog, progress bar updates, and more.  The new tool was custom-built for PhotoDemon, and it has very low memory requirements, excellent performance, and zero 3rd-party dependencies.  (The `Layer > Resize` tool also receives all of these improvements!)
- New [`Layer > Replace` tools](https://github.com/tannerhelland/PhotoDemon/commit/24f50821c1fd665494d72fd4e4e75fc29e8c3a0e), for quickly replacing an existing layer with data from the clipboard or any arbitrary image file.

![layer_replace](media/images/layer_replace.png)

- Overhauled [`Image > Crop` tool](https://github.com/tannerhelland/PhotoDemon/commit/6bfe841f282ae9ec9d75b4cd29065eee11c7e9f2), including new support for retaining editable text layers after cropping (instead of rasterizing them).
- The `Advanced text tool` provides a new "stretch to fit" option, which automatically sizes the font to fit within the text layer's current boundaries.

![text_stretch_to_fit](media/images/text_stretch_to_fit.png)

- New [lock aspect ratio](https://github.com/tannerhelland/PhotoDemon/commit/3b74576eb425c5ff80a4b05615f94a86faabf261) toggle on the Move/Size tool
- New `Edit > Stroke` and `Edit > Fill` tools allow you to easily stroke a selection outline or fill a selected outline with custom pens or brushes.

![edit_fill_and_stroke](media/images/edit_fill_and_stroke.webp)

### Batch processor

- New support for [preserving folder structure](https://github.com/tannerhelland/PhotoDemon/commit/4c6e7040440e5f2424485670d04d618a7fe211bd) when batch processing images from a complex folder tree
- New support for batch processing [animated image formats (GIF, PNG, WebP)](https://github.com/tannerhelland/PhotoDemon/commit/647927e3130eaeaac4d58376c5b0f20463fbf57b)

![batch_process_animation.png](media/images/batch_process_animation.png)

### User interface 

- A [new compact toolpanel design](https://github.com/tannerhelland/PhotoDemon/commit/471070d3b01b44261ba2289dc32095a9346990a0) requires less on-screen space, while still providing one-click access to all of PhotoDemon's advanced tool features.  (This also enables PhotoDemon to successfully work all the way down to 1024x768 screen resolutions - a rare case of supporting even *older* hardware than previous versions of the app!)
- Adjustment and Effect dialogs are no longer fixed-size - [you can freely resize them at run-time](https://github.com/tannerhelland/PhotoDemon/commit/ab5363a885aec5529a81c28255defe77a516b285), and the preview area will resize accordingly.

![resize_windows.webp](media/images/resize_windows.webp)

- Adjustment and Effect tools now have [built-in Undo/Redo on each dialog](https://github.com/tannerhelland/PhotoDemon/commit/9d7adda0ab158f00d2f0ac393bc19ef800b31b30)
- [Faster app startup time](https://github.com/tannerhelland/PhotoDemon/commit/a56af482d262f6dab1ff016f111a0e909d9bfb98), particularly on Windows 10 and 11
- PhotoDemon can now [automatically restore your previous session](https://github.com/tannerhelland/PhotoDemon/commit/735ba00b2f8da59356fab95c8486cda54b915939) if a system reboot interrupts.

![session restore](media/images/session_restore.png)

- [Improved localization tools](https://github.com/tannerhelland/PhotoDemon/commit/e91936f0a900f2ed5b8513bf046bdfedb0ff0897), including [automated matching against other open-source translations](https://github.com/tannerhelland/PhotoDemon/commit/f0b26251d397de5263ee065d423bbd3989b77629), provide a significantly improved experience for non-EN-US locales.

![language editor](media/images/language_editor.png)

- [Improved clipboard support](https://github.com/tannerhelland/PhotoDemon/commit/84f84be77b7a1f52cb1151eeef8e5df1bbec5fad) when copy/pasting to/from Google Chrome
- New [background image compressor](https://github.com/tannerhelland/PhotoDemon/commit/dbac890b93ec10b36fd2e63aecf96d5e92904c6f) greatly reduces memory usage when working with multiple images at once
- Similarly, a new [run-time resource minimizer](https://github.com/tannerhelland/PhotoDemon/commit/f00f0a81bf9f8fbff0a2c125b774884111de82e3) for UI elements makes PhotoDemon - already among the lightest photo editors - even lighter on system resources.
- PhotoDemon's `Window` menu now displays a [list of open images](https://github.com/tannerhelland/PhotoDemon/commit/009721ddc60246c803ee32ffe4c4376937a09bb4) for immediate access to any open image (even if you've disabled the image tabstrip).
- [Expanded "convenience" buttons in the Layer Toolbox](https://github.com/tannerhelland/PhotoDemon/commit/a421afaaddfee746e1769768503f300cf4849616), including new Shift+Click behavior (see button tooltips)
- [Additional hotkeys have been implemented](https://github.com/tannerhelland/PhotoDemon/commit/08b2ad83e2e1fc89e2aa69f219a1da9d036098ce) to better match other photo editing software
- [Recent image and macro files](https://github.com/tannerhelland/PhotoDemon/commit/e2c17eaeda95abb2e27fd9bc036a6cf5047a184b) will now appear in search results from PhotoDemon's built-in search tool (Ctrl+F)

### Other

For a full list of changes, [visit the project's commit log](https://github.com/tannerhelland/PhotoDemon/commits/main).

## Stable release

As with past releases, I'd like to allow several weeks for public beta testing.  If no severe issues are encountered, the formal 9.0 release should happen in **September 2022**.

If you encounter bugs or want to provide other feedback, please [create a new issue on GitHub](https://github.com/tannerhelland/PhotoDemon/issues).  Otherwise, I'll see you in a few weeks with the official 9.0 release announcement!

## In conclusion

Thank you for using PhotoDemon.  

I am deeply grateful to everyone who contributed to this release, whether through Patreon, GitHub, or by sending old-fashioned emails.  A full list of contributors is available on [the Contributors page](contributors/), or in the `Help > About` menu of PhotoDemon itself.

Look for a final 9.0 release in the coming weeks, and best wishes for a happy and healthy rest of 2022.
---
author: tanner_h
date: 2014-08-12 15:30:36+00:00
layout: post
slug: photodemon-6-4-beta-is-live
title: PhotoDemon 6.4 beta is live
excerpt: It's that time again - PhotoDemon 6.4 is nearing release, and it's time for beta testing.  A few minor items still need addressing, and some language files are incomplete, but the core program is 99% ready for release - so anyone who can give it a whirl is greatly appreciated.
redirect_from:
  - /809/photodemon-6-4-beta-is-live/
---

## Update 09 September 2014

Version 6.4 has now been officially released, so instead of downloading the beta, you can download the official version from [this download page](download/).

Original beta announcement article follows.

## Update 03 September 2014

PhotoDemon 6.4 is now on its third beta release.  Beta 3 contains a number of important bug-fixes relative to betas 1 and 2.

Thank you to everyone who has already submitted feedback.  If you have additional suggestions or requests, time's running out to modify the code before 6.4 releases - so please [get in touch soon](about/contact/) if you have any feedback on this release.

## Overview

It's that time again: PhotoDemon 6.4 is nearing release, and it's time for beta testing.  A few minor items still need addressing, and some language files are incomplete, but the core program is 99% ready for release - so anyone who can give it a whirl is greatly appreciated.

The biggest change in this version is new support for image layers.  As part of implementing layers, many program elements were rewritten from scratch, so this development cycle was a tough one.  Hopefully the improvements were worth the wait!

Because so many parts of the program received overhauls, this beta may be more buggy than past betas.  I have extensively tested the code on Windows 7 and 8, and many excellent coders have contributed their own testing, but with so many new features it's tough to catch all problems.  As a result, please don't do any serious photo editing work with the beta, and just to be safe, please don't test it on any photos you can't afford to lose.  I strongly recommend copying some test images to their own folder, and trying the beta on those copies.

As always, [I'd love to hear your thoughts](about/contact/) on the new release!

Now, for the good stuff.  For users upgrading from 6.2, here are all the new features and improvements you'll find in version 6.4.  (A full list of changes is available here: [PhotoDemon 6.4 Development Roadmap](https://github.com/tannerhelland/PhotoDemon/issues/122)).

### Layers

Layers were the primary focus of this release cycle, and they have already been talked about in past [blog](2014/05/02/photodemon-6-4-layer-preview) [posts](2014/06/24/photodemon-6-4-update-new-features-new-ui-non-destructive-editing).  As a quick recap for newcomers:

  * Each image now supports an unlimited number of layers
  * Layers can be reordered using drag-drop, or the large arrow buttons on the new layer toolbox
  * Layers can be hidden or shown by clicking the layer's "eye" hover button
  * Layers can be merged up, merged down, and duplicated using the other hover buttons on the layer panel
  * Variable opacity and twenty-four layer blend modes are supported.
  * Layered images can be resized, rotated, flipped and mirrored without flattening the image.  Many programs don't allow layered images to be arbitrarily rotated without first flattening the image, but PhotoDemon can do it without trouble!

![media/images/import/PhotoDemon_64_Arbitrary_Rotation_preview-570x325.jpg](media/images/import/PhotoDemon_64_Arbitrary_Rotation_preview.jpg) 
*Here's an example of PhotoDemon rotating an image with five unique layers - no flattening required!*

  * A new Layers menu provides all the same options as the Layers toolbox, plus additional options like Flatten Image, Merge Visible Layers, adding/removing individual layer's transparency, and adjusting layer orientation (flip, rotate, etc).	
  * Layers can be moved around the image canvas in real-time using the new "Move" tool.
  * The new "Move" tool also allows you to non-destructively resize layers.
  * When moving and sizing layers, you can simply click the relevant layers in the window.  Selecting them from the Layer toolbox is not required.
  * Layered images can be saved to PhotoDemon's new layer-friendly file format (.PDI, for "PhotoDemon Image").
  * New layer options are available in the Edit menu, including Cut and Copy From Layer, and Paste as New Layer (vs Paste as New Image).

I'm very proud of PhotoDemon's new layers support.  Thank you to everyone who helped test these features during development.

### New non-destructive edit options

I've already mentioned non-destructive layer resizing, but version 6.4 also provides some new non-destructive edit tools.  These live in the new "quick fix" menu on the toolbar (marked by a light bulb).

![media/images/import/PD_64_quick_fix-570x388.jpg](media/images/import/PD_64_quick_fix.jpg) 

*Note the six "quick-fix" adjustments at the bottom of the screen.*

Non-destructive means that these changes are not permanently applied to the image.  If you want to undo any edit, simply set the slider back to zero, or use the "reset" button on the quick-fix panel.  This allows you to customize these parameters whenever you like, without harming image quality.

### Numerous interface improvements

![media/images/import/PD_6-4_split_toning-570x323.jpg](media/images/import/PD_6-4_split_toning.jpg)

![media/images/import/PD_64_interface_example-570x325.jpg](media/images/import/PD_64_interface_example.jpg)

New slider, radio button, and check boxes have been created specifically for PhotoDemon.  Besides being prettier, they are also much more usable.  The sliders in particular now provide much more feedback than the horrible old scroll bars they replaced.

Many more interface improvements will be coming in 6.4, but I think this is a solid start to making PD not just the prettiest free photo editor, but also the most functional.

### New tools galore

  * New Fade tool.  After applying an action to an image or layer, you can use Edit > Fade to fade the effect after the fact.  Blend mode can also be adjusted.

![media/images/import/PD_64_fade-570x319.jpg](media/images/import/PD_64_fade.jpg)

  * New Straighten tool, for more nuanced control than Arbitrary Rotate

![media/images/import/PD_64_straighten-570x325.jpg](media/images/import/PD_64_straighten.jpg)

  * New auto-correct options for one-click color, contrast, and lighting fixes
  * New auto-enhance options for color, contrast, and lighting.  These provide an easy way to make a photo more dramatic or colorful, without fiddling with a dialog.
  * Split-toning 

![media/images/import/PD_64_split_toning-570x323.jpg](media/images/import/PD_64_split_toning.jpg)

  * HDR (no exposure stack required)

![media/images/import/PD_64_hdr_polarbears-570x327.jpg](media/images/import/PD_64_hdr_polarbears.jpg)

  * Colored pencil artistic effect, with four pencil modes (normal, luminous, pastel, and graphite)

![media/images/import/PD_64_colored_pencil-570x327.jpg](media/images/import/PD_64_colored_pencil.jpg)

  * Glass Tiles 

![media/images/import/PD_64_glass_tiles-570x325.jpg](media/images/import/PD_64_glass_tiles.jpg)

  * Stained Glass

![media/images/import/PD_64_stained_glass1-570x324.jpg](media/images/import/PD_64_stained_glass1.jpg)

  * Fragment 

![media/images/import/PD_64_fragment-570x330.jpg](media/images/import/PD_64_fragment.jpg)

  * [Kuwahara filtering](http://en.wikipedia.org/wiki/Kuwahara_filter) 

![media/images/import/PD_64_Kuwahara-570x325.jpg](media/images/import/PD_64_Kuwahara.jpg)

  * Sunshine 

![media/images/import/PD_64_sunshine-570x325.jpg](media/images/import/PD_64_sunshine.jpg)

  * Remove Noise (bilateral smoothing) 

![media/images/import/PD_64_remove_noise-570x325.jpg](media/images/import/PD_64_remove_noise.jpg)

### Improvements to existing tools

Like any release cycle, many of PhotoDemon's existing tools have received performance, quality, and other improvements.  Some of the notable updates include:

* Improved Curves dialog, with new per-channel curve support, and an improved interface (including live display of curve parameters)

![media/images/import/PD_64_curves-570x372.jpg](media/images/import/PD_64_curves.jpg)

* Overhauled Levels dialog, including per-channel level support, click-to-set color options, and a new [best-in-class Auto Levels option](https://github.com/tannerhelland/PhotoDemon/commit/b047c67b4cc5948d657f98b360db44f21c6ff017)

![media/images/import/PD_64_levels-570x305.jpg](media/images/import/PD_64_levels.jpg)

* Color Balance now allows you to limit color adjustments by tonal range

![media/images/import/PD_64_color_balance-570x325.jpg](media/images/import/PD_64_color_balance.jpg)

* Overhauled comic book filter, with new options for ink density and color smoothing

![media/images/import/PD_64_comic_book-570x327.jpg](media/images/import/PD_64_comic_book.jpg)

* Overhauled Relief filter, with new options for angle, thickness, and relief depth

![media/images/import/PD_64_relief-570x327.jpg](media/images/import/PD_64_relief.jpg)

* Overhauled Emboss/Engrave filter, with new options for angle, thickness, and depth

![media/images/import/PD_64_emboss_engrave-570x327.jpg](media/images/import/PD_64_emboss_engrave.jpg)

* Overhauled Edge Enhance filter, with new options for edge detection mode, direction, and strength

![media/images/import/PD_64_edge_enhance-570x322.jpg](media/images/import/PD_64_edge_enhance.jpg)

* Overhauled Find Edges dialog, with new edge operators and directionality support

![media/images/import/PD_64_edge_detect-570x322.jpg](media/images/import/PD_64_edge_detect.jpg)

* Overhauled Rainbow filter, with new options for offset, angle, strength, and saturation boosting

![media/images/import/PD_64_rainbow-570x325.jpg](media/images/import/PD_64_rainbow.jpg)

* Overhauled Fog filter, with new options for scale, contrast, density, and render quality

![media/images/import/PD_64_fog-570x326.jpg](media/images/import/PD_64_fog.jpg)

* Overhauled Ignite filter (formerly Burn), with new options for intensity, flame height, and strength

![media/images/import/PD_64_ignite-570x327.jpg](media/images/import/PD_64_ignite.jpg)

### Undo History browser

The new Edit > Undo History browser allows you to jump to any point in an image's past (or future, if you've already undone some changes).

![media/images/import/PD_64_undo_history-570x416.jpg](media/images/import/PD_64_undo_history.jpg)

### New Performance options

I've always tried to achieve a balance of quality and performance in PhotoDemon, but depending on the limits of your PC, you may favor one parameter over the other.  A new Performance Options category allows you to customize how PhotoDemon handles certain trade-offs - for example, if you're low on disk space, you might prefer to heavily compress Undo/Redo data, which saves disk space at a slight performance trade-off.  Similarly, if you have a weak video card, you may want to reduce the amount of on-screen interface decorations (drop-shadows, etc) in order to improve render performance.

![media/images/import/PD_64_performance_options-570x394.jpg](media/images/import/PD_64_performance_options.jpg)

Note that none of these new options affect image adjustment or effect quality - they only affect the interface and other on-screen elements, so you don't have to worry about images or edits being lower-quality as a result of these changes.

### Minor improvements worth noting

As always, version 6.4 includes many small improvements.  Some highlights include:

  * Much better drag/drop support, including improved support for dragging images from web browsers
  * Improved status bar, including a clickable "resize image" button and "fit image on-screen" button
  * New Malay language support (machine translation only, improvements welcome!)
  * New Swedish language support (machine translation only, improvements welcome!)
  * Improved support for using arrow keys to modify various settings
  * New asynchronous image metadata processing.  Images with extensive metadata now load (and save) much faster than before.
  * Reduced program startup time, and greatly reduced shutdown time if many images were loaded
  * Improved mousewheel zoom, with zoom now preserving cursor location, instead of defaulting to position (0, 0)
  * New Select > Erase selected area option
  * Many improvements to Content-Aware resizing, including faster performance, symmetrical seam removal, and ESC-to-cancel functionality
  * Improved image load time, especially for large images and/or complex image formats

For a full list of this version's bug-fixes, performance improvements, and tool enhancements, please visit [PhotoDemon's commit log.](https://github.com/tannerhelland/PhotoDemon/commits/master)

## Known bugs

  * Translations for some languages are missing phrases for new tools and features.  These will be added before 6.4's final release.

## Official release timeline

Barring any major bugs, the official 6.4 release should happen within several weeks.  Feature-wise, it will be roughly identical to this beta release.  The only changes should be minor bug fixes and performance improvements.  Automatic update notifications for existing PhotoDemon installs will also go live at that point.

If you find any bugs, or if you have suggestions to improve version 6.4 before it releases, [please let me know](about/contact/)!  Once version 6.4 is released, any updates will be postponed to version 6.6.

Thank you again to everyone who helped with version 6.4's development, and thank you to everyone who can help test this beta version!

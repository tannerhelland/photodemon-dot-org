---
author: tanner_h
date: 2020-07-28 12:00:00+00:00
layout: post
slug: photodemon-8-0-beta
title: PhotoDemon 8.0 beta is now available
excerpt: After 2.5 years of work, a new PhotoDemon release is almost ready. New features include clone and pattern brush tools, a new gradient tool, support for Adobe Photoshop (PSD) images, massive performance improvements, new filters and effects, and much more.
---

![screen-capture](media/images/pd_8.0_beta.png)

## Overview

After 2.5 years of work, PhotoDemon 8.0 is almost ready. Highlights of this release include new clone and pattern brush tools, a new gradient tool, support for Adobe Photoshop (PSD) images, animated GIF and PNG images, Windows Icon (ICO) images, and OpenRaster (ORA) images, massive performance improvements, new filters and effects, and much more.

This release was a monumental effort, and it would not be possible without all the amazing contributors who donated money, time, and feedback.  [Thank you to everyone who donates!](donate/)  Your support makes this project possible.

## Download the beta

If you already have a copy of PhotoDemon, you're good to go!  The program will automatically update according to your preference in the **Tools > Options > Updates** menu.  (Make sure you've selected update notifications for the **stable and beta releases** or **stable, beta, and developer releases** track.)

If you want to manually download a fresh copy of the beta, [**click here**](https://github.com/tannerhelland/PhotoDemon/releases/download/v8.0-beta.1/PhotoDemon-8.0-beta.zip) or **[visit the download page](download/)**.

## Special thanks

**Thank you** to [all of PhotoDemon's Patreon supporters](https://www.patreon.com/photodemon), whose regular donations make this project possible.

Thank you as well to everyone who contributed bug reports, feature ideas, and feedback over the past few years.  I am grateful to all of you.  ❤

## Stable release

As with past releases, I'd like to allow several weeks for everyone to test this beta.  If no horrific issues are encountered, a stable release will follow sometime in **August 2020**.

If you encounter bugs or want to provide any other feedback, please [create a new issue on GitHub](https://github.com/tannerhelland/PhotoDemon/issues) as soon as possible.  Otherwise, I'll see you again in a few weeks with an official 8.0 release announcement!

## What's new and improved

In no particular order, here's some of the new stuff available in PhotoDemon 8.0.  Where applicable, I've tried to link each update to its relevant commit and/or feature request page on [GitHub](https://github.com/tannerhelland/PhotoDemon) or [Patreon](https://www.patreon.com/photodemon), or where applicable, an explanation of the feature somewhere like Wikipedia.

**Note**: this page contains animated images.  These animations are supported by all major mobile and desktop browsers, but if you're using an old browser (like Internet Explorer, [which should no longer be used](https://en.wikipedia.org/wiki/Internet_Explorer#End_of_life)), you may not see the animations.  Switch to a modern browser like Edge, Firefox, Safari or Chrome to see this page in its full glory!

First up, **Clone and Pattern stamp brushes** are now available.  I've [already written about these at-length](2020/01/31/new-clone-and-pattern-brushes), so visit that article for more details, but as a quick summary, a clone brush allows you to "paint" with a brush that's copied from one or more other images.  You can use this to remove blemishes from an image (by using an un-blemished region as the brush's source), or you can use it to paint various patterns, as in the sample animation below.  The new tools support brushes up to 1,000 pixels in size, and the usual range of brush features (including edge softness, opacity, blend mode, and more) are fully supported.

![screen-capture](media/images/pattern_brush.png)

A [new on-canvas **gradient tool** is also available](https://www.patreon.com/posts/26199115).  Gradients can be created in eight shapes with four edge-wrapping modes.  The tool supports real-time previewing and editing, even on very large (20+ megapixel) images.

![screen-capture](media/images/gradient_tool.png)
    
As part of the new gradient tool, a greatly expanded and updated **gradient editor** now ships with the program.  Choose from a built-in collection of stylized gradients, or create and save your own using the interactive editor:

![screen-capture](media/images/gradient_editor.png)
 
PhotoDemon now ships with [built-in support for **Adobe Photoshop (PSD) files** and their open-source equivalent, **OpenRaster (ORA) files**](2019/02/20/psd-support-now-available).  All Photoshop color models are supported, and images with embedded color profiles are automatically color-managed.  PhotoDemon can also export images to PSD and ORA format(s), with full support for layers, blend modes, and many other features, which makes it a breeze to copy your work between programs.

A [**new search tool** is available](https://www.patreon.com/posts/26904685) in the top-right corner of the main window.  Use it to quickly locate tools, adjustments, effects, or any other program feature.  (And if you're more of a keyboard person, Ctrl+F brings up the search bar automatically.)

![screen-capture](media/images/search_tool.png)

[**Canvas rulers** are now displayed automatically](https://www.patreon.com/posts/19178070), with support for measurements in pixels, inches, centimeter and millimeter, points, and picas.

[A **new Measure tool** has been added](https://www.patreon.com/posts/20466383), with built-in support for automatic horizon straightening:

![screen-capture](media/images/measure_straighten.png)

**Selection tools** have seen many improvements, including long-requested support for aspect-ratio locking:

![screen-capture](media/images/selection_aspect_ratio.png)

A [**new Effects > Render menu**](https://www.patreon.com/posts/29679659) is available, including new Cloud and Fiber rendering effects that make great use of the new gradient editor:

![screen-capture](media/images/render_clouds.png)

A new [**state-of-the-art Surface Blur tool**](https://github.com/tannerhelland/PhotoDemon/commit/4c081253b8b38538c6ba489dbf08f4ac00f3dc72) ships in the Effects > Blur menu.  This tool is built using technology from [a 2012 paper by Qingxiong Yang](https://www.semanticscholar.org/paper/Recursive-Bilateral-Filtering-Yang/b0382b60b30be6998a7d68fe62ea4377f8cb41f9), and it outperforms other popular photo editors by 1000% percent or more.  (As an example, applying a 100-pixel radius surface blur to a 12-megapixel iPhone photo takes just 3 seconds in PhotoDemon, and only one CPU core is used.  On the same photo, Paint.NET maxes out 4 CPU cores and take more than *40 seconds* to complete.)

A wide range of minor tools, commands, and effects have been added to further close the gap between PhotoDemon and pro tools like Photoshop.  These range from silly things like a new **Pixelate > Pointillize** effect, to new layer workflow tools (like dedicated **fit layer to canvas size** and **reverse layer order** commands), to a new **Compare Images** tool that auto-calculates [PSNR](https://en.wikipedia.org/wiki/Peak_signal-to-noise_ratio) between photos.  If you haven't already, explore the new Image and Layer menus to see all the new goodies available for experienced Photoshop users.

Many program features can now be [controlled via the keyboard](https://github.com/tannerhelland/PhotoDemon/issues/277), with widespread improvements to tab-order, UI rendering when keys are used for navigation, and keyboard interactions in general.

[Macros can now be directly created from your action history](https://github.com/tannerhelland/PhotoDemon/issues/265).  If you've just performed an awesome set of edits to an image, use the new **Tools > Create macro  > From history...** menu to save those actions to a macro file.  

All edit boxes now support [**simple math expressions**](https://github.com/tannerhelland/PhotoDemon/issues/263):

![screen-capture](media/images/math_expressions.png)

PhotoDemon now ships with [a **custom-built PNG engine**](https://github.com/tannerhelland/PhotoDemon/commit/8206ae38831bc095afa49556420bbb7d5c15778f).  This greatly improves performance when loading and saving PNG images, copying+pasting images between applications, and using file formats that directly embed PNG data (like OpenRaster files).  The new engine also produces smaller PNG files than other software by using advanced compression technology by [the open-source libdeflate library](https://github.com/ebiggers/libdeflate).

That custom PNG engine I just mentioned?  It was very helpful in adding **animated PNG support** to the project.  In fact, all animations on this page were created in PhotoDemon, by PhotoDemon, using the new **Tools > Animated screen capture** menu.  (Unlike animated GIFs, animated PNGs support 16-million colors, high-resolution timestamps, and potentially smaller file sizes.)

Similarly, [**animated GIF files** are now supported](https://github.com/tannerhelland/PhotoDemon/issues/278)!  Animations can be previewed right inside the main window, using the Navigation panel in the top-right.  Create your own animated images by using the new **File > Export > Animated GIF** and **File > Export > Animated PNG** menus.

[**Windows icon (ICO) files** are now fully supported](https://github.com/tannerhelland/PhotoDemon/issues/300).  Icon frames are loaded as separate layers, and when exporting ICO files, PhotoDemon can auto-generate as many icon frame formats as you request, in both legacy (uncompressed bitmap) and modern (PNG) formats.  Even better, beginners can just select which Windows version they want to target, and PhotoDemon will figure out what frames to generate for you.

[Layers can now be split out into individual images](https://github.com/tannerhelland/PhotoDemon/commit/7395bd5fdb98900367071c438e7b5b8c1d24b53c), edited at will, then reassembled back into their original image.  This makes some complex editing tasks much easier.

The batch processor now supports **drag+drop from Windows Explorer when creating a batch process list**.  This makes it a snap to add complex collections of files or folders.

More than a dozen Adjustment filters have been **rewritten for improved quality** across a wide range of photography styles.  The **Auto-Correct** and **Auto-Enhance** tools now produce faster, subtler results, particularly on skin-tones, while standard adjustments like **Exposure** and **Gamma** received updated user interfaces to make them even faster and simpler to use.

Many program behaviors now support **customization via prompts**.  For example, Drag-dropping images onto the canvas now displays a dialog for how to handle the dropped image, and you can always ask PhotoDemon to remember your preference in the future:

![screen-capture](media/images/drag_drop_prompt.png)

[Color palettes can now be applied from any palette file](https://github.com/tannerhelland/PhotoDemon/commit/51762e02b98a9e7a0a7ff4d24017d2b84152189e) using the **Effects > Stylize > Palettize** menu.  Supported palette formats include [GIMP](https://github.com/tannerhelland/PhotoDemon/commit/51762e02b98a9e7a0a7ff4d24017d2b84152189e), [Adobe Photoshop](https://github.com/tannerhelland/PhotoDemon/commit/5656f65d5065986295ea6896b96c51e7871000a1), [Paint.NET](https://github.com/tannerhelland/PhotoDemon/commit/99424653df60bc64a9cfd029acc0f3b532a6b494), and [PaintShop Pro/JASC](https://github.com/tannerhelland/PhotoDemon/commit/43866448e32a5791e57d4e1146e96bed3cf26490).  Palettes can also be generated from any image and exported to all of these formats [using the new **File > Export > Palette menu**](https://github.com/tannerhelland/PhotoDemon/commit/2182f6c3e855502d31e5fb707c747da3293df414).

Dozens of effects have received large performance and feature updates.  Nearly all **transform, distort, and artistic filters** have been rewritten for improved speed, while noise removal tools like the **Median filter** are now significantly faster at large radii and/or on large images.  (These improvements were made possible by a number of new effect engines, including a [multiresolution wavelet optimizer](https://en.wikipedia.org/wiki/Discrete_wavelet_transform).)

PhotoDemon now provides a [**high-speed perfect color matcher**](https://github.com/tannerhelland/PhotoDemon/commit/398d589944f5e0a5ff75ea8556cea5424898a253) using [KD-trees](https://en.wikipedia.org/wiki/K-d_tree).  This improves performance on many adjustments and effects, and it also improves performance when saving images to certain file formats (especially palette-based formats, like GIF).

**Saved adjustment and effect presets** can now be [edited, deleted, or rearranged to your liking](https://github.com/tannerhelland/PhotoDemon/commit/da788898f1c70c46b9528acd627e6441dd067ec3).

Using the program in languages other than English no longer incurs minor UI performance penalties, thanks to a new custom-built [Boyer-Moore text matching engine](https://en.wikipedia.org/wiki/Boyer%E2%80%93Moore_string-search_algorithm).

The **color selector panel** of the main window now provides a list of recently used colors at the bottom of the panel:

![screen-capture](media/images/new_color_selector.png)

...and the color selector can also be switched to [a new "use palette from file" mode](https://github.com/tannerhelland/PhotoDemon/commit/904b1c6d5b72a9e4488648f50bcebe6bb51a2080), including auto-matching colors to their nearest palette equivalent when using the color selector tool:

![screen-capture](media/images/color_selector_palette.png)

Speaking of the right-side toolbar, [**all panels can now be resized to your liking**](https://github.com/tannerhelland/PhotoDemon/commit/20556e3f1eda1e34e984f79b1e879dadbe37400e):

![screen-capture](media/images/resize_panels.png)

Want to quickly strip all metadata from an image?  Just [use the new **Image > Metadata > Remove all metadata** tool](https://github.com/tannerhelland/PhotoDemon/commit/d0f9f7ffff5b76aabfd8de7a54e5154a0528001c).

As part of PhotoDemon's long-running commitment to user privacy, **photodemon.org has been migrated to a secure ([https](https://en.wikipedia.org/wiki/HTTPS)) server**.  All PhotoDemon update checks and downloads are now served exclusively over secured connections.

Tools that use random numbers now support [**a new UI for entering random seed values**](https://github.com/tannerhelland/PhotoDemon/commit/90e02d57dc7cc741db7f5aef276b2aaecccb30d9) (inspired [by Minecraft](https://minecraft.gamepedia.com/Seed_(level_generation)), of all things).  This allows you to recreate "random" effects identically across multiple images.

Various improvements have been made to **running PhotoDemon on OSX and Linux via [Wine](https://en.wikipedia.org/wiki/Wine_(software))**, including fixing a number of Wine-specific UI problems.

As part of a new initiative to make PhotoDemon as stable as possible, [**debug logging now auto-activates** whenever a program crash is detected](https://github.com/tannerhelland/PhotoDemon/commit/50cb4c85d2982feb4ab4c46d4f033c2ac73c78ee).  You can always [send those debug logs directly to me](https://photodemon.org/about/) to help solve any problems you encounter.

Oh boy, this list of changes is already insanely long, but my list of improvements still has another 50+ items listed.  Rather than continue detailing various changes, let me just refer interested parties to [PhotoDemon's commit history](https://github.com/tannerhelland/PhotoDemon/commits/master).  It contains a list of all 1,000+ changes since the last stable release!

## In conclusion

I can't thank you enough for sticking with me through the past 2.5 years.  During PhotoDemon 8.0's development cycle, I've become a father, survived a pandemic (well, at least so far), replaced both a failed hard-drive and failed power supply on my aging development PC (thank goodness for backups), [started a Patreon initiative to support PhotoDemon's ongoing development](https://www.patreon.com/photodemon), and consistently missed my goal of providing you with regular updates.  I'll try to do better with PhotoDemon 9.0... but first, maybe I should just focus on getting 8.0 out the door.  ;)

If you have any questions, comments, or feedback on this 8.0 beta, [please let me know](about/).  I am so grateful to everyone who contributed to this release, whether through Patreon, GitHub, or by sending good old-fashioned emails.  A full list of contributors to this release is available on [the Contributors page](contributors/), or in the **Help > About menu** of PhotoDemon itself.

Please let me know how the 8.0 beta works for you, and best wishes for a happy and healthy rest of your summer.
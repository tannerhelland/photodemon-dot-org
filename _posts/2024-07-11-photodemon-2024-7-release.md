---
author: tanner_h
date: 2024-07-11 08:00:00+00:00
layout: post
slug: photodemon-2024-7
title: PhotoDemon 2024.7 is here
excerpt: A new PhotoDemon release is here!  As part of a commitment to more frequent releases, PhotoDemon now uses calendar versioning.  The new 2024.7 release includes many new features and improvements, including JPEG-XL support, PDF support (import only, export coming soon!), "magnetic" object snapping and smart guides, a greatly expanded `File > Export` menu, improved PSD compatibility, Japanese language support, and much more.
---

![screen-capture](media/images/photodemon_2024.6.png)

## Overview

After more than a year of work, PhotoDemon 2024.7 is available to download. Highlights of this release include JPEG-XL support, PDF support (import only, export coming soon!), "magnetic" layer snapping and smart guides, an expanded `File > Export` menu, improved PSD compatibility, Japanese language support, and much more.

Like all PhotoDemon releases, PhotoDemon 2024.7 runs on any Windows PC sold in the past 20 years.  All modern versions of Windows (XP through the latest Windows 11 insider builds) are fully supported.

## Download the new release

If you already have a copy of PhotoDemon, you're good to go!  PhotoDemon will automatically update according to the preference set in your `Tools > Options > Updates` menu.

If you want to manually download a fresh copy, **[click here](https://github.com/tannerhelland/PhotoDemon/releases/download/v2024.7/PhotoDemon-2024.7.zip)** or **[visit the download page](download/)**.

## Special thanks

This release exists thanks to many wonderful contributors who donated money, time, and feedback to the project. 

If you find PhotoDemon useful, **[please consider making a small donation](donate/)**.  Your support makes this 100% free, 100% open-source project possible.

**[Thank you especially to all of PhotoDemon's Patreon supporters](https://www.patreon.com/photodemon)**.  Thank you also to everyone who makes a [one-time donation](donate/).

Finally, thank you to everyone who contributed translations, bug reports, ideas, and feedback to this release.  I am grateful to all of you.  ❤

## Why is PhotoDemon's version number so big?

If you use PhotoDemon's nightly builds, you know that new features arrive all the time, but converting that steady stream of nightly updates into new stable releases has always been challenging.

Going forward, I am committed to more frequent PhotoDemon releases.  As part of this commitment, I have switched PhotoDemon to **calendar versioning**.

**[Calendar versioning](https://calver.org/)** attempts to make version numbers more meaningful.  Instead of incrementing numbers on a whim, calendar versioning simply uses the year and month of release.  This makes it trivial to know when an application was last updated, and in my case, it spares me needing to save up enough changes to warrant "major" version number changes.

Because this version released in July 2024, PhotoDemon's new version number is 2024.7.

This release includes a number of smaller features and improvements that have been available for some time in nightly builds.  Some of the larger features originally planned for "PhotoDemon 10.0" are still under construction, and these will ship incrementally throughout the second half of this year.

I look forward to sharing more stable releases with you in the coming months!

## What's new and improved in this release

### Import PDF documents

PhotoDemon can now import PDF documents as if they were image files.  Each page can be imported to its own layer.

Detailed control is provided over document size and resolution...

![pdf-import-size](media/images/pdf-import-1.png)
*(The PDF in these examples is [the free print-and-play PDF of the "Village Pillage" card game](https://boardgamegeek.com/boardgame/247342/village-pillage).)*

...which pages you import (including arbitrary page ranges)...

![pdf-import-pages](media/images/pdf-import-2.png)

...and document rendering settings, including full support for annotations, page transparency, and antialiasing.

![pdf-import-rendering](media/images/pdf-import-3.png)

PDF export is still a work in progress.  It will arrive in a future release.

### Save and load JPEG-XL images

JPEG-XL images (.jxl) may eventually become the next-generation replacement for traditional JPEG images.  The JPEG-XL format provides higher quality than traditional JPEGs at potentially smaller file sizes.  JPEG-XL also supports a variety of new features, including HDR, animations, and more.

Unfortunately, like all attempts to replace the venerable JPEG format, the JPEG-XL format is extremely complex and ever-evolving.  Support for the format in other software is mixed, and some companies ([Google, notably](https://arstechnica.com/gadgets/2023/04/free-software-group-decries-google-dropping-space-saving-jpeg-xl-format/)) have dropped support due to ongoing problems.  At this point, no one knows if JPEG-XL will ultimately replace JPEGs or if it will remain an academic curiosity.

One of the biggest problems with the current JPEG-XL reference library is that errors can [completely crash both the library any apps using it](https://github.com/libjxl/libjxl/issues/1450), a problem that has existed for years.  The format also has much larger memory and performance needs than traditional JPEGs, so it is best used on higher-end devices.

With these caveats in mind, you can now load and save JPEG-XL files in PhotoDemon.  To prevent the JPEG-XL reference library from crashing PhotoDemon itself, JPEG-XL support is available as a separate, optional install.  If you are on a compatible operating system (Windows 7 or later) and you try to load or save a JPEG-XL file, PhotoDemon will offer to download and configure a portable copy of the JPEG-XL reference library.  This one-time download will permanently enable JPEG-XL support for that PhotoDemon instance.

If you choose to enable JPEG-XL support, PhotoDemon can periodically look for updated copies of the library.  It will prompt you for updates (when interacting with JPEG-XL images) as your PhotoDemon settings allow.  This should lead to improved JPEG-XL compatibility and performance over time.

### Additional image format improvements

PDFs and JPEG-XL images are not the only new formats supported by this release.  Additional improvements include:

- [WBMP images](https://en.wikipedia.org/wiki/Wireless_Application_Protocol_Bitmap_Format) can now be [imported and exported](https://github.com/tannerhelland/PhotoDemon/commit/b31d68a56d773440e6b482fbbcc136110489e56d).  (This format is ancient and not especially relevant in 2024, but Photoshop supports it natively so PhotoDemon should too!)
- [XBM images](https://en.wikipedia.org/wiki/X_BitMap) can now be [imported](https://github.com/tannerhelland/PhotoDemon/commit/a1b3e225631f77b176df520d430ad08657ba8981).  (This format is ancient and not especially relevant in 2024, but GIMP supports it natively so PhotoDemon should too!)
- Photoshop (PSD) file support continues to [improve with every release](https://github.com/tannerhelland/PhotoDemon/commit/8a7bd8120aad2ce73922fb4b277fce3fe7f6a663).
- [Lossless JPEG (JPEG-LS)](https://en.wikipedia.org/wiki/Lossless_JPEG) support has been expanded and improved.
- OpenRaster (ORA) and comic book archives (CBZ) now support [Zip64-encoded files](https://github.com/tannerhelland/PhotoDemon/commit/9fcbf98c3e517c7c29bffd55fba99398008d3092).
- SVG support has seen a number of [performance and feature improvements](https://github.com/tannerhelland/PhotoDemon/commit/36aa245e7cc2b1051f775efe60299679ed13ac2e), and SVGs can now be [batch-converted to other formats](https://github.com/tannerhelland/PhotoDemon/commit/d69936f3fde1535c8bb9c17305aba6061c9cd4eb).
- EMF and WMF images now support [custom size at import-time (and batch process support)](https://github.com/tannerhelland/PhotoDemon/commit/18812e6ef7d552b3da6ce430cbb0613316e8e63e).
- Icon (ICO) files have seen many improvements, including [quality improvements and new features](https://github.com/tannerhelland/PhotoDemon/issues/453) when creating icons from scratch.
- WebP images received [security and performance improvements](https://github.com/tannerhelland/PhotoDemon/commit/71062a92848d80df593f8f4b7767f9d3e472c21a).
- Like JPEG-XL images, AVIF images also lean on third-party libraries (due to the complexity of the format).  PhotoDemon can also auto-update the required AVIF libraries [independently from PhotoDemon itself](https://github.com/tannerhelland/PhotoDemon/commit/4256c717019c7f8d5ba61cb7946bd45bd1d1c347).

### "Magnetic" snapping and smart guides for the **Move** tool

Precisely aligning layers is now much easier, thanks to the addition of "magnetic" snapping and smart guides.

This is one of those features where an image is probably worth a thousand words:

![snap-and-smart-guides](media/images/photodemon-2024-snap-and-smart-guides.png)

"Magnetic" snapping works by automatically aligning layer boundaries (and/or center lines, optionally) to other nearby objects.  It works on all layer types and can align to canvas edges, nearby layers, or object center lines.  (Each of these options can be independently toggled from the `View > Snap to` menu.)

"Smart guides" are the blue lines that appear when an object is snapped.  They display which boundaries are being snapped together.  You can toggle these from the `View > Show extras > Smart guides` menu.

*All* snapping options can be toggled on/off using the `View > Snap` menu.

### **Move** tool can now show distances

In conjuction with snapping and smart guides, the `Move tool` can now show precise distances when moving objects:

![show-distances](media/images/photodemon-2024-show-distances.png)

This feature can be enabled independently of snapping, using the `Move tool > other options > show distances` check box.

In related news, the `show layer boundaries` setting has moved from the `Move tool` to the `View > Show extras > Layer edges` menu.  This matches Photoshop's behavior, and now allows you to see layer boundaries even when using other tools.

### Redesigned and expanded **File > Export** menu

The `File > Export` menu is greatly improved in this release:

![file-export](media/images/photodemon-2024-file-export-menu.png)

The old format-specific animation menus have been condensed into a single `Export > Animation` menu, and new options exist for exporting the current image to a standalone file, or individual layer(s) to standalone files.

Exporting the current image to file does *not* update its save state (so if it has changes, you will still receive a "do you want to save changes" warning when you close it).  This is useful for saving an image to a layered format while you work, but periodically exporting it to a flat or lossy format like JPEG.

Exporting layers to file provides many options for how the layers are exported:

![export-layers](media/images/photodemon-file-export-layers.png)

This feature was designed to be similar to Photoshop's implementation, and it is especially useful for tasks like exporting all frames from an animation, or all pages from a PDF, to individual image files.

(In similar news, the `Layer > Add > From file` menu now supports adding multiple layers at once, so you can easily re-assemble separate image files into a single layered image.)

### **File > Save** and **File > Save as** improvements

The `File > Save` and `File > Save as` menus are possibly the most important menus in an application, and PhotoDemon's `Save/Save as` menus have picked up some new smarts since the last release.

[Manually entered file extensions are now detected](https://github.com/tannerhelland/PhotoDemon/issues/472), and PhotoDemon will automatically redirect the save operation to the appropriate save format.  This means you no longer need to interact with the file format dropdown if you don't want to.

Additionally, the `Tools > Options` menu now provides [additional control over `Save as` filename behavior](https://github.com/tannerhelland/PhotoDemon/commit/4630df0eb9d0524919eafb8e527f6531db5bd1f2).  You can now set `Save as` to automatically increment the target filename (e.g. if `image file.png` exists, PhotoDemon will suggest `image file (2).png`), or simply reuse the last filename as-is.  The same option exists for `File > Save` operations. 

### Right-click menus for the layer toolbox

As has long been requested, PhotoDemon now provides a comprehensive right-click menu for the layer toolbox:

![export-layers](media/images/layer-toolbox-right-click.png)

It's a little silly that it took me so long to add this feature, but in my defense, the toolkit PhotoDemon is built with does not support Unicode text, so I had to write a right-click menu system from scratch in order to display languages like Japanese or Chinese.  

Anyway, you should know the official PhotoDemon motto by now - better late than never!

### New **Advanced text layer** features

PhotoDemon provides two text tools: a "basic" one that relies on native Windows text rendering, and an "advanced" text tool that uses a custom renderer with many additional features.

The `advanced text tool` now supports justified text alignment, rendering text outline and fill in either order (outline above or below fill), and additional antialiasing settings to bring it closer to parity with Photoshop's text tool.

I am also actively working on "styles" support for both text tools, which will allow you to save all text settings as singular presets.  Unfortunately, this feature isn't quite ready for release, but look for it later this year.

### Many updates to localization files and features

Like every new PhotoDemon release, all language files have all seen numerous updates and improvements thanks to many generous volunteers.  Thank you to everyone who contributes to PhotoDemon's extensive localization support.

This is also the first PhotoDemon release to ship with full Japanese language support.  Thank you to Kenji Hoshimoto for this contribution!

## Additional upgrades and improvements.

Those are some of the biggest improvements available in PhotoDemon 2024.7, but they are far from the only ones.  

Here is an abbreviated list of other highlights in the 2024.7 release.

- Copy + Paste now [retains editable text layers](https://github.com/tannerhelland/PhotoDemon/commit/c4beae550d38554b5c71b6bc3c4cbe0f67eda776).
- A number of UI animations now [use adaptive frame rates](https://github.com/tannerhelland/PhotoDemon/commit/5f52283f29fe27c7b652d9309ec3dd3b4f2902e5) for more fluidity on high-end systems, and better responsiveness on low-end systems.
- Rulers (and distance displays on the Move tool) can now use [`Percent` as a measurement option](https://github.com/tannerhelland/PhotoDemon/commit/406fd150d5eb1e44d32655e2b12725df72798087).
- The main window now allows you to [drag+drop files onto more UI targets](https://github.com/tannerhelland/PhotoDemon/commit/c75966872d7347d15cf483aefef3beb9345f31cb).
- ["Behind" is now available as a blend mode](https://github.com/tannerhelland/PhotoDemon/commit/c3840d940ba19700cf652693ff327cf6c912e6d1), allowing you to paint "behind" a given layer.
- The 3rd-party ExifTool library (used to handle image metadata) has seen many updates, and it is now capable of [in-place upgrades](https://github.com/tannerhelland/PhotoDemon/commit/e2b011560e8b4793c36b39688550d340610f58c3).
- `Layers > Add > from File` now supports adding multiple files at once
- 32-bit Photoshop filters have received [expanded support](https://github.com/tannerhelland/PhotoDemon/commit/4d3c2a8319bdfc0ecbc0f0c0e07a6904fb36830d).
- The `Hand tool` now natively supports [arrow key movement](https://github.com/tannerhelland/PhotoDemon/commit/39a39f4f9bbd6a950c46bdaf5e54202320d95e8e).
- `Effects > Transform > Perspective` now supports [custom forshortening](https://github.com/tannerhelland/PhotoDemon/commit/27f6d12242fad25e14b0226831d88fdd4ee7dc31).
- Running PhotoDemon under Linux has improved thanks to [better Wine support](https://github.com/tannerhelland/PhotoDemon/commit/b8ee65f3276c577a683259022bad22d5d064736f).
- Windows XP support [has improved](https://github.com/tannerhelland/PhotoDemon/commit/8b339413e4604a568c829df9f42e52aacd786d51), particularly its behavior with 3rd-party libraries that have XP-specific limitations.

### Other

These are just the highlights of version 2024.7.  For an exhaustive list of changes, [review the project's commit log](https://github.com/tannerhelland/PhotoDemon/commits/main).  

## In conclusion

Thank you for using PhotoDemon.  

I am so grateful to everyone who contributed to this release, whether through Patreon, GitHub, or by sending old-fashioned emails.  A full list of contributors is available on [the Contributors page](contributors/), or in the `Help > About` menu of PhotoDemon itself.  PhotoDemon's ever-expanding community is full of amazing individuals, and they are the reason I can give the software away for free.

If you find PhotoDemon useful, **[please consider making a small one-time donation](donate/)** or **[joining our Patreon family](https://www.patreon.com/photodemon)**.  I'd love to add you to the next contributor list.

I hope you enjoy version 2024.7, and I'll be back later this year with even more new features and improvements.  See you then!
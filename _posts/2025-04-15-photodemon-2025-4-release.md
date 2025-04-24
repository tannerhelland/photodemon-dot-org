---
author: tanner_h
date: 2025-04-24 08:00:00+00:00
layout: post
slug: photodemon-2025-4
title: PhotoDemon 2025.4 is here
excerpt: PhotoDemon 2025.4 is now available.  This release brings a new on-canvas crop tool, size and location persistence for effect and adjustment dialogs, support for custom font folders, bad file extension repair, reduced memory usage, import/export support for legacy PCX images, and much more.
---

![screen-capture](media/images/photodemon-2024-5-with-text.png)

## Overview

PhotoDemon 2025.4 is here!  Highlights of this release include a new on-canvas crop tool, size and location persistence for effect and adjustment dialogs, support for custom font folders, bad file extension repair, reduced memory usage, import/export support for legacy PCX images, and much more.

Like all previous PhotoDemon releases, version 2025.4 runs on any Windows PC sold in the past 20 years.  All modern versions of Windows (XP through the latest Windows 11 insider builds) are fully supported.

## Download the new release

If you already have a copy of PhotoDemon, you're good to go!  PhotoDemon will automatically update according to your preference in the `Tools > Options > Updates` menu.

To manually download a fresh copy, **[click here](https://github.com/tannerhelland/PhotoDemon/releases/download/v2025.4/PhotoDemon-2025.4.zip)** or **[visit the download page](download/)**.

## Special thanks

This release exists thanks to many wonderful volunteers who donated time, translations, money, and feedback to the project. 

If you find PhotoDemon useful, **[please consider making a small donation](donate/)**.  Your support makes this 100% free, 100% open-source project possible.

**[Thank you especially to all of PhotoDemon's Patreon supporters](https://www.patreon.com/photodemon)**.  Thank you also to everyone who makes a [one-time donation](donate/).

Finally, thank you to everyone who contributed translations, bug reports, ideas, and feedback to this release.  I am grateful to all of you.  ❤

## What's new and improved in this release

### On-canvas crop tool

PhotoDemon has always supported cropping images via its (many!) selection tools.  But new to this release is a dedicated on-canvas crop tool, available from the *layout* section of the toolbox:

![screen-capture](media/images/photodemon-crop-tool.png)

Like other on-canvas tools, a lot of work went into making this new crop tool both convenient and precise.  You can click-drag to create (and edit) a crop rectangle, and you can set precise position and measurement values with the text boxes in the top toolbar.

![screen-capture](media/images/crop-tool-edit.webp)

The user interface highlights different edit points in real-time, and you can modify the "highlight" or "shield" effect (as Photoshop calls it) to your liking.  Here's what a 50% "white" highlight looks like, for example:

![screen-capture](media/images/crop-tool-highlight-settings.png)

As you've noticed in the above screenshots, you can also overlay different guides on the crop region.  This can help you achieve that perfect [rule of thirds composition](https://en.wikipedia.org/wiki/Rule_of_thirds), for example:

![screen-capture](media/images/crop-tool-guides.png)

If you need to crop to a fixed size or aspect ratio, worry not - preset lists are available for both:

![screen-capture](media/images/crop-tool-presets.png)

These lists are generated from simple text files saved in the `Data/Presets/Template_Sizes.txt` and `Data/Presets/Template_Aspects.txt` files.  You can freely modify those files to your liking, removing or adding whatever presets you like!  (Note that you can add presets in pixel or "real-world" measurements - both are supported.)

Finally, there are a number of additional options for the crop process itself.  You can choose to crop the entire image or just the active layer.  Activate the `allow enlarging` toggle to let the crop rectangle float outside the image, so you can crop to a new, **larger** size.  

When cropping the full image, you can also toggle `delete cropped pixels`.  When this is turned *off*, image boundaries are adjusted to achieve the crop, but no actual pixels are removed.  (This is also called **non-destructive cropping**.)

The new crop tool incorporates many ideas from other popular photo editors, and I hope it helps you crop images more easily than ever.

### Size and location persistence for effect and adjustment dialogs

This new feature is simple: when you interact with any `Adjustment`, `Effect`, or `File > Save` window, PhotoDemon now remembers any size and position changes you make to that window.  Those changes are automatically restored the next time you use that tool.

If you like your effect windows huge and weirdly positioned, this feature's for you!

### Improved and expanded user preferences

In recent years, PhotoDemon's `Tools > Options` dialog has become a little too cluttered for my liking.  On old PCs, preferences might take several seconds to load, and individual panels had become overwhelmed with toggles.

So in this release, I redesigned the `Tools > Options` dialog and rewrote the backend that manages it.  Individual panels are now loaded on-demand, which makes the dialog's startup time basically instantaneous, even on very old PCs.

While I was here, I took the time to organize the various panels into more modern and manageable categories:

![screen-capture](media/images/photodemon-tools-options.png)

The new organization allows individual pages to "breathe" a little better, and it's also given me room to add some long-requested options from users.

Some of the new user options in this release include:

#### Custom fonts

Some users like to keep their system font list clean, so rather than add new fonts to Windows itself (which in turn adds them to *all* software on your PC), they instead manage custom fonts manually, adding them only to software that actually uses it.

![screen-capture](media/images/tools-options-fonts.png)

In this release, you can now tell PhotoDemon about those secret font folders with the `Tools > Options > Fonts` panel.  Any folders added here (and their sub-folders!) will be automatically scanned for font files.  Even very large font collections shouldn't impact app startup performance, but I'd love more feedback on this from users with insane font lists!

Part of the way this performance is achieved is by forcing an app restart after font collection changes.  I apologize for this inconvenience, but it was a necessary evil for handling large font collections in a speedy way.

Since I now have a place to stick weird font options, I thought I'd expose a silly option that has existed for awhile but was previously kept hidden - the ability to change PhotoDemon's interface font.  If you really want it, you can now get the Comic Sans interface of your dreams:

![screen-capture](media/images/oh-no-comic-sans.png)

This won't work with *all* fonts due to inherent font spacing issues, but for accessibility reasons, I'm glad users now have a way to manipulate it.

#### Custom menu mnemonics handling

Menu mnemonics are the letters you can type (while holding down the `Alt` key) to access individual menus, like `Alt+F` for `File`.  PhotoDemon generates these mnemonics automatically at run-time for your current language.

Before, English equivalent mnemonics were automatically shown for languages without 1:1 keyboard-letter mapping.  Now, however, you can manually turn on or off the display of mnemonics for *any* language:

![screen-capture](media/images/japanese-mnemonics.png)

#### Splash screen

If you don't like PhotoDemon's minimalist splash screen (the logo that pops up while the app initializes), you can now turn it off.  This doesn't affect program startup time, but it provides a "cleaner" appearence for those who frequently start/stop the app.

#### Mousewheel behavior

By default, PhotoDemon uses the mousewheel for scrolling, and Ctrl+Mousewheel for zooming.

You can now swap this behavior from the `Tools > Options > Input devices` panel.

#### Disable import-time color management entirely

PhotoDemon has long supported embedded color profiles to improve (or rather, "make accurate") the display of various image formats.  But in a classic case of "no good deed goes unpunished", there are a *lot* of images out there with malformed color data.  Images with bad profiles can do more harm than good, so I've now added a toggle for disabling import-time color management entirely.

(There are actually two toggles for this - one for disabling standard ICC color profiles, and another for disabling format-specific color profile data, like the sRGB, gamma, and/or chromaticity chunks available to PNG files.)

#### In conclusion (new program options)...

So those are a few of the `Tools > Options` updates in this release.  If you want yet *other* ways to customize PhotoDemon, [let me know](https://photodemon.org/about/#contact) and I'll see what I can do!

### Reduced memory usage

As part of PhotoDemon's ongoing goal to be the smallest, lightest photo editor money (can't) buy, this release includes an exciting new memory management feature.

When working with multiple images, PhotoDemon can now automatically suspend "inactive" images to disk.  This effectively allows you to work with an unlimited\* number of images at once.

*(\*In this context, "unlimited" technically means "limited only by available hard drive space.")*

Let's say that you have a giant image open - "Large Image 1" - and you then load another giant image - "Large Image 2".  While "Large Image 2" loads, if PhotoDemon detects that available RAM is becoming problematic, it will silently migrate all (or some) of "Large Image 1" pixel data out to the hard drive, compressing the data as it does so using the high-speed [lz4 compressor](https://github.com/lz4/lz4).

If/when you switch from "Large Image 2" back to "Large Image 1", any suspended pixel data is silently retrieved.  And, if necessary, portions of "Large Image 2" may then be migrated out to disk to ensure seamless behavior if available RAM remains low.

PhotoDemon also activates this new memory manager when RAM runs low under other circumstances, like effects or adjustments that require multiple copies of the active layer.  You don't have to do anything - it all happens behind-the-scenes.

If you have a modern PC with tons of RAM, this feature may never kick in.  But if, like me, you still use ancient PCs for some tasks, this feature will allow you to work with larger images, and larger image *collections*, than ever before.

### Bad file extension repair

Images downloaded from the Internet are frequently labeled incorrectly.  For example, an image named "Image.JPG" may actually be in PNG format.  In previous releases, wrong file extensions could sometimes trip up PhotoDemon, especially if it assigned a mislabeled image to the wrong third-party library.

This behavior has been fixed in the current release and PhotoDemon will now *always* double-check file contents before assuming a given image format.  But why not take this a step further and **fix** incorrectly labeled images so that they don't break *other* software!

In PhotoDemon 2025.4, if you load a mislabeled image, a message like this now appears:

![screen-capture](media/images/bad-file-extension.png)

Click "Yes" to fix the faulty file once and for all, or "No" to leave the file as the mislabeled monster it is.

### Improved single-pixel painting for pencil, brush, and eraser tools

PhotoDemon supports [sub-pixel positioning](https://en.wikipedia.org/wiki/Subpixel_rendering) for its paint tools.  When zoomed-in, this allows you to place paint strokes anywhere "inside" a given pixel, and PD automatically figures out the antialiasing required to make that positioning work.

But sometimes - like when doing pixel art - you don't want this behavior, which is why PhotoDemon now provides an "align to pixel grid" toggle for the pencil, paintbrush, and eraser tools.

Here's an animation of the old behavior (still available when "align to pixel grid" is turned **off**:

![screen-capture](media/images/paint-align-grid-off.png)

Here's an animation of the new behavior (available when "align to pixel grid" is turned **on**:

![screen-capture](media/images/paint-align-grid-on.png)

This new toggle provides absolute precision when working at a single-pixel level, but you can turn it off whenever you want smooth, natural-looking brush strokes.

### Import/export support for legacy PCX images

With every new release, I try to do at least one deep dive into an image format I haven't studied before.  This time, it was the venerable [PCX image file format](https://en.wikipedia.org/wiki/PCX).

PhotoDemon previously used a third-party library for PCX support, but in this release, it now has its own PCX decoder and encoder.  The new encoder+decoder pair is significantly faster, covers many more PCX variants (including the multi-page DCX extension), and can even fix some PCX images that were incorrectly encoded by other software.

While PCX is rarely used for new images (modern formats like PNG are far superior), Photoshop still supports PCX for both loading and saving, so I'm happy to report that PhotoDemon now covers it well too.

### Magnetic "angle snapping" when rotating layers

Last year, the 2024.7 release added support for "magnetic snapping" when positioning layers.  In this release, snapping support expands to include layer *rotation* too.

Hold down the `Shift` key to snap a layer to 15° increments, or toggle the new 90°, 45°, and 30° angle options in the `View > Snap to` menu to always snap when rotating.  (There is also a new "angle snap distance" preference in the `Tools > Options > Input devices` panel.)

### Many updates to localization files and features

Like every new PhotoDemon release, language files have seen numerous updates and improvements thanks to many generous volunteers.  Thank you so much to everyone who contributes to PhotoDemon's extensive localization support!

Notably, this is also the first PhotoDemon release to ship with support for the following languages:

[Czech, by LsGeorge](https://github.com/tannerhelland/PhotoDemon/commit/25f917d76fc1e91ea2a9d6f8622f855fd18f23fd).<br />
[Ukranian, by bulbaka](https://github.com/tannerhelland/PhotoDemon/commit/10103eec88c613183bf42923f6c888548ea60d1d).

Thank you these authors for their contributions, and an extra big thank-you to everyone who continues to offer their localization services with each new PhotoDemon release.

## Additional upgrades and improvements.

Those are some of the biggest improvements available in PhotoDemon 2025.4, but alongside the usual bug-fixes and performance enhancements, a few other new features snuck in.

Other highlights of this release include:

- All `File > Export` dialogs are now [freely resizable at run-time](https://github.com/tannerhelland/PhotoDemon/commit/24a11abec30bf4a12ea212ca7620f05a94d38721).
- Improved and expanded [`Adjustments > Color > Colorize` tool](https://github.com/tannerhelland/PhotoDemon/commit/53af99703975d51fdb89052424fcca64dd06ebfa).
- Improved [`Adjustments > Histogram > Display histogram` tool](https://github.com/tannerhelland/PhotoDemon/commit/7b050c43a9a3225fdc2a0a3dd1c02bbfecce78dc).
- Improved startup performance thanks to [on-demand loading of some non-essential plugins](https://github.com/tannerhelland/PhotoDemon/commit/c15d9407ff0a27129ca3c550d74887ff512125e0).
- Improved quality of [automatically exported icon frames](https://github.com/tannerhelland/PhotoDemon/commit/ccf1e08d5b4adbca3f714d48106cbc4a3c4b9fed).
- Reduced memory usage of [animation effect and viewer dialogs](https://github.com/tannerhelland/PhotoDemon/commit/a66339bd8d256bddee032356bb87e142369685cf).
- The titlebar now displays [the canonical file format of an image](https://github.com/tannerhelland/PhotoDemon/commit/6c943787d47f97f490234617375946321e8946d9), instead of just its file extension.
- Improved [AVIF image support](https://github.com/tannerhelland/PhotoDemon/commit/e65d318d185194eb670bca03ce5ca5f794d99d9a).
- Improved [JPEG-XL coverage](https://github.com/tannerhelland/PhotoDemon/commit/8ccde59df461a7e4565420538b725f1b80254cd8), thanks to third-party [libjxl library](https://github.com/libjxl/libjxl) updates.
- Improved [PaintShop Pro (PSP) format coverage](https://github.com/tannerhelland/PhotoDemon/commit/888d42b19eeb0ec77e22d5676717d704ee981bdc).
- Improved [WebP coverage](https://github.com/tannerhelland/PhotoDemon/commit/59722aafd31f7aee380cd6c0d867f53728dcabe6), thanks to third-party [libwebp library](https://chromium.googlesource.com/webm/libwebp) updates.
- Improved [PDF coverage](https://github.com/tannerhelland/PhotoDemon/commit/4d15e287259b909318534194035c5c70b15428e5), thanks to third-party [pdfium library](https://github.com/chromium/pdfium) updates.
- Improved [SVG coverage](https://github.com/tannerhelland/PhotoDemon/commit/9282e7631e25bdb6e13ac52065ec35d597b40ad9) thanks to third-party [resvg library](https://github.com/linebender/resvg) updates.
- [UI improvements on high-DPI displays](https://github.com/tannerhelland/PhotoDemon/commit/39185953c290ce7901eef087d733b60efb6a5d88).

### Other

For an exhaustive list of changes and bug-fixes, [review the project's commit log](https://github.com/tannerhelland/PhotoDemon/commits/main).  

## In conclusion

Thank you for using PhotoDemon.  

I am grateful to everyone who contributes to each release, whether through donations, Patreon, GitHub, or by sending old-fashioned emails.  A full list of contributors is available on [the Contributors page](contributors/), or in the `Help > About` menu of PhotoDemon itself.  PhotoDemon's ever-expanding community is full of amazing individuals, and they are the reason I can give this program away for free.

If you find PhotoDemon useful, **[please consider making a small one-time donation](donate/)** or **[joining our Patreon family](https://www.patreon.com/photodemon)**.  I'd love to add you to the next contributor list.

I hope you enjoy this release, and I hope to see you later this year with the next one.  
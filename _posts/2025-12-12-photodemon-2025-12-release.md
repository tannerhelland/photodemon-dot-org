---
author: tanner_h
date: 2025-12-12 08:00:00+00:00
layout: post
slug: photodemon-2025-12
title: PhotoDemon 2025.12 is here
excerpt: PhotoDemon 2025.12 is now available.  This release brings improved file format support (DDS, JPEG-2000, and PNG in particular), new viewport options, improved compatibility with Windows XP and 7, and numerous optimizations and bug-fixes.
---

## Overview

Let's squeeze one more PhotoDemon release into 2025, shall we?

PhotoDemon 2025.12 is now available.  I had hoped to have at least one major new feature ready before the end of the year, but I'm running out of time to make that happen... so I've decided to play it safe and postpone any major new features to early next year.  

Instead, today's 2025.12 release collects a number of file format improvements, important bug-fixes, localization updates, and a few minor new features.  (On the plus side, a lack of major overhauls means this release should be *extra* stable!)

Like all previous PhotoDemon releases, version 2025.12 runs on any Windows PC sold in the past 20 years.  All modern versions of Windows (XP through the latest Windows 11 insider builds) are fully supported, and this release even includes a few dedicated compatibility improvements for both Windows XP and Windows 7.  

(Yes, PhotoDemon is still tested on those operating systems.)

## Download the new release

If you already have a copy of PhotoDemon, you're good to go!  PhotoDemon will automatically update according to your preference in the `Tools > Options > Updates` menu.

To manually download a fresh copy, **[click here](https://github.com/tannerhelland/PhotoDemon/releases/download/v2025.12/PhotoDemon-2025.12.zip)** or **[visit the download page](download/)**.

## Special thanks

This release exists thanks to many wonderful volunteers who donated time, translations, money, and feedback to the project. 

If you find PhotoDemon useful, **[please consider making a small donation](donate/)**.  Your support makes this 100% free, 100% open-source project possible.

**[Thank you especially to all of PhotoDemon's Patreon supporters](https://www.patreon.com/photodemon)**.  Thank you also to everyone who makes a [one-time donation](donate/).

Finally, thank you to everyone who contributed translations, bug reports, ideas, and feedback to this release.  I am grateful to all of you.  ❤

## What's new and improved in this release

Let's assume you're all as busy as I am this time of year, so instead of a huge essay with a billion photos, let's revert to a simple, text-only list of noticeable improvements in this release.  

(Thank you for allowing me to be lazier than usual this time around.)

### File formats

This release includes major updates for a few different file formats.

#### Overhauled JPEG-2000 support

PhotoDemon now ships with [the OpenJPEG library](https://www.openjpeg.org/) for greatly expanded and improved JPEG-2000 support.  JPEG-2000 images load up to *10x* faster than previous builds, broken JP2 images can now (often) be recovered, memory usage when importing/exporting JP2 images is way down, and a ton of JP2-related bugs and compatibility failures have finally been resolved.

After aggressively testing PhotoDemon's JPEG-2000 implementation against the official [OpenJPEG image conformance suite](https://github.com/uclouvain/openjpeg-data), I feel confident stating that PD provides more comprehensive JPEG-2000 coverage than any other open-source photo editor.  Here are some of my developer notes from [the main JP2 compatibility commit](https://github.com/tannerhelland/PhotoDemon/commit/20f16fa57deda8b2c5c3b178b702dd78a704ba76):

- Grayscale, RGB/A, and YUV/A color formats are all supported.
- Images tagged as "unknown" are now imported successfully in *most* cases (using heuristics to "guess" how to treat the image data).
- Per-channel subsampling is now supported.
- All color-depths (called "precisions" in JP2 parlance) are now supported.
- Signed color definitions are now supported.
- Many improvements have been made to import performance, and load time of large JPEG-2000 images is often reduced 90+% vs previous releases.
- Embedded ICC profiles (color management) are now supported.
- "Broken" or partially-broken JP2 images can often be largely recovered by the new import process.
- Unicode filenames and paths are now supported.
- Mislabeled JP2 files (bad file extensions) are now properly identified, and we'll offer to fix.
- Images that exceed 32-bit memory limits can now be auto-downsized and imported into PD at a workable fraction of their original size.
- Weird edge-case behavior with nonstandard subsampling, color handling, and other quirky states has been overhauled to match OpenJPEG's reference library behavior wherever possible.  This means PD now produces identical results in conformance suite handling to OpenJPEG's reference handler.

Thank you to everyone who submitted JPEG-2000-related bug reports in previous builds.  Your comments helped motivate this overhaul!

#### New DDS (DirectDraw Surface) support

**The good news:** PhotoDemon now uses the excellent [DirectXTex library](https://github.com/microsoft/DirectXTex) for DDS import and export.  This brings huge compatibilty improvements, and PD should now successfully handle almost every variety of the (very complex) DDS format.  For the first time, PhotoDemon can also *export* DDS images.

**The bad news:** like many modern tools, DirectXTex is only compatible with 64-bit operating systems.  PhotoDemon automatically handles interoperability for you, but full DDS support will only be activated on 64-bit systems.

#### PNG coverage for the new 2025 specification update

In 2025, the W3C [officially endorsed an updated PNG specification](https://www.w3.org/news/2025/portable-network-graphics-png-specification-third-edition-is-now-a-w3c-recommendation/).  This specification formalized some popular-but-unofficial-features (like animated PNGs, which PhotoDemon has supported for years).  But it also included a few new features, like [color space chunks for modern HDR data](https://github.com/w3c/ColorWeb-CG/blob/08d0981ae5163b76275d0777d0166eab85396371/hdr-in-png-requirements.md).

PhotoDemon's PNG engine [now supports these new features](https://github.com/tannerhelland/PhotoDemon/commit/ef4f3fe27c43e525c036a3a0aee7268babc1b75d), making it one of the first open-source photo editors compatible with these updates.  This update also ensures that PNG images continue to look the same in PD as they do in your web browser.

#### Other file format improvements

Updates to relevant 3rd-party libraries bring improved coverage for WebP, HEIF/HEIC, and PDF files.  Coverage and bug-fixes for BMP-format images [has also improved](https://github.com/tannerhelland/PhotoDemon/commit/4ae73e9a1954cf635cb250e41d99ac4a1be0c071).

### Front-end improvements

- New [`Image > Show in file manager`](https://github.com/tannerhelland/PhotoDemon/commit/4c915eaf774394f6454c71c854554ebe6df8bd83) menu 
- New user preference to toggle automatic [`activate Move tool after paste`](https://github.com/tannerhelland/PhotoDemon/commit/12d4665392936b99bebefac265a8bc80cec15ed2)
- [`150% zoom` is now available](https://github.com/tannerhelland/PhotoDemon/commit/82497553e43474b7d8cb39d6abef9f3eba6bfdbc) on the main viewport
- New option to [`reset all "remember my choice"`](https://github.com/tannerhelland/PhotoDemon/commit/dfbc963ee5478b101671149c7f2ad3c806995f8a) options
- New [`View > Center image in viewport`](https://github.com/tannerhelland/PhotoDemon/commit/afa29e783d37f648f3952d5c75db40b7bf80b7af) menu
- New [default hotkeys for rotate image left/right](https://github.com/tannerhelland/PhotoDemon/commit/15d0ab8afd568ee74f50957770631fba07dddbe6) (Ctrl+\[ and Ctrl+\], respectively)
- Improved tracking for [custom hotkey combinations](https://github.com/tannerhelland/PhotoDemon/commit/391f1f5975f72292d79e4e578ba06171df01eaea)
- Crop tool: `ENTER` and `ESC` hotkeys are now enabled for [committing or clearing the active crop](https://github.com/tannerhelland/PhotoDemon/commit/c95a594a4e1ec453288dd0aca831e2843d6815cb)
- The [3rd-party libraries dialog has been hardened](https://github.com/tannerhelland/PhotoDemon/commit/2fcbe32d8385fb391478e13a5bec6b147a9b0ccf) to prevent click-happy users from accidentally disabling essential libraries.

### Back-end improvements

- Critical bug-fixes for users in [Taiwanese and other `Traditional Chinese` language locales](https://github.com/tannerhelland/PhotoDemon/commit/1d54ddda88efea4cb034a719a96473e5f5dba0d4).  A huge shout-out and thank-you to [笙歌](https://github.com/love80312) for their help with this!
- Ongoing improvements to XP and Windows 7 compatibility, particularly regarding [3rd-party library behavior](https://github.com/tannerhelland/PhotoDemon/commit/2a89bab62b445d4ab6f5aad206be6b74fbf152c2).
- A number of bug-fixes for [high-DPI displays](https://github.com/tannerhelland/PhotoDemon/commit/2f4838472f537d41ece02c544357a088f60f4497)
- Improved [program shutdown performance](https://github.com/tannerhelland/PhotoDemon/commit/b01e52ee15466f0c6c1028b573ed33ca37b2051f)
- Corrupt preferences files can now (usually) be [detected and silently reset](https://github.com/tannerhelland/PhotoDemon/commit/b2d89b9a91aacbae458deb198df787b4bf6271a5), preventing crashes on subsequent sessions if you yank out PhotoDemon's USB drive without safely ejecting it.
- Fixes for [Unicode captions not displaying](https://github.com/tannerhelland/PhotoDemon/commit/0ce428153de701865f265301c98c34551b1a55be) correctly in some esoteric dialogs
- Fixes for the main window's caption [not diplaying changed file formats correctly](https://github.com/tannerhelland/PhotoDemon/commit/9b112d7ff241b8ad3af4e8946170baffe4e07130) after a `File > Save As` operation.

### Many updates to localization files and features

Like every new PhotoDemon release, language files have seen numerous updates and improvements thanks to many generous volunteers.  A huge thank-you to everyone who contributes to PhotoDemon's extensive localization support.

Notably, this is also the first PhotoDemon release to ship with support for the following languages:

[Turkish, by Berat Tezer](https://github.com/tannerhelland/PhotoDemon/commit/3855401363138bdfcb192a2f5ae29e703c27c623).<br />
[Hungarian, by Bánszki István](https://github.com/tannerhelland/PhotoDemon/commit/3622ff627c5f9690761231d099e694ee38eab17e).<br />
[Romanian, by L. Ivanov](https://github.com/tannerhelland/PhotoDemon/commit/1f9f7dc67f3bc96ea7a0852187ce5d3fa774f1e4).<br />

Thank you these authors for their contributions, and an extra big thank-you to everyone who continues to offer their localization services with each new PhotoDemon release.

### Other

For an exhaustive list of changes and bug-fixes, [review the project's commit log](https://github.com/tannerhelland/PhotoDemon/commits/main).  

## In conclusion

Thank you for using PhotoDemon.  

I am grateful to everyone who contributes to each release, whether through donations, Patreon, GitHub, or by sending old-fashioned emails.  A full list of contributors is available on [the Contributors page](contributors/), or in the `Help > About` menu of PhotoDemon itself.  PhotoDemon's ever-expanding community is full of amazing individuals, and they are the reason I can give this program away for free.

If you find PhotoDemon useful, **[please consider making a one-time donation](donate/)** or **[making small monthly donations on Patreon](https://www.patreon.com/photodemon)**.  I'd love to add you to the next contributor list.

I hope you enjoy this release, and I hope to see you next year with an even bigger one.  
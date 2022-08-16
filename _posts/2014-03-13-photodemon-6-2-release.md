---
author: tanner_h
date: 2014-03-13 15:21:01+00:00
layout: post
slug: photodemon-6-2-release
title: PhotoDemon 6.2 release
excerpt: After five months of hard work, PhotoDemon 6.2 is officially ready for download.
redirect_from:
  - /726/photodemon-6-2-release/
---

After five months of hard work, PhotoDemon 6.2 is officially ready for download.

Functionally, this release is very similar to [the 6.2 beta](2014/02/21/photodemon-6-2-beta-is-live) that launched three weeks ago.  The primary changes from the beta are completed language translations, and miscellaneous bug fixes.

For those upgrading directly from version 6.0, you're going to notice a lot of improvements!  You can find a full write-up (with screenshots) [here](2014/02/21/photodemon-6-2-beta-is-live), but for those in a hurry, here is an abbreviated list of updates:

  * Brand-new interface, including image tabs, dockable toolbars, and a greatly improved status bar

  * Completely color-managed workflows, including comprehensive support for embedded profiles in all relevant image formats (JPEG, PNG, TIFF, etc), and per-monitor profile support via the Tools -> Options menu.

  * New hardware-accelerated viewport engine

  * Spanish and Portuguese translations.  These are primarily machine-based at present, so if you can help improve them, please [contact me](about/contact/).

  * New color selector, with support for RGB/HSV, CSS/HTML hex, and grabbing colors from the screen

  * Comprehensive resize options, including support for percent-based resize, print units (inches and cm), and embedded DPI

  * All-new JPEG dialog, with live quality previews, automatic quality handling, custom presets, and per-image metadata options

  * Live previews for all potentially lossy export dialogs, including JPEG, JPEG-2000, JPEG-XR, and WebP

  * WebP and JPEG-XR support (import and export)

  * Autosaves are now provided

  * New Hand tool for quickly scrolling large images

  * New [Content-Aware Resize tool](http://en.wikipedia.org/wiki/Seam_carving)

  * Improved tool previews, including support for previewing either the full image, or the image at 100% zoom plus scrolling

  * Asynchronous metadata handling for much faster image loading and saving

  * Improved Screen Capture tool, including per-window capture

  * The "Black and White" tool has been redesigned so that any black/white conversion supports reduction to any number of gray shades.  A full-featured dithering engine has also been added, with support for ten different dithering algorithms.

  * New "Replace Color" tool makes it easy to change the color of clothing, hair, or any other item in a photo.

  * New "Chroma Blur" tool is helpful for noise removal; only color data is blurred, but luminance is left unchanged.

  * A new File -> Revert option makes it easy to quickly restore the on-disk version of an image.

  * All scroll controls in the program have been redesigned against a new scroll bar class.  This should improve a number of old bugs where the mouse would get "stuck" on a scroll bar control.  Improved precision also means tools can offer more detailed settings.

  * Many minor improvements to metadata handling.  Things like color space and software are correctly marked in exported files, and changes to metadata importing have made it much faster, while still providing the most comprehensive listing possible.

  * Lots of improvements for XP users, including live selection feathering, Recent File icons, and overall stability improvements.

  * Rewritten Recent File handler.  You can now keep as many files as you want in the Recent Files menu, and a "Load all recent files" option makes it easy to restore an entire group of photos for editing.

  * Selected areas can now be exported as their own image using the Select -> Export menu.

  * Windows 7 and 8 users can now use the integrated Windows Print dialog for much better printing support and features.

  * When applying actions to a selection, the preview window will now show the selection as it appears on the image.  This is better than the old system of just showing the selected area, as you can now see what impact the edits will have on the final image.

  * The Preferences -> Advanced panel now displays a report of what functions are hardware accelerated on your system.  This should be fairly standard across systems and OSes, but for curious power users, the data may be interesting.

  * Windows 7 and 8 users now benefit from taskbar progress reports while edits are processing.

  * Update checks are now asynchronous, meaning they happen in the background without slowing down the main program.

  * When reducing a semi-transparent image to 8bpp (e.g. GIFs), you can now choose any background color for compositing semi-transparent pixels.

  * As always, there are many more miscellaneous bug-fixes, performance improvements, and tool enhancements.  For a detailed list of updates since 6.0, please visit [PhotoDemon's commit log](https://github.com/tannerhelland/PhotoDemon/commits/main).

## Enjoy!

I hope you enjoy version 6.2.  If you have any feedback, please [send me a message](about/contact/).  I'd love to hear from you.

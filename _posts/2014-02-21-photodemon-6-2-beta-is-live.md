---
author: tanner_h
date: 2014-02-21 16:17:08+00:00
layout: post
slug: photodemon-6-2-beta-is-live
title: PhotoDemon 6.2 beta is live
excerpt: I have two primary goals with the 6.2 release - modernizing PhotoDemon's interface, and preparing the program for Layers support.  
redirect_from:
  - /681/photodemon-6-2-beta-is-live/
---

## Overview

It's that time again: PhotoDemon 6.2 is nearing release, and it's time for beta testing!  A few minor items still need addressing, but the program is 99% ready for release, so anyone who can give it a whirl is greatly appreciated.

The 6.2 release cycle has been a bit different from past ones.  Historically, my work on PhotoDemon was guided by three things: adding core features present in other photo editors but missing in PD, adding things that sounded fun and/or interesting to develop, and adding things requested by users.  After a good number of features were completed, I'd call it a new version, and there was never much rhyme nor reason to it.

With 6.2, this helter-skelter development approach changed.  For the first time, I prepared a roadmap in advance, and stuck to it closely throughout the dev cycle.  This resulted in more focused development, and instead of a bunch of random new tools, this release includes a number of sweeping changes that improve whole swaths of the program.

There were two primary focuses of the 6.2 roadmap: modernizing PhotoDemon's interface, and preparing for Layers support.  I am happy to report that both of these goals have been met, and the full focus for 6.4 will be implementing said Layers.

But rather than focusing on the future, let's talk about this release.  For users upgrading from 6.0, here are all the neat improvements coming your way:

### Brand-new interface

![media/images/import/PD_6-2-beta-570x406.jpg](media/images/import/PD_6-2-beta.jpg)

The old MDI "floating-window" interface is gone for good.  In its place is a sleek, lightweight tabbed interface.  There are too many improvements to note, so let me just mention the biggest changes:

  * All loaded images are displayed in a tabstrip that can be freely shown/hidden, moved, and resized.  (I prefer the left-hand side, but you can stick it wherever you like!)  Unsaved images are marked with an asterisk, and image tiles can be hovered to see their full name and location.

  * All toolbars are docked by default, but you can switch them to free-floating mode if desired.  While floating, toolbars will remain semi-transparent until hovered.

  * A new, dedicated status bar provides quick access to zoom, image size, mouse coordinates, and relevant messages and progress updates.

The new interface was the single biggest project of this release cycle.

### Color-Managed Workflows

![media/images/import/Color_Managed_Workflow-570x394.jpg](media/images/import/Color_Managed_Workflow.jpg)

This was a huge project, and an exciting addition for both casual and professional users.  PhotoDemon now provides a fully color-managed workflow across the entire program (including the main viewport, all tool dialogs, and even small things like color selection windows!).  This means you no longer have to worry about making edits to an image, only to have those edits look completely different on other people's monitors.

Images with embedded ICC profiles are now processed according to those profiles, and color management is implemented for all ICC-supporting formats (including JPEG, PNG, and TIFF, among others).  

If you've already set up proper monitor color management through Windows, PhotoDemon will automatically detect and use those settings.  For professional users who desire more control, you can also specify per-monitor profiles through the Preferences dialog.  PhotoDemon will automatically track which monitor it is on, and apply the proper profile accordingly.

### New color selector

![media/images/import/PhotoDemon_Color_Selection-570x317.jpg](media/images/import/PhotoDemon_Color_Selection.jpg)

This is a huge improvement over the stock Windows color selection dialog (which hasn't changed in 20 years).  Many thanks to the open-source photo editor GIMP, whose color selector served as the primary inspiration for this one.  

Direct RGB and HSV modification is supported, and live color bars show the impact of modifying any individual value.  Hex input is also supported, a list of recent colors is automatically saved, and a "grab color from screen" tool allows you to pick colors from anywhere on your desktop - even from other software!

(And for pro users, note that the entire dialog is color-managed.)

### New Viewport Engine

All things viewport-related should now be much faster, particularly on low-end machines and when editing images with transparency.  Additionally, hardware acceleration is now used for many viewport elements (if supported by your video card).

### Comprehensive Resize options

![media/images/import/PhotoDemon_Resize_Dialog1-570x462.jpg](media/images/import/PhotoDemon_Resize_Dialog1.jpg)

In past versions, PhotoDemon always required you to resize images using pixel values - but no more!  All resize dialogs (Image Resize, Canvas Resize, etc) now support resizing by pixels, percent, or even physical units like inches and cm.

In conjunction with this new feature, resolution data is automatically read from image files, and PhotoDemon will automatically write updated resolution data to exported files.

### New Undo/Redo engine

A new Undo/Redo engine is much faster and slimmer than past version, so any action that creates Undo data (including selections) should now perform significantly better.

### All-new JPEG dialog

![media/images/import/PhotoDemon_Export_JPEG_Final-570x302.jpg](media/images/import/PhotoDemon_Export_JPEG_Final.jpg)

![media/images/import/PhotoDemon_Export_JPEG_Final_Metadata-570x302.jpg](media/images/import/PhotoDemon_Export_JPEG_Final_Metadata.jpg)

As the most common image format, JPEGs deserve special consideration.  PhotoDemon's new JPEG export dialog provides many new features, including:

  * Live previews, so you no longer have to blindly guess at image quality

  * Automatic quality detection.  If selected, PhotoDemon will automatically test different JPEG quality levels until it finds one that meets your request.

  * Quick access to metadata, including the option to change metadata handling for a given image (such as stripping all metadata)

  * Support for presets, so you can quickly access customized settings in the future.  For example, I use presets like "Web Quality + remove private metadata" vs "Print Quality and strip all metadata".

  * Last-used settings are automatically remembered.

### Live previews for all potentially lossy export dialogs

JPEG-2000, JPEG-XR, and WebP formats now provide live previews in their export dialogs.

### New WebP and JPEG-XR support (import and export)

I don't know if anyone uses these formats, but they're there if you need 'em!

### New Autosave engine

![media/images/import/PhotoDemon_Autosave_Dialog-570x448.jpg](media/images/import/PhotoDemon_Autosave_Dialog.jpg)

I hope no one ever needs to make use of this, but just in case: in the event of a power failure, critical error, or other problem, PhotoDemon can now auto-recover whatever image(s) you were last working on.  Because this feature is based off the Undo/Redo engine, it requires no extra overhead (so program performance is unchanged), and no "timer" system.  The last change you made will always be what is found and restored.

The feature also works for images that have never been saved (like images pasted from the clipboard, or freshly acquired from a scanner).

### New Hand tool for scrolling large images

On the primary window, images that exceed the size of the viewport can now be scrolled by use of a Hand tool.  As before, mousewheel (plus Ctrl and Shift modifiers), scroll bars, and zoom hotkeys are also available.

### New Content-Aware Resize tool

![media/images/import/Broadway_tower_before-570x386.jpg](media/images/import/Broadway_tower_before.jpg) 

*Initial image, courtesy of Wikipedia ([http://en.wikipedia.org/wiki/File:Broadway_tower_edit.jpg](http://en.wikipedia.org/wiki/File:Broadway_tower_edit.jpg)).*

![media/images/import/Broadway_tower_normal_resize-570x570.jpg](media/images/import/Broadway_tower_normal_resize.jpg) 

*Image resized using a standard resize algorithm.  Note the undesirable stretching.*

![media/images/import/Broadway_tower_content_aware_resize-570x570.jpg](media/images/import/Broadway_tower_content_aware_resize.jpg) 

*The same image, resized using a content-aware algorithm.  Uninteresting features (like sky and grass) have been shrunk preferentially, leaving the interesting features (person, castle) intact.*

Content-aware resize is a cutting-edge technique for resizing images without distorting their contents.  It was recently added to PhotoShop in version CS4, and nearly all free photo editors lack a comparable tool.

But not PhotoDemon!  The new content-aware resize tool supports both shrinking and enlarging, and as mentioned above, it supports resizing by percent, pixel, or physical units (inches, cm).

### Improved tool previews

![media/images/import/updated-vignetting-tool-570x325.jpg](media/images/import/updated-vignetting-tool.jpg)

Tool dialogs now provide an option to toggle between "fit whole image on screen" and "show image at 100%".  When showing the image at 100%, the image can be click-dragged, so even large images can be fully inspected.

Also, the preview tool now supports "click to set a center point" behavior when relevant.  This new feature affects nearly a dozen tools, mostly in the Distort menu, and makes it simple to do things like rotate the image around an arbitrary point.

### Asynchronous image metadata handling

Parsing image metadata occupies a huge chunk of the image load process.  To improve performance, metadata handling is now completely asynchronous, meaning it will operate in parallel with the rest of the image loading process.  This greatly improves load performance for all images, and is especially crucial during batch processing.

Similarly, when saving an image to file, metadata embedding is also handled asynchronously, so you can continue working while metadata processing completes.

### Improved Screen Capture tool

![media/images/import/PhotoDemon_Screenshot_Dialog-570x321.jpg](media/images/import/PhotoDemon_Screenshot_Dialog.jpg)

Individual program windows can now be selected from a list, with or without their window decorations (titlebar, borders, etc).  Of course, the full desktop can still be captured with or without PhotoDemon present on the screen.

### Minor improvements worth noting

![media/images/import/PhotoDemon_BlackAndWhite_Dialog-570x331.jpg](media/images/import/PhotoDemon_BlackAndWhite_Dialog.jpg)

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

  * As always, there are many more miscellaneous bug-fixes, performance improvements, and tool enhancements.  For a detailed list of updates since 6.0, please visit [PhotoDemon's commit log](https://github.com/tannerhelland/PhotoDemon/commits/master).

## Known bugs

  * Translations for some languages are missing phrases for new tools and features.  These will be added before release.

## Official release timeline

Barring any major bugs, the official 6.2 release should happen within several weeks.  Feature-wise, it will be identical to this beta release.  The only changes will be minor bug fixes and performance improvements.  Automatic update notifications for existing PhotoDemon installs will also go live at that point.

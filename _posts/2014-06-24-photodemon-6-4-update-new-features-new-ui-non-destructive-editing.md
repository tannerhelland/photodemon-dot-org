---
author: tanner_h
date: 2014-06-24 15:28:42+00:00
layout: post
slug: photodemon-6-4-update-new-features-new-ui-non-destructive-editing
title: 'PhotoDemon 6.4 Update: New Features, New UI, Non-Destructive Editing'
excerpt: Layers are now a fully integrated part of PhotoDemon's workflow.  All the expected features are there - variable opacity, 24 blend modes, drag/drop layer reordering, flattening and merging, etc.  In the PhotoDemon tradition, there are also some extra amenities, like support for one-click merge up or merge down operations, automatically fitting the canvas to the active layer or all layers, trimming empty space from images, and other little things...
redirect_from:
  - /775/photodemon-6-4-update-new-features-new-ui-non-destructive-editing/
---

If you've been waiting for new news about PhotoDemon 6.4, thank you for your patience!  This has been a longer release cycle than usual, but I think the wait will be worth it, because the next release (version 6.4) will have some **really** amazing improvements.

## Layers and Non-Destructive Editing

I've already talked a little bit about [the new Layers support](2014/05/02/photodemon-6-4-layer-preview) coming to PhotoDemon, but now that I've had to time to refine many layer-related features, let me talk about them a bit more.  As always, you can try these new features by [downloading PhotoDemon's latest nightly build](download/).  Nightly builds should be quite stable by this point, so I'd love to hear your thoughts!

![media/images/import/PD_6-4-570x368.jpg](media/images/import/PD_6-4.jpg)

Layers are now a fully integrated part of PhotoDemon's workflow.  All the expected features are there - variable opacity, 24 blend modes, drag/drop layer reordering, flattening and merging, etc.  In the PhotoDemon tradition, there are also some extra amenities, like support for one-click merge up or merge down operations, automatically fitting the canvas to the active layer or all layers, trimming empty space from images, and other little things that keep with our tradition of providing a powerful but intuitive interface.

In the screenshot above, you can also see a new "quick fix" tool section at the bottom of the screen.  This area is still under development, but there are already some helpful options for rapidly adjusting an image (or layer) without delving into the menus.  I'm currently working on a few more tools for the Quick Fix section, but you can already try out Exposure, Contrast, Clarity, and Vibrance adjustments, which all work in real-time.

Even better, all quick-fix adjustments are _non-destructive_.  This means that you can modify them at any time without harming the image, or using Undo to return to a previous state.  

As an example, if you increase an image's exposure, sharpen it, then decide that you initially raised the exposure too much - no problem!  PhotoDemon's new non-destructive rendering pipeline means you can change any of the quick-fix settings at any time, without losing image data or Undoing to a previous image state.

Some other technical details, for those who are interested: PhotoDemon provides fully automatic management of layer boundaries.  Boundaries are automatically extended or shrunk to fit the relevant layer area, which is not just convenient, but it also makes PhotoDemon's saved files much smaller than files in comparable formats (XCF, PDN), because dead space is auto-trimmed whenever images are written to file.

Layers are also created with alpha channels by default, making it trivially easy to work with transparency, even when starting from a 24bpp base.  When using the move/resize layer tool, the cursor can automatically select the layer beneath a mouse click, saving you from constantly returning to the Layers dialog to switch between them.  A hover menu on each layer toolbox panel also allows for one-click merge up, merge down, duplicate, and visibility toggle functions.

![media/images/import/PD_6-4_non-destructive-resizing-570x392.jpg](media/images/import/PD_6-4_non-destructive-resizing.jpg) 

Also added to the non-destructive feature set is layer resizing.  Layers can be resized at any time without the changes being made permanent.  Any edits made in the background - adjustments, effects, whatever - will be applied to the _original_ image data, so if you resize the later again in the future, there will be no loss of quality.

This provides excellent flexibility when working with layered images, as you no longer have to worry about harming image data when making small changes or adjustments.

## Interface Improvements

From the screenshots above, you might have noticed some much-needed improvements to PhotoDemon's user interface.  Chief among these is an overhaul of the slider controls used throughout the program.

![media/images/import/PD_6-4_new_sliders-570x325.jpg](media/images/import/PD_6-4_new_sliders.jpg)

Besides looking much better, the new sliders support a variety of appearances, which should make various settings much more intuitive.  Other interface changes are still being implemented, but I hope that small improvements like the new slider make the program much more pleasant to use.

## Updates to Existing Tools

![media/images/import/PD_6-4_new_levels-570x305.jpg](media/images/import/PD_6-4_new_levels.jpg) 

*PhotoDemon's new Levels dialog*

![media/images/import/PD_6-4_new_curves-570x372.jpg](media/images/import/PD_6-4_new_curves.jpg) 

*PhotoDemon's updated Curves dialog*

Moving on from Layers, many of PhotoDemon's most important Adjustment tools have seen large improvements since version 6.2.  The Levels dialog has been completely reworked from scratch, with new support for per-channel level corrections, click-to-set shadow and highlight tones, and a [best-in-class Auto Levels feature](https://github.com/tannerhelland/PhotoDemon/commit/b047c67b4cc5948d657f98b360db44f21c6ff017).

The Curves dialog has also seen improvements, with per-channel Curve support, and a live display of current node settings.

![media/images/import/PD_6-4_new_emboss-570x327.jpg](media/images/import/PD_6-4_new_emboss.jpg)

![media/images/import/PD_6-4_new_enhance_edges-570x322.jpg](media/images/import/PD_6-4_new_enhance_edges.jpg)

![media/images/import/PD_6-4_new_rainbow-570x325.jpg](media/images/import/PD_6-4_new_rainbow.jpg)

Improvements are not just limited to core adjustments, either.  Many Effects tools have seen similar improvements, with expanded options, more intuitive dialogs, and both performance and accuracy improvements.  Above are some good examples of dialogs that have seen significant changes since version 6.2.

## New Tools and Features

No article is complete without a sneak peek at some of the new tools we've implemented.  In no particular order, here are some of the neat features coming to PhotoDemon 6.4.

![media/images/import/PD_6-4_split_toning-570x323.jpg](media/images/import/PD_6-4_split_toning.jpg) 

Dedicated split-toning tool

![media/images/import/PD_6-4_glass_tiles-570x325.jpg](media/images/import/PD_6-4_glass_tiles.jpg) 

New Glass Tiles effect

![media/images/import/PD_6-4_sunshine-570x325.jpg](media/images/import/PD_6-4_sunshine.jpg) 

New Sunshine effect

![media/images/import/PD_6-4_fragment-570x330.jpg](media/images/import/PD_6-4_fragment.jpg) 

New Fragment effect

![media/images/import/PD_6-4_lens_flare-570x325.jpg](media/images/import/PD_6-4_lens_flare.jpg) 

New Lens Flare effect

![media/images/import/PD_6-4_bilateral_smoothing-570x325.jpg](media/images/import/PD_6-4_bilateral_smoothing.jpg) 

New Bilateral Smoothing noise reduction tool

More tools are currently under construction, but this is a good sampling of the many cool things you can look forward to in the next release.

## The Little Things

As always, version 6.4 includes a ton of small features that may not make for great bullet points in an article like this, but taken together, they represent a much more fluid, enjoyable, and stable piece of software.  A few highlights:

- New Active Undo/Redo engine that saves only the bare minimum of changed information between actions.  This makes Undo/Redo data creation much faster, and much smaller on your hard drive.
- Improved status bar, with a dedicated "fit image on-screen" button, and a clickable "Resize Image" icon next to the image size display
- Much better drag/drop support, particularly from web browsers
- Arrow keys are now supported for all relevant tools, making it much easier to nudge or clear selections, or quickly change layers or modify layer opacity
- Overhauled interaction with the excellent [ExifTool metadata](http://www.sno.phy.queensu.ca/~phil/exiftool/) plugin.  Loading images with extensive metadata is now much faster and more reliable.
- Tools with color selection features will now live-update their previews, even when you are in the color selector dialog. 
- Mouse-wheel zoom will now zoom to the cursor location, instead of defaulting to position (0, 0)

And so much more.  If you ever have a small annoyance (or a big one) with a PhotoDemon feature, please let me know, and I'll do my best to rectify it quickly.  It's very important to me that the program avoids the small annoyances that bog down other software.

## Release Date

I'm afraid I still haven't decided on an official release date.  :(  My apologies for this!  Because Layers work was so extensive, I'm trying to do as much testing as possible to make sure the program is rock-solid.  This release is also laying the groundwork for paint tools, which makes it a crucial one, even if a lot of the most intense work is not immediately visible to end-users.

While you continue waiting (patiently) for a release date, please do feel free to play with [the latest development build](download/).  That's one of the great things about an open-source program like PhotoDemon - you don't have to wait for an official release to try out new features!

As always, comments, compliments, and criticisms welcome, and I hope you're as excited about version 6.4 as I am, even though the wait has been a long one...

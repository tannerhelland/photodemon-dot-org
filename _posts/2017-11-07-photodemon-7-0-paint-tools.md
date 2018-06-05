---
author: tanner_h
date: 2017-11-07 20:52:00+00:00
layout: post
slug: photodemon-7-0-paint-tools
title: 'PhotoDemon 7.0: new on-canvas paint tools'
excerpt: PhotoDemon 7.0 now ships with full-featured pencil, paintbrush, eraser, bucket fill, and color picker tools. If you've used paint programs in the past, you probably know what each of these tools do.  For first-timers, here's a quick run-down.
redirect_from:
  - /1606/photodemon-7-0-paint-tools/
---

*(This is part of a series about PhotoDemon 7.0.  For the full 7.0 article collection, visit [this page](2017/11/28/photodemon-7-0-release).)*

PhotoDemon 7.0 now ships with full-featured pencil, paintbrush, eraser, bucket fill, and color picker tools.

![media/images/import/Painting-570x397.gif](media/images/import/Painting.gif)   This is a short painting demo on a 12 megapixel base image, using 500-px brushes.  (This animated GIF only displays 8 frames per second, so actual painting is quite a bit smoother.)

If you've used paint programs in the past, you probably know what each of these tools do.  For first-timers, here's a quick run-down.

**Pencil tool:** Hard-edged brush with options for size, color, opacity, blend and alpha modes.

**Paintbrush tool:** Same features as the pencil tool, but with additional settings for brush softness, flow, and spacing.

**Eraser tool:** Same features as the paintbrush tool, but with the blend mode forced to "Erase" mode and alpha mode set to "Normal".

**Paint bucket:** Automatically fill similarly-colored regions of a layer or image.  Options include fill type (solid, pattern, gradient), blend and alpha mode, opacity, antialiasing, tolerance and comparison modes, global vs local sampling, and layer vs image fill.

**Color picker:** Select colors from the current layer or image.  Options include sample radius, sample layer vs merged, and color details in a variety of different color spaces.

![media/images/import/color_picker-570x397.jpg](media/images/import/color_picker.jpg) The new color-picker tool in action.  The panel at the bottom of the screen provides real-time feedback on colors as you move the mouse across the canvas.

You've probably seen "blend mode" options in a bunch of other photo editors, but what do I mean when I say that these tools also support different "alpha modes"?  Basically, layers and brushes can now use three different alpha channel modes, and this determines how transparency works during layer and brush compositing.  The three modes are "normal", "locked" - which protects the alpha channel against editing, and "inherit".  Alpha inheritance is [a concept I borrowed from Krita](https://www.extremraym.com/en/krita-2-9-2-top-features/#Layer_Inherit_Alpha), and it allows a layer or brush to "inherit" the opacity values of the layer beneath it.  This allows for very convenient clipping mask behavior while painting, as in the animation below.

![media/images/import/Alpha_inheritance-570x415.gif](media/images/import/Alpha_inheritance.gif)  The "Color" blend mode plus "Inherit" alpha mode allows me to quickly recolor this FireFox logo, without worrying about the underlying transparent areas.

Alpha inheritance works with both layers *and* brushes, so you can use it to make a layer "acquire" the shape of the layer beneath it.

![media/images/import/Alpha_inheritance_layers-570x392.gif](media/images/import/Alpha_inheritance_layers.gif)  In this short example, note how the top layer "inherits" the transparency data of the layer beneath it.

In a similar vein, "Erase" is not just a tool - it's actually a blend mode!  This means that you can "erase" a layer using another layer, as in the animation below.

![media/images/import/Erase_blendmode-570x392.gif](media/images/import/Erase_blendmode.gif)  The "erase" blend mode lets you use the contents of one layer to erase the contents of the layers beneath it.

I could spend a lot more time talking about paint-related features, but I still have quite a few release announcement articles to write.  So let me quickly dump some miscellaneous paint features in a list:

  * Paint brushes all provide dynamic, radius-accurate cursors.  No more guessing where paint will actually be applied.
  * Grain Extract and Grain Merge blend modes are now available, and supported by both brushes and layers.
  * Canvas "overscroll" is now supported.
  * Paint tools use a dynamic framerate approach, which allows very large brushes to be used even on very old PCs.  (Brushes are arbitrarily limited to 2000 pixels, but if users need bigger brushes, I can easily bump up the limit.)
  * As you'd expected, all paint tools work nicely with the selection engine, so you can easily restrict painting, erasing, and fills to specific image regions (animation below).

![media/images/import/paint_selection-570x397.gif](media/images/import/paint_selection.gif)  This is a short example of painting an active selection with an Overlay-mode.  All selection shapes and features are compatible with all paint tools.

All of the new paint tools are built on a custom paint engine that produces very fluid results on a wide range of PC hardware, including PCs without dedicated video cards.  If your PC has enough power to run Windows XP, it also has enough power to support PD's new paint tools, even on large images or at large brush sizes.

[Return to the main PhotoDemon 7.0 release announcement](2017/11/28/photodemon-7-0-release)

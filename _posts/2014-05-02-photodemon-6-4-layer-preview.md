---
author: tanner_h
date: 2014-05-02 14:57:43+00:00
layout: post
slug: photodemon-6-4-layer-preview
title: 'PhotoDemon 6.4 preview: Layers'
excerpt: Layers support has been one of the largest undertakings since PhotoDemon went public some 18 months ago, but so far progress has been smooth and steady.  Here are some of the Layers-releated features already available in the latest development build...
redirect_from:
  - /748/photodemon-6-4-layer-preview/
---

_Note: this blog post describes a work in progress. Features shown here may change before the next PhotoDemon release._

It's been just over a month since PhotoDemon 6.2 released, but a number of important changes have already hit PhotoDemon's development branch. Foremost among those changes is full support for image layers:

![media/images/import/PhotoDemon_64_Layer_Preview_11-570x363.jpg](media/images/import/PhotoDemon_64_Layer_Preview_11.jpg) 

*A snapshot of the current PhotoDemon 6.4 development build, showing a multilayer image with various blend modes, opacity, and more.*

Layers support has been one of the largest undertakings since PhotoDemon went public some 18 months ago, but so far progress has been smooth and steady.  If you'd like to test the latest development build, [head over to the Downloads page and click the "Latest Development Release" button](download/).  (Like all development releases, there will be some bugs and unfinished features - consider yourself warned!)

Here are some of the Layers-releated features already available in the latest development build:
	
  * Support for an unlimited number of Layers
  * Copy, Copy Merged, Paste as New Image, and Paste as New Layer are now available in the Edit menu
  * Layers can be reordered using the large arrow buttons on the Layer toolbox
  * Layers can be hidden or shown with a single click
  * Layers can be merged up, merged down, and duplicated using the hover buttons on the layer panel
  * Variable opacity and six layer blend modes are currently available.  (In the screenshot above, the Tardis wallpaper is demonstrating the "Soft Light" blend mode.)
  * Layered images can be resized, rotated, flipped and mirrored without flattening the image.  Many programs don't allow layered images to be arbitrarily rotated without first flattening the image, but PhotoDemon can do this without trouble!

![media/images/import/PhotoDemon_64_Arbitrary_Rotation_preview-570x325.jpg](media/images/import/PhotoDemon_64_Arbitrary_Rotation_preview.jpg)

*Here's an example of PhotoDemon rotating an image with five unique layers - no flattening required!*
	
  * A new Layers menu provides all the same options as the Layers toolbox, plus additional options like Flatten Image, Merge Visible Layers, and adding/removing individual layer's transparency.
  * Layers can be moved around the image canvas in real-time using the new "Move" tool.
  * Layered images can be saved to PhotoDemon's new layer-friendly file format (.PDI).
  * All items in the Selections, Adjustments, and Effects menus are in working order.  Adjustments and Effects always apply to the currently active layer, allowing you to edit each layer individually.

There are probably other items I'm forgetting, but this should give an idea of how much progress has been made over the past month.

Of course, much more Layers work is currently underway.  My current task is non-destructive Layer resizing, which will allow for resizing layers on-canvas in real-time, without harming the original layer contents.  Once this is complete, I've got a bunch of UI (user interface) work planned, which will hopefully improve the discoverability of PhotoDemon's many unique features.

Feedback and testing is always welcome, but please note that bugs are expected at this early stage of development.

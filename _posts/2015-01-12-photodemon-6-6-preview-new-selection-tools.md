---
author: tanner_h
date: 2015-01-12 17:46:35+00:00
layout: post
slug: photodemon-6-6-preview-new-selection-tools
title: 'PhotoDemon 6.6 preview: new selection tools'
excerpt: At long last, PhotoDemon now provides fully powered polygon, lasso, and magic wand selection tools.  As with other selection tools, non-destructive antialiasing and feathering are supported for all selection types.
redirect_from:
 - /934/photodemon-6-6-preview-new-selection-tools/
---

_Note: this article describes a work in progress. Features shown here may change before the next PhotoDemon release._

I hope everyone had a nice holiday season.  Work on PhotoDemon always slows a bit at the end of the year, but now that we're into January, I am back to working on PD whenever time allows.  A lot of great new features and improvements are already available in [the 6.5 development builds](download/) (which will eventually become the 6.6 stable release), and in this article, I'll be talking about three great new features in particular.

As always, you can download the latest development builds, updated nightly, from [the download page](download/).  As with the stable PhotoDemon releases, nightly builds do not require installation.  Just unzip the program folder, then click PhotoDemon.exe to begin.  

## Today's preview: three new selection tools

![media/images/import/PD_magic_wand_demo-570x328.jpg](media/images/import/PD_magic_wand_demo.jpg)  

PhotoDemon's new magic wand tool in action.  This image, and other images in the article, are courtesy Bing's Wallpaper of the Day feature. 

At long last, PhotoDemon now provides fully powered polygon, lasso, and magic wand selection tools.  As with other selection tools, non-destructive antialiasing and feathering are supported for all selection types.  (In the screenshot above, feathering has been activated to soften the edges of a magic wand selection.)

## Magic Wand selections

Let's talk about the magic wand tool first, because it's quite an improvement over the magic wand tool in other photo editors.  In the screenshot above, you can see a small circle near the center of the selection.  This is the current selected magic wand point.  You can click and drag that point (in real-time!) to preview the magic wand's capture area for other points, as demonstrated by the animated GIF below:

![media/images/import/PD_magic_wand_drag-570x372.gif](media/images/import/PD_magic_wand_drag.gif)  

To make capturing the "perfect" area easier, PhotoDemon's magic wand tool provides live previews when dragging the magic wand starting point.

You can also use the arrow keys for fine-tuned adjustments, which should make it much easier to capture exactly the area you want.

The magic wand supports global or contiguous capture.  (Global capture ignores continuity, and searches the entire image for matching pixels.)  You can also select from all layers or just the current one, and seven different comparison modes are provided, as seen in this screenshot:

![media/images/import/PD_magic_wand_comparison_modes-570x372.jpg](media/images/import/PD_magic_wand_comparison_modes.jpg) 

Comparison modes should be self-explanatory, except perhaps for Composite (which compares both color and alpha values), vs Color (which ignores alpha).

## Polygon selections

Like magic wand, the new polygon and lasso tools are also part of PhotoDemon's non-destructive pipeline.  After creating a polygon selection, you can drag individual points to get your selection "just right."

![media/images/import/PD_polygon_selection_edit-570x372.jpg](media/images/import/PD_polygon_selection_edit.jpg) 

In this screenshot, I've dragged the top-right polygon point to a new location.

This makes it trivial to adjust the selection, even after creating it.  

The polygon selection tool also supports the notion of "curvature", which means you can round polygon junctions and edges, instead of being limited to straight lines only:

![media/images/import/PD_polygon_selection_curvature-570x372.jpg](media/images/import/PD_polygon_selection_curvature.jpg) 

When curvature is cranked up to its maximum value, the selection area takes on a blob-like appearance.  Cardinal splines are used to calculate rounded polygon edges and junctions.

This feature makes it much easier to select non-rectangular objects, while still retaining the ability to edit the selection after it's been created.

## Lasso selections

The new lasso tool works exactly as you'd expect:

![media/images/import/PD_lasso_selection_demo-570x372.jpg](media/images/import/PD_lasso_selection_demo.jpg) 

The new lasso selection tool in action.  Lasso selections are auto-completed, and they can be moved to a new location after creation.

For those of us who don't have perfectly steady hands, the Backspace key can be used to retreat the lasso while drawing.  This makes it easy to correct mistakes, without having to recreate the entire selection from scratch.

All selection tools (except for magic wand) now support an Outline view mode, as you can see in some of the screenshots above.  For those who prefer the existing Highlight view mode, you can now choose your own highlight color:

![media/images/import/PD_oval_selection_green_highlight-570x372.jpg](media/images/import/PD_oval_selection_green_highlight.jpg)  

Here's a basic oval selection, using green as a Highlight color instead of the default red.

All Adjustment and Effect tools support the new selection types, and as with the old Square, Oval, and Line selection tools, you can save and load selections to file, to easily reuse them on other photos.  Selections of any type can also be grown or shrunk, inverted, or manually feathered at any radius by using the Select menu.

## Much more to come

Eagle-eyed readers may notice a number of other significant changes in the above screenshots, but I'll leave discussion of version 6.6's many other new features for future articles.  For now, know that you can play with version 6.6's new features by [downloading the latest nightly build](download/).  Coders are also welcome to peruse the latest source code on [PhotoDemon's GitHub page](https://github.com/tannerhelland/PhotoDemon), or view a detailed list of changes via [PhotoDemon's always up-to-date commit log](https://github.com/tannerhelland/PhotoDemon/commits/main).

In the coming weeks, I'll be previewing some of the other great new features slated for 6.6's.  Many thanks to all those who have contributed to version 6.6 so far, and if you have any suggestions after reading this article (or playing with the development build), please [get in touch](about/contact/)!

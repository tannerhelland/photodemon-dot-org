---
author: tanner_h
date: 2013-09-19 17:47:46+00:00
layout: post
slug: photodemon-6-0-beta-is-live
title: PhotoDemon 6.0 beta is live
excerpt: It's taken nearly six months, but PhotoDemon 6.0 is finally ready for release.  I've already talked about some of the great features this release includes, like powerful selection tools, metadata (EXIF) support, Curves and other new tools, but today I have some additional improvements to announce.
redirect_from:
  - /350/photodemon-6-0-beta-is-live/
---

*(Note: this article was originally posted at [my personal website](http://www.tannerhelland.com/5106/photodemon-60-beta/), before photodemon.org existed.)*

## Overview

It's taken nearly six months, but PhotoDemon 6.0 is finally ready for release.  I've [already talked about some of the great features this release includes](http://www.tannerhelland.com/4996/photodemon-60-preview/), like powerful selection tools, metadata (EXIF) support, Curves and other new tools, so I'd recommend glancing through the linked article if you're curious.

Since that article, a number of other features have been added or improved: 

  * All tools now support save/load presets, reset to default, randomize, and automatic save/load of last-used settings.  These items are all accessible from a new "command bar" at the bottom of each tool dialog.

  * Three new blur tools: motion, radial, and zoom blur.  These tools [outperform similar tools in GIMP and Paint.NET](http://www.tannerhelland.com/5109/performance-photodemon-gimp-paintnet/).

  * Much faster Gaussian and Box blur tools (20x improvement!)

  * A new [chroma key](http://en.wikipedia.org/wiki/Chroma_key) ("green screen") tool with performance comparable to professional tools, including full support for edge blending.  Find it in the Image -> Transparency -> Make color transparent menu.

  * A new Language Editor makes contributing new translations fast and easy.

  * New variable-strength Sharpen tool

  * New Oil Painting tool

  * Minor improvements to many tools, including polar coordinate conversion, perspective correction, wave distort, ripple distort, figured glass, tile image, posterize, rotate, custom filters, histogram.

  * Any tool with a "color" option now allows you to pick a color directly from the image by clicking the preview.

  * Much better support for high-DPI screens, including tablets.

  * Faster viewport rendering for 32bpp images.

Again, these new features are only a fraction of what 6.0 includes.  [Please check out the 6.0 preview article](http://www.tannerhelland.com/4996/photodemon-60-preview/) for news on all the other new tools and improvements.

## Acknowledgments

This 6.0 release represents six months of hard work from a variety of contributors.  While I am very grateful to all of PhotoDemon's talented contributors, a few deserve special mention.  Thank you to:

  * [Frank Donckers](http://www.planetsourcecode.com/vb/scripts/BrowseCategoryOrSearchResults.asp?lngWId=1&blnAuthorSearch=TRUE&lngAuthorId=2213335741&strAuthorName=Frank%20Donckers&txtMaxNumberOfEntriesPerPage=25) for again providing the German, French, and Dutch translations, and for contributing many pieces of code to the new Language Editor, including the Google Translate interface.  Amazing stuff.

  * [GioRock](http://www.planetsourcecode.com/vb/scripts/BrowseCategoryOrSearchResults.asp?lngWId=1&blnAuthorSearch=TRUE&lngAuthorId=77440558266&strAuthorName=GioRock&txtMaxNumberOfEntriesPerPage=25) for the Italian translation, and for detailed testing of many small translation items.  It takes a ton of work to get all of PD's text translating properly, and GioRock debugged many items for me, which benefits users of every language.

  * [Kroc Camen](http://camendesign.com/) for a new IDE-safe mouse interface class, derived from his own [open-source VB project](https://github.com/Kroc/MaSS1VE).  Kroc also reviews many of PD's individual commits, where he catches many small items I overlook.

  * [Robert Rayment](http://www.planetsourcecode.com/vb/scripts/ShowCode.asp?txtCodeId=66991&lngWId=1) for helping me profile and optimize a number of PD's more taxing functions, and for many suggestions on tweaks and improvements.  Many of the performance improvements available in this new version are a result of Robert's help.  Please check out his own [VB image editor](http://www.planetsourcecode.com/vb/scripts/ShowCode.asp?txtCodeId=66991&lngWId=1) if you can.

## Known bugs

  * <del>EXIF data is not maintained with certain combinations of preferences (delay loading EXIF + export full data when saving).  This is caused by a metadata caching issue, and will be fixed by release.</del>  Fixed!

  * <del>ExifTool plugin is slightly out of date.  It will be updated to its latest version upon 6.0's release.</del>  Fixed!

  * <del>Metadata menus sometimes become disabled even when metadata is available.  This will be fixed by release.</del>  Fixed!

  * <del>OK and Cancel buttons are not currently translated.  This will be fixed by release.</del>  Fixed!

  * <del>Some hotkeys don't fire unless the main form is first clicked.  This is a known problem with VB, and will _hopefully_ be fixed by release.</del>  Fixed!

  * <del>Master language file is missing a few minor text entries.  This will be fixed by release.</del>  Fixed!

The beta version was released before these bugs items were fixed.  Developers can download updated source code, with these fixes, [from GitHub](https://github.com/tannerhelland/PhotoDemon).

## Official release timeline

Barring any major bugs, the official 6.0 release should happen within several weeks.  Feature-wise, it will be identical to this beta release.  The only changes will be minor bug fixes and performance improvements.  Automatic update notifications for existing PhotoDemon installs will also go live at that point.

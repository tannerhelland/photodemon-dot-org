---
author: tanner_h
date: 2015-03-24 14:15:47+00:00
layout: post
slug: photodemon-6-6-release
title: PhotoDemon 6.6 release
excerpt: After six months of hard work, PhotoDemon 6.6 is officially ready for download.
redirect_from:
  - /1092/photodemon-6-6-release/
---

After six months of hard work, PhotoDemon 6.6 is officially ready for download.

Functionally, this release is very similar to [the 6.6 betas](2015/03/12/photodemon-6-6-beta-is-live) made available over the past month.  Many thanks to everyone who tested the beta - your suggestions and comments were invaluable.  Thank you also to the amazing volunteer translators, coders, and other contributors, without whom continued development would not be possible.

As I mentioned in the beta announcement, version 6.6 is a little different from past PD releases.  For 2015, my focus is threefold: adding on-canvas paint tools (and related tools, like text and shapes), implementing visual theming (including dark themes), and making the program 100% Unicode-compatible.  Progress on these tasks is coming along nicely, but due to their complexity, it will be a few months before everything is ready to go.  I don't want to wait that long to release an update, so what I've done is back-port as many non-paint-tool upgrades and improvements as I can to the 6.4 codebase - that's what you'll find in version 6.6.

As such, this release is more about refinement than epic new features (although there are still some great new tools, like [polygon, lasso, and magic wand selections](2015/01/12/photodemon-6-6-preview-new-selection-tools)).  Some of the other new features, like automatic updates, will make it much easier to ship future improvements.

You can find [a full write-up (with images) here](2015/03/12/photodemon-6-6-beta-is-live), but for those in a hurry, here is an abbreviated list of what's new and improved in this release.
	
  * **New selection tools**: magic wand, lasso, and polygon.	
  * **Automatic updates**, including delta patches for smaller files (like languages).  Customize the new update options from the Tools > Options menu.
  * Numerous **interface improvements**, including new tab strip, text up/down, image buttons, and other controls created specifically for PhotoDemon.
  * **Improved file format support**, including RAW support for 200 new camera models (via LibRaw), WMF and EMF metafile support, improved PNG compatibility, and many metadata improvements.
  * New **tone-mapping dialog for HDR and RAW images**.  Tone-mapping is also provided for high bit-depth variants of common formats, like 48- and 64-bit PNGs.
  * **Adaptive supersampling** is now available for all Distort and Transformation tools.
  * A number of **New and/or overhauled tools**, including Cross-Screen, Lens Flare, single-shot HDR, Channel Mixer, Surface Blur, Unsharp Masking, and more.
  * **Many improvements to existing tools**, including performance, accuracy, and interface improvements to Curves, Levels, Green Screen (Chroma Key), Color Balance, Kaleidoscope, Zoom Blur, Motion Blur, and many others.
  * **Improved performance program-wide**, including a new viewport pipeline, improved image compositor, updated localization engine, and new internal image manager.
  * **Improved localization and translation support**.  This is the first PD release to ship without any incomplete language files - thank you again to the amazing volunteer translators that made this possible!
  * **Many improvements to the main editor screen**, including a resizable and customizable left-hand toolbox, auto-hiding of the options toolbox, and new quick-access buttons for Save Lossless Copy and Fade Last Effect.
  * New **Fit Image, Fit Width, and Fit Height "smart zoom" options**.
  * Many other bug-fixes, performance, and accuracy improvements throughout the program

For a full list of this version's bug-fixes, performance improvements, and tool enhancements, please visit [PhotoDemon's commit log](https://github.com/tannerhelland/PhotoDemon/commits/master).

## Enjoy!

Thank you again to everyone who helped with this version's development, testing, translation and release.  I'd like to specifically call-out a few amazing folks who made this version possible: Helmut Kuerbiss, Roy (rk), Raj Chaudhuri, Will Stampfer, Hans Nolte, Zhu JinYong, Frans van Beers, GioRock, Frank Donckers, and Kroc Camen.  Thank you to these fine folks, and everyone else who contributed their time and expertise.

I hope you enjoy version 6.6.  If you have any feedback, please [send me a message](about/contact/).

In the meantime, it's back to work for me.  The next release (with all the features mentioned at the start of this article) will be big enough to warrant a jump to version 7.0, and I look forward to sharing more about it in the coming months.

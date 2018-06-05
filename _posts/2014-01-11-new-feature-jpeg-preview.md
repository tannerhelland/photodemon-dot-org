---
author: tanner_h
date: 2014-01-11 19:46:47+00:00
layout: post
slug: new-feature-jpeg-preview
title: 'New feature in 6.2: improved JPEG dialog'
excerpt: PhotoDemon 6.2 will ship with a complete redesigned JPEG export dialog.  
redirect_from:
  - /645/new-feature-jpeg-preview/
---

PhotoDemon 6.2 is getting nearer and nearer to completion, so I thought it would be fun to start sharing previews of some of the new features arriving in that release.  (Remember - you can try out these new features at any time by downloading the latest [development release](http://photodemon.org/downloads/nightly/PhotoDemon_nightly.zip).)

First up is a fix for one of my biggest photo editing pet peeves.  Almost everyone will need to save a JPEG file at some point in their life, and when they do, they are typically presented with a dialog like this:

![media/images/import/JPEG-Export-Options.jpg](media/images/import/JPEG-Export-Options.jpg)

The problem?  How can I possibly know what quality level is acceptable without a preview?  For some images, a value of 90 may be necessary to achieve "good quality", while other images may be fine at 70 or less.  But it's impossible to find an ideal value without saving the same image over and over again, then manually comparing the results.

I'm a hypocrite to complain about this when PhotoDemon 6.0 also fails to provide a preview in its JPEG dialog, but PhotoDemon 6.2 will finally solve the matter once and for all.  It includes an entirely new JPEG dialog with a number of improvements:

![media/images/import/PhotoDemon_JPEG_Export-570x546.jpg](media/images/import/PhotoDemon_JPEG_Export.jpg) 

*Thank you to [dA user Benlo](http://benlo.deviantart.com/art/Bioshock-Infinite-Early-street-concept-363408527) for the lovely artwork in this screenshot.*

The most obvious improvement is a live preview of the saved image.  This should make it much easier to find an acceptable quality value, or to know what the effects of advanced settings like subsampling do.  (Hint: better subsampling improves image sharpness, at the cost of a slightly larger file.)

Also added is PhotoDemon's standard command bar (the bar with all the buttons at the bottom).  Besides nice things like a "reset to default values" button, the command bar also provides a way to save and load custom presets.  If you want to set a preset for "Website quality" that has relatively low quality settings and progressive encoding, while having another preset for "Photo album" that has much higher quality, improved subsampling, and embedded thumbnails, it's now a piece of cake to do so.  Just set all settings to the values you want, type a memorable name in the box at the bottom of the screen, then press Enter (or tap the "save preset" button to the right of the text box) to save those values as a preset.  You can then access those settings in a single click whenever you need them again.

Finally, the new dialog will automatically remember your last-used settings.  My apologies for not adding this sooner, and many thanks to helpful user Jon for encouraging me to fix it!

This is one of the smallest enhancements coming in 6.2, but possibly one of the most meaningful for everyday users.  Stay tuned for more articles about other improvements coming in 6.2.

---
author: tanner_h
date: 2017-11-07 20:51:32+00:00
layout: post
slug: photodemon-7-0-miscellaneous-improvements
title: 'PhotoDemon 7.0: miscellaneous improvements'
excerpt: Some new features don't fit into an obvious category, so here's a quick list of miscellaneous improvements in the 7.0 release.
redirect_from:
  - /1730/photodemon-7-0-miscellaneous-improvements/
---

*(This is part of a series about PhotoDemon 7.0.  For the full 7.0 article collection, visit [this page](2017/11/28/photodemon-7-0-release).)*

Some new features don't fit into an obvious category, so here's a quick list of miscellaneous improvements in the 7.0 release.

## New Batch Repair tool

![media/images/import/batch_repair-570x477.jpg](media/images/import/batch_repair.jpg)

Corrupt hard drives, USB drives, and SD cards are much less common these days, but they can still ruin your day.

A friend recently experienced this while using a sketchy internet cafe on an overseas trip, and when he mentioned it to me, I tried to use PhotoDemon's wide image format support to construct a new Batch Repair tool for him.  (The new tool is accessible from the File > Batch > Repair menu.) 

Please note that the tool works best on drives that have already been partially salvaged using built-in Windows tools.  Specifically, the drive should have one or more folders full of arbitrarily numbered .CHK files.  If you don't see this, please use [this helpful tutorial](https://www.tekrevue.com/tip/fix-hard-drives-chkdsk-windows-10/) to run chkdsk manually.

Once Windows has copied any usable data into dedicated .CHK files, PhotoDemon's Batch Repair tool can try to identify as many intact photos, video, and audio files as possible.  In the case of my beleaguered friend, we were able to salvage more than 1,800 photos and videos from a corrupt SD card.

(I really hope you never need to use this tool - but hey, it's there if you need it.)

## Improved hotkey support

![media/images/import/hotkey_tooltip.jpg](media/images/import/hotkey_tooltip.jpg)

All tools are now accessible via hotkey.  The hotkeys mimic their counterparts in other photo editors, but if there's any confusion, just hover over a tool button to see the associated key.

Similarly, if two tools share the same hotkey (like square and circle selections), just press the key multiple times to toggle between the two.

## New collapsible right-side helper panels

![media/images/import/right_panel.jpg](media/images/import/right_panel.jpg)

On the right side of the primary viewport, PhotoDemon now provides access to two extra helper panels:

The **Navigator panel** provides a bird's eye view of the current image.  Click-drag inside this panel to quickly move around the image.  Similarly, if you are working while zoomed-in, this panel helps you see how the full image is coming along.

The **Color panel** allows you to quickly modify the active color.  A hue/saturation box on the right provides quick access to the full color spectrum, while the left panel allows you to "nudge" the active color toward a slightly different alternative.  If you want to raise a full color dialog, click the large center circle of the "nudge" control.

## Faster image loading

Common image formats like JPEG and PNG should load roughly 2x faster in PhotoDemon 7.0 (compared to PhotoDemon 6.6).  Images with embedded ICC profiles will see even larger gains.

Better yet, PhotoDemon's native PDI file format loads (and saves) up to 5x faster than before.

## ICC profile support for grayscale and HDR images

As part of PhotoDemon's improved image import pipeline, embedded ICC profiles are now supported across a much wider range of images.  Best of all, HDR images with embedded profiles no longer require manual tone-mapping intervention; instead, PhotoDemon will use the embedded profile to automatically handle everything for you.

## Simplified batch processor

PhotoDemon's batch processor is a great way to convert image collections between different formats, or to modify large sets of images "all at once".

In 7.0, this tool gains some new features.  Like everything else in the program, it is now 100% Unicode aware.  Full subfolder trees can now be added and removed in a single step.  And perhaps best of all, PhotoDemon's upgraded export engine is available to the batch processor, meaning you can specify extremely detailed export options for your batch processes - including advanced features like "export as web-optimized PNG".

## Reset buttons everywhere

![media/images/import/slider_reset_demo.jpg](media/images/import/slider_reset_demo.jpg)

PhotoDemon has long provided reset buttons in the bottom-left of each dialog.  These are great for resetting all controls in a window to their default state.

But sometimes, you don't want to reset *all* controls - just one of them!  Most PhotoDemon controls now provide built-in reset buttons right there in the control.  Just look for the round "reset arrow".

## Better battery life on Windows 8+

On Windows 8 or later, all time-based events in the program are automatically configured using [coalescing timers](https://view.officeapps.live.com/op/view.aspx?src=http%3A%2F%2Fdownload.microsoft.com%2Fdownload%2F9%2FC%2F5%2F9C5B2167-8017-4BAE-9FDE-D599BAC8184A%2FTimerCoal.docx).  As that link discusses, this allows the operating system to "coalesce" multiple timer events together, reducing the frequency at which the CPU needs to be revved up.  

## Drag/drop directly from zip files

When loading images from zip archives, most programs require you to first unzip all images.  PhotoDemon 7.0 can do you one better - zip archives opened via Windows Explorer now support full drag/drop, so just drag any zipped images into the program, and it will automatically handle the unzip process for you.

## Improved WMF and EMF support

WMF and EMF are vector image formats.  They are heavily used by the Microsoft Office line of software, and PhotoDemon now provides much better support for these files, especially when using the Windows clipboard.  This should lead to better results when copy+pasting objects like Excel charts.

## Limited support for non-portable mode

As you probably know, PhotoDemon is a _portable application_.  This means it never requires administrator rights or installation prior to using it.

Unfortunately, some users still try to place PhotoDemon inside admin-restricted folders, like "C:\Program Files".  In past releases, this would cause the program to crash.

In 7.0, I have added limited workarounds for this scenario.  If you place PhotoDemon into a restricted folder, the program will now recognize this and reroute all access requests to the unrestricted AppData folder for the current user.  (In Windows 10, this is somewhere like "C:\Users\YourUserName\AppData\Local")  

This allows the program to work normally, but it has two side-effects:

  1. PhotoDemon's data is now spread across two folders.  If you decide to move the program (e.g. to a portable drive), you will lose any customized program settings, as they will remain in your local AppData folder.
  2. Automatic updates will be forcibly deactivated.  If PhotoDemon can't access its own folder, it obviously can't update its files!

PhotoDemon's emphasis will always be on its portable mode implementation, but for those who really want to keep it inside "C:\Program Files" or a similar folder, you'll at least have a still-functioning program with this release.

## Bad .zip extractions are fixed automatically

Some people still use terrible old zip programs ([cough cough](https://en.wikipedia.org/wiki/WinZip)), and these programs have a tendency to extract .zip files as a single flat file list, instead of preserving folder structure.

When you run PhotoDemon for the first time, it now checks for this situation and attempts to rectify it automatically.  Note that this only works if PhotoDemon has access to its own folder, which means it will fail inside admin-restricted folders (like "C:\Program Files").  If you insist on unzipping the program to a restricted location, please make sure you unpack the zip file correctly, as PhotoDemon can't fix it for you!

## In conclusion

It's impossible to cover all miscellaneous updates in a single article, so for the truly curious, you may want to visit [PhotoDemon's lengthy commit log](https://github.com/tannerhelland/PhotoDemon/commits/main) for this release.  That link provides a full list of all changes and improvements, including the gritty technical details of everything mentioned here.

[Return to the main PhotoDemon 7.0 release announcement](2017/11/28/photodemon-7-0-release)

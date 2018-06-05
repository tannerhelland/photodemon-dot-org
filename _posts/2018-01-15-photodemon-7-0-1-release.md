---
author: tanner_h
date: 2018-01-15 17:27:27+00:00
layout: post
slug: photodemon-7-0-1-release
title: PhotoDemon 7.0.1 release
excerpt: PhotoDemon 7.0.1 contains minor security and stability improvements relative to PhotoDemon 7.0.  It is recommended for all users.
redirect_from:
 - /1852/photodemon-7-0-1-release/
---

## Download

If you already have a copy of PhotoDemon, you're good to go!  The program will automatically update according to your preference in the "Tools > Options" menu.

If you want to manually download a new copy, **[visit the download page](download/)**.

## Overview

PhotoDemon 7.0.1 contains minor security and stability improvements relative to [PhotoDemon 7.0](2017/11/28/photodemon-7-0-release.html).  It is recommended for all users.

There is also one meaningful feature change in this build.  PhotoDemon's auto-update engine now requires a secure connection (https).  For the vast majority of users, this doesn't change anything.  It simply makes automatic updates safer.

For users on very old, unpatched versions of Windows XP or Windows Vista, however, there is a small risk that PhotoDemon's automatic updates will no longer work, because those systems do not support modern security protocols.  Note that PhotoDemon will still function normally, but if you use it on an unpatched copy of XP or Vista, *you* will be responsible for downloading future updates.

I try to never risk disabling program features, but this is a rare "necessary evil" to protect the largest number of users.  Of course, up-to-date XP and Vista installs work just fine with this change - it is only original installs (with no subsequent patching) that may be affected.

I do not anticipate additional updates for the 7.0 version line, so barring any surprises, my focus is now on the next major release!

## Special thanks

Thank you to everyone who submitted bug reports and feature requests since 7.0 released.  Please keep your ideas and suggestions coming!

I also want to mention a special thank you to contributor [Jason Peter Brown](https://github.com/jpbro).  Jason submitted a series of very helpful patches to this release, which not only fixed some obnoxious issues, but also saved me a great deal of time.  Thank you, Jason!

## Final thoughts

If you have any feedback on this release, please [file a new issue on GitHub](https://github.com/tannerhelland/PhotoDemon/issues).  
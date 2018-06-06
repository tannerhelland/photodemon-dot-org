---
author: tanner_h
date: 2018-06-06 11:00:00+00:00
layout: post
slug: nightly-builds-have-moved
title: Nightly builds have moved - please re-download
excerpt: As part of the migration to a new website platform, nightly build auto-updates have been reworked.  If auto-updates have stopped working for you, please manually re-download the latest nightly build.
redirect_from:
 - /1982/nightly-builds-have-moved-please-re-download-manually/
---

This is just a quick FYI post for users of [PhotoDemon's nightly build](download/). (Nightly builds are automatically created every night from the latest source code. They contain new features, but may be buggy.) 

As I [talked about last week](http://photodemon.org/1905/the-future-of-photodemon/), photodemon.org will soon be upgraded. As part of this upgrade, nightly builds have been moved from a single shared server to a new, much faster [CDN](https://en.wikipedia.org/wiki/Content_delivery_network). This means that automatic updates can be served much faster than before, but unfortunately, this also required permanent changes to PhotoDemon's automatic update code. 

If you find that your nightly build copy is no longer auto-updating, please [manually download a new copy](download/). You can just copy the /App subfolder and PhotoDemon.exe files over your existing ones. No other special steps are required. 

Thank you to everyone who helps test nightly builds, and I apologize for any inconvenience this may cause.
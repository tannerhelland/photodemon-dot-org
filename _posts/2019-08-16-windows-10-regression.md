---
author: tanner_h
date: 2019-08-16 10:30:00+00:00
layout: post
slug: august-win-10-update-crashes
title: Warning - latest Windows 10 update may break nightly builds, but a patch is available
excerpt: The latest Windows 10 update ("2019-08 Cumulative Update for Windows 10 Version 1903") breaks a critical system library used by PhotoDemon.  Microsoft is currently "working on a fix", but in the meantime, you may find that older nightly builds crash without warning.  (Stable builds *should* be okay.)  I have uploaded a new nightly build to mitigate the worst of this issue.

---

I woke up this morning to find my latest PhotoDemon developer build crashing on every startup.  An investigation showed a critical error occurring in certain assignment statements, literally the simplest lines of code a program can contain, e.g. statements like:

x = y

A check of the Windows settings page showed that my PC had downloaded a new Windows 10 update overnight, and a follow-up search revealed that I was not the only developer (or user) experiencing sudden crashes across a wide range of software.  

It turns out that Microsoft themselves broke a critical system library as part of their latest Windows 10 patch ("2019-08 Cumulative Update for Windows 10 Version 1903").  Official issue details [are available at microsoft.com](https://docs.microsoft.com/en-us/windows/release-information/status-windows-10-1903#629msgdesc).  To quote that page:

> After installing KB4512508, applications... may stop responding and you may receive an "invalid procedure call error."

> Microsoft is presently investigating this issue and will provide an update when available.

Great.  Just great.

Digging a bit deeper, I located [a developer page](https://answers.microsoft.com/en-us/msoffice/forum/all/windows-update-2019-08-cumulative-update-has/baeea089-9bba-4a2a-9660-0a220f1656e9?auth=1&page=1) where a Microsoft Escalation Engineer was kind enough to elaborate on the bug.  Apparently Microsoft engineers are aware of the issue, and are doing their best to formulate fix.  Per that engineer:

> I am a Sr. Escalation Engineer for Microsoft, and we are already working multiple support cases that have been opened for this issue.  The update that was released yesterday contained a change in the oleaut32.dll that mitigates a specific security exploit. Unfortunately, this mitigation unexpectedly caused all these VBA and VB6 apps that were passing an empty ParamArray to start getting E_INVALIDARG in return from an internal function call.  This bubbled up to the errors you are seeing.

> We are taking this very seriously and discussing the possibilities for a safe and quick way to resolve this.  Since it was caused by a security update, there may be some obstacles to simply reverting the changes we made.

> Nevertheless, our full attention is on this issue now, and please rest assured that we will provide an update when we can safely do so.

Knowing which system library was at fault made it easier to develop an emergency workaround for the worst occurrences of the bug, so thank you to that engineer for sharing some technical details.

I've pushed out an emergency nightly build update [(details here)](https://github.com/tannerhelland/PhotoDemon/commit/754fc156378ad7fde2d09f62643498ff023a5f90) which contains hastily written mitigation code that should allow PhotoDemon to start, even if you've already installed the latest Windows 10 update.  (Or if, like me, Windows silently installed it for you.)  

Unfortunately, if your local copy of PhotoDemon fails to start due to this issue, PhotoDemon's auto-updater will obviously not be able to update the program for you - you'll need to [manually download a fresh copy](download/), or wait for Microsoft to patch the issue on their end.

I apologize for any inconvenience this may cause, and I can only hope that Microsoft is more cautious in the future.  

In the meantime, if you encounter any surprise crashes with nightly builds, please [get in touch](about/) and I'll do my best to add new workarounds for this problem.
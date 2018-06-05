---
author: tanner_h
date: 2015-02-19 15:48:01+00:00
layout: post
slug: coming-in-photodemon-6-6-automatic-updates
title: 'Coming in PhotoDemon 6.6: automatic updates'
excerpt: PhotoDemon 6.6 includes a bunch of new features designed to make updates more frequent, more reliable, and less of a hassle for everyone - me, translators, and end-users included.
redirect_from:
  - /996/coming-in-photodemon-6-6-automatic-updates/
---

Release dates are a funny thing.

When I first made PhotoDemon available online, my goal was to release an update every six weeks.  That quickly turned to two months, then three months, and the last stable release (version 6.4) took six months to release.  Version 6.6 is already nearing the six month mark as well, so I am long past due on finding a way to release new versions in a more timely fashion.

Aside from coding new features, the biggest delay has traditionally been language translations.  PD's translations are created by volunteers, and they can't really start their work until I've finished adding new text to the program.  Then, depending on time constraints, translations can takes anywhere from one week to many weeks.  (Some awesome volunteers, like Frank Donckers, actually manage translations for multiple languages - so their work is especially tough!)

![media/images/import/PD_66_translation_example-570x338.jpg](media/images/import/PD_66_translation_example.jpg) Here's what PhotoDemon's translators see.  Current translations include more than 13,000 words - or enough for a small book!

This presents a conundrum when trying to release a new version: do I wait for all translations to complete - penalizing those who use the original English text - or do I release the project anyway, knowing some translations may not be ready for several weeks?

PhotoDemon 6.4 took the latter approach.  Unfortunately, some language changes were never patched back in to the stable version, so to this day, version 6.4 is incomplete for some languages.  The German language file in particular saw many improvements from a team of volunteers, but because releasing a new version takes so much work, the updates never got backported to 6.4.

There's a better solution to this, and in PhotoDemon 6.6, I've finally implemented it.

## Silent, granular, automatic updates

PhotoDemon 6.6 includes a bunch of new features designed to make updates more frequent, more reliable, and less of a hassle for everyone - me, translators, and end-users included.

![media/images/import/PD_66_new_update_options-570x395.jpg](media/images/import/PD_66_new_update_options.jpg) A sample of the new update options available in version 6.6.

## Automatic updates

First up, PhotoDemon is now capable of silently updating itself, without any annoying prompts or actions from the user.  Historically, PD could notify you of an update, but you had to manually visit photodemon.org, download the new .zip file, and extract it yourself.  This is a hassle, and it's one reason I spread out PD releases - so users wouldn't be bombarded with "go download an update" notifications.

As of version 6.6, PhotoDemon is now capable of downloading new updates in the background, and silently patching itself when the download is complete.  As with all PhotoDemon features, this whole thing happens entirely in PD's folder.  Admin rights are not required, no registry edits are made, and no [UAC prompts](http://en.wikipedia.org/wiki/User_Account_Control) are raised.  

Because most existing update solutions don't work for portable software, PD's solution was custom-built from the ground up.  I've gone to great lengths to ensure that portability is not affected **at all** by this feature, and I'm pretty excited to have a portable app that can auto-update seamlessly.

Still to-do is a small prompt to let the user know they can restart to receive new features, but even this is going to be much less invasive than before.  (Probably a small window in the corner that automatically closes itself after ~10 seconds.)  I'm also debating a preference for allowing the old update behavior, where an update notification is raised but no automatic patching occurs.  I have mixed feelings about this, but might be tempted to add it if someone can make a compelling case - so [please let me know](about/contact/) if an option like this is important to you.

Update files required for patching the entire program and all plugins clock in around 7 MB, so pretty small.  Of course, you can disable updates completely if you prefer to manually patch your software on your own schedule.  Just select "never" as the update frequency, and PhotoDemon will no longer touch your Internet connection or download anything related to the program, even the ~1 KB update XML files.  (But if you do this, please make sure to manually check [photodemon.org](http://photodemon.org) periodically!)

Many thanks to those who helped develop and test this feature, including Hans Nolte and Jason Brown for helping me work through some issues with cheap antivirus software that incorrectly raised false-positive warnings during the automatic update process.

## Granular updates

Next up, PhotoDemon is now capable of patching languages separate from the program itself.  Language files are much smaller (~70 KB per language, compressed), so there's no reason to force a full program update if only one or two languages need to be patched.

New language files are silently downloaded in the background as they become available, and if the currently in-use language has an update, PhotoDemon is smart enough to load and apply the new text **without requiring you to restart the program**.  Pretty cool, eh?

This allows me to release program updates as soon as the code is ready, and updated translations will be automatically made available as soon as PD's great translators finish their work.  I believe this is best way to make sure the latest, highest-quality translations are available to everyone who needs them, without delaying updates for users who need only the default English text.

I'm also planning to apply this same logic to PhotoDemon's various 3rd-party plugins, so they can also be patched independently.  Work for this is currently underway (and a matching preference is available, as you can see in the screenshot above), but it may not be available until closer to 6.6's release.

## Built-in support for various update tracks

PhotoDemon downloads have always been available in three varieties:

**Stable builds**.  These are the most common downloads, and the best option for an average PD user.  Stable builds take awhile to receive new features, but they receive more testing than any other version, so they're the least likely to have weird bugs or incomplete features.

**Beta builds**.  Beta releases appear infrequently, typically right before a new stable build is set to launch.  They provide a last-ditch way to catch any unnoticed bugs, and PhotoDemon typically sees several thousand downloads for each beta release - my sincere thanks to all those who help test these!

**Nightly (developer) builds**.  Per the name, nightly builds are automatically assembled every night, using the latest PhotoDemon source code.  These builds can vary in quality from "totally stable" to "crash unpredictably."  That said, they've become much more stable as PD's picked up more contributors, and this is the version PhotoDemon's developers and translators typically use.

Historically, users who wanted to try a new version had to visit photodemon.org and download a whole new copy of the program.  In version 6.6, you can try a new build simply by visiting the Tools > Options menu, and selecting a new update track.  The next time you run the program, PD will automatically patch itself against whatever version you select.

This should make it much easier for curious users to try a new version without the hassle of downloading a whole new copy of the project.  This will also allow beta version testers to upgrade to the stable build as soon as it's ready, without any effort on their part.

(As an FYI: switching from nightly builds to stable builds won't be active until 6.6 releases.  This is necessary because 6.4 doesn't support these features, so switching to it would prevent future updates!)

## New back-end for generating update files

A crucial part of the new update code is the back-end that builds and uploads the actual update files.  There's a surprising amount of work involved in this.  Obviously the updated files themselves need to be compressed and uploaded, but also, special update XML files need to be generated.  To minimize the amount of downloading required by end-users, PhotoDemon uses a few tiny XML files to report the latest version of each file in the program.  These files allow the program to download only the files it needs, rather than downloading the entire project every time a single file is updated.

There are also security concerns with automatic updates, so a lot of work is required to [checksum](http://en.wikipedia.org/wiki/Checksum) each file before and after updating, to make sure there were no errors or malicious interference during transmission.  PhotoDemon uses multiple checksum reports, both internal to the update files and externally reported in separate XML files, to ensure safety during the update process.

These tasks have all been automated on my end, so all I have to do is run my update script and all relevant files are scanned, versioned, checksummed, compressed, and uploaded without any work on my part.  While not so interesting for end-users, this is a key part of making the update process is both accurate and timely.  (So basically, it's a much better solution than waiting for me to get off my lazy ass and assemble all that data manually... :)

## So when will version 6.6 be ready?

These update features were the last major to-do item on 6.6's release list.  

A few finishing touches are currently underway, and once this article is done, I'll be emailing PD's amazing translators to let them know all program text is ready for 6.6's release.  In the meantime, I'm going to start tracking down a few final bugs, and filling in some missing program icons and other minor issues.

For those who can't wait, the latest nightly builds should be quite stable, and of course they include all the features above!  You can always grab the latest nightly build from [the download page](download/), and as you've seen, any updates will be silently patched through as they become available.

Thank you again to everyone who helped with 6.6's release.  If you have any last-minute feedback or suggestions, [please get in touch](about/contact/).  There's still time to modify PD before release, so if you have an idea, now's the time to share it.

Otherwise, the next article you see from me should be a 6.6 beta release.  (Woohoo!)

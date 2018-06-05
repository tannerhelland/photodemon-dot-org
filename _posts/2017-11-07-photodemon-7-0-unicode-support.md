---

author: tanner_h
date: 2017-11-07 20:51:17+00:00
layout: post
slug: photodemon-7-0-unicode-support
title: 'PhotoDemon 7.0: now with full Unicode support'
excerpt: After many months of detailed study, development, and testing, PhotoDemon 7.0 will finally be capable of displaying text from any language, and working with files or folders with names from any character set.  Similarly, any text that you enter inside the program - from text tools to filenames - now supports characters from any language.  (Note that this is true across all versions of Windows, including Windows XP if SP3 is installed.)
redirect_from:
  - /1624/photodemon-7-0-unicode-support/
---

*(This is part of a series about PhotoDemon 7.0.  For the full 7.0 article collection, visit [this page](2017/11/28/photodemon-7-0-release).)*

[Unicode](https://en.wikipedia.org/wiki/Unicode) is the current technology standard for multi-language text.  Supporting it is not easy, especially in the programming toolkit I use to build PhotoDemon.  (A toolkit that dates back to 1998!)

To enable full Unicode support in PhotoDemon 7.0, I first needed [a custom-built UI toolkit](2017/11/07/photodemon-7-0-final-ui-update.html) capable of rendering text from any language.  Next, all file interactions - including things like loading and saving image files - had to be rewritten to handle Unicode filenames.  Then there were a billion little details that needed to be dealt with, like copy+pasting Unicode text, or handling user-created objects with esoteric characters in their names, or addressing the many different ways that [on-screen IMEs](https://en.wikipedia.org/wiki/Input_method) work.

After many months of detailed study, development, and testing, PhotoDemon 7.0 will finally be capable of displaying text from any language, and working with files or folders with names from any character set.  Similarly, any text that you enter inside the program - from text tools to filenames - now supports characters from any language.  (Note that this is true across _all_ versions of Windows, including Windows XP if SP3 is installed.)

All this Unicode work made it possible to finally ship a full Simplified Chinese translation with this release.  Thank you to contributor ChenLin for his work on it!

Other new language translations in this release include:
- Indonesian by Ari Sohandri Putra
- Italian by GioRock
- German by Roy K, with additional contributions from Helmet Kuerbiss
- Macedonian by Boban G
- Spanish by Plinio Garcia
- Vlaams by Frank Donckers

(If I've forgotten anyone, I sincerely apologize - and please let me know!)

While I'm here, I want to take a little extra time to thank Roy K in particular.  Roy has been faithfully updating PhotoDemon's German language release for the past two years, and he has also worked on updating all of PhotoDemon's machine-translated language files.  Roy catches many translation and Unicode-related bugs during development, and the 7.0 release would have taken much longer without his help.

So thank you, Roy!

Other miscellaneous improvements to PhotoDemon's language support include:

  * A rewritten live-translation engine, which is significantly faster than the last iteration.  Non-English languages no longer experience performance delays when loading complicated dialogs.
  * Language files now use a specialized cache, which means faster startup time for everyone.
  * Files imported from esoteric places (including the system clipboard, drag/drop targets, and online sources) no longer result in "????" characters.
  * Unicode metadata handled by the 3rd-party ExifTool library can now be properly interpreted by PhotoDemon.
  * Unicode support is also what allows OpenType features in PhotoDemon's text tools, as discussed in the [text tool release announcement](2015/08/03/coming-soon-best-in-class-text-tools.html).

Many thanks to everyone who has reported Unicode-related bugs during this development cycle.  More than any other feature, this one would not be possible without outside help.

[Return to the main PhotoDemon 7.0 release announcement](2017/11/28/photodemon-7-0-release)

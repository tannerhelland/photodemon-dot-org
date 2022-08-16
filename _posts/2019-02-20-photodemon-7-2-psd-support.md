---
author: tanner_h
date: 2019-02-20 11:00:00+00:00
layout: post
slug: psd-support-now-available
title: Help test new Photoshop (PSD) and OpenRaster (ORA) image support
excerpt: PhotoDemon 7.2 will ship with full support for layered image formats like Adobe Photoshop (PSD, PSB) and OpenRaster (ORA) files.  Help me improve these features by downloading the latest nightly build and trying it with your own PSD and ORA files.
---

In developer lore, there's a famous story about a programmer who thought it might be nice to support Adobe Photoshop files (PSDs) in his own application.  I recently ran into the story [on StackOverflow](https://stackoverflow.com/questions/5355708/psd-file-format/5355949#5355949), where the retelling goes something like this:

> At this point, I'd like to take a moment to speak to you about the Adobe PSD format.  

> PSD is not a good format.  PSD is not even a bad format.  Calling it such would be an insult to other bad formats, such as PCX or JPEG. No, PSD is an abysmal format. Having worked on this code for several weeks now, my hate for PSD has grown to a raging fire that burns with the fierce passion of a million suns.

> If there are two different ways of doing something, PSD will do both, in different places. It will then make up three more ways no sane human would think of, and do those too. PSD makes inconsistency an art form. Why, for instance, did it suddenly decide that these particular chunks should be aligned to four bytes, and that this alignment should not be included in the size? Other chunks in other places are either unaligned, or aligned with the alignment included in the size. Here, though, it is not included. Either one of these three behaviours would be fine. A sane format would pick one. PSD,   of course, uses all three, and more.

> Trying to get data out of a PSD file is like trying to find something in the attic of your eccentric old uncle who died in a freak freshwater shark attack on his 58th birthday. That last detail may not be important for the purposes of the simile, but at this point I am spending a lot of time imagining amusing fates for the people responsible for this Rube Goldberg of a file format.

> Earlier, I tried to get a hold of the latest specs for the PSD file format. To do this, I had to apply to [Adobe] for permission to apply to them to have them consider sending me this sacred tome. This would have involved faxing them a copy of some document or other, probably signed in blood. I can only imagine that they make this process so difficult because they are intensely ashamed of having created this abomination. I was naturally not gullible enough to go through with this procedure, but if I had done so, I would have printed out every single page of the spec, and set them all on fire. Were it within my power, I would gather every single copy of those specs, and launch   them on a spaceship directly into the sun.

> PSD is not my favourite file format.

Programmers can be dramatic, but this is a rare case where the drama is probably warranted.  Photoshop files are incredibly complex.  Photoshop itself provides thousands upon thousands of features, and PSD files have to store intricate details on all of them.  PSD files are also largely backward-compatible, which means you can edit a photo in a modern-day version of Photoshop, then open the same file in a 20-year-old copy of Photoshop and many features will still work!

This complexity has led authors of other major open-source photo editors to [write things like](https://forums.getpaint.net/topic/97-psd-file-format-support/):

> I looked into [PSD file support] awhile ago and it would take months of work to make [our application] even have a chance of being compatible with PSD files.  Same goes for Photoshop filter plugins and RAW files: they would've been enormous work items that would've taken one person months to complete.

> So all these features were quickly axed, and will not be in [our application] for the forseeable future.

For many years, users have requested Photoshop file support in PhotoDemon, and my response has been along the same lines - are you crazy, there's just no way, it would take years of work, etc.

But in recent months, several things changed.

For one, Adobe finally made [the PSD specification publicly available](https://www.adobe.com/devnet-apps/photoshop/fileformatashtml/).  The spec is hundreds of pages long and full of errors, but this is still a **huge** improvement over forcing 3rd-party developers to sign specialized legal documents just to *read* the spec.

The other thing that changed is that I've gradually written many other file importers and exporters for PhotoDemon.  For example, I recently wrote import and export engines for [OpenRaster (ORA) files](https://en.wikipedia.org/wiki/OpenRaster), the open-source equivalent of Photoshop files.  OpenRaster files support multiple layers, blend modes, opacities, layer names, and other Photoshop-like features, and you can load and save them in major free photo editors like [GIMP](https://www.gimp.org/), [MyPaint](http://mypaint.org/), and [Krita](https://krita.org/en/).  Adding support to PhotoDemon didn't take long (thanks in part to [a simple, clear spec](https://www.openraster.org/)) and it got me thinking - was it finally time to tackle Photoshop file support?

![Krita screenshot](media/images/krita_orig_ora.png)

*This lovely image is ["Our Code of Conduct" by David Revoy, CC-by](https://www.peppercarrot.com/en/article455/our-code-of-conduct).  At that link, he provides the original KRA file he created in Krita.  Here's how it looks in Krita...*

![PD screenshot](media/images/pd_import_ora.png)

*...and here's the same file, saved to OpenRaster format and opened in PhotoDemon. Individual layers are fully intact!  (The minor color differences are due to PhotoDemon's lack of support for layer groups.  Groups are on my to-do list!)*

The title of this article gives the punchline away, but yes - it *was* time for me to tackle PSD support.  Over the past few weeks I've chipped away at the project, and I am happy to report that PhotoDemon is now capable of loading Photoshop files of every shape and size.  All 9 color spaces in the official specification are fully covered (monochrome, grayscale, indexed, duotone, RGB, CMYK, multichannel, and Lab), and they are supported at every supported color-depth (including HDR images with 16-bit and 32-bit channels).

Photoshop features like layer names, visibility, blend modes and opacity are automatically translated by PhotoDemon.  Some advanced Photoshop features like "layer masks" are migrated to their closest PhotoDemon equivalent (e.g. merged into the image's alpha channel), which produces a visually identical image that is simply represented in a way PhotoDemon can understand.

Obviously Photoshop is a huge program with a massive feature set, and PhotoDemon cannot replicate every feature found in PSD files.  Unsupported Photoshop-only features (like layer styles) are still parsed and stored internally, but activating them will require new features in PhotoDemon itself - features that I hope aren't *too* far off!  This is actually one of the biggest advantages of having my own PSD engine: as I add new features to PhotoDemon, I can immediately mirror that support in reading/writing PSD files.

Unfortunately, some of Photoshop's most helpful features - like editable text layers - remain undocumented by Adobe.  Because PhotoDemon also supports editable text layers, I would love to add support for this feature when working with PSD files, but this will remain a "work in progress" for the forseeable future, or at least until Adobe chooses to reveal their proprietary text layer format.  (In the meantime, I'm working with other open-source developers to try and reverse-engineer the format, but it's hard to predict if it will produce any usable results.  Fingers crossed!)

One of the things I am most proud of in PhotoDemons's PSD engine is that it is the only 3rd-party engine (out of dozens tested) that fully passes all PSD images in [Apple's color management test suite](https://developer.apple.com/library/archive/technotes/tn2115/_index.html#//apple_ref/doc/uid/DTS10004098-CH1-SECTION9).

![Good ICC screenshot](media/images/sample_rgba8_psd.png)

Apple's test image collection is a neat collection of images with specialized [embedded color profiles](https://en.wikipedia.org/wiki/ICC_profile).  These color profiles give instructions on how to accurately reproduce colors in each image, and they are a key component of [color management](https://en.wikipedia.org/wiki/Color_management).  When the image's colors are reproduced correctly, the test image looks like the sample image above...

![Bad ICC screenshot](media/images/sample_rgba8_bad.png)

...but when a color profile is ignored, the test image instead looks like this.

Apple test collection provides images in many different formats, including Photoshop PSDs.  There are twelve different PSD images in the collection, each representing a different color depth or model.  PhotoDemon is the only software I've tested (aside from Photoshop itself, of course), that correctly loads all twelve.

![PhotoDemon passing the ICC tests](media/images/icc_test_suite_passed.png)

*All twelve test images open at once.  Even CMYK and black-and-white images pass the test!*

Color fidelity has been a large point of focus in PhotoDemon, and it's especially critical in images coming from Photoshop (which has long been the standard-bearer of quality color management).  It's very exciting to have hard proof that PhotoDemon's approach to color management is working well, and I love that it handles color management "magically" in PSD files without any work on the user's part.

So you might be wondering - isn't it a little suspicious that such a notoriously difficult project was tackled in just the past few weeks?  I wish I could claim to be some kind of savant, but alas, I am far from that.  Instead, PSD support is just the icing on a cake that has been a long time in the making.

[As PhotoDemon's Patreon supporters know](https://www.patreon.com/posts/how-to-use-new-7-19823148), a bunch of new digital palette features are available in PhotoDemon's nightly builds.  One of the palette features I've added is support for Adobe-format palettes, including both swatches and color tables.  Part of the reason I tackled that project was to familiarize myself with Adobe files and patterns, as preparation for someday tackling PSD support.  Similarly, adding OpenRaster support late last year was a great way to ensure that PhotoDemon's layer features could easily be connected to outside file formats.  Projects like these may not seem related to PSD files, but they were critical building blocks on the path to PSD support.  Without them, this project probably would have taken much longer!

I've spent most of this article talking about importing Photoshop and OpenRaster images, but of course, you can also save these files from PhotoDemon too.  Exporting PSD files is particularly cool, as PhotoDemon is able to save PSD files that are smaller than those produced by Photoshop itself!

![Comparison of five PSD file sizes](media/images/small_PSD_sizes.png)

*Sample of a 5-layer PSD file, exported from five different programs.  PhotoDemon's PSD compressor produces excellent results, and its PSD files are often smaller than the PSDs produced by Photoshop.*

If you're interested in the technical details of PhotoDemon's new PSD support, you can always check out the [publicly available commit log](https://github.com/tannerhelland/PhotoDemon/commits/main), or investigate the PSD engine's [source](https://github.com/tannerhelland/PhotoDemon/blob/main/Classes/pdPSD.cls) [code](https://github.com/tannerhelland/PhotoDemon/blob/main/Classes/pdPSDLayer.cls) [directly](https://github.com/tannerhelland/PhotoDemon/blob/main/Classes/pdPSDLayerInfo.cls).  Like all PhotoDemon source code, the new PSD engine is [BSD-licensed](https://github.com/tannerhelland/PhotoDemon/blob/main/LICENSE.md) and available for other developers to freely use or learn from.

If you are a heavy user of Photoshop or OpenRaster files, I'd appreciate you taking the new features for a spin.  Nightly builds with these new features are available at [PhotoDemon's download page](https://photodemon.org/download/), and if you run into any surprises when loading or saving files, you can file a bug report on GitHub by clicking [the New Issue button on this page](https://github.com/tannerhelland/PhotoDemon/issues).  I have tested thousands of files while working on the source code, but as you've seen, Photoshop files are both enormous and enormously complicated, so additional testing is always welcome.

Thank you, as always, for being a PhotoDemon user.  Hope you have a great February!
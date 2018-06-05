---
author: tanner_h
date: 2013-10-25 00:06:37+00:00
layout: post
slug: photodemon-6-2-new-interface
title: PhotoDemon 6.2's new, customizable interface
excerpt: Up through version 6.0, PhotoDemon used a very old interface style called MDI, or "multiple document interface".  That's about to change.
redirect_from:
  - /530/photodemon-6-2-new-interface/
---

Photo editors come in a lot of shapes and sizes.

Some editors give every part of the program its own window:

![media/images/import/GIMP-multiwindow-570x355.jpg](media/images/import/GIMP-multiwindow.jpg)

Others lock images into place, but allow you to freely move toolbars:

![media/images/import/Chasys-Draw-570x389.jpg](media/images/import/Chasys-Draw.jpg)

Some software locks toolbars into place, but give images their own windows:

![media/images/import/AZ-Paint-Pro-570x427.jpg](media/images/import/AZ-Paint-Pro.jpg)

While still others lock both toolbars and images into a single, predefined layout:

![media/images/import/MS-Paint-570x392.jpg](media/images/import/MS-Paint.jpg)

For photo editors that support working with multiple images at once, there are even more variations.  Some editors give each image its own window that lives "within" the main program window.  Others use a single image panel, and you can switch between images via a tabstrip.  Still other software spawns a unique copy of the program for each loaded image.

Each of these approaches has strengths and weaknesses, but which approach you prefer probably comes down to a single factor: _which layout are you most familiar with_?  If you are accustomed to a Photoshop-style layout, chances are you'll prefer other pieces of software that behave similarly.

(This observation will become important in a moment!)

### First, a bit of history

Up through version 6.0, PhotoDemon used a very old interface style called [MDI, or "multiple document interface"](https://en.wikipedia.org/wiki/Multiple_document_interface).  MDI is an imprecise name, as there are many ways to implement a multi-document interface - for example, modern web browsers use a subset of MDI called TDI, or "tabbed document interface" - but most developers use the term MDI to refer specifically to this old interface style.

In a traditional MDI layout, each "child" window lives "within" the parent window.  In the case of PhotoDemon, this meant that each loaded image received its own "child" window, which could never be moved outside the larger PhotoDemon "parent" window.

![media/images/import/MDI-interface-570x351.jpg](media/images/import/MDI-interface.jpg) 

MDI has never been a great interface paradigm.  (There are many reasons for this, and [a good discussion of the topic can be found here](http://stackoverflow.com/questions/486020/is-there-still-a-place-for-mdi?lq=1).)  PhotoDemon only used it because a decade ago, when I first added support for loading multiple images, MDI could be switched on automatically in my development tools, making it the simplest way for me to support multiple images.  

In the years since, I have wanted to move away from traditional MDI, but the question has always been - move away to _what_?  Of all the different photo editor interfaces, which one was right for PhotoDemon?

In version 6.2, I'm finally going to answer that question.  After much deliberation, I have decided that the answer is... _all of the above_.

### Choice: Too much of a good thing

It's well-known that as far as human psychology is concerned, [too much choice is not a good thing](http://www.businessinsider.com/the-fundamentals-of-choice-2011-2).  This is [especially true](http://www.joelonsoftware.com/uibook/chapters/fog0000000059.html) in [user interface design](http://www.lukew.com/ff/entry.asp?419).  In fact, one of my all-time favorite usability quotes comes from that second link:

> "...users care about a lot less things than you might think. They are using your software to accomplish a task. They care about the task. If it's a graphics program, they probably want to be able to control every pixel to the finest level of detail. If it's a tool to build a web site, you can bet that they are obsessive about getting the web site to look exactly the way they want it to look.
> 
> They do not, however, care one whit if the program's own toolbar is on the top or the bottom of the window. They don't care how the help file is indexed. They don't care about a lot of things, and it is the designers' responsibility to make these choices for them so that they don't have to. **It is the height of arrogance for a software designer to inflict a choice like this on the user simply because the designer couldn't think hard enough to decide which option is really better.**

*(emphasis mine)*

With that in mind, let's talk about PhotoDemon's new interface, and how it finds that sweet spot between too much and too little user choice.

### PhotoDemon's new interface

![media/images/import/interface_11-570x378.jpg](media/images/import/interface_11.jpg)

The first time you run it, PhotoDemon will default to this lovely new tabbed interface.  

After much consideration and research, I strongly believe a tabbed interface is the best default layout.  Most users are familiar with tabs thanks to web browsers, and a tabbed layout works particularly well with photo editing software, because it allows you to see a thumbnail of each open image.  (This is a big improvement over the old MDI layout, where you could easily lose image windows behind other images.)

If only one image is loaded, the image tabstrip will disappear, giving you maximum workspace for your image.

Note that the tab bar is fully resizable - just click and drag its bottom border to make it larger or smaller.  All tab thumbnails are automatically updated as you edit an image, and a small asterisk appears in the corner of images that have unsaved changes.

The other big change from 6.0 is that the selection toolbar has been moved to the bottom of the screen.  There are many reasons for this, not least of which is that the right-hand side of the screen needs to be saved for [future features](https://en.wikipedia.org/wiki/Layers_%28digital_image_editing%29)... ;)

[95% of users don't modify software settings from their default values](http://www.uie.com/brainsparks/2011/09/14/do-users-change-their-settings/), so most PhotoDemon users will never switch from the default tabbed interface.  I'm perfectly happy with this - in fact, this layout is my preferred interface paradigm for the program!

### But what about the other 5%?

As I've already mentioned, I don't think there is one right way to build a photo editor.

So for users who prefer another interface style, you are about to be made very happy - because changing PhotoDemon's default layout could not be easier.

First, a disclaimer.  As both a user and a developer, I am not a fan of highly customizable interfaces.  

_(What?  Then why are you talking about PhotoDemon's new customizable interface?  Bear with me - I'm getting to the point!)_

As a user, I would much rather have a group of professional designers pick the best interface for me.  They have access to tools and test groups and research that I do not, so I am happy to trust their judgment.  I shouldn't have to heavily customize software to make it do what I want - it should do what I want out of the box!

As a developer, the thought of making a fully customizable interface where the user can move or dock or float or magnetize everything in the program... well, it makes me extremely nervous.  Not only would it take _years_ for a single developer like me to build such a complex system, but almost no one would make use of such a feature, for the same reason I just described - who wants to heavily customize their software just to make it usable?

To once again quote [that excellent usability article](http://www.joelonsoftware.com/uibook/chapters/fog0000000059.html):

> "But wait!" you say. "It's important to have options for advanced users who want to tweak their environments!" In reality, it's not as important as you think...
> 
> Most advanced users use several computers regularly; they upgrade their computer every couple of years, they reinstall their operating system every three weeks. It's true that the first time they realized you could completely remap the keyboard in Word, they changed everything around to be more to their liking, but as soon as they upgraded to Windows 95 those settings got lost, and they weren't the same at work, and eventually they just stopped reconfiguring things. I've asked a lot of my "power user" friends about this; hardly any of them do any customization other than the bare minimum necessary to make their system behave reasonably.

I probably fall into that "power user" category, and I definitely do only the bare minimum necessary to make my system behave reasonably.  In fact, that's the main reason I gave up Linux for Windows for my day-to-day computing.  (But that's another story for another day.)

So what does this mean for PhotoDemon?  It means I can boil my entire philosophy about PD's interface to these three points:

  1. The default interface should be so good that casual users should not be motivated to change it.
  2. Power users are a different story, because they may already be accustomed to another interface style.  These individuals shouldn't have to learn a whole new interface just to use my program.
  3. That said, no one likes customizing software.  If someone wants to adjust PhotoDemon's interface, they should be able to do it in one, maybe two mouse clicks.  Anything more is a waste of their time.

With that in mind, here's how to recreate your favorite photo editing interface in PhotoDemon 6.2.

### The all-powerful Window menu

![media/images/import/new_window_menu.png](media/images/import/new_window_menu.png) 

From two new menu items - "Floating toolboxes" and "Floating image windows" - you can now make PhotoDemon's interface work like any other mainstream photo editor.  

![media/images/import/interface_3-570x378.jpg](media/images/import/interface_3.jpg) 

If you really liked the way previous version of PhotoDemon worked, do not fear - the old MDI mode is still available.  From the default interface, simply select "Floating windows" to restore a layout nearly identical to prior versions.  Each image receives its own window, and you can move those windows anywhere you like within the parent window.  Traditional commands like Cascade and Tile Horizontally/Vertically appear in the Window menu while in this mode.

![media/images/import/interface_2-570x353.jpg](media/images/import/interface_2.jpg) 

From the default layout, you can also choose to enable "floating toolbars" while leaving images docked.  This mode should look familiar to users of [Paint.NET](http://www.getpaint.net/) or [Pixelmator](http://www.pixelmator.com/).  As floating windows, you can move toolbars anywhere you want on the screen, including onto separate monitors.  Each toolbar's location will be automatically memorized and restored on subsequent sessions.

I've gone to great lengths to make this mode as frustration-free as possible.  Toolbar windows will always remain above the main window, but if you switch away from PhotoDemon, their top-most status will be automatically disabled.  When moving the main window, all toolbars move along with it as if invisibly tethered.  Finally, minimizing the main PhotoDemon window will also hide all tool windows, so you don't have to worry about stranded windows cluttering up your screen.

Also, as you can see from the screenshot, if a tool window does not have focus, it will automatically become semi-transparent.

![media/images/import/interface_4-570x344.jpg](media/images/import/interface_4.jpg)

The last mode arises if you select both "floating toolbars" and "floating images."  All the benefits from "floating toolbars" mode remain, e.g. all windows move together as a group when the main window is moved or minimized, and toolbars still remain on top of image windows.  

I'm not a huge fan of this mode, but for users accustomed to this kind of power after using [GIMP](http://www.gimp.org/) or Photoshop, know that you can now do the same with PhotoDemon.

### Want the new interface today?

If you're feeling brave, PhotoDemon's nightly development builds ([available here](download/)) already include the new interface options.  While there are still a few small kinks to work out, the new interface options should be 99% stable, so feel free to give them a whirl!  If you do happen to come across any bugs, [please report them](about/contact/) so I can get them fixed right away.

### In conclusion

I am very happy to finally give PhotoDemon a modern, customizable primary interface.  The default tabbed mode is a real pleasure to use, and now that I've had access to it for a few weeks, it is very hard for me to return to 6.0's layout.  

And if you don't agree with me, know that you now have the option to customize the program's interface however you like - and you can do it without a plethora of obnoxious menus or settings boxes to navigate.  In my testing, no other photo editor makes it this easy to obtain the interface you want.

If you have any additional feedback on PhotoDemon's new layout, [be sure to let me know](about/contact/).  The 6.2 release is still a long way off, so there's lots of time to improve things further!

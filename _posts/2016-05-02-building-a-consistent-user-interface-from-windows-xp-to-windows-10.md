---
author: tanner_h
date: 2016-05-02 19:51:50+00:00
layout: post
slug: building-a-consistent-user-interface-from-windows-xp-to-windows-10
title: Building a consistent user interface from Windows XP to Windows 10
excerpt: In its next release, PhotoDemon will finally be running on its own custom-built user interface toolkit.  This toolkit has slowly been constructed over the past two years, but it's finally nearing completion, and it will make a ton of long-awaited fixes and improvements possible.  
redirect_from:
  - /1316/building-a-consistent-user-interface-from-windows-xp-to-windows-10/
---

As you probably know, PhotoDemon is a *portable application*.  Portable applications meet a few special criteria:

1. You don't need to install the program to use it.  
2. You don't need administrator privileges to use it.
3. You can run the program from a USB drive, CD, or any other removable media, because...
4. You can move the program between folders (or entire computers) without losing your settings or breaking the app.

While portable applications are great for users, they can be pretty unpleasant for developers.  Developers (like me!) very much appreciate installer software because installers handle many difficult tasks - like analyzing a PC's capabilities and installing the best program version for it, or setting up a bunch of required folders and resources so I don't have to.

Because portable applications don't use installers, they have to do all the heavy lifting themselves.  For example, today you might run PhotoDemon on a top-of-the-line Windows 10 PC, but tomorrow, you might run it on the old Windows XP computer at your local library.  PhotoDemon has to adjust to these different environments on-the-fly, and this is the source of many development headaches.

![old computer](https://upload.wikimedia.org/wikipedia/commons/a/a0/Old_computer_4.jpg) *You might be able to run PhotoDemon on this old guy, but no promises.  Image [c/o Wikipedia](https://commons.wikimedia.org/wiki/File:Old_computer_4.jpg)*

When trying to develop a user-friendly photo editor, these limitations become even more unpleasant.  On Windows XP, for example, a simple object like a list or a button may behave totally differently from how it does on Windows 7.  In fact, the program's entire interface may look and behave differently from PC to PC!

Why does the user's operating system affect the way a portable application behaves?  Basically, it's a huge amount of work to create a program's interface elements (menus, buttons, drop-down boxes, lists, checkboxes, radio buttons, labels, etc).  So instead, applications use a set of interface elements called the [Windows Common Controls](https://msdn.microsoft.com/en-us/library/windows/desktop/bb773169(v=vs.85).aspx).  With common controls, Windows itself creates and renders the controls, and the controls simply notify the developer when something interesting happens, like _"hey - a user just clicked on me!"_

There are a lot of perks to using common controls, but first and foremost is the amount of work it saves.  Instead of building some two-dozen controls of my own, I can just let Windows handle them, which frees me up to work on other things (like photo editing tools!).

But there are plenty of downsides, too.  For example..

- Because Windows itself draws the controls, users on different Windows versions receive totally different visual experiences.
- Controls may behave differently on different Windows versions.  (For example, some Windows versions may have nice accessibility features - like changing a control's appearance when you hover it with the mouse - while other ones do nothing.)
- For PhotoDemon, specifically, the program's development toolkit is tied to an older version of the Windows controls, one that doesn't support [Unicode text](https://en.wikipedia.org/wiki/Unicode).  While this allows PhotoDemon to operate all the way back to unpatched versions of Windows XP, it also greatly limits our features on modern versions of Windows.

As an example of this, here's a quick gallery of the same dialog as it appears on different versions of Windows.  Can you tell which objects are "common controls", and which ones were custom-built?

![media/images/import/PD_64_options_XP-570x391.jpg](media/images/import/PD_64_options_XP.jpg) *One of PhotoDemon's options panels, as it appears on Windows XP.  The drop-down boxes and command buttons are Windows Common Controls, so Windows paints them with XP visual styles.*

![media/images/import/PD_64_Win7-570x392.jpg](media/images/import/PD_64_Win7.jpg) *On Windows 7, the drop-down boxes and command buttons look... shiny, I guess?*

![media/images/import/PD_64_options_classic-570x391.jpg](media/images/import/PD_64_options_classic.jpg) *Older versions of Windows have a "classic theme" option that makes everything Win-95 style.  Ugh.*

![media/images/import/PD_64_options_Win10-570x396.jpg](media/images/import/PD_64_options_Win10.jpg) *The same panel on Windows 10.  For some reason, Microsoft engineers thought it was a good idea to make drop-down boxes gray, which historically indicated locked or disabled controls.  (sigh)*

For a long time, I managed to live with these limitations, but over the past two years they've bothered me more and more.  Whether it's basic limitations (like text fitting differently from version to version) to more egregious ones (dark interface themes are basically impossible), the limitations of the common controls have frequently interfered with my ability to improve PhotoDemon.

And then Windows 10 arrived.  Like any new Windows release, I had to spend a lot of time fixing various interface-related issues caused by the new update, but with [Windows 10's rolling development model](https://en.wikipedia.org/wiki/Windows_10#Updates_and_support), there's no guarantee the program's interface won't change/break/explode whenever a new patch is released.  I now need to test no less than five major versions of Windows (XP, Vista, 7, 8/8.1, and 10) - I also need to fully support these without leaning on an installer.

The workload has simply gotten too large, so it was time to make a change.  

In its next release, PhotoDemon will finally be running on its own custom-built user interface toolkit.  This toolkit has slowly been constructed over the past two years, but it's finally nearing completion, and it will make a ton of long-awaited fixes and improvements possible.

Specifically, here's what it means for you.

## Theme support

Here is an animation of PhotoDemon's "work-in-progress" theme support:

![media/images/import/color_themes-570x320.gif](media/images/import/color_themes.gif) *This very messy window lets me test a whole bunch of PD's custom controls at once.  As you can see, theme support is coming along nicely!*

Though still a work in progress, PD's custom UI toolkit finally makes dark themes possible, as well as themes that use different highlight colors.  (Dark themes don't just look cool - they're also [an important accessibility feature](http://www.cgpgrey.com/blog/dark-mode-as-accessibility-feature), and they're also relevant for constructing a proper digital darkroom.)

As the animation above demonstrates, themes can be swapped at run-time.  Any combination of light+dark+accent colors is supported.  (I use blue, green, and violet for testing, because they're very distinctive, but any accent colors are possible!)

There are still a lot of little theme issues to iron out, but none of it would be possible without the new interface toolkit.

## Interactive elements are much more discoverable

In many ways, websites have surpassed desktop applications in usability.  If a webpage element is interactive, it often animates when you move your mouse over it, and it clearly shows a "hand" pointer to match.

In desktop applications, this is much less predictable.  Clickable items sometimes use a hand (e.g. "[command links](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742403(v=vs.85).aspx)", as Microsoft calls them), but most times, you just get an arrow pointer.  Some elements are animated while others are not.  Some interactive elements are conveyed with color, but in Windows 10, many things now appear as monochrome, and are slightly "dimmed" when hovered.  (Or worse, they rotate between "dark gray" and "black" - who makes these decisions??)

I strongly dislike these inconsistencies, especially when learning new software, because I can't easily tell what I'm allowed to interact with.  PhotoDemon's next release tries to fix this.

Here is a demonstration on a typical PhotoDemon dialog:

![media/images/import/PD_hover_UI-570x326.gif](media/images/import/PD_hover_UI.gif) 

Interactive items always use a hand pointer, and all standard controls highlight their borders and/or background when hovered.  You no longer have to guess at which on-screen objects are interactive.

## Clearer indicators for the visually impaired

As the above animation shows, PhotoDemon tries to highlight interactive elements not just by changing a control's color when hovered - a chunkier border is also added.  For color-blind users, this is a huge improvement over color changes alone.

Similarly, unlike Windows common controls, hovered animations always combine at least two out of three elements (changes in hue, changes in luminance, and changes in thickness) to convey interactions, and wherever possible, all three changes are used.  This provides clear, distinctive messaging, and combined with theme support (which lets you set your own accent color), visual impairments will be a much smaller hurdle to using the program.

## Consistent experiences on all versions of Windows

Whether you're on Windows XP or some future version of Windows 10, PhotoDemon will always look and behave the same way.  From a usability standpoint, this is crucial.  Humans are very attuned to minor differences in appearance and behavior ([the "uncanny valley" effect](https://en.wikipedia.org/wiki/Uncanny_valley)), and when a program's interface changes from PC to PC, it hurts your reflexive ability to interact with it.  

From here on out, PhotoDemon will finally be able to provide strong visual consistency, regardless of what operating system you're using - meaning that once you get comfortable with its interface, you never have to learn a new one.

## New controls that use a similar visual language

[Progressive disclosure](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742409(v=vs.85).aspx) is an important concept in interaction design.  Progressive disclosure means that initially, a program only provides the minimum information necessary to complete a task.  However, advanced users can _progressively disclose_ more information by clicking on various on-screen elements.  This presents a nice experience for both beginners and advanced users.

In the "progressive disclosure" article linked above, Microsoft shows _six different visual approaches_ to progressive disclosure, including chevrons, arrows, plus/minus buttons, and rotating triangles.  Each of these mechanisms looks and behaves differently, with some glyphs indicating the disclosure state _after_ you click them, while others show the _current_ disclosure state.  All the usual caveats about different behavior across Windows versions also applies.

As much as possible, I prefer to reduce complex systems like that down to just one consistent visual indicator.  For example, in the next release, PhotoDemon makes better use of simple "title bars" - brief captions (with rotating arrows) that easily show/hide information panels.

Here is an animated demonstration:

![media/images/import/new_controls-570x348.gif](media/images/import/new_controls.gif) 

Don't want to see a panel?  Click the title bar to show/hide it.  As with all other controls, the title bar's clickable nature is revealed by hover animations and a hand cursor.

This allows you to switch between simple dialogs and complex ones at your leisure, and once you're comfortable with one "title bar" control, you're comfortable with all title bar controls.  After all - you've got better things to do than learn a half-dozen different mechanisms for performing the same basic task!

## Custom controls designed for photo editing

Photo editors require a lot of unique controls, controls that aren't easily covered by the Windows Common Controls.  Past versions of PhotoDemon already included a few of these, but now, the entire interface toolkit uses similar visual language for both standard controls (like buttons and lists) and weird controls, like what I'm about to show you.

Choosing a color is a common photo editor task.  Because it can be time-consuming to pop open a dedicated color editing window, PhotoDemon now provides a much quicker way to manipulate colors.

Here is an animated example:

![media/images/import/color_selector.gif](media/images/import/color_selector.gif) 

The right side of the control lets you quickly select a new hue from the wheel, or a new luminance or saturation from the box.  On the left, you can quickly "nudge" your color to a close relative, a bit like mixing paints on a traditional palette.  (And of course, you can click the large center button to pull up a full-featured color editor.)

Controls like this are much easier to produce with the new interface toolkit, because they use the same building blocks as other controls (including light/dark themes, chunky borders on hover, and other features).

## In conclusion

I'm terrible at providing regular updates here on the PhotoDemon website, and for that I apologize.  It's difficult to find time to write meaningful progress updates, and what little time I do find is usually spent working on PhotoDemon itself.

Of course, if you [follow PhotoDemon's development on GitHub](https://github.com/tannerhelland/PhotoDemon/commits/main), you know that interesting new features arrive every day.  As usual, this article just covers the tip of the iceberg with what's coming in the next release, but because this new interface toolkit has taken up so much development time, I thought it warranted a more detailed discussion.

As always, thank you to everyone [who donates to PhotoDemon's development](donate/).  Every donation, however small, means that much more time I can spend working on the program, so my sincerest **thank you** to everyone who's contributed.  PhotoDemon wouldn't be possible without you!

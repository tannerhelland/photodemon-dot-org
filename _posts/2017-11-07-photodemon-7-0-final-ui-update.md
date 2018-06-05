---
author: tanner_h
date: 2017-11-07 20:50:59+00:00
layout: post
slug: photodemon-7-0-final-ui-update
title: 'PhotoDemon 7.0: final UI update'
excerpt:  I've talked about PhotoDemon 7.0's new UI in the past, but this is one of those areas where words don't really do it justice.  So let's use pictures!
redirect_from:
  - /1588/photodemon-7-0-final-ui-update/
---

*(This is part of a series about PhotoDemon 7.0.  For the full 7.0 article collection, visit [this page](2017/11/28/photodemon-7-0-release).)*

I've [talked about PhotoDemon 7.0's new UI in the past](2016/05/02/building-a-consistent-user-interface-from-windows-xp-to-windows-10), but this is one of those areas where words don't really do it justice.

So let's use pictures!

![media/images/import/Themes-570x392.gif](media/images/import/Themes.gif)

The first time you run PhotoDemon, a Language and Theme window will be presented. You can choose between light and dark themes, various accent colors, and colored or monochrome icons. If in the future you want to switch to a new theme, no problem - use the Tools > Theme menu to see the choices again.

![media/images/import/monochrome_icons-1.png](media/images/import/monochrome_icons-1.png)

Monochrome icons are all the rage in 2017, so PhotoDemon now ships full light and dark monochrome icon sets.

One of the best things about PhotoDemon's language and theme engine is that changes are applied in real-time. Unlike other software, you don't need to restart the program after changing settings.

Theme support was a massive undertaking, because every element in the program - from buttons to sliders to toolbars to text labels - had to be constructed from scratch. For a project like PhotoDemon, there are more than fifty unique UI elements.  It takes me about a week to develop each element, which means theme support took some 50 * 7 = 350 days of work!

But now that it's *finally* finished, PhotoDemon can provide a consistent user experience across every version of Windows, including the latest Windows 10 developer builds.  Future Windows releases should not negatively impact the user experience, either, because we can manually mitigate any negative changes.

The switch to a custom UI kit has also made it possible to support many indirect enhancements that weren't feasible before, including...

  1. Tab key navigation on all dialogs. Press Tab to iterate through interactive controls (or Shift+Tab for reverse order).
  2. OK and Cancel buttons on any window can now be auto-triggered by the Enter and Esc keys. 
  3. Because everything in the project now runs on the same toolkit, we can pool many rendering resources. This means that the PhotoDemon 7.0 resource count at startup is actually _less_ than PhotoDemon 6.6, despite a huge number of new features.

  <table style="width: 100%;" >
<tbody >
<tr>
<td></td>
<td>User objects</td>
<td>GDI (graphics) objects</td>
</tr>
<tr>

<td>PhotoDemon 6.6
</td>

<td>630
</td>

<td>1,987
</td>
</tr>
<tr>

<td>PhotoDemon 7.0
</td>

<td>195
</td>

<td>279
</td>
</tr>
</tbody>
</table>

Besides freeing up memory, lighter resource counts also mean faster program startup time. On my primary development PC (which is now six years old), PhotoDemon's average startup time is less than two seconds.  I haven't seen another free photo editor that comes anywhere close to this, and keeping startup time to a minimum will always be an important goal.

[Return to the main PhotoDemon 7.0 release announcement](2017/11/28/photodemon-7-0-release)

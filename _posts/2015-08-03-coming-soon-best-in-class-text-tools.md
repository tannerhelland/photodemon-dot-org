---

author: tanner_h
date: 2015-08-03 16:44:54+00:00
layout: post
slug: coming-soon-best-in-class-text-tools
title: 'Coming soon: best-in-class text tools'
excerpt: Most photo editors have miserably poor text tools.  In PhotoDemon, I wanted to see if we could break this trend.  Here's a sneak peek at the result.
redirect_from:
  - /1232/coming-soon-best-in-class-text-tools/
---

It's been several months since I've posted a PD update, but not because work has slowed.  In fact, hundreds of new commits have landed over the summer, and there are now enough new features that it's time to start showing them off.

Today, we're going to talk about text tools.

## Most photo editors have miserably poor text tools

In my experience, text tools seem to fall into two categories:

1. Extremely basic and no fun at all.  You can type out text, change its font and color, and when you're done, "commit it" as a permanent layer.  Boooring.
2. Extremely complex and unwieldy.  You may be able to do neat things with text, but typically, you must first convert the text to a generic path or shape object.  Some typography controls may also be available (character and line spacing, line indentation, etc), but these features are often hit-and-miss.

In PhotoDemon, I wanted something better than this.  Text is a fundamental element of human communication, and in keeping with oue mantra of "simple but powerful", I hoped there was a better way to expose a full range of fun and professional text features, without making text tools so complicated that no one can figure out how to use them.

Here's a first look at the result.

## First, the basic Text Tool

After having conversations with various PD users, it became clear that a certain subset of people appreciate a no-frills text tool.  Paint.NET was mentioned as an example of this, as it allows you to add text quickly and easily, while having control over basic text parameters like font face, size, and color.  (Of course, Paint.NET is frustrating because once you stop editing a text layer, it gets converted to an image layer and you can no longer re-edit it.  Surely we can do better than that!)

For these users, PD now provides a very simple, "no frills" Text Tool:

![media/images/import/PD_basic_text_01-570x313.jpg](media/images/import/PD_basic_text_01.jpg) 

This tool allows you to modify the following parameters:

  * Font face
  * Font size (with sub-pixel accuracy)
  * Font style (bold, underline, italic, strikeout)
  * Color
  * Antialiasing (none, normal, crisp)
  * Clarity (antialiasing contrast)
  * Horizontal alignment (left, center, right)
  * Vertical alignment (top, middle, bottom)

The basic text tool also allows you to set a rectangular bounding region for each text layer.  You can move, resize, and rotate this region at any time, and text will automatically reflow to fit.  The region determines where the horizontal and vertical alignment calculations occur, so you can align text within any rectangular area of your choosing.

![media/images/import/PD_basic_text_02-570x313.jpg](media/images/import/PD_basic_text_02.jpg) *Here's a bunch of text layers in different languages.*

![media/images/import/PD_basic_text_03-570x313.jpg](media/images/import/PD_basic_text_03.jpg) *Here's the same layer, rotated and with new text added.*

One of the neat things about text rotation in PD is that you can freely edit text, even when it's rotated.  Text entry is handled by a dedicated edit box in the lower-left corner instead of on-canvas, meaning you can easily edit text regardless of its size or orientation.

As the above screenshot demonstrates, the basic text tool is fully Unicode compatible.  Font fallback is automatically provided, so if you enter characters unsupported by the current font, PD will substitute another font automatically, allowing you to mix-and-match languages with ease.

Finally, text layers in PhotoDemon are implemented using a new vector engine.  This means that text layers can be re-edited at any time, so fixing typos or rewriting text is a piece of cake.  (Shame on any software that doesn't work this way!)

## Next, the advanced Typography Tool

While the basic text tool is fun, it mostly exists for "quick and dirty" text tasks.  It manages a ton of behind-the-scenes settings for you, but what if you're the kind of user who _likes_ controlling every aspect of your text?

For you, I've created the Typography tool.

![media/images/import/PD_typography_01-570x327.jpg](media/images/import/PD_typography_01.jpg) *PhotoDemon's typography tool, with a variety of features activated*

Before we get into the things you can do with PD's typography tool, let me first discuss some of the technological underpinnings that make this tool possible.

Text rendering is complicated because it sits at the crossroads of a lot of complicated issues.

First, you need to process the user's keyboard input.  This is complicated when Unicode is involved, because the user should be able to freely intermix left-to-right and right-to-left text from any language of their choosing.  Also, basic concepts like what defines a "word" are important (e.g. for word-wrap, where words automatically wrap to the next line).  Western languages use spaces to define words, but some languages - like Thai - do not.  For Thai text, you have to use a dictionary to know where words break.

Next, you need to convert the user's input from the abstract concept of "letters" into actual "glyphs", which are the shapes that appear on-screen.  This step is important because fonts may not include glyphs for every possible character - for example, instead of a glyph for **à**, they may only provide a glyph for **a** and **`**, and it's up to the program to figure out how to combine those to form a new letter.

Once that's done, you must manage a whole bunch of font-specific settings.  The newer OpenType font format gives font creators extremely precise control over a font's appearance.  For example, a cursive-style font may contain a dozen different glyphs for the letter "e".  The font cleverly selects a specific "e" depending on the surrounding letters, to make sure text flows smoothly.

![media/images/import/PD_OpenType_Support-570x321.jpg](media/images/import/PD_OpenType_Support.jpg) *Text with and without OpenType support.  Look for subtle differences in the OpenType version, e.g. the way "p" and "e" smoothly flow together.*

Finally, I had a bunch of custom features I wanted PhotoDemon to provide.  This includes things like inter-character spacing, character orientation, line spacing and padding, and visual aspects like color and shading.  Because Windows does not provide native support for these features, they had to be implemented from scratch.

I bring this up for two reasons: to help explain why it's taken several months to get all this working, and to give you an idea of the detail involved in building a text tool "correctly."  After working on this over the summer, I can see why most photo editors don't go beyond basic text editing!

Of course, PhotoDemon is not "most photo editors."  ;)

The new Typography tool aims to give you control over all these detailed features.  This kind of precise editing may not matter to everyone, but for those who take text seriously, I hope they find PD's typography tool to be the best text tool they've ever used.

## Typography settings: an overview

PD's Typography tool breaks settings into three groups: character, paragraph, and visual.  Because there are so many settings, I felt it worthwhile to place each category into its own panel.  This allows you to ignore irrelevant settings, while quickly accessing the items important to you.

At all times, the text entry box remains on the left, so you can continue editing text while playing with any other settings.

Let's talk about each settings category in turn.

## Character-level settings

Character-level settings affect each character equally.  The most obvious set of character settings is font settings, which should be familiar at this point:

![media/images/import/PD_typography_settings_character_font-570x69.jpg](media/images/import/PD_typography_settings_character_font.jpg)

In addition to font settings, the Typography tool also provides a group of "special" character settings:

![media/images/import/PD_typography_settings_character_special-570x67.jpg](media/images/import/PD_typography_settings_character_special.jpg)

These include:
	
  * Remapping.  For Latin languages, this can automatically convert letters to their lower-, upper-, or title-case equivalents.  For CJK languages, you can autoconvert between traditional and simplified Chinese characters, or hiragana/katakana.	
  * Character spacing.  Move letters closer together or further apart.  This works in conjunction with kerning, so you do not lose kerning's benefits when modifying intercharacter spacing.
  * Orientation.  Rotate each letter individually.  In the screenshot at the top of this section, orientation was used to "tilt" the characters.
  * Jitter.  Randomly shift letters (horizontally and/or vertically) within the pixel grid.  Slight jitter mimics the behavior of typewriters, where mechanical realities prevent each character from being perfectly positioned.  I find that a slight amount of jitter gives text a bit more character, instead of looking too rigid and uniform.
  * Inflation.  Inflation treats letters like a balloon, inflating them along their edges.  In the screenshot at the top of this section, you can see how each letter is actually a swollen outline instead of a normal character.
  * Mirror.  Characters can be horizontally and/or vertically mirrored.

The crucial thing about these settings is that you can modify them at any time.  All typography features are non-destructive, so you can play with them to your heart's content, and revisit them at any point in the future.

## Paragraph-level settings

![media/images/import/PD_typography_settings_paragraph-570x86.jpg](media/images/import/PD_typography_settings_paragraph.jpg)

Paragraph-level settings are perhaps the least interesting of the bunch.  Options include:
	
  * Horizontal alignment	
  * Vertical alignment
  * Line wrapping ("wordwrap").  Options include no wrapping, manual linebreaks only, auto-wrap at character level, or auto-wrap at word level.  I believe all Unicode-compatible languages are supported; please notify me if you discover otherwise!
  * Horizontal and vertical padding.  These options are similar to CSS padding, and they define the amount of padding distance inserted between text and its boundary region.  Because typography layers allow you to auto-paint the text region background, this option may be helpful.
  * Line spacing.  This works in conjunction with the default line spacing specified by the font, allowing you to shrink or enlarge line spacing accordingly.

Still to-do are a few additional settings like paragraph indentation, but this should give you a good gist of the level of control PD provides over paragraph-level handling.

## Visual settings

The visual settings category presents two roughly identical panels - one for the text itself, and one for the text region background.

![media/images/import/PD_typography_visual_settings_text-570x74.jpg](media/images/import/PD_typography_visual_settings_text.jpg)

![media/images/import/PD_typography_visual_settings_background-570x74.jpg](media/images/import/PD_typography_visual_settings_background.jpg)

When you need text to "stand out" against a complex background, auto-filling its background comes in handy, so that's why background gets its own panel.  

These panels have gone through many iterations, and in their current form, they actually look quite simple.  You can toggle fill and outline for the text and/or background, or you can combine the two for fill + outline.

But the real fun begins when you click on the fill and outline boxes themselves.

## New universal fill settings

Implementing text tools in PD is about a lot more than just text (if you can believe it, given all the text stuff discussed above).

Text is very different from PD's existing feature set, because it involves something called **vector data**.  Traditionally, PhotoDemon has only dealt with **raster data**.  Raster data is a grid of pixels, with each pixel having its own color.  This grid of pixels can be manipulated in various ways, but only as a full grid.  If the grid shows a picture of, say, a circle, PD has no knowledge of the circle - only of the grid itself.

Vector data works differently.  Vector data is described not as a grid, but as a collection of mathematical formulas, like lines and curves.  These lines and curves represent distinct objects - circles, squares, or complex figures like letters or numbers.  Because PhotoDemon understands the geometry of these figures, it can manipulate that geometry in interesting ways.

Perhaps most interesting is that vector data clearly defines the "edges" and "shape" of an object.  This allows PD to trace text edges with extreme precision, for example, or to paint the shape in creative ways.  If the underlying font face or style is changed, no problem - PD just generates a new collection of geometric definitions, and seamlessly reapplies the outline and fill settings to the updated geometry.

Because PD stores text using vector data, I wanted to make sure that all the complicated vector work was reusable for future vector tools.  For example, PD still lacks shape tools, and a "pen" or "path"-type tool that allows you to create your vector outlines and objects.

To that end, the entire vector engine driving the new text tools is 100% reusable by future tools, starting with the universal fill dialog.

![media/images/import/PD_fill_solid-570x386.jpg](media/images/import/PD_fill_solid.jpg) *Solid fill settings are the least interesting of the bunch, but they're probably the most useful!*

Clicking on the "fill settings" box for either the text or text background raises a new universal fill dialog.  This dialog gives you three choices for filling your text (with more choices coming in the future).

First up is solid fills.  These paint the text with a single color and opacity.  Not too interesting, but honestly, it's the fill setting you'll probably use most often.  

Obviously, you can click on the color box to raise PD's standard color dialog.  A live preview is provided to give you an idea of how color + opacity work together.

![media/images/import/PD_fill_pattern-570x386.jpg](media/images/import/PD_fill_pattern.jpg)

Next is pattern fills.  If you've ever used Paint.NET's shape tool, this will be familiar to you.

This fill mode uses two colors to create - you guessed it - various patterns!

![media/images/import/PD_pattern_dropdown.jpg](media/images/import/PD_pattern_dropdown.jpg)

More than 50 patterns are provided, and the custom-built dropdown makes it easy to find one you like.

(Honestly, this setting is a little eclectic, but because other software provides it, I figured "why not" include it in PD, too?)

![media/images/import/PD_fill_gradient-570x386.jpg](media/images/import/PD_fill_gradient.jpg)

The third fill type is gradient fills.  This panel may not look like much, but that's because the real fun starts when you click on the new gradient editor control (the box on the left of the screenshot).

![media/images/import/PD_gradient_editor_01-570x418.jpg](media/images/import/PD_gradient_editor_01.jpg)

PhotoDemon now includes a full-featured gradient editor.  While this tool is still under heavy construction, enough of the UI is in place to give you an idea of how the final version will work.

The gradient editor allows you to construct your own gradients using a streamlined, straightforward interface.  Similar to other tools in PD (like Curves), new gradient nodes can be created by left-clicking anywhere in the interactive editor bar.  Right-clicking a node removes it.  You can add an unlimited number of nodes, each with their own color, opacity, and position.  Nodes can easily be dragged right and left to reorder or reposition them.

At present, a few different gradient shapes are also provided, and some support variable angles.  I'm still exploring the best way to present these shapes and features, so the final iteration may look different (especially if the number of shapes grows), but this should provide a good idea of what's possible.

![media/images/import/PD_gradient_linear-570x327.jpg](media/images/import/PD_gradient_linear.jpg) *Same gradient, but switched to a linear shape instead of radial.*

I'll also save the "automatic gradient" tab for another time.  Can't reveal all of PD's secrets just yet, you know?  ;)

What's so great about this universal fill dialog is that it works with any arbitrary shape.  Right now, PD only uses it for text tools, but in the future, all shape, arrow, path, and similar tools will have access to these features from day one.  Similarly, if I add a new fill feature (for example, texture fills are on my to-do list), all vector tools can automatically access that feature the day it lands.

## New universal outline settings

Because vector objects are defined by mathematical formulas, filling them isn't the only thing you can do.  You can also trace their outlines.  To that end, PD also includes a new universal outline dialog.

![media/images/import/PD_outline_01-570x388.jpg](media/images/import/PD_outline_01.jpg)

Like the fill dialog, the outline dialog works with any vector tool, including text.  It gives you strict control over how a shape is traced, with a live preview to help get a feel for how the various settings interact.

Besides a solid outline, combinations of dots and dashes are also supported.  The shape can be further controlled by specifying how to draw junctions between lines and curves, and how to draw the ends of those lines and curves.

![media/images/import/PD_outline_02-570x388.jpg](media/images/import/PD_outline_02.jpg) 

For example, here's a new outline, using triangular-shaped dots and dashes.

Just like fill changes, outline changes occur in real-time.  As you edit text, it is rendered on-screen with all your current settings automatically applied.  You can revisit fill and outline decisions at any time without losing your text edits, and as you rotate, resize, or move text, all visual features are automatically updated to match.

I am not aware of any other photo editor that provides this level of control over text appearance, while still keeping the text fully editable.  Yay for us!

## Much more to come

Like so many things in PD, this first draft of the new Text and Typography tools is just the tip of the iceberg.  These tools are still under heavy construction, so if you have ideas or suggestions for what you'd like to see in the next release, please [get in touch](about/contact/)!  There's still plenty of time for me to consider new features or additions to these tools.

For the extremely adventurous, the current text tool prototypes are available in [PD's development builds](download/).  There are still some bugs to resolve and some UI features to clean up, but if you don't mind a few hiccups, you're welcome to give the new tools a spin.  (And again: feedback is always welcome, even at these early stages.)

## While we're here...

Before wrapping this up, I just wanted to mention that some of the neat features you've seen today - like non-destructive text layer rotation - have also been extended to normal image layers.  Layers of any type can now be resized, rotated, and skewed non-destructively.  These changes required yet another rewrite of PD's viewport engine, but as a result, it's working faster than ever before, even with all these crazy features activated.  For the early adopters out there, performance on Windows 10 should be especially good.

Many thanks to all those who have donated to the PhotoDemon project, whether financially or with your time, feedback, or coding expertise.  Your donations are what make this project possible, and I hope the work we're doing remains worthy of your support!

As for a firm release date, I'm afraid the next official release is still a ways off, but I really appreciate your patience as I work on making PhotoDemon the best free photo editor money can('t) buy.  :)

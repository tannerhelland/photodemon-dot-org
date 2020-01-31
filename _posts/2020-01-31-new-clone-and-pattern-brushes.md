---
author: tanner_h
date: 2020-01-31 10:30:00+00:00
layout: post
slug: new-clone-and-pattern-brushes
title: Clone and Pattern Brush tools now available in nightly builds
excerpt: I'm excited to announce that the latest PhotoDemon nightly builds have (finally) received a long-requested feature - clone and pattern brush tools.  I'd love your help testing them.

---

I'm excited to announce that [the latest PhotoDemon nightly builds](https://photodemon.org/download/) have (finally) received a long-requested feature: clone and pattern brush tools.

For the unfamiliar, a [clone brush (or "clone stamp", as Photoshop calls it)](https://en.wikipedia.org/wiki/Clone_tool) allows you to paint directly on an image - but instead of painting with a solid color, a clone brush will instead paint from another location on the image - or perhaps from another image entirely!

Let me show a quick example.  This is a photo I took many years ago of a picture hanging on the wall of my grandparent's home.  Unfortunately, I took the photo at a slight angle, and the reflection from an overhead light caused a bright white spot to appear on the left side of the image:

![screen-capture](media/images/Clone_stamp_ex_1.png)
 
Let me show you how I used the new clone stamp tool to fix my mistake.

First, I corrected the skew of the photo (caused by my poor camera angle) by using PhotoDemon's `Effects > Transform > Perspective` menu, as in this animation:

![screen-capture](media/images/Clone_stamp_ex_2.gif)
 
By "pulling out" the bottom-left corner, the tool was able to project the image to a new, straighter vantage point.

Next, I realized I had inadvertently captured part of the picture frame at the top and bottom of the photo.  I didn't want these in the final result, so I removed them using the rectangular selection tool and the `Image > Crop to Selection` menu:

![screen-capture](media/images/Clone_stamp_ex_3.gif)
 
With the photo finally oriented correctly, I could now use the clone stamp tool to fix the white blob on the left.  

A clone brush works in two phases.  First, you must select the part of the image that you want to clone **from**.  In my case, I wanted to cover up the bright white reflection using the tan-colored background nearby.  (This looked like it would be the least-distracting way to "fill in" the blob.)  

To set a new source for the clone brush, just hold down the `Ctrl` key and click your desired source location.

With the source location set, all that's left to do was paint over the white spot!  Note that PhotoDemon's clone brush helpfully provides two outlines: one to show where I'm currently painting **to**, and another to show where the tool is cloning **from**.  

![screen-capture](media/images/Clone_stamp_ex_4.gif)

The end result looks much better, with no evidence that the horrible reflection ever existed:
 
![screen-capture](media/images/Clone_stamp_ex_final.png)

So that's a quick example of how the clone brush can help you "fix" an unwanted region of an image.

Of course, like most tools, clone tools can also be used for more creative purposes.  For example, let's talk about the popular technique of taking a photo and turning it black-and-white **except** for a single object.  Let's try it on this photo of a flower (a marigold, I think?).

![flower](media/images/flower.png)
 
First, load the photo into PhotoDemon.

Next, use the `Layer > Add > Duplicate of current layer` menu to create a copy of the photo.  

Then use the `Adjustments > Black and white` menu to turn the duplicate layer into a black-and-white photo.

Here is an animation showing these steps:

![screen-capture](media/images/Clone_stamp_flower_1.gif)
 
Next, we're going to use the clone tool in an interesting way.  Switch to the clone tool, make sure the `aligned` option is set, then select the original layer (the colored one) from the Layers toolbox.

*(What does the `aligned` option do?  It maintains the brush's alignment between strokes, instead of resetting each time you release the mouse.  For tasks like this, it's a lifesaver!)*

Hold down the `Ctrl` key, then click the center of the flower to set it as the source of the clone brush.

Then, switch back to the duplicate layer (the black-and-white one) by clicking it in the Layers toolbox.

Now, line up the two brush cursors, then paint over the flower!

With each stroke, the clone stamp "fills in" the painted area (on the black-and-white layer) with the contents of the source layer (the original color layer).  Pretty neat!

Here's a very quick-and-dirty demonstration of me attempting this technique.  You'll get better results if you take your time and use a few different brush sizes to paint the flower carefully.  I flew through it to keep the animation short.

![screen-capture](media/images/Clone_stamp_flower_2.gif)

I love how simple this technique is.

Like everything in PhotoDemon, I've tried to make the new clone brush tool as flexible as possible.  For example, you can clone from the current layer, or a different layer in the same image, or you can even clone from any layer in a *separate* image!  You can also sample from multiple layers at once by using the `sample all layers` option, and again, you can sample those layers from the *current* image or from *any other loaded image*.

PhotoDemon's clone stamp tool can also be used as a pattern brush tool.  The only difference between a clone brush and a pattern brush is that a pattern brush **tiles** the source image as you paint, allowing you to create an extended pattern.  Let me demonstrate this with an image of a fleur-de-lis, [courtesy of Wikipedia](https://en.wikipedia.org/wiki/Fleur-de-lis):

![fleur](media/images/Fleur_de_lys_(or).svg)

If I load the image into PhotoDemon, then create a new image with arbitrary dimensions, I can use the clone stamp tool with the `pattern` toggle to paint a repeating fleur-de-lis pattern, as in this short animation:

![screen-capture](media/images/Clone_stamp_fleur.gif)

Note that the `pattern` setting can tile in a basic pattern, or like the animation above, you can ask it to "flip" the image as it tiles.

Like PhotoDemon's regular paint brush tool, the new clone and pattern brush provides a number of other settings, including opacity, hardness (how "soft" the brush's edges are), ink flow, and blend and alpha modes.  The tool is also fully compatible with images and layers that contain transparency, and it also restricts itself to the currently selected region, if any.  

And that wraps up today's update!  To try the new clone tool, **[download the latest nightly build from PhotoDemon's download page](download/)**.  If you'd like to share feedback, please [file an issue at GitHub](https://github.com/tannerhelland/PhotoDemon/issues/new/choose).

Thank you, as always, for using PhotoDemon.  I hope you find the new clone and pattern brush useful.
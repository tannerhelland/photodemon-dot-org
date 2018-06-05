---
author: tanner_h
date: 2017-11-07 20:52:11+00:00
layout: post
slug: photodemon-7-0-new-adjustments-and-effects
title: 'PhotoDemon 7.0: new Adjustments and Effects'
excerpt: Even though new adjustments and effects weren't the focus of this release cycle, there were plenty of opportunities to make improvements.  A full list of adjustment and effect changes would require ten more articles as long as this one, but suffice it to say that in one way or another, every filter in the project has seen at least minor performance improvements, and many have received top-to-bottom overhauls.  Let's spotlight a few of the more interesting changes.
redirect_from:
  - /1639/photodemon-7-0-new-adjustments-and-effects/
---

*(This is part of a series about PhotoDemon 7.0.  For the full 7.0 article collection, visit [this page](2017/11/28/photodemon-7-0-release).)*

Even though new adjustments and effects weren't the focus of this release cycle, there were plenty of opportunities to make improvements.  A full list of adjustment and effect changes would require ten more articles as long as this one, but suffice it to say that in one way or another, every filter in the project has seen at least minor performance improvements, and many have received top-to-bottom overhauls.  Let's spotlight a few of the more interesting changes.

## New Effects

...Now that I see this list in its entirety, I guess I _did_ add quite a few new effects to this release.  Yikes!

![media/images/import/anisotropic_diffusion_sample-570x328.jpg](media/images/import/anisotropic_diffusion_sample.jpg) Effects > Noise > Anisotropic Diffusion

![media/images/import/color_halftone_sample-570x325.jpg](media/images/import/color_halftone_sample.jpg) Effects > Pixelate > Color Halftone

![media/images/import/crystallize_sample-570x325.jpg](media/images/import/crystallize_sample.jpg) Effects > Pixelate > Crystallize

![media/images/import/donut_sample-570x327.jpg](media/images/import/donut_sample.jpg) Effects > Distort > Donut

![media/images/import/harmonic_mean_sample-570x328.jpg](media/images/import/harmonic_mean_sample.jpg) Effects > Noise > Harmonic mean

![media/images/import/mean_shift_sample-570x328.jpg](media/images/import/mean_shift_sample.jpg) Effects > Noise > Mean-shift

![media/images/import/metal_sample-570x328.jpg](media/images/import/metal_sample.jpg) Effects > Nature  > Metal

![media/images/import/mezzotint_sample-570x328.jpg](media/images/import/mezzotint_sample.jpg) Effects > Pixelate > Mezzotint

![media/images/import/outline_sample-570x328.jpg](media/images/import/outline_sample.jpg) Effects > Stylize > Outline

![media/images/import/palettize_sample-570x348.jpg](media/images/import/palettize_sample.jpg) Effects > Stylize > Palettize

![media/images/import/plastic_wrap_sample-570x327.jpg](media/images/import/plastic_wrap_sample.jpg) Effects > Artistic > Plastic Wrap

![media/images/import/portrait_glow_sample-570x328.jpg](media/images/import/portrait_glow_sample.jpg) Effects > Stylize > Portrait Glow

![media/images/import/range_filter_sample-570x328.jpg](media/images/import/range_filter_sample.jpg) Effects > Edge > Range filter

![media/images/import/snow_sample-570x326.jpg](media/images/import/snow_sample.jpg) Effects > Nature > Snow

![media/images/import/snn_sample-570x328.jpg](media/images/import/snn_sample.jpg) Effects > Blur > Symmetric nearest-neighbor


## Improved adjustment tools

PhotoDemon's old Shadow/Highlight tool was pretty darn poor.  I feel bad that it shipped in its original state, so for 7.0, the entire algorithm has been reworked.  The new results are _so much better_ that I've promoted the tool to the main Adjustments menu, because I find myself using it all the time.

Here's a quick before/after example - notice how much detail the tool recovered in the shadowy portions of this image, particularly the tree trunks:

![media/images/import/shadow_highlight_sample2-456x570.jpg](media/images/import/shadow_highlight_sample2.jpg)

Best of all, RAW photos aren't required.  The sample image above is a standard 24-bpp JPEG c/o Bing's "image of the day".  

Another adjustment tool that really needed an overhaul was the old brightness/contrast tool.  Brightness and contrast were among the first digital photographic adjustments, and as technology has improved, so has our knowledge of their limitations.

To help new users who rely on this tool (instead of the more capable Levels or Curves tools), I've borrowed a page from the Photoshop playbook and added two modes to PhotoDemon's Brightness/Contrast tool: a "legacy" mode that uses the traditional algorithm, and a "modern" mode that uses the 3rd-party [LittleCMS library](http://www.littlecms.com/) to produce a much more intuitive result.  Here is a side-by-side comparison of the new brightness/contrast tool's results, when setting "brightness" to +75 and "contrast" to +50:

![media/images/import/brightness_contrast_comparison-570x321.jpg](media/images/import/brightness_contrast_comparison.jpg)


Notice how the modern algorithm retains the overall lighting scheme of the image, while gently modifying only the relevant colors.  The legacy tool, by contrast (pun intended), completely wrecks the lighting.

## No more bad "one-click" effects

In previous releases, PhotoDemon provided some silly "one-click" effects.  These effects offered no user-controllable options, which also meant no preview window where you could experiment before processing the full image.  

In this release, all remaining one-click effects have been rewritten as fully customizable, pro-grade tools.  Here are some examples of old one-click filters that are now full effects:

![media/images/import/film_noir_sample-570x328.jpg](media/images/import/film_noir_sample.jpg) Effects > Artistic > Film Noir

![media/images/import/antique_sample-570x325.jpg](media/images/import/antique_sample.jpg) Effects > Stylize > Antique

![media/images/import/atmosphere_sample-570x326.jpg](media/images/import/atmosphere_sample.jpg) Effects > Nature > Atmosphere


## Heavily improved or rewritten tools

As part of overhauling PhotoDemon's UI in this release, each tool needed to be revisited to ensure the new interface worked correctly.  This gave me a nice opportunity to revisit, expand, and optimize various tool options.  While there are too many changes to fully discuss, let me highlight some of the tools that have seen large improvements.

![media/images/import/add_noise_sample-570x326.jpg](media/images/import/add_noise_sample.jpg) Effects > Noise > Add noise

![media/images/import/rotation_sample-570x326.jpg](media/images/import/rotation_sample.jpg) Image > Rotate > Arbitrary

![media/images/import/correct_distortion_sample-570x334.jpg](media/images/import/correct_distortion_sample.jpg) Effects > Distort > Correct distortion

![media/images/import/equalize_histogram_sample-570x327.jpg](media/images/import/equalize_histogram_sample.jpg) Adjustments > Histogram > Equalize

![media/images/import/exposure_sample-570x328.jpg](media/images/import/exposure_sample.jpg) Adjustments > Photography > Exposure

![media/images/import/motion_blur_sample-570x328.jpg](media/images/import/motion_blur_sample.jpg) Effects > Blur > Motion blur

![media/images/import/sunshine_sample-570x327.jpg](media/images/import/sunshine_sample.jpg) 
Effects > Light and shadow > Sunshine

In addition to new features, many tools received significant performance enhancements.  For example...

  * Image > Rotate > Arbitrary is 2x faster
  * Adjustments > Color > Replace Color is 2x faster
  * Effects > Stylize > Vignetting is 3x faster
  * Effects > Nature > Fog is 4x faster
  * Image > Rotate > Straighten is 5x faster
  * Effects > Light and Shadow > Cross-screen is 6x faster
  * Effects > Blur > Motion Blur is 10x faster
  * Effects > Pixelate > Fragment is 20x faster

And those are just the improvements I tracked!  Almost every tool in the project should be faster than it was in 6.6, despite many tools offering new features and improved quality.

[Return to the main PhotoDemon 7.0 release announcement](2017/11/28/photodemon-7-0-release)

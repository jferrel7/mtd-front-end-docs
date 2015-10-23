---
layout: default
title: MTD Front-End Docs / Images
---

# Images

* [Overview](#overview)
* [Iconic Icons](#iconic-icons)
* [Responsive Images](#responsive-images)
* [FPO Images](#fpo-images)
* [Image File Locations](#image-file-locations)

## Iconic Icons

Natural Logic owns a license for the [Iconic icon set](https://useiconic.com/). In most cases we use SVG versions and in fewer cases we use the actual image files. 

Where possible, the SVG icons are preferred as we can set color and size properties via CSS. We have found that on filterable type pages where the results area HTML is injected using underscore.js that the image files are preferred as it prevents calling Iconic to inject the SVG icons.

Anytime an SVG icon is used, a fallback image is also needed for browsers that don't yet support SVG. See HTML example below:

*Example:*<br/>
<pre><code>&lt;img class="iconic thin-caret" data-src="/wcpics/Troy/en_US/thin-caret.svg" data-fallback="/wcpics/Troy/en_US/right-arrow.png" width="7px" height="11px" /&gt;
</code></pre>

## Responsive Images

All of the current responsive sites in our code repo have support for picture tag usage via the [picturefill polyfill](http://scottjehl.github.io/picturefill/). Picturefill allows us to use the picture element, srcset and sizes attributes on browsers that don't support them yet.

Retina images and non-retina images should be used to serve the appropriate image based on the devices capabilities. Here's an example pulled from the Troy-Bilt homepage. The example includes an IE 9 hack to allow it to work on IE9 browsers.

*Example:*<br/>
<pre><code>&lt;span class="img-wrap"&gt;   
  &lt;picture&gt;
    &lt;!--[if IE 9]&gt;&lt;video style="display: none;"&gt;&lt;![endif]--&gt;
    &lt;source srcset="/wcpics/Troy/en_US/homepage/lg/top-hero-flex-lg-1x.jpg 1x, /wcpics/Troy/en_US/homepage/lg/top-hero-flex-lg-2x.jpg 2x" media="(min-width: 60em)"&gt;
    &lt;!--[if IE 9]&gt;&lt;/video&gt;&lt;![endif]--&gt;
    &lt;img srcset="/wcpics/Troy/en_US/homepage/sm/top-hero-flex-sm-1x.jpg 1x, /wcpics/Troy/en_US/homepage/sm/top-hero-flex-sm-2x.jpg 2x"&gt;
  &lt;/picture&gt;
&lt;/span&gt;
</code></pre>

## FPO Images

To assist MTD engineers, FPO images should be clearly marked in a way so it's easily verifiable that an image is FPO. Either including FPO in the filename or placing the image in an FPO folder are acceptable ways to identify FPO images.

## Image File Locations

The following paths are where new responsive image files are stored in the mtd-shared-checkout repo.

* Troy-Bilt - `/public/wcpics/Troy/en_US`
* Cub Cadet - `/public/wcpics/CubCadet/images/r/` and `/public/wcpics/CubCadet/images/v2/`
* MTD Parts - `/public/wcpics/BuyMTDOnlineUS/en_US/images/v2`


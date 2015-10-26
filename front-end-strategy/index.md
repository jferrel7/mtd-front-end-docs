---
layout: default
title: MTD Front-End Docs / Front-End Strategy
---

# Front-End Strategy

* [Overview](#overview)
* [Strategy](#strategy)
  * [Siloing Global Header and Footer](#siloing-global-header-and-footer)
  * [Caching with AppCache](#caching-with-appcache)
  * [Route Based Resource Loading](#route-based-resource-loading)
  * [Lazy Loading Images](#lazy-loading-images)

## Overview

We are currently in the process of converting all MTD sites to be responsive. As part of the move to a responsive architecture, the front-end strategy has changed from our previous (legacy) approach.

## Strategy

Performance is no longer a nice thing to have, it is expected by search engines and users. Users may be browsing via a gigabit connection or via a 3G connection. In either case, the website should load in a timely manner. By only loading resources that a user needs for a given page, we can improve the page load performance. We can also lazy load images so they aren't requested until the page loads.

### Siloing Global Header and Footer

No matter which page a user goes to, it will always include a global site header and footer. With this in mind, we have siloed all CSS and Javascript that is required by a sites global header and footer. This includes all of our standard Javascript libraries as well. 

While working locally, we don't use the minified versions of the global CSS and Javascript. However, in production and on the Heroku preview site, the minified versions are used.

A normalized CSS file is included in the global CSS file so that all browsers behave in the same manner.

The following javascript libraries are included in the global minified javascript file and should be used wherever possible. Adding javascript libraries that perform duplicate functionality will hinder site performance and maintenance.

1. [**Iconic**](https://useiconic.com) - Injects SVG icons and provides fallback to images for browsers that don’t support SVG.
2. [**URI.js**](http://medialize.github.io/URI.js/) - Javascript library for working with and manipulating
URLs
3. [**Lazysizes**](https://github.com/aFarkas/lazysizes) - Lazy loader for images
(responsive and normal), iframes and more, that detects any visibility
changes triggered through user interaction, CSS or JavaScript without
configuration.
4. [**Velocity**](http://julian.com/research/velocity/) - An animation engine with the
best of jQuery and CSS transitions combined.
5. [**Hover Intent**](http://cherne.net/brian/resources/jquery.hoverIntent.html) -
Mega menu hover library that uses slight delay of mouseover event to
prevent accidental loading of mega menu content.
6. [**FastClick**](https://github.com/ftlabs/fastclick) - A library for eliminating the 300ms delay between a physical tap and the firing of a click event on mobile browsers.
7. [**Hammer**](http://hammerjs.github.io) - A library that can recognize gestures made by touch, mouse and pointerEvents.

### Caching with AppCache

Barring a complete redesign, the global header and footer's appearance and functionality should not change. Therefore, we cache all images, CSS and Javascript related to the global header and footer indefinitely using AppCache. 

If a change is needed to the global header and footer; we can invalidate our cache by bumping a version number in the Cache Manifest file.

A more [in depth explainer for AppCache at MTD](/front-end-strategy/app-cache.html) is available.

### Route Based Resource Loading

In order to provide the best performance we can, a page should only load images, CSS or Javascript that are needed for the given page, aka route. 

If the user is coming to the site via a link from a search they performed on Google for a product, we don't need to load any front-end code that is not related to the rendering of our site shell (global header and footer) or the product page that the user requested. 

### Lazy Loading Images

Where possible, we encourage using lazy loading of images. This technique allows the HTML document to be sent down to the user, and any images we need on the page will load once the HTML document is ready. Since no image src tags are specified, this makes the HTML document much smaller in file size thereby helpng perceived page load time. 

In combination with the picture tag, we can load art directed images for various screen sizes and account for retina images as well.
---
layout: default
title: MTD Front-End Docs / Javascript
---

# Javascript

* [Coding Style](#coding-style)
* [Common CSS Classes Used in the Javascript](#common-css-classes-used-in-the-javascript)
* [Common URL Query Parameters used in the Javascript](#common-url-query-parameters-used-in-the-javascript)
* [JS Libraries Included in global.min.js](#js-libraries-included-in-globalminjs)
* [JS File Locations](#js-file-locations)

## Coding Style

Custom javascript files use the object literal syntax currently. 

Function names should be descriptive enough so that when another developer reads the function name, it is clear what the function does.

Javascript files are broken down into logical components. That could be a page or certain group of pages that have shared JS functionality, like Knowledge Center (e.g. `/public/wcsstore/Troy/javascript/r/components/knowledge-center.js`). Or whether it is more component based and used on many pages, like Product Ratings stars (`/public/wcsstore/Cub/javascript/components/product-ratings.js`). 

The following items also highlight some javascript best practices we attempt to follow.

* Cache jQuery lookups on page load where possible.
* Keep variables within functions unless the variable needs to be accessed by other functions.
* When binding to events, consider the number of possible elements on the page that your code will apply to. If there could be more than 2-3 elements, than scope the event to the document body or other wrapping HTML element so you can apply the event like below. The technique below would only apply one event, which is much better for performance.

*Example:*
<pre><code>$filterContainer.on('click', '.' + filterCategoryClass, function(e) {
  e.preventDefault();
  ...
}
</code></pre>

## Common CSS Classes Used in the Javascript

There are various shared and common CSS classes that enevitably need to be used in the javascript. We keep these various classes in global-site.js (which is bundled in global.min.js) so that they aren't littered over all of our other javascript files. Here's an example from the current Cub Cadet global-site.js:

*Example:*
<pre><code>var activeClass = 'active',
    expandedClass = 'expanded',
    hideClass = 'hide',
    invalidClass = 'invalid',
    openClass = 'open',
    showClass = 'show',
    toggleClass = 'toggle';

  cubcadet.css = {
    active: activeClass,
    expanded: expandedClass,
    hide: hideClass,
    invalid: invalidClass,
    open: openClass,
    show: showClass,
    toggle: toggleClass
  }
</code></pre>

To access these CSS class names from your javascript file, use the code snippet below as a reference and substitute whichever class name you need. We are using the "active" class name below:

*Example:*
<pre><code>$btnSearch.removeClass(cubcadet.css.active);
</code></pre>

## Common URL Query Parameters used in the Javascript

As with CSS class names, we often need to refer to query parameters that apply to WebSphere Commerce. We want to keep our JS code so that it matches query parameters used in Commerce so we keep those query parameter's in global-site.js as well.

*Example:*
<pre><code>  troybilt.urlParams = {
    searchTerm: 'searchTerm'
  }
</code></pre>

To access a URL param that is stored in global-site.js in your javascript file, use the snippet bleow as a reference. We are accessing the "searchTerm" query parameter.

*Example:*
<pre><code>url.setQuery(TROYBILT.urlParams.searchTerm, $searchInput.val());
</code></pre>

## JS Libraries Included in global.min.js

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
7. [**Hammer**](http://hammerjs.github.io) - Only used on Troy-Bilt currently. A library that can recognize gestures made by touch, mouse and pointerEvents.

## JS File Locations

The following paths are where new responsive JS files are stored in the mtd-shared-checkout repo for each site.

* Troy-Bilt Global Header and Footer JS - `/public/wcsstore/Troy/javascript/r/`
* Troy-Bilt Page or Component JS - `/public/wcsstore/Troy/javascript/r/components/`
* Cub Cadet Global Header and Footer JS - `/public/wcsstore/Cub/javascript/r/`
* Cub Cadet Page or Component JS - `/public/wcsstore/Cub/javascript/components/`
* MTD Parts Global Header and Footer JS - `/public/wcsstore/BuyMTDOnlineUS/javascript/r/`
* MTD Parts Page or Component JS - `/public/wcsstore/BuyMTDOnlineUS/javascript/r/components/`

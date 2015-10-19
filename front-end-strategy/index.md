---
layout: default
title: MTD Front-End Docs / Front-End Strategy
---

# Front-End Strategy

* [Overview](#instructions-for-windows)
* [Strategy](#instructions-for-mac)

## Overview

We are currently in the process of converting all MTD sites to be responsive. As part of the move to a responsive architecture, the front-end strategy has changed from our previous (legacy) approach.

## Strategy

Performance is no longer a nice thing to have, it is expected by search engines and users. Users may be browsing via a gigabit connection or via a 3G connection. In either case, the website should load in a timely manner. By only loading resources that a user needs for a given page, we can improve the page load performance. We can also lazy load images so they aren't requested until the page loads.

### Global Header and Footers Isolated

No matter which page a user goes to, it will always include a global site header and footer. With this in mind, we have isolated and encapsulated all CSS and Javascript that is required by the sites global header and footer. This includes all of our standard Javascript libraries as well. 

### Caching with AppCache

Barring a complete redesign, the global header and footer's appearance and functionality should not change. Therefore, we cache all images, CSS and Javascript related to the global header and footer indefinitely using AppCache. 

If a change is needed to the global header and footer; we can invalidate our cache by bumping a version number in the Cache Manifest file.

A more [in depth explainer for AppCache at MTD](/front-end-strategy/app-cache.html) is available.

### Route Based Resource Loading

In order to provide the best performance we can, a page should only load images, CSS or Javascript that are needed for the given page, aka route. 

If the user is coming to the site via a link from a search they performed on Google for a product, we don't need to load any front-end code that is not related to the rendering of our site shell (global header and footer) or the product page. 
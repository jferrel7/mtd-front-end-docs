---
layout: default
title: MTD Front-End Docs / Build Process
---

# Build Process

* [Grunt](#grunt)
* [Concatenation and Minification](#concatentation-and-minification)

## Grunt

[Grunt](http://gruntjs.com/) is currently used as the build tool of choice on all MTD front-end sites. 

Each site includes a `responsive-build` directory in the wcstore brand folders (e.g. `/public/wcsstore/Troy/responsive-build`). This directory includes the Grunt configuration file and is where concatenated and minfied files are written too when the grunt task is ran.

The grunt task is only needed if and when a change is made to normalize.css, global-base.css, global-site.js, global-header.js or global-footer.js.

## Concatenation and Minification

Currently, only resources used by the global header and footer are included in concatenation and minification tasks. For JS, the grunt config file includes all of our [standard JS libraries](/javascript/#js-libraries-included-in-globalminjs) as well.

global.min.js and global.min.css are the names of the files produced when running the grunt task. 

At some point in the future, we may want to try and concatenate and minfiy other "bundles" to support our route based loading of CSS and JS. However, we are not at that point yet and need to get the current front-end strategy in place and functioning.

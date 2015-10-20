---
layout: default
title: MTD Front-End Docs / MTD AppCache Explainer
---

# MTD AppCache Explainer

## What is AppCache?

HTML5 provides an application caching mechanism that stores resources (images, css,
javascript) on the device of the site being viewed. Developers can use the AppCache interface
to specify which resources should be cached.

## What benefits can be achieved by using AppCache?

**Speed**: cached resources are stored physically on the device, and therefore load faster

**Reduced server load**: the browser only downloads resources that have changed from the
server

**Offline-ready**: since resources are cached locally, the site can load resources without an
internet connection. Making the MTD sites work fully offline would require more work to account
for content, etc; but getting started down that path now makes sense.

## What do we want to cache now?

We want to cache images, CSS and Javascript files which are needed for the site shell, the
global header and footer.

Caching these resources will greatly improve the perceived load time for each site.

## How does it work?

Typically, you would specify a path to the AppCache manifest file from the HTML document.
This approach has one major drawback, it would also cache the HTML document itself. We
don’t want the HTML document cached so we are using an alternative approach.

We use a javascript library named appcache-nanny, instead of having to specify the manifest
file. The script dynamically loads an iframe that includes an HTML file which contains a
reference to our app cache manifest file. This approach allows us to cache the resources we
want to, but not cache our HTML document that has actual real content in it.

Currently, we have created a manifest directory in /wcsstore/[brand] folder. It contains two files,
appcache-loader.html and manifest.appcache.

appcache-loader.html is the file that gets loaded into the iframe by appcache-nanny.js
manifest.appcache contains the list of files we want cached. Note: Your web server will probably
need to be configured so that files with the extension .appcache are served with the mime type
of “text/cache-manifest”.

## How do we invalidate the cache when needed?

The manifest.appcache allows us to invalidate the cache. By simply bumping the version number
inside the file. We currently do this manually, as it typically shouldn’t be invalidated very
frequently.
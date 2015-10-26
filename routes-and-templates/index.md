---
layout: default
title: MTD Front-End Docs / Routes &amp; Templates
---

# Routes &amp; Templates

* [Sinatra](#sinatra)
* [Routes](#routes)
* [Templates](#templates)
* [Route Based CSS and JS](#route-based-css-and-js)
* [Models](#models)
* [Device Type Detection](#device-type-detection)
* [Multilingual](#multilingual)


## Sinatra

The front-end code is powered by [Sinatra](http://www.sinatrarb.com), a Ruby based gem for creating web applications. 

## Routes

Using the *app.rb* file in root of the repo, we can add routes (e.g. /troybilt/products/detail) that render the templates we want. Routes can be get, post, put, patch, delete. Any HTTP method is achievable.

Routes for newer responsive sites are stored near the top of the file. They are grouped by brand so they are easily findable.

## Templates

All templates are stored in the views directory as .erb files. The views folder contains directories for each site.

Any new responsive template, should be stored in views/brand/responsive folder. When we complete making all of the sites responsive, we will delete any old templates that remain outside of the views/brand/responsive folders.

We use layout files to place global header and footers on all sites. Each brand's layout file is included in their respective responsive folders.

When new templates are added, please update any links in the site's global header or footers as necessary. We want the front-end site to be as close to production as possible, so links should go to pages that exist. For example, the Parts and Support page exists for the Troy-Bilt site, so we updated the global header so that clicking on Parts and Support in the header takes us to that page.

## Route Based CSS and JS

Each individual route is responsible for adding the necessary CSS and JS to include on the page. See our [front-end strategy](/front-end) section for more information on why we chose this approach.

For example, on the Troy-Bilt homepage route (e.g. /troybilt), we use a Ruby array variable @cssIncldes to include our homepage.css file. The layout file is already setup to check for our CSS and JS variables and will include them when the route is rendered.

*Example*
<pre><code>@cssIncludes = ['/wcsstore/Troy/css/r/homepage.css']
</code></pre>

An identical approach is used for JS files that are needed for a given route. The code below is needed for the Troy-Bilt Knowledge Center routes.

*Example*
<pre><code>@jsIncludes = ['/wcsstore/Troy/javascript/r/components/knowledge-center.js']
</code></pre>

## Models

In some cases, we use Ruby models to allow us to mock the Websphere Commerce functionality. That might be rendering content for products or adding an item to the cart. Models provide an easy way to make the front-end environment as close to Commerce as possible so minimal or no changes to any front-end files are required by MTD Engineers.

## Device Type Detection

In some cases, we need to render different HTML based on the device type the site is being used on. This doesn't happen often, but is a handy tool to have available. The device detection is not dynamic on the local development environment, only the Heroku web server. 

Inside app.rb, in the `before do` section, we have 3 boolean variables (@isMobileDevice, @isTabletDevice, and @isDesktopDevice). When working in the local development environment, just set the variables how you need them.

The Heroku environment, [https://mtdp.co](https://mtdp.co), uses the Wurfl Cloud gem to dynamically detect the device type and set our variables appropriately. 

## Multilingual

The Sinatra app is also setup to support multilingual sites. The language files that contain keys and translations are stored in the locales directory located in the root of the repo. There is an English and French file currently. The keys are organized alphabetically.

The Troy-Bilt layout file provides a good blueprint for using the multilingual capabilities. 

*Example*
<pre><code><%=I18n.t :order_tracking %>
</code></pre>
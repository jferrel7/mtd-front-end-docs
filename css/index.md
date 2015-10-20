---
layout: default
title: MTD Front-End Docs / CSS
---

# CSS

* [Coding Style](#coding-style)
* [Namespacing](#namespacing)
* [Using REMs](#using-rems)
* [Common Elements](#common-elements)
* [CSS File Locations](#css-file-locations)

## Coding Style

Use existing responsive CSS files as guides for any updates needed or for new CSS files. Here are some coding styles to follow as well:

* Only use one CSS selector per line when multiple elements are targeted using a single style block. This keeps the CSS easy to read and maintain.
* Use 2 spaces for tabs
* Keep style blocks and selectors indented (including inside media query blocks) appropriately for better readability.
* Place comments at the top of new CSS files that describe the intended usage.
* Comments throughout the remainder of the CSS file should be used sparingly and only when absolutely necessary so we don't cause bloat in the file.
* When adding a media query, use em to specify any sizes. Place a comment directly above the media query to indicate the pixel size.

## Namespacing 

In order to separate styles logically and to avoid conflicts with other styles that could be on a page, we use namespacing heavily to help avoid issues and keep our CSS stored in a modular manner.

We use class names prefixed with `.r-` for our first selector of a page or component. All styles that relate to that page or component should use that selector to set any styles within the page or component. 

The remainder of a namespaced class name might be like `.r-home` for homepage, `.r-kc` for Knowledge Center. The important part is that all CSS styles use this prefix for a given page or component so that we avoid style conflicts and any given page has as few dependencies on other code elsewhere.

An example: setting an h1 style on the homepage, the selector would be `.r-home h1`. 

## Using REMs

We use REMs to specify font sizes, line height, padding and margins. 

An element with a font-size of 1rem is equal to 16px. 

An element with a line-height of 1.5rem is equal to 24px.

## Common Elements

Elements like buttons (class name = button) or breadcrumbs generally already have styles that exist in global-content.css or in some cases global-base.css. 

Adding new common elements to global-content.css should be done only when truly needed. Please use restraint from going overboard with adding new code to global-content.css. 

## CSS File Locations

The following paths are where new responsive CSS files are stored in the mtd-shared-checkout repo.

* Troy-Bilt - `/public/wcsstore/Troy/css/r/`
* Cub Cadet - `/public/wcsstore/Cub/css/r/`
* MTD Parts - `/public/wcsstore/BuyMTDOnlineUS/css/r/`

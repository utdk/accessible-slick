accessible-slick
----------------

_the last (accessible) carousel you'll ever need_

A fully accessible, WCAG 2.0 / 2.1 compliant, drop-in replacement for Slick Slider (1.8.1) intended to make life easier for real-world dev teams who need to pass accessibility audits.

This package implements [accessibility and usability improvements](#what-makes-this-accessible) crafted and tested by native screen reader users and expert accessibility consultants at [Accessible360](https://accessible360.com) based on their experiences helping to make hundreds of carousels accessible for clients around the world. Read on to learn more about [why this package exists](#why-is-this-needed), its [features](#what-makes-this-accesible), [how to use it](#usage), and how you can get involved!

#### Demo

https://accessible360.github.io/accessible-slick

#### CDN

##### Example using jsDelivr

Just add a link to the css file in your `<head>`:

```html
TODO: pending publish to NPM
```

Then, before your closing `<body>` tag add:

```html
TODO: pending publish to NPM
```

#### Package Managers

```sh
TODO: pending publish to NPM
```

## Why is this needed?

Almost by design, carousels are pretty hard for screen reader users (especially newbies) to understand and interact with successfully, let alone enjoy. Its hard to know where slides begin and end, how the slide navigation dots work, or where the various controls are. Carousels also vary quite a bit between sites or even just between pages, so it can be difficult for screen reader users to build up a reliable mental model that applies to ALL carousels. And let's not even get started on on autoplay functionality ([WCAG 2.2.2](https://www.w3.org/WAI/WCAG21/Understanding/pause-stop-hide.html), anyone?)!

As one of the most widely used carousel packages out there, Slick Slider has many of these same accessibility issues, making it a consistent source of frustration for dev teams when they go through an accessibility audit. Efforts have been made in the Slick Slider repo to improve these issues (especially in version 1.8.1), but those efforts have also introduced new accessibility issues too!

In the long term it'd be great to contribute some improvements to the core Slick Slider repo, but that may or may not be possible considering it's [been abandoned](https://github.com/kenwheeler/slick/graphs/code-frequency) (but not deprecated) by it's original author since 2016. A maintainer or two has recently stepped up to resume development, but with over [1,000 open issues](https://github.com/kenwheeler/slick/issues?q=is%3Aissue+is%3Aopen+accessibility) and nearly [200 open PRs](https://github.com/kenwheeler/slick/pulls?q=is%3Apr+is%3Aopen+accessibility) (some with conflicting approaches), its unlikely that the big fixes needed will make their way to the master branch any time soon.

In the short term, we're releasing our take on an accessible Slick Slider implementation as a fork that respects the original functionality and API features as much as possible so you can improve the accessibility of your carousels **right now**! We'll make it available through all the same channels (like NPM and jsDelivr) so upgrading is as easy as changing the URLs in your `<link>` and `<script>` tags without having to even _touch_ your existing JavaScript code!


## What makes this accessible?

`TODO`

### New features ✨

Feature | Why
--------|----
Wrapper now has `role="region"` and a configurable `aria-label` | Tells screen reader users exactly where the carousel begins and ends in the DOM and gives them a landmark they can jump to or skip easily. Use the [`regionLabel` setting](#new-settings) to change the `aria-label` text (defaults to `'carousel'`).

### Feature changes ⚠️

`TODO: list out changes made to original package with reasoning.`

### Deprecated features ❌

`TODO: list out old features that no longer do anything.`

## Usage

All of the original settings, events, and other API features are available, so your existing configurations won't need to be tweaked at all! Refer to the original Slick Slider documentation to see how to use them:

* [Data attribute settings](https://github.com/kenwheeler/slick#data-attribute-settings)
* [Settings](https://github.com/kenwheeler/slick#settings)
* [Events](https://github.com/kenwheeler/slick#events)
* [Methods](https://github.com/kenwheeler/slick#methods)

### New settings

Setting | Type | Default | Description
--------|------|---------|------------
regionLabel | string | 'carousel' | Text to use for the `aria-label` that is placed on the wrapper (see [New features](#new-features) section for details).


## Development
If you'd like to contribute changes or just make modifications for your own use, use the following process:

1. Install all the dev dependencies with NPM:

```sh
npm install
```

2. Make your changes to the source files. You'll want to focus on:
    * `slick/slick.js`
    * `slick/slick.scss`
    * `slick/slick-theme.scss`

3. Build! Multiple build systems are available to help with future-proofing. Use whichever one you like - the output is the same!

```sh
# Build with Gulp (see gulpfile.js)
gulp

# OR build with Grunt (see gruntfile.js)
grunt
```

4. Check your changes by loading up `docs/index.html` in your browser.
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
[Wrapper](https://github.com/Accessible360/accessible-slick/issues/7) now has `role="region"` and a configurable `aria-label`. | Tells screen reader users exactly where the carousel begins and ends in the DOM and gives them a landmark they can jump to or skip easily. Use the [`regionLabel` setting](#new-settings-) to change the `aria-label` text (defaults to `'carousel'`).
[Each slide](https://github.com/Accessible360/accessible-slick/issues/9) now has `role="group"` with a generic, numbered `aria-label`. | Tells screen reader users exactly where each individual slide begins and ends in the DOM. It should fit the vast majority of use cases, but if you _really_ want to disable it you can do so with the new [`useGroupRole` setting](#new-settings-).

### Feature changes ⚠️

Feature | Why
--------|----
[Previous and Next button markup](https://github.com/Accessible360/accessible-slick/issues/8) improved to no longer use `aria-label`, and to safely hide the icons from screen readers. | See the [First Rule of ARIA Use](https://www.w3.org/TR/using-aria/#rule1). Also, custom font icons are read out as "unrecognizable characters" by screen readers, so they need to be hidden from them.
Tab markup is no longer used for [slide dots](https://github.com/Accessible360/accessible-slick/issues/10) or [slides](https://github.com/Accessible360/accessible-slick/issues/9). | Carousels don't look like tabs, so real users wouldn't expect them to work like tabs. Especially when there are multiple slides visible at a time.
Keyboard navigation with the `Left` and `Right` arrow keys [has been removed](https://github.com/Accessible360/accessible-slick/issues/15). | The `Left` and `Right` keys are already used by screen readers for virtual cursor navigation, and other users have no reason to expect this functionality exists without visible instructions or clues.


## Usage

All of the original events and methods, and most of the original settings, still work great so your existing configurations won't need to be tweaked at all! Refer to the original Slick Slider documentation to see how to use them:

* [Data attribute settings](https://github.com/kenwheeler/slick#data-attribute-settings)
* [Settings](https://github.com/kenwheeler/slick#settings)
* [Events](https://github.com/kenwheeler/slick#events)
* [Methods](https://github.com/kenwheeler/slick#methods)

A couple new settings have been added, and a few problematic ones have been deprecated. Sliders with these settings passed in will still work great (better, actually), and will now come with soft console warnings alerting you about them.

### New settings ✨

Setting | Type | Default | Description
--------|------|---------|------------
regionLabel | string | 'carousel' | Text to use for the `aria-label` that is placed on the wrapper.
useGroupRole | boolean | true | Controls whether `role="group"` and an `aria-label` are applied to each slide.

### Deprecated settings ❌

Setting | Reason(s)
--------|----------
focusOnChange | Per [WCAG 3.2.2](https://www.w3.org/WAI/WCAG21/Understanding/on-input.html) and user research, keyboard focus should never be moved unless the user is told ahead of time. Even if explaining, moving focus like this would suck for keyboard users, so this setting had to go. [See issue #11](https://github.com/Accessible360/accessible-slick/issues/11).
focusOnSelect | Unnecessary since keyboard navigation has been removed. Even with keyboard navigation, tab stops on non-actionable elements is very strange for keyboard users, and really just adds work for them. [See issue #11](https://github.com/Accessible360/accessible-slick/issues/11).
accessibility | Equal access should not be a feature that can be turned off. This setting actually made the slides _less_ accessible by introducing unintuitive tab markup, keyboard navigation that conflicts with screen readers, and more. [See issue #12](https://github.com/Accessible360/accessible-slick/issues/12).


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
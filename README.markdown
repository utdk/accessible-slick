accessible-slick
----------------

_the last (accessible) carousel you'll ever need_

A fully accessible, WCAG 2.0 / 2.1 compliant, drop-in replacement for Slick Slider (1.8.1) intended to make life easier for real-world dev teams who need to pass accessibility audits.

This package implements [accessibility and usability improvements](#what-makes-this-accessible) crafted and tested by native screen reader users and expert accessibility consultants at [Accessible360](https://accessible360.com) based on their experiences helping to make hundreds of carousels accessible for clients around the world. Read on to learn more about [why this package exists](#why-is-this-needed), its [features](#what-makes-this-accesible), [how to use it](#usage), and [how you can get involved!](#contributing)

#### Demo

https://accessible360.github.io/accessible-slick

Also check out this [collection of ready-to-use demos on CodePen](https://codepen.io/collection/nwRGZk) for common scenarios like hero banners, scrolling product cards, PDP thumbnail images, and more!

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

This package implements the following changes, all of which have been tested and discussed with Accessible360's team of native screen reader users, low-vision keyboard-only users, and experienced accessibility engineers:

### New features ✨

<table>
  <thead>
    <tr>
      <th scope="col" width="40%" align="left">Feature</th>
      <th scope="col" align="left">Why</th>
    </tr>
  </thead>
  <tbody>
    <tr valign="top">
      <th scope="row" align="left"><a href="https://github.com/Accessible360/accessible-slick/issues/7">Wrapper</a> now has <code>role="region"</code> and a configurable <code>aria-label</code>.</th>
      <td>Tells screen reader users exactly where the carousel begins and ends in the DOM and gives them a landmark they can jump to or skip easily. Use the <a href="#new-settings-"><code>regionLabel</code> setting</a> to change the <code>aria-label</code> text (defaults to <code>'carousel'</code>).</td>
    </tr>
    <tr valign="top">
      <th scope="row" align="left"><a href="https://github.com/Accessible360/accessible-slick/issues/9">Each slide</a> now has <code>role="group"</code> with a generic, numbered <code>aria-label</code>.</th>
      <td>Tells screen reader users exactly where each individual slide begins and ends in the DOM. It should fit the vast majority of use cases, but if you <em>really</em> want to disable it you can do so with the new <a href="#new-settings-"><code>useGroupRole</code> setting</a>.</td>
    </tr>
    <tr valign="top">
      <th scope="row" align="left">Enabling autoplay now automatically adds a <a href="https://github.com/Accessible360/accessible-slick/issues/13">pause/play toggle button</a> as the first focusable element (with <a href="https://github.com/Accessible360/accessible-slick/issues/20">customizable icons</a>!).</th>
      <td><a href="https://www.w3.org/WAI/WCAG21/Understanding/pause-stop-hide.html">WCAG 2.2.2</a> requires that all auto-updating content comes with a way to pause, stop, or hide it. For carousels, pause/play icon buttons are the most familiar option. Since autoplay is so disruptive for keyboard and screen reader users, as well as people with certain cognitive conditions, the button is the very first piece of content in the slider so it can be reached right away.</td>
    </tr>
    <tr valign="top">
      <th scope="row" align="left"><a href="https://github.com/Accessible360/accessible-slick/issues/18">Instructions can be now provided</a> for screen reader users</th>
      <td>If your slider uses complex logic or unconventional interaction behaviors, there is a good chance that screen reader users will have an especially hard time figuring it out. If you're using the `asNavFor` setting or any of the API methods/events, you should probably explain how your carousel works to screen reader users.</td>
    </tr>
  </tbody>
</table>

### Feature changes ⚠️

<table>
  <thead>
    <tr>
      <th scope="col" width="40%" align="left">Feature</th>
      <th scope="col" align="left">Why</th>
    </tr>
  </thead>
  <tbody>
    <tr valign="top">
      <th scope="row" align="left"><a href="https://github.com/Accessible360/accessible-slick/issues/8">Previous and Next button markup</a> improved to use less ARIA and to safely hide the icons from screen readers.</th>
      <td>Per the <a href="https://www.w3.org/TR/using-aria/#rule1">First Rule of ARIA Use</a>, <code>aria-label</code> has been removed in favor of inner screen-reader-only text. Also, the HTML5 <code>disabled</code> is now used instead of <code>aria-disabled</code> for more consistency across all input modalities. Finally, the custom icons are attached to inner <code>span</code>s that are properly hidden from screen readers with <code>aria-hidden</code>.</td>
    </tr>
    <tr valign="top">
      <th scope="row" align="left">Tab markup is no longer used for <a href="https://github.com/Accessible360/accessible-slick/issues/10">slide dots</a> or <a href="https://github.com/Accessible360/accessible-slick/issues/9">slides</a>.</th>
      <td>Carousels <a href="https://www.w3.org/TR/wai-aria-practices-1.1/examples/tabs/tabs-1/tabs.html">don't look like tabs</a>, so real users wouldn't expect them to work like tabs, especially when there are multiple slides visible at a time.</td>
    </tr>
    <tr valign="top">
      <th scope="row" align="left">Keyboard navigation with the <code>Left</code> and <code>Right</code> arrow keys <a href="https://github.com/Accessible360/accessible-slick/issues/15">has been removed</a>.</th>
      <td>The <code>Left</code> and <code>Right</code> keys are already used by screen readers for virtual cursor navigation, and other users have no reason to expect this functionality exists without visible instructions or clues.</td>
    </tr>
  </tbody>
</table>


## Usage

All of the original events and methods, and most of the original settings, are still available and work as expected, so your existing configurations won't need to be updated at all! Refer to the original Slick Slider documentation to see how to use them:

* [Data attribute settings](https://github.com/kenwheeler/slick#data-attribute-settings)
* [Settings](https://github.com/kenwheeler/slick#settings)
* [Events](https://github.com/kenwheeler/slick#events)
* [Methods](https://github.com/kenwheeler/slick#methods)

### New settings ✨
In addition the original functionality, the following new settings have been added:

Setting | Type | Default | Description
:-------|:-----|:--------|:-----------
regionLabel | string | 'carousel' | Text to use for the `aria-label` that is placed on the wrapper.
useGroupRole | boolean | true | Controls whether `role="group"` and an `aria-label` are applied to each slide.
useAutoplayToggleButton | boolean | true | Controls whether a pause/play icon button is added when autoplay is enabled. Setting this to `false` without providing an alternative control would likely violate [WCAG 2.2.2](https://www.w3.org/WAI/WCAG21/Understanding/pause-stop-hide.html), so be careful!
instructionsText | string | `null` | Instructions for screen reader users placed at the very beginning of the slider markup. **If you are using `asNavFor` or adding custom functionality with API methods/events, you probably need to supply instructions!**
pauseIcon | string (html \| jQuery selector) \| object (DOM node \| jQuery object) | `<span class="slick-pause-icon" aria-hidden="true"></span>` | Custom element to use as the "pause" icon inside the autoplay pause/play toggle button, when `autoplay` is enabled.
playIcon | string (html \| jQuery selector) \| object (DOM node \| jQuery object) | `<span class="slick-play-icon" aria-hidden="true"></span>` | Custom element to use as the "play" icon inside the autoplay pause/play toggle button, when `autoplay` is enabled.

### Deprecated settings ❌
The following settings have been removed from the API, but if you pass them in through your initialization function or data attributes nothing bad will happen! If any of these settings are passed in, you'll just get a soft console warning letting you know that the setting is no longer relevant.

Setting | Reason(s)
:-------|:---------
accessibility | Equal access should not be a feature that can be turned off. This setting actually made the slides _less_ accessible by introducing unintuitive tab markup, keyboard navigation that conflicts with screen readers, and more. [See issue #12](https://github.com/Accessible360/accessible-slick/issues/12).
focusOnChange | Per [WCAG 3.2.2](https://www.w3.org/WAI/WCAG21/Understanding/on-input.html) and user research, keyboard focus should never be moved unless the user is told ahead of time. Even when explained, moving focus like this would suck for keyboard users, so this setting had to go. [See issue #11](https://github.com/Accessible360/accessible-slick/issues/11).
focusOnSelect | Unnecessary since keyboard navigation has been removed. Even with keyboard navigation, tab stops on non-actionable elements is very strange for keyboard users, and really just adds work for them. [See issue #11](https://github.com/Accessible360/accessible-slick/issues/11).


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


## Contributing

If you feel this package can be improved in some way, please start by [proposing your change in a new Issue](https://github.com/Accessible360/accessible-slick/issues/new) before spending a bunch of time writing code! We'll talk through the problem and your proposed solution, and possibly even do some light prototyping and testing with live users with disabilities to see how it feels for real people.

When your change is given the green light and you're ready to code, [create a fork of this repository](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo) and commit your changes there. [Open a pull request (PR)](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) to the master branch of this repo and we'll get that sucker integrated!

**If your change is really minor (like a spelling or formatting fix), feel free to just go ahead and open up a pull request and skip the prior validation!** We'll review and discuss your changes in the PR directly, if needed.


## Credits

Massive kudos to [Ken Wheeler](https://github.com/kenwheeler) and the entire [Slick Slider community](https://github.com/kenwheeler/slick) for creating the original package.

This fork was started by [Jason Webb](https://github.com/jasonwebb), Developer Advocate at <a href="https://accessible360.com" target="_blank">Accessible360</a>.

<a href="https://accessible360.com" target="_blank"><img src="https://raw.githubusercontent.com/Accessible360/accessible-slick/master/docs/images/accessible360-logo.png" alt="Accessible360 logo with tagline Better. For All." width="400"></a>
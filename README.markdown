accessible-slick
----------------

_the last (accessible) carousel you'll ever need_

## What is this repo?

* An accessible drop-in replacement for the Slick Slider package intended to ease the pain for real-world dev teams trying to conform to WCAG 2.0/2.1 (Web Content Accessibility Guidelines)


## Why is this needed?

* Slick Slider is widely used, but has a number of accessibility issues that consistently cause pain for many companies when they undergo accessibility audits. [[1]](https://diginclusion.com/industry-updates/wai-aria-dark-art-of-accessibility/)
* Its [been abandoned](https://github.com/kenwheeler/slick/graphs/code-frequency) by it's original author.
* The contributor community is stalemated about how (and if) to proceed with accessibility. [[1]](https://github.com/kenwheeler/slick/issues?q=is%3Aissue+is%3Aopen+accessibility) [[2]](https://github.com/kenwheeler/slick/pulls?q=is%3Apr+is%3Aopen+accessibility)
* A practical, easy solution is needed _right now_, even if its imperfect (baby steps!).


## How is this package accessible?

* Implements a numbers of accessibility and usability enhancements identified and tested by professional accessibility auditors and native screen reader and keyboard-only live users at Accessible360.

### Feature additions

`TODO: list out new features with reasoning.`

### Code changes

`TODO: list out changes made to original package with reasoning.`


## TODO

- [ ] Add `role="region"` to the wrapper.
- [ ] Add a generic but clear `aria-label` to the wrapper.
- [ ] Add screen-reader-only instructions as the first inner child of the wrapper.
- [ ] Make the default Previous and Next buttons accessible.
- [ ] Make the default slide dots accessible.
- [ ] Remove the `accessibility` feature toggle (make it accessible by default!).
  - [ ] Remove `initADA` method.
  - [ ] Remove `activateADA` method.
- [ ] Deprecate the `focusOnChange` setting.
- [ ] Deprecate the `focusOnSelect` setting.
- [ ] Hide content in non-visible slides from all users.
- [ ] Automatically add a visible pause button whenever `autoplay` is enabled to fulfill [WCAG 2.2.2](https://www.w3.org/WAI/WCAG21/Understanding/pause-stop-hide.html).

### Non-a11y changes

- [ ] Turn this list into Issues when ready.
- [ ] Implement a cross-platform build system (currently uses a Makefile, which isn't natively usable on Windows).
- [ ] Publish as an NPM package.
  - [ ] Set up official user account on npmjs.org.
  - [ ] Update `package.json` metadata file.
- [ ] Delete `bower.json`, since the Bower registry is now deprecated.
- [ ] Delete `slick.jquery.json`, since the jQuery Plugin Registry is now deprecated.
- [ ] Consider hosting via a CDN (using jsDelivr?).
- [ ] Update the demo page (`./index.html`) to document new features.
  * This should have a similar format to the original package's doc page so its nice and familiar, but without feeling like a rip-off.
- [ ] Update this README to contain clear, friendly guidance in a format similar to the original package so its familiar for devs.
- [ ] Add usage guidance with accessibility best practices.


## References

* http://shouldiuseacarousel.com/
* https://diginclusion.com/industry-updates/wai-aria-dark-art-of-accessibility/


## Development

`TODO: pending replacement of Makefile-based build system with something else.`


## Installation

`TODO: pending publish of packages on npm and Bower.`


## Usage

`TODO: provide demo page link.`

All of the original settings, events, and other API features are available.

* [Settings](https://github.com/kenwheeler/slick#settings)
* [Events](https://github.com/kenwheeler/slick#events)
* [Methods](https://github.com/kenwheeler/slick#methods)
# head-support__8b636e38

- Source URL: https://htmx.org/extensions/head-support/
- Source file: `fetch/htmx_org_8b636e38.html`
- Hash: `8b636e38`
- Category: `htmx/extensions`

<div class="top-nav">

<div class="c">

<div class="menu">

<div class="logo-wrapper">

<a href="/" class="logo light">&lt;<strong>/</strong>&gt; htm<strong>x</strong></a> <img src="data:image/svg+xml;base64,PHN2ZyBfPSJvbiBjbGljayB0b2dnbGUgLnNob3cgb24gI25hdiIgY2xhc3M9ImhhbWJ1cmdlciIgdmlld2JveD0iMCAwIDEwMCA4MCIgd2lkdGg9IjI1IiBoZWlnaHQ9IjI1IiBzdHlsZT0ibWFyZ2luLWJvdHRvbTotNXB4Ij4KICAgICAgICAgICAgICAgICAgICA8cmVjdCB3aWR0aD0iMTAwIiBoZWlnaHQ9IjIwIiBzdHlsZT0iZmlsbDpyZ2IoNTIsIDEwMSwgMTY0KSIgcng9IjEwIiAvPgogICAgICAgICAgICAgICAgICAgIDxyZWN0IHk9IjMwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjIwIiBzdHlsZT0iZmlsbDpyZ2IoNTIsIDEwMSwgMTY0KSIgcng9IjEwIiAvPgogICAgICAgICAgICAgICAgICAgIDxyZWN0IHk9IjYwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjIwIiBzdHlsZT0iZmlsbDpyZ2IoNTIsIDEwMSwgMTY0KSIgcng9IjEwIiAvPgogICAgICAgICAgICAgICAgPC9zdmc+" class="hamburger" />

</div>

<div id="nav" class="navigation" hx-boost="true">

<div class="navigation-items" preload="mouseover">

<div>

[docs](/docs/)

</div>

<div>

[reference](/reference/)

</div>

<div>

[examples](/examples/)

</div>

<div>

[talk](/talk/)

</div>

<div>

[essays](/essays/)

</div>

<div hx-disable="">

<span style="display:none;">Search</span>

</div>

<div>

<div id="github-stars" class="github-stars" hx-preserve="true">

<a href="https://github.com/bigskysoftware/htmx" class="github-button" data-color-scheme="no-preference: light; light: light; dark: dark;" data-icon="octicon-star" data-show-count="true" aria-label="Star bigskysoftware/htmx on GitHub">star</a>

</div>

</div>

</div>

</div>

</div>

</div>

</div>

<div class="c content">

# htmx Head Tag Support Extension

The `head-support` extension adds support for <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/head" rel="noopener" target="_blank">head tags</a> in responses to htmx requests.

htmx began as a library focused on *partial replacement* of HTML within the `body` tag. As such, merging additional information such as the head tag was not a focus of the library. (This is in contrast with, for example, TurboLinks, which was focused on merging entire web pages retrieved via AJAX into the browser.)

The [`hx-boost`](https://htmx.org/attributes/hx-boost/) attribute moved htmx closer to this world of full HTML-document support & support for extracting the `title` tag out of head elements was eventually added, but full head tag support has never been a feature of the library. This extension addresses that shortcoming.

## Installing

The fastest way to install `head-support` is to load it via a CDN. Remember to always include the core htmx library before the extension and [enable the extension](https://htmx.org/extensions/head-support/#usage).

``` HTML
<head>
    <script src="https://cdn.jsdelivr.net/npm/htmx.org@2.0.8/dist/htmx.min.js" integrity="sha384-/TgkGk7p307TH7EXJDuUlgG3Ce1UVolAOFopFekQkkXihi5u/6OCvVKyz1W+idaz" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/htmx-ext-head-support@2.0.5" integrity="sha384-cvMqHzjCJsOHgGuyB3sWXaUSv/Krm0BdzjuI1rtkjCbL1l1oHJx+cHyVRJhyuEz0" crossorigin="anonymous"></script>
</head>
<body hx-ext="head-support">
...
```

An unminified version is also available at https://cdn.jsdelivr.net/npm/htmx-ext-head-support/dist/head-support.js.

While the CDN approach is simple, you may want to consider <a href="https://blog.wesleyac.com/posts/why-not-javascript-cdn" rel="noopener" target="_blank">not using CDNs in production</a>. The next easiest way to install `head-support` is to simply copy it into your project. Download the extension from `https://cdn.jsdelivr.net/npm/htmx-ext-head-support`, add it to the appropriate directory in your project and include it where necessary with a `<script>` tag.

For npm-style build systems, you can install `head-support` via <a href="https://www.npmjs.com/" rel="noopener" target="_blank">npm</a>:

``` shell
npm install htmx-ext-head-support
```

After installing, you’ll need to use appropriate tooling to bundle `node_modules/htmx-ext-head-support/dist/head-support.js` (or `.min.js`). For example, you might bundle the extension with htmx core from `node_modules/htmx.org/dist/htmx.js` and project-specific code.

If you are using a bundler to manage your javascript (e.g. Webpack, Rollup):

- Install `htmx.org` and `htmx-ext-head-support` via npm
- Import both packages to your `index.js`

``` JS
import `htmx.org`;
import `htmx-ext-head-support`; 
```

## Usage

``` html
<body hx-ext="head-support">
...
</body>
```

With this installed, all responses that htmx receives that contain a `head` tag in them (even if they are not complete HTML documents with a root `<html>` element) will be processed.

How the head tag is handled depends on the type of htmx request.

If the htmx request is from a boosted element, then the following merge algorithm is used:

- Elements that exist in the current head as exact textual matches will be left in place
- Elements that do not exist in the current head will be added at the end of the head tag
- Elements that exist in the current head, but not in the new head will be removed from the head

If the htmx request is from a non-boosted element, then all content will be *appended* to the existing head element.

If you wish to override this behavior in either case, you can place the `hx-head` attribute on the new `<head>` tag, with either of the following two values:

- `merge` - follow the merging algorithm outlined above
- `append` - append the elements to the existing head

### Controlling Merge Behavior

Beyond this, you may also control merging behavior of individual elements with the following attributes:

- If you place `hx-head="re-eval"` on a head element, it will be re-added (removed and appended) to the head tag on every request, even if it already exists. This can be useful to execute a script on every htmx request, for example.
- If you place `hx-preserve="true"` on an element, it will never be removed from the head

### Example

As an example, consider the following head tag in an existing document:

``` html
<head>
<link rel="stylesheet" href="https://the.missing.style">
<link rel="stylesheet" href="/css/site1.css">
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
</head>
```

If htmx receives a request containing this new head tag:

``` html
<head>
<link rel="stylesheet" href="https://the.missing.style">
<link rel="stylesheet" href="/css/site2.css">
<script src="/js/script2.js"></script>
<script src="/js/script3.js"></script>
</head>
```

Then the following operations will occur:

- `<link rel="stylesheet" href="https://the.missing.style">` will be left alone
- `<link rel="stylesheet" href="/css/site1.css">` will be removed from the head
- `<link rel="stylesheet" href="/css/site2.css">` will be added to the head
- `<script src="/js/script1.js"></script>` will be removed from the head
- `<script src="/js/script2.js"></script>` will be left alone
- `<script src="/js/script3.js"></script>` will be added to the head

The final head element will look like this:

``` html
<head>
<link rel="stylesheet" href="https://the.missing.style">
<script src="/js/script2.js"></script>
<link rel="stylesheet" href="/css/site2.css">
<script src="/js/script3.js"></script>
</head>
```

## Events

This extension triggers the following events:

- `htmx:removingHeadElement` - triggered when a head element is about to be removed, with the element being removed available in `event.detail.headElement`. If `preventDefault()` is invoked on the event, the element will not be removed.
- `htmx:addingHeadElement` - triggered when a head element is about to be added, with the element being added available in `event.detail.headElement`. If `preventDefault()` is invoked on the event, the element will not be added.
- `htmx:afterHeadMerge` - triggered after a head tag merge has occurred, with the following values available in the event `detail`:
- `added` - added head elements
- `kept` - kept head elements
- `removed` - removed head elements
- `htmx:beforeHeadMerge` - triggered before a head merge occurs

</div>

<div class="c content">

<div class="row">

<div class="6 col footer-haiku">

## haiku

*javascript fatigue:\
longing for a hypertext\
already in hand*

</div>

<div class="6 col footer-menu">

<div>

[docs](/docs/)

</div>

<div>

[reference](/reference/)

</div>

<div>

[examples](/examples/)

</div>

<div>

[talk](/talk/)

</div>

<div>

[essays](/essays/)

</div>

<div>

[@htmx_org](https://twitter.com/htmx_org)

</div>

</div>

</div>

<div class="row" style="text-align: center;">

<div class="col">

<img src="/img/bss_bars.png" style="max-width: 30px; margin-top: 3em;" />

</div>

</div>

</div>

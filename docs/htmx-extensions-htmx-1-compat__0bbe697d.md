# htmx-1-compat__0bbe697d

- Source URL: https://htmx.org/extensions/htmx-1-compat/
- Source file: `fetch/htmx_org_0bbe697d.html`
- Hash: `0bbe697d`
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

# htmx 1.x Compatibility Extension

The `htmx-1-compat` extension allows you to almost seamlessly upgrade from htmx 1.x to htmx 2.

## Installing

The fastest way to install `htmx-1-compat` is to load it via a CDN. Remember to always include the core htmx library before the extension and enable the extension.

``` HTML
<head>
    <script src="https://cdn.jsdelivr.net/npm/htmx.org@2.0.8/dist/htmx.min.js" integrity="sha384-/TgkGk7p307TH7EXJDuUlgG3Ce1UVolAOFopFekQkkXihi5u/6OCvVKyz1W+idaz" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/htmx-ext-htmx-1-compat@2.0.2" integrity="sha384-lcvVWaNjF5zPPUeeWmC0OkJ2MLqoWLlkAabuGm+EuMSTfGo5WRyHrNaAp0cJr9Pg" crossorigin="anonymous"></script>
</head>
<body hx-ext="htmx-1-compat">
...
```

An unminified version is also available at https://cdn.jsdelivr.net/npm/htmx-ext-htmx-1-compat/dist/htmx-1-compat.js.

While the CDN approach is simple, you may want to consider <a href="https://blog.wesleyac.com/posts/why-not-javascript-cdn" rel="noopener" target="_blank">not using CDNs in production</a>. The next easiest way to install `htmx-1-compat` is to simply copy it into your project. Download the extension from `https://cdn.jsdelivr.net/npm/htmx-ext-htmx-1-compat`, add it to the appropriate directory in your project and include it where necessary with a `<script>` tag.

For npm-style build systems, you can install `htmx-1-compat` via <a href="https://www.npmjs.com/" rel="noopener" target="_blank">npm</a>:

``` shell
npm install htmx-ext-htmx-1-compat
```

After installing, you’ll need to use appropriate tooling to bundle `node_modules/htmx-ext-htmx-1-compat/dist/htmx-1-compat.js` (or `.min.js`). For example, you might bundle the extension with htmx core from `node_modules/htmx.org/dist/htmx.js` and project-specific code.

If you are using a bundler to manage your javascript (e.g. Webpack, Rollup):

- Install `htmx.org` and `htmx-ext-htmx-1-compat` via npm
- Import both packages to your `index.js`

``` JS
import `htmx.org`;
import `htmx-ext-htmx-1-compat`; 
```

## What it covers

Htmx 2 introduced a few <a href="https://v2-0v2-0.htmx.org/migration-guide-htmx-1/" rel="noopener" target="_blank">breaking changes</a>.

To make upgrading from htmx 1.x to htmx 2 easier, we’re providing this extension that reverts most of those, so you’re able to benefit from the other changes without breaking your application.

### Obsolete attributes

- htmx 2 removed the deprecated <a href="https://htmx.org/attributes/hx-ws/" rel="noopener" target="_blank">hx-ws</a> and <a href="https://htmx.org/attributes/hx-sse/" rel="noopener" target="_blank">hx-sse</a> attributes, that this extension restores.
- htmx 2 removed the deprecated `hx-on` attribute in favor of the wildcard <a href="https://htmx.org/attributes/hx-on/" rel="noopener" target="_blank"><code>hx-on*</code> attribute</a>, that this extension restores.

### Default Changes

- reverts <a href="https://htmx.org/reference/#config" rel="noopener" target="_blank">htmx.config.scrollBehavior</a> to ‘smooth’.
- makes `DELETE` requests use a form-encoded body rather than URL parameters (htmx 2 uses URL parameters for `DELETE` as default as per <a href="https://www.rfc-editor.org/rfc/rfc9110.html#name-delete" rel="noopener" target="_blank">the spec</a>).
- allows cross-domain requests by default (htmx 2 now forbids it by default).

## What it does not cover

- IE11 support was dropped in htmx 2, and this extension cannot revert that. If you need IE11 support, please stay with htmx 1 that will continue being supported.
- htmx 2 introduced the breaking change that is the <a href="https://v2-0v2-0.htmx.org/api/#swap" rel="noopener" target="_blank">swap method</a> to the extensions API. If you were only using core extensions, then you shouldn’t need any additional work. If you were using custom or community extensions, make sure that they were updated to work with htmx 2’s API.

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

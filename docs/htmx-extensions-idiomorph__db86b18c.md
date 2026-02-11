# idiomorph__db86b18c

- Source URL: https://htmx.org/extensions/idiomorph/
- Source file: `fetch/htmx_org_db86b18c.html`
- Hash: `db86b18c`
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

# htmx Idiomorph Extension

<a href="https://github.com/bigskysoftware/idiomorph" rel="noopener" target="_blank">Idiomorph</a> is a DOM morphing algorithm created by the htmx creator. DOM morphing is a process where an existing DOM tree is “morphed” into the shape of another in a way that resuses as much of the existing DOM’s nodes as possible. By preserving nodes when changing from one tree to another you can present a much smoother transition between the two states.

You can use the idiomorph morphing algorithm as a [swapping](https://htmx.org/extensions/idiomorph/@attributes/hx-swap) strategy by including the idiomorph extension.

## Installing

The fastest way to install `idiomorph` is to load it via a CDN. Remember to always include the core htmx library before the extension and [enable the extension](https://htmx.org/extensions/idiomorph/#usage).

``` HTML
<head>
    <script src="https://cdn.jsdelivr.net/npm/htmx.org@2.0.8/dist/htmx.min.js@2.0.7" integrity="sha384-/TgkGk7p307TH7EXJDuUlgG3Ce1UVolAOFopFekQkkXihi5u/6OCvVKyz1W+idaz" crossorigin="anonymous"></script>
    <script src="https://unpkg.com/idiomorph@0.7.4/dist/idiomorph-ext.min.js" integrity="sha384-SsScJKzATF/w6suEEdLbgYGsYFLzeKfOA6PY+/C5ZPxOSuA+ARquqtz/BZz9JWU8" crossorigin="anonymous"></script>
</head>
<body hx-ext="morph">
```

Unminified versions are also available at: <a href="https://unpkg.com/idiomorph/dist/idiomorph-ext.js" rel="noopener" target="_blank">https://unpkg.com/idiomorph/dist/idiomorph-ext.js</a>

While the CDN approach is simple, you may want to consider <a href="https://blog.wesleyac.com/posts/why-not-javascript-cdn" rel="noopener" target="_blank">not using CDNs in production</a>. The next easiest way to install `idiomorph` is to simply copy it into your project. Download idiomorph with htmx extension from `https://unpkg.com/idiomorph/dist/idiomorph-ext.min.js`, add them to the appropriate directory in your project and include them where necessary with `<script>` tags.

For npm-style build systems, you can install `idiomorph` via <a href="https://www.npmjs.com/" rel="noopener" target="_blank">npm</a>:

``` shell
npm install idiomorph
```

After installing, you’ll need to use appropriate tooling to bundle `node_modules/idiomorph/dist/idiomorph-ext.js` (or `node_modules/idiomorph/dist/idiomorph-ext.min.js`). For example, you might bundle the extension with htmx core from `node_modules/htmx.org/dist/htmx.js` and project-specific code.

If you are using a bundler to manage your javascript (e.g. Webpack, Rollup):

- Install `htmx.org` and `idiomorph` via npm
- Import both packages to your `index.js`

``` JS
import `htmx.org`;
import `idiomorph/htmx`;
```

## Usage

Once you have referenced the idiomorph extension, you can register it with the name `morph` on the body and then begin using `morph`, `morph:outerHTML` or `morph:innerHTML` as swap strategies.

- `morph` & `morph:outerHTML` will morph the target element as well as it’s children
- `morph:innerHTML` will morph only the inner children of an element, leaving the target untouched

``` html
<body hx-ext="morph">
  <button hx-get="/example" hx-swap="morph">
    Morph My Outer HTML
  </button>

  <button hx-get="/example" hx-swap="morph:outerHTML">
    Morph My Outer HTML
  </button>

  <button hx-get="/example" hx-swap="morph:innerHTML">
    Morph My Inner HTML
  </button>
</body>
```

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

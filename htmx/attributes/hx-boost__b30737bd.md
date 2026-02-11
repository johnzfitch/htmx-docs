# hx-boost__b30737bd

- Source URL: https://htmx.org/attributes/hx-boost/
- Source file: `fetch/htmx_org_b30737bd.html`
- Hash: `b30737bd`
- Category: `htmx/attributes`

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

# `hx-boost`

The `hx-boost` attribute allows you to “boost” normal anchors and form tags to use AJAX instead. This has the <a href="https://en.wikipedia.org/wiki/Progressive_enhancement" rel="noopener" target="_blank">nice fallback</a> that, if the user does not have javascript enabled, the site will continue to work.

For anchor tags, clicking on the anchor will issue a `GET` request to the url specified in the `href` and will push the url so that a history entry is created. The target is the `<body>` tag, and the `innerHTML` swap strategy is used by default. All of these can be modified by using the appropriate attributes, except the `click` trigger.

For forms the request will be converted into a `GET` or `POST`, based on the method in the `method` attribute and will be triggered by a `submit`. Again, the target will be the `body` of the page, and the `innerHTML` swap will be used. The url will *not* be pushed, however, and no history entry will be created. (You can use the [hx-push-url](https://htmx.org/attributes/hx-push-url/) attribute if you want the url to be pushed.)

Here is an example of some boosted links:

``` html
<div hx-boost="true">
  <a href="/page1">Go To Page 1</a>
  <a href="/page2">Go To Page 2</a>
</div>
```

These links will issue an ajax `GET` request to the respective URLs and replace the body’s inner content with it.

Here is an example of a boosted form:

``` html
<form hx-boost="true" action="/example" method="post">
    <input name="email" type="email" placeholder="Enter email...">
    <button>Submit</button>
</form>
```

This form will issue an ajax `POST` to the given URL and replace the body’s inner content with it.

## Notes

- `hx-boost` is inherited and can be placed on a parent element
- Only links that are to the same domain and that are not local anchors will be boosted
- All requests are done via AJAX, so keep that in mind when doing things like redirects
- To find out if the request results from a boosted anchor or form, look for [`HX-Boosted`](https://htmx.org/reference/#request_headers) in the request header
- Selectively disable boost on child elements with `hx-boost="false"`
- Disable the replacement of elements via boost, and their children, with [`hx-preserve="true"`](https://htmx.org/attributes/hx-preserve/)

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

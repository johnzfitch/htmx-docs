# hx-replace-url__c1979717

- Source URL: https://htmx.org/attributes/hx-replace-url/
- Source file: `fetch/htmx_org_c1979717.html`
- Hash: `c1979717`
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

# `hx-replace-url`

The `hx-replace-url` attribute allows you to replace the current url of the browser <a href="https://developer.mozilla.org/en-US/docs/Web/API/History_API" rel="noopener" target="_blank">location history</a>.

The possible values of this attribute are:

1.  `true`, which replaces the fetched URL in the browser navigation bar.
2.  `false`, which disables replacing the fetched URL if it would otherwise be replaced due to inheritance.
3.  A URL to be replaced into the location bar. This may be relative or absolute, as per <a href="https://developer.mozilla.org/en-US/docs/Web/API/History/replaceState" rel="noopener" target="_blank"><code>history.replaceState()</code></a>.

Here is an example:

``` html
<div hx-get="/account" hx-replace-url="true">
  Go to My Account
</div>
```

This will cause htmx to snapshot the current DOM to `localStorage` and replace the URL \`/account’ in the browser location bar.

Another example:

``` html
<div hx-get="/account" hx-replace-url="/account/home">
  Go to My Account
</div>
```

This will replace the URL \`/account/home’ in the browser location bar.

## Notes

- `hx-replace-url` is inherited and can be placed on a parent element
- The [`HX-Replace-Url` response header](https://htmx.org/headers/hx-replace-url/) has similar behavior and can override this attribute.
- The [`hx-history-elt` attribute](https://htmx.org/attributes/hx-history-elt/) allows changing which element is saved in the history cache.
- The [`hx-push-url` attribute](https://htmx.org/attributes/hx-push-url/) is a similar and more commonly used attribute, which creates a new history entry rather than replacing the current one.

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

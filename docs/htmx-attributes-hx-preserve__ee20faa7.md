# hx-preserve__ee20faa7

- Source URL: https://htmx.org/attributes/hx-preserve/
- Source file: `fetch/htmx_org_ee20faa7.html`
- Hash: `ee20faa7`
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

# `hx-preserve`

The `hx-preserve` attribute allows you to keep an element unchanged during HTML replacement. Elements with `hx-preserve` set are preserved by `id` when htmx updates any ancestor element. You *must* set an unchanging `id` on elements for `hx-preserve` to work. The response requires an element with the same `id`, but its type and other attributes are ignored.

## Notes

- `hx-preserve` is not inherited

- You can use `hx-preserve="true"` or use it as a boolean attribute with just `hx-preserve`

- Some elements cannot unfortunately be preserved properly, such as `<input type="text">` (focus and caret position are lost), iframes or certain types of videos. To tackle some of these cases we recommend the <a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/morphdom-swap/README.md" rel="noopener" target="_blank">morphdom extension</a>, which does a more elaborate DOM reconciliation

- When using [History Support](https://htmx.org/docs/#history) for actions like the back button `hx-preserve` elements will also have their state preserved

- Avoid using [hx-swap](https://htmx.org/attributes/hx-swap/) set to `none` with requests that could contain a `hx-preserve` element to avoid losing it

- `hx-preserve` can cause elements to be removed from their current location and relocated to a new location when swapping in a partial/oob response

  ``` html
  <div id="new_location">
    Just relocated the video here
    <div id="video" hx-preserve></div>
  </div>
  ```

- Can be used on the inside content of a [hx-swap-oob](https://htmx.org/attributes/hx-swap-oob/) element

  ``` html
  <div id="notify" hx-swap-oob="true">
    Notification updated but keep the same retain
    <div id="retain" hx-preserve></div>
  </div>
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

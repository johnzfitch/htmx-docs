# hx-select-oob__5b275e78

- Source URL: https://htmx.org/attributes/hx-select-oob/
- Source file: `fetch/htmx_org_5b275e78.html`
- Hash: `5b275e78`
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

# `hx-select-oob`

The `hx-select-oob` attribute allows you to select content from a response to be swapped in via an out-of-band swap.\
The value of this attribute is comma separated list of elements to be swapped out of band. This attribute is almost always paired with [hx-select](https://htmx.org/attributes/hx-select/).

Here is an example that selects a subset of the response content:

``` html
<div>
   <div id="alert"></div>
    <button hx-get="/info" 
            hx-select="#info-details" 
            hx-swap="outerHTML"
            hx-select-oob="#alert">
        Get Info!
    </button>
</div>
```

This button will issue a `GET` to `/info` and then select the element with the id `info-details`, which will replace the entire button in the DOM, and, in addition, pick out an element with the id `alert` in the response and swap it in for div in the DOM with the same ID.

Each value in the comma separated list of values can specify any valid [`hx-swap`](https://htmx.org/attributes/hx-swap/) strategy by separating the selector and the swap strategy with a `:`, with the strategy otherwise defaulting to `outerHTML`.

For example, to prepend the alert content instead of replacing it:

``` html
<div>
   <div id="alert"></div>
    <button hx-get="/info"
            hx-select="#info-details"
            hx-swap="outerHTML"
            hx-select-oob="#alert:afterbegin">
        Get Info!
    </button>
</div>
```

## Notes

- `hx-select-oob` is inherited and can be placed on a parent element

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

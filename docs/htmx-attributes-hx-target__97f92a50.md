# hx-target__97f92a50

- Source URL: https://htmx.org/attributes/hx-target/
- Source file: `fetch/htmx_org_97f92a50.html`
- Hash: `97f92a50`
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

# `hx-target`

The `hx-target` attribute allows you to target a different element for swapping than the one issuing the AJAX request. The value of this attribute can be:

- A CSS query selector of the element to target.
- `this` which indicates that the element that the `hx-target` attribute is on is the target.
- `closest <CSS selector>` which will find the <a href="https://developer.mozilla.org/docs/Web/API/Element/closest" rel="noopener" target="_blank">closest</a> ancestor element or itself, that matches the given CSS selector (e.g. `closest tr` will target the closest table row to the element).
- `find <CSS selector>` which will find the first child descendant element that matches the given CSS selector.
- `next` which resolves to <a href="https://developer.mozilla.org/docs/Web/API/Element/nextElementSibling" rel="noopener" target="_blank">element.nextElementSibling</a>
- `next <CSS selector>` which will scan the DOM forward for the first element that matches the given CSS selector. (e.g. `next .error` will target the closest following sibling element with `error` class)
- `previous` which resolves to <a href="https://developer.mozilla.org/docs/Web/API/Element/previousElementSibling" rel="noopener" target="_blank">element.previousElementSibling</a>
- `previous <CSS selector>` which will scan the DOM backwards for the first element that matches the given CSS selector. (e.g. `previous .error` will target the closest previous sibling with `error` class)

Here is an example that targets a div:

``` html
<div>
    <div id="response-div"></div>
    <button hx-post="/register" hx-target="#response-div" hx-swap="beforeend">
        Register!
    </button>
</div>
```

The response from the `/register` url will be appended to the `div` with the id `response-div`.

This example uses `hx-target="this"` to make a link that updates itself when clicked:

``` html
<a hx-post="/new-link" hx-target="this" hx-swap="outerHTML">New link</a>
```

## Notes

- `hx-target` is inherited and can be placed on a parent element

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

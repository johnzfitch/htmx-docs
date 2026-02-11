# hx-disabled-elt__d9629999

- Source URL: https://htmx.org/attributes/hx-disabled-elt/
- Source file: `fetch/htmx_org_d9629999.html`
- Hash: `d9629999`
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

# `hx-disabled-elt`

The `hx-disabled-elt` attribute allows you to specify elements that will have the `disabled` attribute added to them for the duration of the request. The value of this attribute can be:

- A CSS query selector of the element to disable.
- `this` to disable the element itself
- `closest <CSS selector>` which will find the <a href="https://developer.mozilla.org/docs/Web/API/Element/closest" rel="noopener" target="_blank">closest</a> ancestor element or itself, that matches the given CSS selector (e.g. `closest fieldset` will disable the closest to the element `fieldset`).
- `find <CSS selector>` which will find the first child descendant element that matches the given CSS selector
- `next` which resolves to <a href="https://developer.mozilla.org/docs/Web/API/Element/nextElementSibling" rel="noopener" target="_blank">element.nextElementSibling</a>
- `next <CSS selector>` which will scan the DOM forward for the first element that matches the given CSS selector (e.g. `next button` will disable the closest following sibling `button` element)
- `previous` which resolves to <a href="https://developer.mozilla.org/docs/Web/API/Element/previousElementSibling" rel="noopener" target="_blank">element.previousElementSibling</a>
- `previous <CSS selector>` which will scan the DOM backwards for the first element that matches the given CSS selector. (e.g. `previous input` will disable the closest previous sibling `input` element)

Here is an example with a button that will disable itself during a request:

``` html
<button hx-post="/example" hx-disabled-elt="this">
    Post It!
</button>
```

When a request is in flight, this will cause the button to be marked with <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/disabled" rel="noopener" target="_blank">the <code>disabled</code> attribute</a>, which will prevent further clicks from occurring.

The `hx-disabled-elt` attribute also supports specifying multiple CSS selectors separated by commas to disable multiple elements during the request. Here is an example that disables buttons and text input fields of a particular form during the request:

``` html
<form hx-post="/example" hx-disabled-elt="find input[type='text'], find button">
    <input type="text" placeholder="Type here...">
    <button type="submit">Send</button>
</form>
```

Note that you can also use the `inherit` keyword to inherit parent values for a disabled elements and add additional disabled element CSS selectors:

``` html
<main hx-disabled-elt="#logout-button">
    ...
  <form hx-post="/example" hx-disabled-elt="inherit, find input[type='text'], find button">
    <input type="text" placeholder="Type here...">
    <button type="submit">Send</button>
  </form>
</main>
```

## Notes

- `hx-disabled-elt` is inherited and can be placed on a parent element

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

# hx-disinherit__c0f0f88f

- Source URL: https://htmx.org/attributes/hx-disinherit/
- Source file: `fetch/htmx_org_c0f0f88f.html`
- Hash: `c0f0f88f`
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

# `hx-disinherit`

The default behavior for htmx is to “inherit” many attributes automatically: that is, an attribute such as [hx-target](https://htmx.org/attributes/hx-target/) may be placed on a parent element, and all child elements will inherit that target.

The `hx-disinherit` attribute allows you to control this automatic attribute inheritance. An example scenario is to allow you to place an `hx-boost` on the `body` element of a page, but overriding that behavior in a specific part of the page to allow for more specific behaviors.

htmx evaluates attribute inheritance as follows:

- when `hx-disinherit` is set on a parent node
  - `hx-disinherit="*"` all attribute inheritance for this element will be disabled
  - `hx-disinherit="hx-select hx-get hx-target"` disable inheritance for only one or multiple specified attributes

``` html
<div hx-boost="true" hx-select="#content" hx-target="#content" hx-disinherit="*">
  <a href="/page1">Go To Page 1</a> <!-- boosted with the attribute settings above -->
  <a href="/page2" hx-boost="unset">Go To Page 1</a> <!-- not boosted -->
  <button hx-get="/test" hx-target="this"></button> <!-- hx-select is not inherited -->
</div>
```

``` html
<div hx-boost="true" hx-select="#content" hx-target="#content" hx-disinherit="hx-target">
  <!-- hx-select is automatically set to parent's value; hx-target is not inherited -->
  <button hx-get="/test"></button>
</div>
```

``` html
<div hx-select="#content">
  <div hx-boost="true" hx-target="#content" hx-disinherit="hx-select">
    <!-- hx-target is automatically inherited from parent's value -->
    <!-- hx-select is not inherited, because the direct parent does
    disables inheritance, despite not specifying hx-select itself -->
    <button hx-get="/test"></button>
  </div>
</div>
```

## Notes

- Read more about [Attribute Inheritance](https://htmx.org/docs/#inheritance)

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

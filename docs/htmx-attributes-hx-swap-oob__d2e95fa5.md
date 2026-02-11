# hx-swap-oob__d2e95fa5

- Source URL: https://htmx.org/attributes/hx-swap-oob/
- Source file: `fetch/htmx_org_d2e95fa5.html`
- Hash: `d2e95fa5`
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

# `hx-swap-oob`

The `hx-swap-oob` attribute allows you to specify that some content in a response should be swapped into the DOM somewhere other than the target, that is “Out of Band”. This allows you to piggyback updates to other element updates on a response.

Consider the following response HTML:

``` html
<div>
 ...
</div>
<div id="alerts" hx-swap-oob="true">
    Saved!
</div>
```

The first div will be swapped into the target the usual manner. The second div, however, will be swapped in as a replacement for the element with the id `alerts`, and will not end up in the target.

The value of the `hx-swap-oob` can be:

- `true`
- any valid [`hx-swap`](https://htmx.org/attributes/hx-swap/) value
- any valid [`hx-swap`](https://htmx.org/attributes/hx-swap/) value, followed by a colon, followed by a CSS selector

If the value is `true` or `outerHTML` (which are equivalent) the element will be swapped inline.

If a swap value is given, that swap strategy will be used and the encapsulating tag pair will be stripped for all strategies other than `outerHTML`.

If a selector is given, all elements matched by that selector will be swapped. If not, the element with an ID matching the new content will be swapped.

### Using alternate swap strategies

As mentioned previously when using swap strategies other than `true` or `outerHTML` the encapsulating tags are stripped, as such you need to encapsulate the returned data with the correct tags for the context.

When trying to insert a `<tr>` in a table that uses `<tbody>`:

``` html
<tbody hx-swap-oob="beforeend:#table tbody">
   <tr>
       ...
   </tr>
</tbody>
```

A “plain” table:

``` html
<table hx-swap-oob="beforeend:#table2">
   <tr>
       ...
   </tr>
</table>
```

A `<li>` may be encapsulated in `<ul>`, `<ol>`, `<div>` or `<span>`, for example:

``` html
<ul hx-swap-oob="beforeend:#list1">
   <li>...</li>
</ul>
```

A `<p>` can be encapsulated in `<div>` or `<span>`:

``` html
<span hx-swap-oob="beforeend:#text">
   <p>...</p>
</span>
```

### Troublesome Tables and lists

Note that you can use a `template` tag to encapsulate types of elements that, by the HTML spec, can’t stand on their own in the DOM (`<tr>`, `<td>`, `<th>`, `<thead>`, `<tbody>`, `<tfoot>`, `<colgroup>`, `<caption>`, `<col>` & `<li>`).

Here is an example with an out-of-band swap of a table row being encapsulated in this way:

``` html
<div>
    ...
</div>
<template>
    <tr id="row" hx-swap-oob="true">
        ...
    </tr>
</template>
```

Note that these template tags will be removed from the final content of the page.

### Slippery SVGs

Some element types, like SVG, use a specific XML namespace for their child elements. This prevents internal elements from working correctly when swapped in, unless they are encapsulated within a `svg` tag. To modify the internal contents of an existing SVG, you can use both `template` and `svg` tags to encapsulate the elements, allowing them to get the correct namespace applied.

Here is an example with an out-of-band swap of svg elements being encapsulated in this way:

``` html
<div>
    ...
</div>
<template><svg>
    <circle hx-swap-oob="true" id="circle1" r="35" cx="50" cy="50" fill="red" /> 
</svg></template>
<template><svg hx-swap-oob="beforebegin:#circle1">
    <circle id="circle2" r="45" cx="50" cy="50" fill="blue" /> 
</svg></template>
```

This will replace circle1 inline and then insert circle2 before circle1.

Note that these `template` and `svg` wrapping tags will be removed from the final content of the page.

## Nested OOB Swaps

By default, any element with `hx-swap-oob=` attribute anywhere in the response is processed for oob swap behavior, including when an element is nested within the main response element. This can be problematic when using <a href="https://htmx.org/essays/template-fragments/" rel="noopener" target="_blank">template fragments</a> where a fragment may be reused as an oob-swap target and also as part of a bigger fragment. When the bigger fragment is the main response the inner fragment will still be processed as an oob swap, removing it from the dom.

This behavior can be changed by setting the config `htmx.config.allowNestedOobSwaps` to `false`. If this config option is `false`, OOB swaps are only processed when the element is *adjacent to* the main response element, OOB swaps elsewhere will be ignored and oob-swap-related attributes stripped.

## Notes

- `hx-swap-oob` is not inherited

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

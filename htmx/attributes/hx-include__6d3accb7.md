# hx-include__6d3accb7

- Source URL: https://htmx.org/attributes/hx-include/
- Source file: `fetch/htmx_org_6d3accb7.html`
- Hash: `6d3accb7`
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

# `hx-include`

The `hx-include` attribute allows you to include additional element values in an AJAX request. The value of this attribute can be:

- A CSS query selector of the elements to include.
- `this` which will include the descendants of the element.
- `closest <CSS selector>` which will find the <a href="https://developer.mozilla.org/docs/Web/API/Element/closest" rel="noopener" target="_blank">closest</a> ancestor element or itself, that matches the given CSS selector (e.g. `closest tr` will target the closest table row to the element).
- `find <CSS selector>` which will find the first child descendant element that matches the given CSS selector.
- `next <CSS selector>` which will scan the DOM forward for the first element that matches the given CSS selector. (e.g. `next .error` will target the closest following sibling element with `error` class)
- `previous <CSS selector>` which will scan the DOM backwards for the first element that matches the given CSS selector. (e.g. `previous .error` will target the closest previous sibling with `error` class)

Here is an example that includes a separate input value:

``` html
<div>
    <button hx-post="/register" hx-include="[name='email']">
        Register!
    </button>
    Enter email: <input name="email" type="email"/>
</div>
```

This is a little contrived as you would typically enclose both of these elements in a `form` and submit the value automatically, but it demonstrates the concept.

Note that you can also use the `inherit` keyword to inherit parent values for inclusion and add additional values:

``` html
<main hx-include="#hidden-input">
    ...
    <button hx-post="/example" hx-include="inherit, [name='email']">
        Post It!
    </button>
    Enter email: <input name="email" type="email"/>
</main>
```

Finally, note that if you include a non-input element, all input elements enclosed in that element will be included.

## Notes

- `hx-include` is inherited and can be placed on a parent element

- While `hx-include` is inherited, it is evaluated from the element triggering the request. It is easy to get confused when working with the extended selectors such as `find` and `closest`.

  ``` html
  <div hx-include="find input">
      <button hx-post="/register">
          Register!
      </button>
      Enter email: <input name="email" type="email"/>
  </div>
  ```

  In the above example, when clicking on the button, the `find input` selector is resolved from the button itself, which does not return any element here, since the button doesn’t have any `input` child, thus in this case, raises an error.

- A standard CSS selector resolves to <a href="https://developer.mozilla.org/docs/Web/API/Document/querySelectorAll" rel="noopener" target="_blank">document.querySelectorAll</a> and will include multiple elements, while the extended selectors such as `find` or `next` only return a single element at most to include

- `hx-include` will ignore disabled inputs

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

# hx-headers__f078b009

- Source URL: https://htmx.org/attributes/hx-headers/
- Source file: `fetch/htmx_org_f078b009.html`
- Hash: `f078b009`
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

# `hx-headers`

The `hx-headers` attribute allows you to add to the headers that will be submitted with an AJAX request.

By default, the value of this attribute is a list of name-expression values in <a href="https://www.json.org/json-en.html" rel="noopener" target="_blank">JSON (JavaScript Object Notation)</a> format.

If you wish for `hx-headers` to *evaluate* the values given, you can prefix the values with `javascript:` or `js:`.

``` html
  <div hx-get="/example" hx-headers='{"myHeader": "My Value"}'>Get Some HTML, Including A Custom Header in the Request</div>

  <div hx-get="/example" hx-headers='js:{myVal: calculateValue()}'>Get Some HTML, Including a Dynamic Custom Header from Javascript in the Request</div>
```

## Security Considerations

- By default, the value of `hx-headers` must be valid <a href="https://developer.mozilla.org/en-US/docs/Glossary/JSON" rel="noopener" target="_blank">JSON</a>. It is **not** dynamically computed. If you use the `javascript:` prefix, be aware that you are introducing security considerations, especially when dealing with user input such as query strings or user-generated content, which could introduce a <a href="https://owasp.org/www-community/attacks/xss/" rel="noopener" target="_blank">Cross-Site Scripting (XSS)</a> vulnerability.

- Whilst far from being a foolproof solution to <a href="https://owasp.org/www-community/attacks/csrf" rel="noopener" target="_blank">Cross-Site Request Forgery</a>, the `hx-headers` attribute can support backend services to provide <a href="https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html" rel="noopener" target="_blank">CSRF prevention</a>. For more information see the <a href="https://htmx.org/docs/#csrf-prevention" rel="noopener" target="_blank">CSRF Prevention</a> section.

## Notes

- `hx-headers` is inherited and can be placed on a parent element.
- A child declaration of a header overrides a parent declaration.

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

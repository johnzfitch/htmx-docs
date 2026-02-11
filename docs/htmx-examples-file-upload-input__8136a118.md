# file-upload-input__8136a118

- Source URL: https://htmx.org/examples/file-upload-input/
- Source file: `fetch/htmx_org_8136a118.html`
- Hash: `8136a118`
- Category: `htmx/examples`

<div class="top-nav">

<div class="c">

<div class="menu">

<div class="logo-wrapper">

<a href="/" class="logo light">&lt;<strong>/</strong>&gt; htm<strong>x</strong></a> <img src="data:image/svg+xml;base64,PHN2ZyBfPSJvbiBjbGljayB0b2dnbGUgLnNob3cgb24gI25hdiIgY2xhc3M9ImhhbWJ1cmdlciIgdmlld2JveD0iMCAwIDEwMCA4MCIgd2lkdGg9IjI1IiBoZWlnaHQ9IjI1IiBzdHlsZT0ibWFyZ2luLWJvdHRvbTotNXB4Ij4KICAgICAgICAgICAgICAgICAgICA8cmVjdCB3aWR0aD0iMTAwIiBoZWlnaHQ9IjIwIiBzdHlsZT0iZmlsbDpyZ2IoNTIsIDEwMSwgMTY0KSIgcng9IjEwIiAvPgogICAgICAgICAgICAgICAgICAgIDxyZWN0IHk9IjMwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjIwIiBzdHlsZT0iZmlsbDpyZ2IoNTIsIDEwMSwgMTY0KSIgcng9IjEwIiAvPgogICAgICAgICAgICAgICAgICAgIDxyZWN0IHk9IjYwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjIwIiBzdHlsZT0iZmlsbDpyZ2IoNTIsIDEwMSwgMTY0KSIgcng9IjEwIiAvPgogICAgICAgICAgICAgICAgPC9zdmc+" class="hamburger" />

</div>

<div id="nav" class="navigation">

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

# Preserving File Inputs after Form Errors

When using server-side error handling and validation with forms that include both primitive values and file inputs, the file input’s value is lost when the form returns with error messages. Consequently, users are required to re-upload the file, resulting in a less user-friendly experience.

To overcome the problem of losing the file input value, you can use the `hx-preserve` attribute on the `input` element:

``` html
<form method="POST" id="binaryForm" enctype="multipart/form-data" hx-swap="outerHTML" hx-target="#binaryForm">
    <input hx-preserve id="someId" type="file" name="binaryFile">
    <!-- Other code here, such as input error handling. -->
    <button type="submit">Submit</button>
</form>
```

If the file field is returned with errors on it, they will be displayed provided that `hx-preserve` was placed in the `input` only and not the element that would show the errors (e.g. `ol.errorlist`). If in a given circumstance you want the file upload input to return *without* preserving the user’s chosen file (for example, because the file was an invalid type), you can manage that on the server side by omitting the `hx-preserve` attribute when the field has the relevant errors.

Alternatively, you can preserve file inputs after form errors by restructuring the form so that the file input is located outside the area that will be swapped.

Before:

``` html
<form method="POST" id="binaryForm" enctype="multipart/form-data" hx-swap="outerHTML" hx-target="#binaryForm">
    <input type="file" name="binaryFile">
    <button type="submit">Submit</button>
</form>
```

After:

``` html
<input form="binaryForm" type="file" name="binaryFile">

<form method="POST" id="binaryForm" enctype="multipart/form-data" hx-swap="outerHTML" hx-target="#binaryForm">
    <button type="submit">Submit</button>
</form>
```

1.  Form Restructuring: Move the binary file input outside the main form element in the HTML structure.

2.  Using the form Attribute: Enhance the binary file input by adding the form attribute and setting its value to the ID of the main form. This linkage associates the binary file input with the form, even when it resides outside the form element.

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

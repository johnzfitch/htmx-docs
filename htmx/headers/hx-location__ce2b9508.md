# hx-location__ce2b9508

- Source URL: https://htmx.org/headers/hx-location/
- Source file: `fetch/htmx_org_ce2b9508.html`
- Hash: `ce2b9508`
- Category: `htmx/headers`

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

# HX-Location Response Header

This response header can be used to trigger a client side redirection without reloading the whole page. Instead of changing the page’s location it will act like following a [`hx-boost` link](https://htmx.org/attributes/hx-boost/), creating a new history entry, issuing an ajax request to the value of the header and pushing the path into history.

A sample response would be:

``` html
HX-Location: /test
```

Which would push the client to test as if the user had clicked on `<a href="/test" hx-boost="true">`

If you want to redirect to a specific target on the page rather than the default of document.body, you can pass more details along with the event, by using JSON for the value of the header:

``` html
HX-Location: {"path":"/test2", "target":"#testdiv"}
```

Path is required and is url to load the response from. The rest of the data mirrors the [`ajax` api](https://htmx.org/api/#ajax) context, which is:

- `source` - the source element of the request
- `event` - an event that “triggered” the request
- `handler` - a callback that will handle the response HTML
- `target` - the target to swap the response into
- `swap` - how the response will be swapped in relative to the target
- `values` - values to submit with the request
- `headers` - headers to submit with the request
- `select` - allows you to select the content you want swapped from a response
- `push` - set to `'false'` or a path string to prevent or override the URL pushed to browser location history
- `replace` - a path string to replace the URL in the browser location history

## Notes

Response headers are not processed on 3xx response codes. see [Response Headers](https://htmx.org/docs/#response-headers)

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

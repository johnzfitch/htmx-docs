# async-auth__1de4079c

- Source URL: https://htmx.org/examples/async-auth/
- Source file: `fetch/htmx_org_1de4079c.html`
- Hash: `1de4079c`
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

# Async Authentication

This example shows how to implement an an async auth token flow for htmx.

The technique we will use here will take advantage of the fact that you can delay requests using the [`htmx:confirm`](https://htmx.org/events/#htmx:confirm) event.

We first have a button that should not issue a request until an auth token has been retrieved:

``` html
  <button hx-post="/example" hx-target="next output">
    An htmx-Powered button
  </button>
  <output>
    --
  </output>
```

Next we will add some scripting to work with an `auth` promise (returned by a library):

``` html
<script>
  // auth is a promise returned by our authentication system

  // await the auth token and store it somewhere
  let authToken = null;
  auth.then((token) => {
    authToken = token
  })
  
  // gate htmx requests on the auth token
  htmx.on("htmx:confirm", (e)=> {
    // if there is no auth token
    if(authToken == null) {
      // stop the regular request from being issued
      e.preventDefault() 
      // only issue it once the auth promise has resolved
      auth.then(() => e.detail.issueRequest()) 
    }
  })

  // add the auth token to the request as a header
  htmx.on("htmx:configRequest", (e)=> {
    e.detail.headers["AUTH"] = authToken
  })
</script>
```

Here we use a global variable, but you could use `localStorage` or whatever preferred mechanism you want to communicate the authentication token to the `htmx:configRequest` event.

With this code in place, htmx will not issue requests until the `auth` promise has been resolved.

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

# lazy-load__31e239c4

- Source URL: https://htmx.org/examples/lazy-load/
- Source file: `fetch/htmx_org_31e239c4.html`
- Hash: `31e239c4`
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

# Lazy Loading

This example shows how to lazily load an element on a page. We start with an initial state that looks like this:

``` html
<div hx-get="/graph" hx-trigger="load">
  <img alt="Result loading..." class="htmx-indicator" width="150" src="/img/bars.svg"/>
</div>
```

Which shows a progress indicator as we are loading the graph. The graph is then loaded and faded gently into view via a settling CSS transition:

``` css
.htmx-settling img {
  opacity: 0;
}
img {
 transition: opacity 300ms ease-in;
}
```

<style>
.htmx-settling img {
  opacity: 0;
}
img {
 transition: opacity 300ms ease-in;
}
</style> <style>
  #demo-server-info {
      padding: 8px;
      position: fixed;
      bottom: 0;
      right: 0;
      left: 0;
      height: 64px;
      width: 100vw;
      background-color: whitesmoke;
      border-top: 2px solid gray;
      overflow: hide;
      margin: 0px;
      z-index: 1;
  }
  #demo-server-info.show {
      max-height: 45vh;
      height: 500px;
      overflow: scroll;
  }
  #demo-activity {
      height:300px
  }

  #demo-activity div {
      vertical-align: top
  }

  #demo-activity ol li {
      list-style-position: inside;
  }

  #demo-canvas {
      margin-bottom: 500px;
      padding-top: 12px;
  }

  @media (prefers-color-scheme: dark) {
    #demo-server-info {
      background-color: var(--footerBackground);
    }
  }
</style>

<div id="demo-server-info">

<div>

Server Requests<span id="request-count"></span> <span id="request-info-toggler" onclick="toggleRequestInfo()" style="cursor: pointer">↑ Show</span>

</div>

<div id="demo-activity" class="row">

<div class="3 col">

</div>

<div id="demo-current-request" class="9 col">

</div>

</div>

</div>

## <a href="#demo" class="zola-anchor" aria-label="Anchor link for: demo">🔗</a>Demo

<div id="demo-canvas">

</div>

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

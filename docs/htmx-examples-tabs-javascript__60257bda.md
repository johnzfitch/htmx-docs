# tabs-javascript__60257bda

- Source URL: https://htmx.org/examples/tabs-javascript/
- Source file: `fetch/htmx_org_60257bda.html`
- Hash: `60257bda`
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

# Tabs (Using JavaScript)

This example shows how to load tab contents using htmx, and to select the “active” tab using Javascript. This reduces some duplication by offloading some of the work of re-rendering the tab HTML from your application server to your clients’ browsers.

You may also consider [a more idiomatic approach](https://htmx.org/examples/tabs-hateoas/) that follows the principle of <a href="https://en.wikipedia.org/wiki/HATEOAS" rel="noopener" target="_blank">Hypertext As The Engine Of Application State</a>.

## <a href="#example-code" class="zola-anchor" aria-label="Anchor link for: example-code">Example Code</a>

The HTML below displays a list of tabs, with added HTMX to dynamically load each tab pane from the server. A simple JavaScript event handler uses the <a href="https://hyperscript.org/commands/take/" rel="noopener" target="_blank"><code>take</code> function</a> to switch the selected tab when the content is swapped into the DOM.

``` html

<div id="tabs" hx-target="#tab-contents" role="tablist"
     hx-on:htmx-after-on-load="let currentTab = document.querySelector('[aria-selected=true]');
                               currentTab.setAttribute('aria-selected', 'false')
                               currentTab.classList.remove('selected')
                               let newTab = event.target
                               newTab.setAttribute('aria-selected', 'true')
                               newTab.classList.add('selected')">
    <button role="tab" aria-controls="tab-contents" aria-selected="true" hx-get="/tab1" class="selected">Tab 1</button>
    <button role="tab" aria-controls="tab-contents" aria-selected="false" hx-get="/tab2">Tab 2</button>
    <button role="tab" aria-controls="tab-contents" aria-selected="false" hx-get="/tab3">Tab 3</button>
</div>

<div id="tab-contents" role="tabpanel" hx-get="/tab1" hx-trigger="load"></div>
```

<style>
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

<div id="tabs" hx-target="#tab-contents" role="tablist" hx-on:htmx-after-on-load="console.log(event)
                               let currentTab = document.querySelector('[aria-selected=true]');
                                          currentTab.setAttribute('aria-selected', 'false')
                                          currentTab.classList.remove('selected')
                                          let newTab = event.target
                                          newTab.setAttribute('aria-selected', 'true')
                                          newTab.classList.add('selected')">

Tab 1

Tab 2

Tab 3

</div>

<div id="tab-contents" role="tabpanel" hx-get="/tab1" hx-trigger="load">

</div>

<style>

    #demo-canvas {
        display:none;
    }

    #tabs {
    }

    #tabs > button {
        border: none;
        display: inline-block;
        padding: 5px 10px;
        cursor:pointer;
        background-color: transparent;
        border: solid 3px rgba(0,0,0,0);
        border-bottom: solid 3px #eee;
    }

    #tabs > button:hover {
        color: var(--midBlue);
    }

    #tabs > button.selected {
        border: solid 3px var(--midBlue);
    }

    #tab-contents {
        padding:10px;
    }
</style>

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

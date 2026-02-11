# tabs-hateoas__b79208cb

- Source URL: https://htmx.org/examples/tabs-hateoas/
- Source file: `fetch/htmx_org_b79208cb.html`
- Hash: `b79208cb`
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

# Tabs (Using HATEOAS)

This example shows how easy it is to implement tabs using htmx. Following the principle of <a href="https://en.wikipedia.org/wiki/HATEOAS" rel="noopener" target="_blank">Hypertext As The Engine Of Application State</a>, the selected tab is a part of the application state. Therefore, to display and select tabs in your application, simply include the tab markup in the returned HTML. If this does not suit your application server design, you can also use a little bit of [JavaScript to select tabs instead](https://htmx.org/examples/tabs-javascript/).

## <a href="#example-code-main-page" class="zola-anchor" aria-label="Anchor link for: example-code-main-page">Example Code (Main Page)</a>

The main page simply includes the following HTML to load the initial tab into the DOM.

``` html
<div id="tabs" hx-get="/tab1" hx-trigger="load delay:100ms" hx-target="#tabs" hx-swap="innerHTML"></div>
```

## <a href="#example-code-each-tab" class="zola-anchor" aria-label="Anchor link for: example-code-each-tab">Example Code (Each Tab)</a>

Subsequent tab pages display all tabs and highlight the selected one accordingly.

``` html
<div class="tab-list" role="tablist">
   <button hx-get="/tab1" class="selected" role="tab" aria-selected="true" aria-controls="tab-content">Tab 1</button>
   <button hx-get="/tab2" role="tab" aria-selected="false" aria-controls="tab-content">Tab 2</button>
   <button hx-get="/tab3" role="tab" aria-selected="false" aria-controls="tab-content">Tab 3</button>
</div>

<div id="tab-content" role="tabpanel" class="tab-content">
   Commodo normcore truffaut VHS duis gluten-free keffiyeh iPhone taxidermy godard ramps anim pour-over.
   Pitchfork vegan mollit umami quinoa aute aliquip kinfolk eiusmod live-edge cardigan ipsum locavore.
   Polaroid duis occaecat narwhal small batch food truck.
   PBR&B venmo shaman small batch you probably haven't heard of them hot chicken readymade.
   Enim tousled cliche woke, typewriter single-origin coffee hella culpa.
   Art party readymade 90's, asymmetrical hell of fingerstache ipsum.
</div>
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

<div id="tabs" hx-target="this" hx-swap="innerHTML">

<div class="tab-list" role="tablist">

Tab 1

Tab 2

Tab 3

</div>

<div id="tab-content" class="tab-content" role="tabpanel">

Commodo normcore truffaut VHS duis gluten-free keffiyeh iPhone taxidermy godard ramps anim pour-over. Pitchfork vegan mollit umami quinoa aute aliquip kinfolk eiusmod live-edge cardigan ipsum locavore. Polaroid duis occaecat narwhal small batch food truck. PBR&B venmo shaman small batch you probably haven't heard of them hot chicken readymade. Enim tousled cliche woke, typewriter single-origin coffee hella culpa. Art party readymade 90's, asymmetrical hell of fingerstache ipsum.

</div>

</div>

<style>
    #demo-canvas {
        display:none;
    }

    #tabs > .tab-list button {
        border: none;
        display: inline-block;
        padding: 5px 10px;
        cursor:pointer;
        background-color: transparent;
        color: var(--textColor);
        border: solid 3px rgba(0,0,0,0);
        border-bottom: solid 3px #eee;
    }

    #tabs > .tab-list button:hover {
        color: var(--midBlue);
    }

    #tabs > .tab-list button.selected {
        border: solid 3px var(--midBlue);
    }

    #tabs > .tab-content {
        padding:10px;
        margin-bottom:100px;
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

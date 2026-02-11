# modal-uikit__91236b72

- Source URL: https://htmx.org/examples/modal-uikit/
- Source file: `fetch/htmx_org_91236b72.html`
- Hash: `91236b72`
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

# Modal Dialogs with UIKit

Many CSS toolkits include styles (and Javascript) for creating modal dialog boxes. This example shows how to use HTMX to display dynamic dialog using UIKit, and how to trigger its animation styles with little or no Javascript.

We start with a button that triggers the dialog, along with a DIV at the bottom of your markup where the dialog will be loaded:

This is an example of using HTMX to remotely load modal dialogs using UIKit. In this example we will use <a href="https://hyperscript.org" rel="noopener" target="_blank">Hyperscript</a> to demonstrate how cleanly that scripting language allows you to glue htmx and other libraries together.

``` html
<button 
   id="showButton"
   hx-get="/uikit-modal.html" 
   hx-target="#modals-here" 
   class="uk-button uk-button-primary" 
   _="on htmx:afterOnLoad wait 10ms then add .uk-open to #modal">Open Modal</button>

<div id="modals-here"></div>
```

This button uses a `GET` request to `/uikit-modal.html` when this button is clicked. The contents of this file will be added to the DOM underneath the `#modals-here` DIV.

Rather than using the standard UIKit Javascript library we are using a bit of Hyperscript, which triggers UIKit’s smooth animations. It is delayed by 10ms so that UIKit’s animations will run correctly.

Finally, the server responds with a slightly modified version of UIKit’s standard modal

``` html
<div id="modal" class="uk-modal" style="display:block;">
   <div class="uk-modal-dialog uk-modal-body">
       <h2 class="uk-modal-title">Modal Dialog</h2>
       <p>This modal dialog was loaded dynamically by HTMX.</p>

       <form _="on submit take .uk-open from #modal">
           <div class="uk-margin">
               <input class="uk-input" placeholder="What is Your Name?">
           </div>
           <button type="button" class="uk-button uk-button-primary">Save Changes</button>
           <button 
               id="cancelButton"
               type="button" 
               class="uk-button uk-button-default" 
               _="on click take .uk-open from #modal wait 200ms then remove #modal">Close</button>
       </form>
   </div>
</div>
```

Hyperscript on the button and the form trigger animations when this dialog is completed or canceled. If you didn’t use this Hyperscript, the modals will still work but UIKit’s fade in animations will not be triggered.

You can, of course, use JavaScript rather than Hyperscript for this work, it’s just a lot more code:

``` javascript

// This triggers the fade-in animation when a modal dialog is loaded and displayed
window.document.getElementById("showButton").addEventListener("htmx:afterOnLoad", function() {
   setTimeout(function(){
       window.document.getElementById("modal").classList.add("uk-open")
   }, 10)
})


// This triggers the fade-out animation when the modal is closed.
window.document.getElementById("cancelButton").addEventListener("click", function() {
   window.document.getElementById("modal").classList.remove("uk-open")
   setTimeout(function(){
       window.document.getElementById("modals-here").innerHTML = ""
       ,200
   })
})
```

<div id="modals-here">

</div>

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

<style>
    @import "https://cdnjs.cloudflare.com/ajax/libs/uikit/3.5.9/css/uikit-core.min.css";
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

# modal-custom__4a481ad7

- Source URL: https://htmx.org/examples/modal-custom/
- Source file: `fetch/htmx_org_4a481ad7.html`
- Hash: `4a481ad7`
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

# Custom Modal Dialogs

While htmx works great with dialogs built into CSS frameworks (like [Bootstrap](https://htmx.org/examples/modal-bootstrap/) and [UIKit](https://htmx.org/examples/modal-uikit/)), htmx also makes it easy to build modal dialogs from scratch. Here is a quick example of one way to build them.

Click here to see a demo of the final result:

Open a Modal

## <a href="#high-level-plan" class="zola-anchor" aria-label="Anchor link for: high-level-plan">High Level Plan</a>

We’re going to make a button that loads remote content from the server, then displays it in a modal dialog. The modal content will be added to the end of the `<body>` element, in a div named `#modal`.

In this demo we’ll define some nice animations in CSS, and then use some <a href="https://hyperscript.org" rel="noopener" target="_blank">Hyperscript</a> to remove the modals from the DOM when the user is done. Hyperscript is *not* required with htmx, but the two were designed to be used together and it is much nicer for writing async & event oriented code than JavaScript, which is why we chose it for this example.

## <a href="#main-page-html" class="zola-anchor" aria-label="Anchor link for: main-page-html">Main Page HTML</a>

``` html
<button class="btn primary" hx-get="/modal" hx-target="body" hx-swap="beforeend">Open a Modal</button>
```

## <a href="#modal-html-fragment" class="zola-anchor" aria-label="Anchor link for: modal-html-fragment">Modal HTML Fragment</a>

``` html
<div id="modal" _="on closeModal add .closing then wait for animationend then remove me">
   <div class="modal-underlay" _="on click trigger closeModal"></div>
   <div class="modal-content">
       <h1>Modal Dialog</h1>
       This is the modal content.
       You can put anything here, like text, or a form, or an image.
       <br>
       <br>
       <button class="btn danger" _="on click trigger closeModal">Close</button>
   </div>
</div>
```

## <a href="#custom-stylesheet" class="zola-anchor" aria-label="Anchor link for: custom-stylesheet">Custom Stylesheet</a>

``` css
/***** MODAL DIALOG ****/
#modal {
   /* Underlay covers entire screen. */
   position: fixed;
   top:0px;
   bottom: 0px;
   left:0px;
   right:0px;
   background-color:rgba(0,0,0,0.5);
   z-index:1000;

   /* Flexbox centers the .modal-content vertically and horizontally */
   display:flex;
   flex-direction:column;
   align-items:center;

   /* Animate when opening */
   animation-name: fadeIn;
   animation-duration:150ms;
   animation-timing-function: ease;
}

#modal > .modal-underlay {
   /* underlay takes up the entire viewport. This is only
  required if you want to click to dismiss the popup */
   position: absolute;
   z-index: -1;
   top:0px;
   bottom:0px;
   left: 0px;
   right: 0px;
}

#modal > .modal-content {
   /* Position visible dialog near the top of the window */
   margin-top:10vh;

   /* Sizing for visible dialog */
   width:80%;
   max-width:600px;

   /* Display properties for visible dialog*/
   border:solid 1px #999;
   border-radius:8px;
   box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.3);
   background-color:white;
   padding:20px;

   /* Animate when opening */
   animation-name:zoomIn;
   animation-duration:150ms;
   animation-timing-function: ease;
}

#modal.closing {
   /* Animate when closing */
   animation-name: fadeOut;
   animation-duration:150ms;
   animation-timing-function: ease;
}

#modal.closing > .modal-content {
   /* Animate when closing */
   animation-name: zoomOut;
   animation-duration:150ms;
   animation-timing-function: ease;
}

@keyframes fadeIn {
   0% {opacity: 0;}
   100% {opacity: 1;}
}

@keyframes fadeOut {
   0% {opacity: 1;}
   100% {opacity: 0;}
}

@keyframes zoomIn {
   0% {transform: scale(0.9);}
   100% {transform: scale(1);}
}

@keyframes zoomOut {
   0% {transform: scale(1);}
   100% {transform: scale(0.9);}
}
```

<style>
/***** MODAL DIALOG ****/

#modal {
    /* Underlay covers entire screen. */
    position: fixed;
    top:0px;
    bottom: 0px;
    left:0px;
    right:0px;
    background-color:rgba(0,0,0,0.5);
    z-index:1000;

    /* Flexbox centers the .modal-content vertically and horizontally */
    display:flex;
    flex-direction:column;
    align-items:center;

    /* Animate when opening */
    animation-name: fadeIn;
    animation-duration:150ms;
    animation-timing-function: ease;
}

#modal > .modal-underlay {
    /* underlay takes up the entire viewport. This is only
    required if you want to click to dismiss the popup */
    position: absolute;
    z-index: -1;
    top:0px;
    bottom:0px;
    left: 0px;
    right: 0px;
}

#modal > .modal-content {
    /* Position visible dialog near the top of the window */
    margin-top:10vh;

    /* Sizing for visible dialog */
    width:80%;
    max-width:600px;

    /* Display properties for visible dialog*/
    border:solid 1px #999;
    border-radius:8px;
    box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.3);
    background-color:white;
    padding:20px;

    /* Animate when opening */
    animation-name:zoomIn;
    animation-duration:150ms;
    animation-timing-function: ease;
}

#modal.closing {
    /* Animate when closing */
    animation-name: fadeOut;
    animation-duration:150ms;
    animation-timing-function: ease;
}

#modal.closing > .modal-content {
    /* Animate when closing */
    animation-name: zoomOut;
    animation-duration:150ms;
    animation-timing-function: ease;
}

@keyframes fadeIn {
    0% {opacity: 0;}
    100% {opacity: 1;}
}

@keyframes fadeOut {
    0% {opacity: 1;}
    100% {opacity: 0;}
}

@keyframes zoomIn {
    0% {transform: scale(0.9);}
    100% {transform: scale(1);}
}

@keyframes zoomOut {
    0% {transform: scale(1);}
    100% {transform: scale(0.9);}
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

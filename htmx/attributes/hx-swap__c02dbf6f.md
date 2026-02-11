# hx-swap__c02dbf6f

- Source URL: https://htmx.org/attributes/hx-swap/
- Source file: `fetch/htmx_org_c02dbf6f.html`
- Hash: `c02dbf6f`
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

# `hx-swap`

The `hx-swap` attribute allows you to specify how the response will be swapped in relative to the [target](https://htmx.org/attributes/hx-target/) of an AJAX request. If you do not specify the option, the default is `htmx.config.defaultSwapStyle` (`innerHTML`).

The possible values of this attribute are:

- `innerHTML` - Replace the inner html of the target element
- `outerHTML` - Replace the entire target element with the response
- `textContent` - Replace the text content of the target element, without parsing the response as HTML
- `beforebegin` - Insert the response before the target element
- `afterbegin` - Insert the response before the first child of the target element
- `beforeend` - Insert the response after the last child of the target element
- `afterend` - Insert the response after the target element
- `delete` - Deletes the target element regardless of the response
- `none`- Does not append content from response (out of band items will still be processed).

These options are based on standard DOM naming and the <a href="https://developer.mozilla.org/en-US/docs/Web/API/Element/insertAdjacentHTML" rel="noopener" target="_blank"><code>Element.insertAdjacentHTML</code></a> specification.

So in this code:

``` html
  <div hx-get="/example" hx-swap="afterend">Get Some HTML & Append It</div>
```

The `div` will issue a request to `/example` and append the returned content after the `div`

### Modifiers

The `hx-swap` attributes supports modifiers for changing the behavior of the swap. They are outlined below.

#### Transition: `transition`

If you want to use the new <a href="https://developer.mozilla.org/en-US/docs/Web/API/View_Transitions_API" rel="noopener" target="_blank">View Transitions</a> API when a swap occurs, you can use the `transition:true` option for your swap. You can also enable this feature globally by setting the `htmx.config.globalViewTransitions` config setting to `true`.

#### Timing: `swap` & `settle`

You can modify the amount of time that htmx will wait after receiving a response to swap the content by including a `swap` modifier:

``` html
  <!-- this will wait 1s before doing the swap after it is received -->
  <div hx-get="/example" hx-swap="innerHTML swap:1s">Get Some HTML & Append It</div>
```

Similarly, you can modify the time between the swap and the settle logic by including a `settle` modifier:

``` html
  <!-- this will wait 1s before doing the settle after it is received -->
  <div hx-get="/example" hx-swap="innerHTML settle:1s">Get Some HTML & Append It</div>
```

These attributes can be used to synchronize htmx with the timing of CSS transition effects.

#### Title: `ignoreTitle`

By default, htmx will update the title of the page if it finds a `<title>` tag in the response content. You can turn off this behavior by setting the `ignoreTitle` option to true.

#### Scrolling: `scroll` & `show`

You can also change the scrolling behavior of the target element by using the `scroll` and `show` modifiers, both of which take the values `top` and `bottom`:

``` html
  <!-- this fixed-height div will scroll to the bottom of the div after content is appended -->
  <div style="height:200px; overflow: scroll" 
       hx-get="/example" 
       hx-swap="beforeend scroll:bottom">
     Get Some HTML & Append It & Scroll To Bottom
  </div>
```

``` html
  <!-- this will get some content and add it to #another-div, then ensure that the top of #another-div is visible in the 
       viewport -->
  <div hx-get="/example" 
       hx-swap="innerHTML show:top"
       hx-target="#another-div">
    Get Some Content
  </div>
```

If you wish to target a different element for scrolling or showing, you may place a CSS selector after the `scroll:` or `show:`, followed by `:top` or `:bottom`:

``` html
  <!-- this will get some content and swap it into the current div, then ensure that the top of #another-div is visible in the 
       viewport -->
  <div hx-get="/example" 
       hx-swap="innerHTML show:#another-div:top">
    Get Some Content
  </div>
```

You may also use `window:top` and `window:bottom` to scroll to the top and bottom of the current window.

``` html
  <!-- this will get some content and swap it into the current div, then ensure that the viewport is scrolled to the
       very top -->
  <div hx-get="/example" 
       hx-swap="innerHTML show:window:top">
    Get Some Content
  </div>
```

For boosted links and forms the default behaviour is `show:top`. You can disable it globally with [htmx.config.scrollIntoViewOnBoost](https://htmx.org/api/#config) or you can use `hx-swap="show:none"` on an element basis.

``` html
<form action="/example" hx-swap="show:none">
  ...
</form>
```

#### Focus scroll

htmx preserves focus between requests for inputs that have a defined id attribute. By default htmx prevents auto-scrolling to focused inputs between requests which can be unwanted behavior on longer requests when the user has already scrolled away. To enable focus scroll you can use `focus-scroll:true`.

``` html
  <input id="name" hx-get="/validation" 
       hx-swap="outerHTML focus-scroll:true"/>
```

Alternatively, if you want the page to automatically scroll to the focused element after each request you can change the htmx global configuration value `htmx.config.defaultFocusScroll` to true. Then disable it for specific requests using `focus-scroll:false`.

``` html
  <input id="name" hx-get="/validation" 
       hx-swap="outerHTML focus-scroll:false"/>
```

## Notes

- `hx-swap` is inherited and can be placed on a parent element
- The default value of this attribute is `innerHTML`
- Due to DOM limitations, it’s not possible to use the `outerHTML` method on the `<body>` element. htmx will change `outerHTML` on `<body>` to use `innerHTML`.
- The default swap delay is 0ms
- The default settle delay is 20ms

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

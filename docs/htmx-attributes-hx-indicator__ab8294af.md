# hx-indicator__ab8294af

- Source URL: https://htmx.org/attributes/hx-indicator/
- Source file: `fetch/htmx_org_ab8294af.html`
- Hash: `ab8294af`
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

# `hx-indicator`

The `hx-indicator` attribute allows you to specify the element that will have the `htmx-request` class added to it for the duration of the request. This can be used to show spinners or progress indicators while the request is in flight.

The value of this attribute is a CSS query selector of the element or elements to apply the class to, or the keyword <a href="https://developer.mozilla.org/docs/Web/API/Element/closest" rel="noopener" target="_blank"><code>closest</code></a>, followed by a CSS selector, which will find the closest ancestor element or itself, that matches the given CSS selector (e.g. `closest tr`);

Here is an example with a spinner adjacent to the button:

``` html
<div>
    <button hx-post="/example" hx-indicator="#spinner">
        Post It!
    </button>
    <img  id="spinner" class="htmx-indicator" src="/img/bars.svg" alt="Loading..."/>
</div>
```

Note that you can also use the `inherit` keyword to inherit parent values for an indicator and add additional indicator CSS selectors:

``` html
<main hx-indicator="#global-indicator">
    ...
    <button hx-post="/example" hx-indicator="inherit, #spinner">
        Post It!
    </button>
    <img  id="spinner" class="htmx-indicator" src="/img/bars.svg" alt="Loading..."/>
</main>
```

When a request is in flight, this will cause the `htmx-request` class to be added to the `#spinner` image. The image also has the `htmx-indicator` class on it, which defines an opacity transition that will show the spinner:

``` css
    .htmx-indicator {
        opacity: 0;
        visibility: hidden;
    }
    .htmx-request .htmx-indicator,
    .htmx-request.htmx-indicator {
        opacity: 1;
        visibility: visible;
        transition: opacity 200ms ease-in;
    }
```

This default `htmx-indicator` CSS also sets the visibility to hidden for better screen reader accessibility and does a quick fade in of the opacity.

If you would prefer a different effect for showing the spinner you could define and use your own indicator CSS. Here is an example that uses `display` rather than opacity (Note that we use `my-indicator` instead of `htmx-indicator`):

``` css
    .my-indicator{
        display:none;
    }
    .htmx-request .my-indicator,
    .htmx-request.my-indicator{
        display:inline;
    }
```

Note that the target of the `hx-indicator` selector need not be the exact element that you want to show: it can be any element in the parent hierarchy of the indicator.

Finally, note that the `htmx-request` class by default is added to the element causing the request, so you can place an indicator inside of that element and not need to explicitly call it out with the `hx-indicator` attribute:

``` html
<button hx-post="/example">
    Post It!
   <img  class="htmx-indicator" src="/img/bars.svg" alt="Loading..."/>
</button>
```

## Demo

This simulates what a spinner might look like in that situation:

Post It! <img src="/img/bars.svg" class="htmx-indicator" alt="Loading..." />

## Notes

- `hx-indicator` is inherited and can be placed on a parent element
- In the absence of an explicit indicator, the `htmx-request` class will be added to the element triggering the request
- If you want to use your own CSS but still use `htmx-indicator` as class name, then you need to disable `includeIndicatorStyles`. See [Configuring htmx](https://htmx.org/docs/#config). The easiest way is to add this to the `<head>` of your HTML:

``` html
<meta name="htmx-config" content='{"includeIndicatorStyles": false}'>
```

- the `htmx-indicator` CSS added when this config is not disabled uses an inline style tag which may need you to set `inlineStyleNonce` config if you have a strict nonce based CSP policy for `style-src`

``` html
<meta name="htmx-config" content='{"inlineStyleNonce": "random-nonce"}'>
```

- If your CSP needs to block all inline style tags then disable `includeIndicatorStyles` and host your own CSS file with a copy of your preferred `htmx-indicator` style from above

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

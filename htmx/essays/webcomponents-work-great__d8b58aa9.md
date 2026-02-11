# webcomponents-work-great__d8b58aa9

- Source URL: https://htmx.org/essays/webcomponents-work-great/
- Source file: `fetch/htmx_org_d8b58aa9.html`
- Hash: `d8b58aa9`
- Category: `htmx/essays`

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

# Web Components Work Great with htmx

Alexander Petros

November 13, 2024

People interested in htmx often ask us about component libraries. React and other JavaScript frameworks have great ecosystems of pre-built components that can be imported into your project; htmx doesn’t really have anything similar.

The first and most important thing to understand is that htmx doesn’t preclude you from using *anything*. Because htmx-based websites are <a href="https://unplannedobsolescence.com/blog/less-htmx-is-more/" rel="noopener" target="_blank">often multi-page apps</a>, each page is a blank canvas on which you can import as much or as little JavaScript as you like. If your app is largely hypermedia, but you want an interactive, React-based calendar for one page, just import it on that one page with a script tag.

We sometimes call this pattern “Islands of Interactivity”—it’s referenced in our explainers [here](https://htmx.org/essays/10-tips-for-ssr-hda-apps/#tip-8-when-necessary-create-islands-of-interactivity), [here](https://htmx.org/essays/hypermedia-friendly-scripting/#islands), and [here](https://htmx.org/essays/you-cant/#myth-5-with-htmx-or-mpas-every-user-action-must-happen-on-the-server). Unlike JS frameworks, which are largely incompatible with each other, using islands with htmx won’t lock you into any specific paradigm.

But there’s a second way that you can re-use complex frontend functionality with htmx, and it’s <a href="https://developer.mozilla.org/en-US/docs/Web/API/Web_components" rel="noopener" target="_blank">Web Components</a>!

## <a href="#practical-example" class="zola-anchor" aria-label="Anchor link for: practical-example">Practical Example</a>

Let’s say that you have a table that says what carnival rides everyone is signed up for:

Name

Carousel

Roller Coaster

Alex

Yes

No

Sophia

Yes

Yes

Alex is willing to go on the carousel but not the roller coaster, because he is scared; Sophia is not scared of either.

I built this as a regular HTML table (<a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/td#technical_summary" rel="noopener" target="_blank">closing tags are omitted</a> for clarity):

``` html
<table>
  <tr><th>Name    <th>Carousel  <th>Roller Coaster
  <tr><td>Alex    <td>Yes       <td>No
  <tr><td>Sophia  <td>Yes       <td>Yes
</table>
```

Now imagine we want to make those rows editable. This is a classic situation in which people reach for frameworks, but can we do it with hypermedia? Sure! Here’s a naive idea:

``` html
<form hx-put=/carnival>
<table>
  <tr>
    <th>Name
    <th>Carousel
    <th>Roller Coaster
  </tr>
  <tr>
    <td>Alex
    <td><select name="alex-carousel"> <option selected>Yes <option>No <option> Maybe</select>
    <td><select name="alex-roller"> <option>Yes <option selected>No <option> Maybe</select>
  </tr>
  <tr>
    <td>Sophia
    <td><select name="sophia-carousel"> <option selected>Yes <option>No <option> Maybe</select>
    <td><select name="sophia-roller"> <option selected>Yes <option>No <option> Maybe</select>
  </tr>
</table>
<button>Save</button>
</form>
```

\
That will give us this table:

Name

Carousel

Roller Coaster

Alex

Sophia

Save

That’s not too bad! The save button will submit all the data in the table, and the server will respond with a new table that reflects the updated state. We can also use CSS to make the `<select>`s fit our design language. But it’s easy to see how this could start to get unwieldy—with more columns, more rows, and more options in each cell, sending all that information each time starts to get costly.

Let’s remove all that redundancy with a web component!

``` html
<form hx-put=/carnival>
<table>
  <tr>
    <th>Name
    <th>Carousel
    <th>Roller Coaster
  </tr>
  <tr>
    <td>Alex
    <td><edit-cell name="alex-carousel" value="Yes"></edit-cell>
    <td><edit-cell name="alex-roller" value="No"></edit-cell>
  </tr>
  <tr>
    <td>Sophia
    <td><edit-cell name="sophia-carousel" value="Yes"></edit-cell>
    <td><edit-cell name="sophia-roller" value="Yes"></edit-cell>
  </tr>
</table>
<button>Save</button>
</form>
```

We still have an entirely declarative <a href="https://htmx.org/essays/hateoas/" rel="noopener" target="_blank">HATEOAS</a> interface—both current state (the `value` attribute) and possible actions on that state (the `<form>` and `<edit-cell>` elements) are efficiently encoded in the hypertext—only now we’ve expressed the same ideas a lot more concisely. htmx can add or remove rows (or better yet, whole tables) with the `<edit-cell>` web component as if `<edit-cell>` were a built-in HTML element.

You’ve probably noticed that I didn’t include the implementation details for `<edit-cell>` (although you can, [of course](https://htmx.org/essays/right-click-view-source/), View Source this page to see them). That’s because they don’t matter! Whether the web component was written by you, or a teammate, or a library author, it can be used exactly like a built-in HTML element and htmx will handle it just fine.

## <a href="#don-t-web-components-have-some-problems" class="zola-anchor" aria-label="Anchor link for: don-t-web-components-have-some-problems">Don’t Web Components have some problems?</a>

A lot of the problems that JavaScript frameworks have supporting Web Components don’t apply to htmx.

Web Components <a href="https://dev.to/ryansolid/web-components-are-not-the-future-48bh" rel="noopener" target="_blank">have DOM-based lifecycles</a>, so they are difficult for JavaScript frameworks, which often manipulate elements outside of the DOM, to work with. Frameworks have to account for some <a href="https://x.com/Rich_Harris/status/1841467510194843982" rel="noopener" target="_blank">bizarre and arguably buggy</a> APIs that behave differently for native DOM elements than they do for custom ones. Here at htmx, we agree with <a href="https://x.com/Rich_Harris/status/1839484645194277111" rel="noopener" target="_blank">SvelteJS creator Rich Harris</a>: “web components are \[not\] useful primitives on which to build web frameworks.”

The good news is that htmx [is not really a JavaScript web framework](https://htmx.org/essays/is-htmx-another-javascript-framework/). The DOM-based lifecycles of custom elements work great in htmx, because everything in htmx has a DOM-based lifecycle—we get stuff from the server, and we add it to the DOM. The default htmx swap style is to just set <a href="https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML" rel="noopener" target="_blank"><code>.innerHTML</code></a>, and that works great for the vast majority of users.

That’s not to say that htmx doesn’t have to accommodate weird Web Component edge cases. Our community member and resident WC expert <a href="https://unmodernweb.com/" rel="noopener" target="_blank">Katrina Scialdone</a> merged <a href="https://github.com/bigskysoftware/htmx/pull/2075" rel="noopener" target="_blank">Shadow DOM support for htmx 2.0</a>, which lets htmx process the implementation details of a Web Component, and supporting that is <a href="https://github.com/bigskysoftware/htmx/pull/2846" rel="noopener" target="_blank">occasionally</a> <a href="https://github.com/bigskysoftware/htmx/pull/2866" rel="noopener" target="_blank">frustrating</a>. But being able to work with both the [Shadow DOM](https://htmx.org/examples/web-components/) and the <a href="https://meyerweb.com/eric/thoughts/2023/11/01/blinded-by-the-light-dom/" rel="noopener" target="_blank">“Light DOM”</a> is a nice feature for htmx, and it carries a relatively minimal support burden because htmx just isn’t doing all that much.

## <a href="#bringing-behavior-back-to-the-html" class="zola-anchor" aria-label="Anchor link for: bringing-behavior-back-to-the-html">Bringing Behavior Back to the HTML</a>

A couple of years ago, W3C Contributor (and Web Component proponent, I think) Lea Verou wrote the following, in a blog post about <a href="https://lea.verou.me/blog/2020/09/the-failed-promise-of-web-components/" rel="noopener" target="_blank">“The failed promise of Web Components”</a>:

> the main problem is that HTML is not treated with the appropriate respect in the design of these components. They are not designed as closely as possible to standard HTML elements, but expect JS to be written for them to do anything. HTML is simply treated as a shorthand, or worse, as merely a marker to indicate where the element goes in the DOM, with all parameters passed in via JS.

Lea is identifying an issue that, from the perspective of 2020, would have seemed impossible to solve: the cutting-edge web developers targeted by Web Components were not writing HTML, they were writing JSX, usually with React (or Vue, or what have you). The idea that <a href="https://unplannedobsolescence.com/blog/behavior-belongs-in-html/" rel="noopener" target="_blank">behavior belongs in the HTML</a> was, in the zeitgeist, considered <a href="https://htmx.org/essays/locality-of-behaviour/" rel="noopener" target="_blank">a violation of separation of concerns</a>; disrespecting HTML was best practice.

The relatively recent success of htmx—itself now a participant in the zeitgeist—offers an alternative path: take HTML seriously again. If your website is one whose functionality can be primarily described with [large-grain hypermedia transfers](https://htmx.org/essays/when-to-use-hypermedia/) (we believe most of them can), then the value of being able to express more complex patterns through hypermedia increases dramatically. As more developers use htmx (and multi-page architectures generally) to structure their websites, perhaps the demand for Web Components will increase along with it.

Do Web Components “just work” everywhere? Maybe, maybe not. But they do work here.

<div style="padding-top: 120px;padding-bottom:40px;text-align: center">

\</\>

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

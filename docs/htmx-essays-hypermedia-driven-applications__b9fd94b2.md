# hypermedia-driven-applications__b9fd94b2

- Source URL: https://htmx.org/essays/hypermedia-driven-applications/
- Source file: `fetch/htmx_org_b9fd94b2.html`
- Hash: `b9fd94b2`
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

# Hypermedia-Driven Applications

Carson Gross

February 06, 2022

## <a href="#genesis" class="zola-anchor" aria-label="Anchor link for: genesis">Genesis</a>

> thesis: MPA - multi-page application
>
> antithesis: SPA - single-page application
>
> synthesis: HDA - hypermedia-driven application
>
> --<a href="https://twitter.com/htmx_org/status/1490318550170357760" rel="noopener" target="_blank">@htmx_org</a>

## <a href="#the-hypermedia-driven-application-architecture" class="zola-anchor" aria-label="Anchor link for: the-hypermedia-driven-application-architecture">The Hypermedia-Driven Application Architecture</a>

The **Hypermedia Driven Application (HDA)** architecture is a new/old approach to building web applications. It combines the simplicity & flexibility of traditional Multi-Page Applications (MPAs) with the better user experience of <a href="https://en.wikipedia.org/wiki/Single-page_application" rel="noopener" target="_blank">Single-Page Applications</a> (SPAs).

The HDA architecture achieves this goal by extending the existing HTML infrastructure of the web to allow hypermedia developers to create more powerful hypermedia-driven interactions.

Following the REST notion of architectural <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm" rel="noopener" target="_blank">constraints</a>, two such constraints characterize the HDA architecture:

- An HDA uses *declarative, HTML-embedded syntax* rather than imperative scripting to achieve better front-end interactivity

- An HDA interacts with the server **in terms of hypermedia** (i.e. HTML) rather than a non-hypermedia format (e.g. JSON)

By adopting these two constraints, the HDA architecture stays within the original <a href="https://developer.mozilla.org/en-US/docs/Glossary/REST" rel="noopener" target="_blank">REST-ful</a> architecture of the web in a way that the SPA architecture does not.

In particular, HDAs continue to use [Hypermedia As The Engine of Application State (HATEOAS)](https://htmx.org/essays/hateoas/), whereas most SPAs abandon HATEOAS in favor of a client-side model and data (rather than hypermedia) APIs.

## <a href="#an-example-hda-fragment" class="zola-anchor" aria-label="Anchor link for: an-example-hda-fragment">An Example HDA fragment</a>

Consider the htmx [Active Search](https://htmx.org/examples/active-search/) example:

``` html
<h3> 
  Search Contacts 
  <span class="htmx-indicator"> 
    <img src="/img/bars.svg" alt=""/> Searching... 
   </span> 
</h3>
<input class="form-control" type="search" 
       name="search" placeholder="Begin Typing To Search Users..." 
       hx-post="/search" 
       hx-trigger="keyup changed delay:500ms, search" 
       hx-target="#search-results" 
       hx-indicator=".htmx-indicator">

<table class="table">
    <thead>
    <tr>
      <th>First Name</th>
      <th>Last Name</th>
      <th>Email</th>
    </tr>
    </thead>
    <tbody id="search-results">
    </tbody>
</table>
```

This is a UX pattern that would typically be associated with an SPA: as the user types, after a slight pause, search results will populate the result table below. However, in this case, it is being achieved entirely within HTML, in a manner consonant with HTML.

This example effectively demonstrates the essential characteristic of an HDA:

- The front end of the feature is specified entirely in declarative htmx attributes, directly in HTML

- The interaction with the server is done via HTTP and HTML: an HTTP `POST` request is sent to the server, HTML is returned by the server and htmx inserts this HTML into the DOM

## <a href="#scripting-in-an-hda" class="zola-anchor" aria-label="Anchor link for: scripting-in-an-hda">Scripting In An HDA</a>

<a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_7" rel="noopener" target="_blank">Code-On-Demand</a> is an optional constraint of the original REST-ful architecture of the web.

Similarly, the HDA architecture has a final, optional constraint:

- Code-On-Demand (i.e. scripting) should, as much as is practical, be done *directly in* the primary hypermedia

This addresses the concern regarding Code-On-Demand that Roy Fielding mentions in his thesis:

> However, (Code-On-Demand) also reduces visibility, and thus is only an optional constraint within REST.

By embedding Code-On-Demand (scripts) directly in HTML, visibility is enhanced, satisfying the [Locality of Behavior](https://htmx.org/essays/locality-of-behaviour/) software design principle.

Three approaches to scripting that satisfy this third constraint are <a href="https://hyperscript.org" rel="noopener" target="_blank">hyperscript</a>, <a href="https://alpinejs.dev" rel="noopener" target="_blank">AlpineJS</a> and <a href="http://vanilla-js.com/" rel="noopener" target="_blank">VanillaJS</a> (when embedded directly on HTML elements).

Here is an example of each of these approaches:

``` html
<!-- hyperscript -->
<button _="on click toggle .red-border">
  Toggle Class
</button>

<!-- Alpine JS -->
<button @click="open = !open" :class="{'red-border' : open, '' : !open}">
  Toggle Class
</button>

<!-- VanillaJS -->
<button onclick="this.classList.toggle('red-border')">
  Toggle Class
</button>
```

In an HDA, hypermedia (HTML) is the primary medium for building the application, which means that:

- All communication with the server is still managed via HTTP requests with hypermedia (HTML) responses
- Scripting is used mainly to enhance the *front-end experience* of the application

Scripting augments the existing hypermedia (HTML) but does not *supersede* it or subvert the fundamental REST-ful architecture of the HDA.

## <a href="#hda-style-libraries" class="zola-anchor" aria-label="Anchor link for: hda-style-libraries">HDA-style libraries</a>

The following libraries allow developers to create HDAs:

- <a href="https://htmx.org" rel="noopener" target="_blank">https://htmx.org</a>
- <a href="https://unpoly.com/" rel="noopener" target="_blank">https://unpoly.com/</a>
- <a href="https://piranha.github.io/twinspark-js/" rel="noopener" target="_blank">https://piranha.github.io/twinspark-js/</a>
- <a href="https://hotwire.dev" rel="noopener" target="_blank">https://hotwire.dev</a>
- <a href="https://hyperview.org/" rel="noopener" target="_blank">https://hyperview.org/</a> (a mobile hypermedia!)

The following scripting libraries, when used appropriately, complement the HDA approach:

- <a href="https://hyperscript.org" rel="noopener" target="_blank">https://hyperscript.org</a>
- <a href="https://alpinejs.dev/" rel="noopener" target="_blank">https://alpinejs.dev/</a>
- <a href="http://vanilla-js.com/" rel="noopener" target="_blank">http://vanilla-js.com/</a> (embedded directly in HTML)

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

The HDA architecture is a synthesis of two preceding architectures: the original Multi-Page Application (MPA) architecture and the (relatively) newer Single-Page Application architecture.

It attempts to capture the advantages of both: the simplicity and reliability of MPAs, with a <a href="https://developer.mozilla.org/en-US/docs/Glossary/REST" rel="noopener" target="_blank">REST-ful Architecture</a> that uses [Hypermedia As The Engine Of Application State](https://htmx.org/essays/hateoas/), while providing a better user experience, on par with SPAs in many cases.

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

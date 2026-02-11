# alternatives__14535d2c

- Source URL: https://htmx.org/essays/alternatives/
- Source file: `fetch/htmx_org_14535d2c.html`
- Hash: `14535d2c`
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

# Alternatives to htmx

Carson Gross

January 12, 2025

[htmx](/) is only one of many different libraries & frameworks that take the [hypermedia oriented](https://htmx.org/essays/hypermedia-driven-applications/) approach to building web applications. I have said before that I think the [ideas of htmx](/essays) / <a href="https://hypermedia.systems" rel="noopener" target="_blank">hypermedia</a> are more important than htmx as an implementation.

Here are some of my favorite other takes on these ideas that I think are worth your consideration:

## <a href="#unpoly" class="zola-anchor" aria-label="Anchor link for: unpoly">Unpoly</a>

<a href="https://unpoly.com/" rel="noopener" target="_blank">Unpoly</a> is a wonderful, mature front end framework that has been used heavily (especially in the ruby community) for over a decade now. It offers best-in-class <a href="https://developer.mozilla.org/en-US/docs/Glossary/Progressive_Enhancement" rel="noopener" target="_blank">progressive enhancement</a> and has many useful concepts such as <a href="https://unpoly.com/up.layer" rel="noopener" target="_blank">layers</a> and sophisticated <a href="https://unpoly.com/validation" rel="noopener" target="_blank">form validation</a>.

I interviewed the author, Henning Koch, [here](https://htmx.org/essays/interviews/henning-koch/)

You can see a demo application using Unpoly <a href="https://demo.unpoly.com/" rel="noopener" target="_blank">here</a>.

## <a href="#triptych" class="zola-anchor" aria-label="Anchor link for: triptych">Triptych</a>

<a href="https://github.com/alexpetros/triptych" rel="noopener" target="_blank">Triptych</a> is a set of <a href="https://alexanderpetros.com/triptych/" rel="noopener" target="_blank">three proposals</a> to bring more generalized hypermedia controls directly into the HTML specification:

- Allow more <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods" rel="noopener" target="_blank">HTTP Methods</a> to be used directly from HTML
- Allow buttons to act as stand-alone hypermedia controls
- Allow hypermedia controls to target any element on the page for replacement

It is <a href="https://github.com/whatwg/html/issues/3577#issuecomment-2294931398" rel="noopener" target="_blank">in the process</a> of being introduced to the <a href="https://whatwg.org/" rel="noopener" target="_blank">WHATWG</a> for inclusion in the HTML specification.

The project includes a <a href="https://github.com/alexpetros/triptych/blob/main/triptych.js" rel="noopener" target="_blank">polyfill</a> that can be used today to implement applications using the proposal today.

## <a href="#fixi-js" class="zola-anchor" aria-label="Anchor link for: fixi-js">fixi.js</a>

<a href="https://github.com/bigskysoftware/fixi" rel="noopener" target="_blank">fixi.js</a> is a minimalist implementation of <a href="https://dl.acm.org/doi/fullHtml/10.1145/3648188.3675127" rel="noopener" target="_blank">generalized hypermedia controls</a> by the htmx team, focusing on being as small as possible and <a href="https://github.com/bigskysoftware/fixi#minimalism" rel="noopener" target="_blank">omitting</a> many of the features found in htmx.

It is intended to be as small as possible (~3.5k unminified & uncompressed, ~1.3k compressed) while still being readable and debuggable, so it can be included in a project directly without requiring any transformations.

## <a href="#datastar" class="zola-anchor" aria-label="Anchor link for: datastar">Datastar</a>

<a href="https://data-star.dev/" rel="noopener" target="_blank">Datastar</a> started life as a proposed rewrite of htmx in typescript and with modern tooling. It eventually became its own project and takes an <a href="https://data-star.dev/guide/getting_started#backend-setup" rel="noopener" target="_blank">SSE-oriented</a> approach to hypermedia.

Datastar combines functionality found in both htmx and <a href="https://alpinejs.dev/" rel="noopener" target="_blank">Alpine.js</a> into a single, tidy package that is smaller than htmx.

You can see many examples of Datastar in action <a href="https://data-star.dev/examples" rel="noopener" target="_blank">here</a>.

## <a href="#nomini" class="zola-anchor" aria-label="Anchor link for: nomini">Nomini</a>

<a href="https://github.com/nonnorm/nomini" rel="noopener" target="_blank">Nomini</a> is a hypermedia implementation that embraces writing JavaScript in the original and intended way, as a simple enhancement to mostly-static pages. Its goal is to add a minimal layer of LoB on top of HTML to allow for powerful server-driven web apps with easily implemented client-side features. Additionally, it is currently the smallest library existing that gives both reactive variables and partial page swaps (~2.8k minified, ~1.4k minzipped).

In essence, Nomini is a tiny reimplementation of Datastar or a combination of Fixi and Alpine.js, intended to be a minimal, pragmatic building block for reactive server-driven UIs.

## <a href="#alpine-ajax" class="zola-anchor" aria-label="Anchor link for: alpine-ajax">Alpine-ajax</a>

Speaking of Alpine (which is a common library to use in conjunction with htmx) you should look at <a href="https://alpine-ajax.js.org/" rel="noopener" target="_blank">Alpine AJAX</a>, an Alpine plugin which integrates htmx-like concepts directly into Alpine.

If you are already an Alpine enthusiast, Alpine AJAX allows you to stay in that world.

You can see many examples of Alpine AJAX in action <a href="https://alpine-ajax.js.org/examples/" rel="noopener" target="_blank">here</a>.

## <a href="#hotwire-turbo" class="zola-anchor" aria-label="Anchor link for: hotwire-turbo">Hotwire Turbo</a>

<a href="https://turbo.hotwired.dev/" rel="noopener" target="_blank">Turbo</a> is a component of the <a href="https://hotwired.dev/" rel="noopener" target="_blank">Hotwire</a> set of web development technologies by <a href="https://37signals.com/" rel="noopener" target="_blank">37Signals</a>, of <a href="https://rubyonrails.org/" rel="noopener" target="_blank">Ruby on Rails</a> fame. It is a polished front end framework that is used heavily in the rails community, but can be used with other backend technologies as well.

Some people who have had a bad experience with htmx <a href="https://news.ycombinator.com/item?id=42615663" rel="noopener" target="_blank">have enjoyed turbo</a>.

## <a href="#htmz" class="zola-anchor" aria-label="Anchor link for: htmz">htmz</a>

<a href="https://leanrada.com/htmz/" rel="noopener" target="_blank">htmz</a> is a brilliant, tiny library that takes advantage of the fact that anchors and forms already have a <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a#target" rel="noopener" target="_blank"><code>target</code></a> attribute that can target an `iframe`.

This, in combination with the `location hash`, is used to allow <a href="https://dl.acm.org/doi/fullHtml/10.1145/3648188.3675127#sec-7" rel="noopener" target="_blank">generalized transclusion</a>.

This is the *entire* source of the library (I’m not joking):

``` html
  <iframe hidden name=htmz onload="setTimeout(()=>document.querySelector(contentWindow.location.hash||null)?.replaceWith(...contentDocument.body.childNodes))"></iframe>
```

Amazing!

## <a href="#twinspark" class="zola-anchor" aria-label="Anchor link for: twinspark">TwinSpark</a>

<a href="https://twinspark.js.org/" rel="noopener" target="_blank">TwinSpark</a> is a library created by <a href="https://solovyov.net/" rel="noopener" target="_blank">Alexander Solovyov</a> that is similar to htmx, and includes features such as <a href="https://twinspark.js.org/api/ts-swap/#morph" rel="noopener" target="_blank">morphing</a>.

It is being <a href="https://twinspark.js.org#who-is-using-this" rel="noopener" target="_blank">used in production</a> on sites with 100k+ daily users.

## <a href="#jquery" class="zola-anchor" aria-label="Anchor link for: jquery">jQuery</a>

Finally, good ol’ <a href="https://jquery.com/" rel="noopener" target="_blank">jQuery</a> has the the <a href="https://api.jquery.com/load/#load-url-data-complete" rel="noopener" target="_blank"><code>load()</code></a> function that will load a given url into an element. This method was part of the inspiration for <a href="https://intercoolerjs.org" rel="noopener" target="_blank">intercooler.js</a>, the precursor to htmx.

It is very simple to use:

``` javascript
  $( "#result" ).load( "ajax/test.html" );
```

and might be enough for your needs if you are already using jQuery.

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

I hope that if htmx isn’t right for your application, one of these other libraries might be useful in allowing you to utilize the hypermedia model. There is a lot of exciting stuff happening in the hypermedia world right now, and these libraries each contribute to that.

Finally, if you have a moment, please give them (especially the newer ones) a star on Github: as an open source developer I know that Github stars are one of the best psychological boosts that help keep me going.

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

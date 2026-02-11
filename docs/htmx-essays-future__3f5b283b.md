# future__3f5b283b

- Source URL: https://htmx.org/essays/future/
- Source file: `fetch/htmx_org_3f5b283b.html`
- Hash: `3f5b283b`
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

# The future of htmx

Carson Gross, Alex Petros

January 01, 2025

## <a href="#in-the-beginning" class="zola-anchor" aria-label="Anchor link for: in-the-beginning">In The Beginning…</a>

htmx began life as <a href="https://intercoolerjs.org" rel="noopener" target="_blank">intercooler.js</a>, a library built around jQuery that added behavior based on HTML attributes.

For developers who are not familiar with it, <a href="https://jquery.com/" rel="noopener" target="_blank">jQuery</a> is a venerable JavaScript library that made writing cross-platform JavaScript a lot easier during a time when browser implementations were very inconsistent, and JavaScript didn’t have many of the convenient APIs and features that it does now.

Today many web developers consider jQuery to be “legacy software.” With all due respect to this perspective, jQuery is currently used on <a href="https://w3techs.com/technologies/overview/javascript_library" rel="noopener" target="_blank">75% of all public websites</a>, a number that dwarfs all other JavaScript tools.

Why has jQuery remained so ubiquitous?

Here are three technical reasons we believe contribute to its ongoing success:

- It is very easy to add to a project (just a single, dependency-free link)
- It has maintained a very consistent API, remaining largely backwards compatible over its life (intercooler.js works with jQuery v1, v2 and v3)
- As a library, you can use as much or as little of it as you like: it stays out of the way otherwise and doesn’t dictate the structure of your application

## <a href="#htmx-is-the-new-jquery" class="zola-anchor" aria-label="Anchor link for: htmx-is-the-new-jquery">htmx is the New jQuery</a>

Now, that’s a ridiculous (and arrogant) statement to make, of course, but it is an *ideal* that we on the htmx team are striving for.

In particular, we want to emulate these technical characteristics of jQuery that make it such a low-cost, high-value addition to the toolkits of web developers. Alex has discussed <a href="https://www.youtube.com/watch?v=lASLZ9TgXyc" rel="noopener" target="_blank">“Building The 100 Year Web Service”</a> and we want htmx to be a useful tool for exactly that use case.

Websites that are built with jQuery stay online for a very long time, and websites built with htmx should be capable of the same (or better).

Going forward, htmx will be developed with its *existing* users in mind.

If you are an existing user of htmx—or are thinking about becoming one—here’s what that means.

### <a href="#stability-as-a-feature" class="zola-anchor" aria-label="Anchor link for: stability-as-a-feature">Stability as a Feature</a>

We are going to work to ensure that htmx is extremely stable in both API & implementation. This means accepting and documenting the <a href="https://htmx.org/quirks/" rel="noopener" target="_blank">quirks</a> of the current implementation.

Someone upgrading htmx (even from 1.x to 2.x) should expect things to continue working as before.

Where appropriate, we may add better configuration options, but we won’t change defaults.

### <a href="#no-new-features-as-a-feature" class="zola-anchor" aria-label="Anchor link for: no-new-features-as-a-feature">No New Features as a Feature</a>

We are going to be increasingly inclined to not accept new proposed features in the library core.

People shouldn’t feel pressure to upgrade htmx over time unless there are specific bugs that they want fixed, and they should feel comfortable that the htmx that they write in 2025 will look very similar to htmx they write in 2035 and beyond.

We will consider new core features when new browser features become available, for example we are <a href="https://htmx.org/examples/move-before/" rel="noopener" target="_blank">already using</a> the experimental `moveBefore()` API on supported browsers.

However, we expect most new functionality to be explored and delivered via the htmx <a href="https://htmx.org/extensions/" rel="noopener" target="_blank">extensions API</a>, and will work to make the extensions API more capable where appropriate.

### <a href="#quarterly-releases" class="zola-anchor" aria-label="Anchor link for: quarterly-releases">Quarterly Releases</a>

Our release schedule is going to be roughly quarterly going forward.

There will be no death march upgrades associated with htmx, and there is no reason to monitor htmx releases for major functionality changes, just like with jQuery. If htmx 1.x is working fine for you, there is no reason to feel like you need to move to 2.x.

## <a href="#promoting-hypermedia" class="zola-anchor" aria-label="Anchor link for: promoting-hypermedia">Promoting Hypermedia</a>

htmx does not aim to be a total solution for building web applications and services: it <a href="https://dl.acm.org/doi/pdf/10.1145/3648188.3675127" rel="noopener" target="_blank">generalizes hypermedia controls</a>, and that’s roughly about it.

This means that a very important way to improve htmx — and one with lots of work remaining — is by helping improve the tools and techniques that people use *in conjunction* with htmx.

Doing so makes htmx dramatically more useful *without* any changes to htmx itself.

### <a href="#supporting-supplemental-tools" class="zola-anchor" aria-label="Anchor link for: supporting-supplemental-tools">Supporting Supplemental Tools</a>

While htmx gives you a few new tools in your HTML, it has no opinions about other important aspects of building your websites. A flagship feature of htmx is that it does not dictate what backend or database you use.

htmx is <a href="https://htmx.org/essays/hypermedia-on-whatever-youd-like/" rel="noopener" target="_blank">compatible with lots of backends</a>, and we want to help make hypermedia-driven development work better for all of them.

One part of the hypermedia ecosystem that htmx has already helped improve is template engines. When we <a href="https://htmx.org/essays/template-fragments/" rel="noopener" target="_blank">first wrote</a> about how “template fragments” make defining partial page replacements much simpler, they were a relatively rare feature in template engines.

Not only are fragments much more common now, that essay is <a href="https://github.com/mitsuhiko/minijinja/issues/260" rel="noopener" target="_blank">frequently</a> <a href="https://github.com/sponsfreixes/jinja2-fragments" rel="noopener" target="_blank">cited</a> as an inspiration for building the feature.

There are many other ways that the experience of writing hypermedia-based applications can be improved, and we will remain dedicated to identifying and promoting those efforts.

### <a href="#writing-research-and-standardization" class="zola-anchor" aria-label="Anchor link for: writing-research-and-standardization">Writing, Research, and Standardization</a>

Although htmx will not be changing dramatically going forward, we will continue energetically evangelizing the ideas of hypermedia.

In particular, we are trying to push <a href="https://dl.acm.org/doi/pdf/10.1145/3648188.3675127" rel="noopener" target="_blank">the ideas</a> of htmx into the HTML standard itself, via the <a href="https://alexanderpetros.com/triptych/" rel="noopener" target="_blank">Triptych project</a>. In an ideal world, htmx functionality disappears into the web platform itself.

htmx code written *today* will continue working forever, of course, but in the very long run perhaps there will be no need to include the library to achieve <a href="https://htmx.org/examples" rel="noopener" target="_blank">similar UI patterns</a> via hypermedia.

## <a href="#intercooler-was-right" class="zola-anchor" aria-label="Anchor link for: intercooler-was-right">Intercooler Was Right</a>

At the <a href="https://intercoolerjs.org/docs#philosophy" rel="noopener" target="_blank">end of the intercooler docs</a>, we said this:

> Many javascript projects are updated at a dizzying pace. Intercooler is not.
>
> This is not because it is dead, but rather because it is (mostly) right: the basic idea is right, and the implementation at least right enough.
>
> This means there will not be constant activity and churn on the project, but rather a <a href="https://en.wikipedia.org/wiki/Stewardship_(theology)" rel="noopener" target="_blank">stewardship</a> relationship: the main goal now is to not screw it up. The documentation will be improved, tests will be added, small new declarative features will be added around the edges, but there will be no massive rewrite or constant updating. This is in contrast with the software industry in general and the front end world in particular, which has comical levels of churn.
>
> Intercooler is a sturdy, reliable tool for web development.

Leaving aside <a href="https://www.youtube.com/watch?v=zGyAWH5btwY" rel="noopener" target="_blank">the snark at the end of the third paragraph</a>, this thinking is very much applicable to htmx. In fact, perhaps even more so since htmx is a standalone piece of software, benefiting from the experiences (and mistakes) of intercooler.js.

We hope to see htmx, in its own small way, join the likes of giants like jQuery as a sturdy and reliable tool for building your 100 year web services.

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

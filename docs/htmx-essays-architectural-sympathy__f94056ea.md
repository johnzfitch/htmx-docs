# architectural-sympathy__f94056ea

- Source URL: https://htmx.org/essays/architectural-sympathy/
- Source file: `fetch/htmx_org_f94056ea.html`
- Hash: `f94056ea`
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

# Architectural Sympathy

Carson Gross

April 06, 2023

# <a href="#mechanical-sympathy-architectural-sympathy" class="zola-anchor" aria-label="Anchor link for: mechanical-sympathy-architectural-sympathy">Mechanical Sympathy &amp; Architectural Sympathy</a>

> You don’t have to be an engineer to be a racing driver, but you do have to have Mechanical Sympathy.

*-Jackie Stewart, racing driver*

The term “mechanical sympathy” was originally coined by Jackie Stewart to capture a characteristic of race car drivers, who needed a deep and intuitive understanding of how a race car worked in order to get the best possible performance out of the vehicle.

This term was applied to software development by Martin Thompson when discussing his <a href="https://martinfowler.com/articles/lmax.html" rel="noopener" target="_blank">LMAX</a> architecture, which utilized a low level and intuitive understanding of how his cloud system functioned in order to maximize the performance of it. Thompson maintained <a href="https://mechanical-sympathy.blogspot.com/" rel="noopener" target="_blank">a blog</a> on the topic for many years, and it is well worth going back and reading the posts there.

## <a href="#architectural-sympathy" class="zola-anchor" aria-label="Anchor link for: architectural-sympathy">Architectural Sympathy</a>

In this brief essay I want to propose another concept and design principle, that of *Architectural Sympathy*:

> Architectural Sympathy is the characteristic of one piece of software adopting and conforming to the architectural design of another piece of software

This is a design principle that I have kept in mind when designing <a href="https://htmx.org" rel="noopener" target="_blank">htmx</a> and <a href="https://hyperscript.org" rel="noopener" target="_blank">hyperscript</a> and I wanted to write it down for reference and so others can think about, criticize and improve it.

### <a href="#htmx-s-architectural-sympathy-for-the-web" class="zola-anchor" aria-label="Anchor link for: htmx-s-architectural-sympathy-for-the-web">htmx’s Architectural Sympathy for The Web</a>

htmx is architecturally sympathetic to The Web because it adopts the underlying [REST-ful](/essays/hateoas) architecture of The Web: exchanging *hypermedia* in a REST-ful manner with a hypermedia server. As much as is practical, htmx takes design cues from the existing Web infrastructure:

- It mimics the core hypermedia-exchange mechanic of links and forms
- It uses CSS selectors for targeting
- It uses standard URL paths for designating end points
- It uses the standard API language for specifying swap types
- Etc.

htmx attempts to *fold in* to the existing conceptual architecture of The Web, rather than replace it.

This is in contrast with the <a href="https://developer.mozilla.org/en-US/docs/Glossary/SPA" rel="noopener" target="_blank">SPA</a> approach to building web applications. Most SPA frameworks have little architectural sympathy with the original web model. Rather, they largely *replace* the original, REST-ful, hypermedia-oriented architecture of the web in favor of a more thick-client like architecture, exchanging information over an [RPC-like fixed-data format](/essays/how-did-rest-come-to-mean-the-opposite-of-rest/) network architecture.

### <a href="#advantages-of-the-architecturally-sympathetic-approach" class="zola-anchor" aria-label="Anchor link for: advantages-of-the-architecturally-sympathetic-approach">Advantages Of The Architecturally Sympathetic Approach</a>

If a new piece of software maintains architectural sympathy with an original piece of software, the following advantages are obtained:

- A developer who is familiar with the original piece of software does not need to learn a whole new conceptual approach when using the new piece of software.
- The design constraints of the original piece of software offer a framework within which to evaluate features for the new piece of software. This makes it easier to <a href="https://grugbrain.dev/#grug-on-saying-no" rel="noopener" target="_blank">say “no”</a> as you develop the new software. (“The enemy of art is the absence of limitations.” –<a href="https://quoteinvestigator.com/2014/05/24/art-limit/" rel="noopener" target="_blank">Orson Welles</a>)
- Experience gained from working with the original piece of software can directly inform the design and implementation of the new software
- There will likely be a subjective feeling of “fit” between the new and original software for users of the new software

### <a href="#disadvantages-of-the-architecturally-sympathetic-approach" class="zola-anchor" aria-label="Anchor link for: disadvantages-of-the-architecturally-sympathetic-approach">Disadvantages Of The Architecturally Sympathetic Approach</a>

Of course, as with any design principle, there are trade-offs when using Architectural Sympathy:

- The shortcomings of the original piece of software are likely to be found in some way in the new software
- The design constraints impressed on the new software by the older software may be so oppressive as to limit progress and functionality in the new software
- It may be difficult for developers to “see the point” of the new software, if it feels too close to the original software
- By maintaining architectural sympathy with the older, original software, the new software risks appearing old itself, a danger in the software business that has often favored new and exciting approaches to problems.
- You may not be able to layer as many new concepts as some users might like on top of the original software

## <a href="#craftsmanship-architectural-sympathy" class="zola-anchor" aria-label="Anchor link for: craftsmanship-architectural-sympathy">Craftsmanship &amp; Architectural Sympathy</a>

A non-software example of architectural sympathy that I like to point to are medieval cathedrals: these cathedrals were often built, rebuilt and improved over centuries by many different builders and architects (such as they were). And yet they were able, over those centuries, to maintain a high level of architectural sympathy with the earlier workers.

Rather than focusing on radically new approaches to building, workers focused on maintaining a coherent whole and, within that framework, on the craftsmanship of their individual contributions. Yes, there were flourishes and changes along the way, but these typically did not sacrifice the conceptual coherence of the whole for the sake of innovation.

Adopting an architecturally sympathetic mindset in software development often means sacrificing how you would like to do things in favor of how an original piece of software did things. While this constraint can chafe at times, it can also produce well crafted software that is harmonious and that dovetails well with existing software.

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

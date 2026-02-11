# a-real-world-react-to-htmx-port__11818234

- Source URL: https://htmx.org/essays/a-real-world-react-to-htmx-port/
- Source file: `fetch/htmx_org_11818234.html`
- Hash: `11818234`
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

# A Real World React -\> htmx Port

Carson Gross

September 29, 2022

It is all well and good talking about [REST & HATEOAS](https://htmx.org/essays/hateoas/) in theory or describing the [Hypermedia-Driven Application](https://htmx.org/essays/hypermedia-driven-applications/) architecture, but, at the end of the day, what matters in software is practical: Does it work? Does it improve things?

We can say for sure that htmx *works*, since we use it in our own software. But it is hard to say that it would be an *improvement* over other approaches, since we haven’t had an apples-to-apples comparison of how htmx might compare with, say, <a href="https://reactjs.org/" rel="noopener" target="_blank">react</a>.

Until now.

<a href="https://github.com/David-Guillot" rel="noopener" target="_blank">David Guillot</a> at <a href="https://www.contexte.com/" rel="noopener" target="_blank">Contexte</a> has given what we are calling <a href="https://en.wikipedia.org/wiki/The_Mother_of_All_Demos" rel="noopener" target="_blank">“The Mother of All htmx Demos”</a> at <a href="https://pretalx.evolutio.pt/djangocon-europe-2022/talk/MZWJEA/" rel="noopener" target="_blank">DjangoCon 2022</a>:

> **From React to htmx on a real-world SaaS product: we did it, and it’s awesome!**
>
> We took the plunge and replaced the 2-year-of-work React UI of our SaaS product with simple Django templates and htmx in a couple of months. We’d like to share our experience with you, with concrete indicators on various aspects, and convince your CTO!

## <a href="#video" class="zola-anchor" aria-label="Anchor link for: video">Video</a>

You can (should!) watch the entire presentation here:

<div class="iframe">

<div id="player">

</div>

<div class="player-unavailable">

# An error occurred.

<div class="submessage">

Unable to execute JavaScript.

</div>

</div>

</div>

## <a href="#executive-summary" class="zola-anchor" aria-label="Anchor link for: executive-summary">Executive Summary</a>

- The effort took about **2 months** (with a 21K LOC code base, mostly JavaScript)
- **No reduction** in the application’s user experience (UX)
- They reduced the **code base size** by **67%** (21,500 LOC to 7200 LOC)
- They *increased* **python code** by **140%** (500 LOC to 1200 LOC), a good thing if you prefer python to JS
- They reduced their total **JS dependencies** by **96%** (255 to 9)
- They reduced their **web build time** by **88%** (40 seconds to 5)
- **First load time-to-interactive** was reduced by **50-60%** (from 2 to 6 seconds to 1 to 2 seconds)
- **Much larger data sets were possible** when using htmx, because react simply couldn’t handle the data
- Web application **memory usage** was reduced by **46%** (75MB to 45MB)

## <a href="#analysis" class="zola-anchor" aria-label="Anchor link for: analysis">Analysis</a>

These are eye-popping numbers, and they reflect the fact that the Contexte application is extremely amenable to hypermedia: it is a content-focused application that shows lots of text and images. We would not expect every web application to see these sorts of numbers.

However, we *would* expect *many* applications to see dramatic improvements by adopting the hypermedia/htmx approach, at least for part of their system.

### <a href="#dev-team-makeup" class="zola-anchor" aria-label="Anchor link for: dev-team-makeup">Dev Team Makeup</a>

One easy-to-overlook aspect of the port is the effect it had on the team’s structure. When Contexte was using react, there was a hard split between back-end and front-end, with two developers being entirely back-end, one developer being entirely front-end, and one developer being “full stack”.

(“Full stack” here means they are comfortable doing work on both the front-end and back-end, and, thus are able to develop features entirely independently across the whole “stack”.)

After the port to htmx, *the entire team* became “full stack” developers. This means that each team member is more effective and able to contribute more value. It also makes development more fun, since developers can own an entire feature. Finally, it can lead to better optimized software, since the developer can make optimizations anywhere in the stack without needing to coordinate with other developers.

## <a href="#slides" class="zola-anchor" aria-label="Anchor link for: slides">Slides</a>

The slides for the presentation can be found here (be sure to check the excellent speakers notes!)

<a href="https://docs.google.com/presentation/d/1jW7vTiHFzA71m2EoCywjNXch-RPQJuAkTiLpleYFQjI/edit?usp=sharing" rel="noopener" target="_blank">https://docs.google.com/presentation/d/1jW7vTiHFzA71m2EoCywjNXch-RPQJuAkTiLpleYFQjI/edit?usp=sharing</a>

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

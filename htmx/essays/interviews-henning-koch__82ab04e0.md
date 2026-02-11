# interviews-henning-koch__82ab04e0

- Source URL: https://htmx.org/essays/interviews/henning-koch/
- Source file: `fetch/htmx_org_82ab04e0.html`
- Hash: `82ab04e0`
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

# An interview with Henning Koch, Creator of Unpoly

Carson Gross

June 13, 2022

I’m very excited to be able to interview Henning Koch, the creator of <a href="https://unpoly.com/" rel="noopener" target="_blank">Unpoly</a>, a hypermedia-oriented javascript library that was created in parallel with intercooler.js.

Thank you for agreeing to an interview!

**Q**: To begin with, why don’t you give the readers a bit of your background both professionally & technically:

> Sure! I’m currently head of development at <a href="https://makandra.de/en" rel="noopener" target="_blank">makandra</a>, a Ruby on Rails consultancy I co-founded back in 2009, after many years of freelancing as a web developer. So my context is working on many different web apps concurrently, and maintaining those for a long time. On a given week we probably touch 10+ projects, for industries ranging from education to automotive to cybersecurity. Unpoly is an extraction from patterns that we saw repeating over and over in client projects.

**Q**: When I created intercooler.js a big part of it was my unwillingness to deal with the popular SPA libraries of the time (Angular & ExtJS, for example). Did Unpoly have a similar history?

> Our team actually went all-in on AngularJS for a while, in an effort to replace the mountains of jQuery spaghetti that we had before. When Google nuked AngularJS with their Angular 2 rewrite, we held a retrospective for that time and came up with mixed results. While we had built some apps that were a great fit for the SPA model, the majority of projects suffered from larger code bases, more dependencies, logic being split between client and server, lots of boilerplate API to move data from where we already have it (the server) to where we need it (the browser).
>
> That was when we gave progressive enhancement another shot, but this time provided some higher-level structure so apps would be relieved of making manual AJAX requests and messing around with individual DOM elements. Basically come up with an HTML6 fantasy spec asking: What if HTML6 was all about server-rendered apps? What features would be in that spec? That thought experiment is what led to Unpoly.

**Q**: Unpoly is a very “batteries included” library, with excellent support for progressive enhancement. I know you are a Rails developer too. Did that influence your approach to Unpoly?

> Definitely! Like Rails, Unpoly ships with strong defaults for everything, and prefers unobtrusive convention over explicit configuration. E.g. if you want Unpoly to handle all your links and forms, you can set that up globally and not change your HTML at all.
>
> Some recent Rails mottos are “Compress the complexity of modern web apps” and “The one person framework”. With my other responsibility at makandra being training young developers, that resonates with me a lot. I really care about maintaining a stack where a single person can be a full-stack developer and deliver good results consistently.
>
> Also, as a Rubyist, I have an excessive obsession with the ergonomics and aesthetics of code *as it is invoked*. I stress a lot over how a feature looks when it is used in client code. When a small idea takes a disproportionate amount of code, this is something I lose sleep over.

**Q**: Did you think much about hypermedia, REST, etc. when you were building Unpoly? Do you find that stuff useful? Interesting?

> I share some of your love for interactive documents that stream their UI together with their content. For me this began in the 1990s with character-based BBS UIs und WinHelp files, until the web eventually supplanted all of that.
>
> Today I’m not super philosophical about it, but I do believe that a hypermedia approach is a sweet spot where you get good UI fidelity with very little and mostly boring code. For the median app, hypermedia probably gives a better result than the SPA model. I file like there’s this enormous disconnect between the theoretical ceiling of an SPA model and what most SPAs deliver. SPAs allow for optimistic UI (which is great!), but that’s just more code than waiting for a JSON endpoint. So once you do any meaningful interaction on a spotty connection, many SPAs degrade to spinners and blank pages.

**Q**: What are the most important technical lessons you draw from unpoly?

> I learnt that browsers handle a *lot* of edge cases right, before you break it by adding JavaScript. Stuff like managing focus, concurrent input, flaky connections. It is not trivial to deliver that same level of correctness, for example, when you emulate a page transition in JavaScript. It takes a lot of code to address that. I always remember this when I see a tiny microlib that claims to re-implement React in 2000 bytes or something. You can’t just code-golf away half your bundle size without trading away some correctness in the process.

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

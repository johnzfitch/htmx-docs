# 10-tips-for-ssr-hda-apps__3447e3b5

- Source URL: https://htmx.org/essays/10-tips-for-ssr-hda-apps/
- Source file: `fetch/htmx_org_3447e3b5.html`
- Hash: `3447e3b5`
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

# 10 Tips For Building SSR/HDA applications

Carson Gross

June 13, 2022

Building web applications using traditional Server-Side Rendering (SSR) or, saying the same thing another way, building [Hypermedia-Driven Applications](https://htmx.org/essays/hypermedia-driven-applications/) (HDAs) requires a mindset shift when compared with building web applications with Single Page Application frameworks like React.

If you come at this style of development with an SPA-engineering hat on, you are likely to be frustrated and miss out on many advantages of this particular architectural choice.

Here are 10 tip to help you make the mental shift smoothly, taking advantage of the strengths of this approach and minimizing the weaknesses of it:

### <a href="#tip-1-maximize-your-server-side-strengths" class="zola-anchor" aria-label="Anchor link for: tip-1-maximize-your-server-side-strengths">Tip 1: Maximize Your Server-Side Strengths</a>

A big advantage of the hypermedia-driven approach is that it makes the server-side environment far more important when building your web application. Rather than simply producing JSON, your back end is an integral component in the user experience of your web application.

Because of this, it makes sense to look deeply into the functionality available there. Many older web frameworks have incredibly deep functionality available around producing HTML. Features like <a href="https://guides.rubyonrails.org/caching_with_rails.html" rel="noopener" target="_blank">server-side caching</a> can make the difference between an incredibly snappy web application and a sluggish user experience.

Take time to learn all the tools available to you.

A good rule of thumb is to shoot to have responses in your application take less than 100ms to complete, and mature server side frameworks have tools to help make this happen.

### <a href="#tip-2-factor-your-application-on-the-server" class="zola-anchor" aria-label="Anchor link for: tip-2-factor-your-application-on-the-server">Tip 2: Factor Your Application On The Server</a>

Server-side environments often have extremely mature mechanisms for factoring (or organizing) your code properly. The <a href="https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller" rel="noopener" target="_blank">Model/View/Controller</a> pattern is well-developed in most environments, and tools like modules, packages, etc. provide an excellent way to organize your code.

Whereas SPAs user interfaces are typically organized via *components*, hypermedia-driven applications are typically organized via *template inclusion*, where the server-side templates are broken up according to the HTML-rendering needs of the application, and then included in one another as needed. This tends to lead to fewer, chunkier files than you would find in a component-based application.

Another technology to look for are [Template Fragments](https://htmx.org/essays/template-fragments/), which allow you to render only part of a template file. This can reduce even further the number of template files required for your server-side application.

### <a href="#tip-3-specialize-your-api-end-points" class="zola-anchor" aria-label="Anchor link for: tip-3-specialize-your-api-end-points">Tip 3: Specialize Your API End Points</a>

Unlike a [JSON API](https://htmx.org/essays/hypermedia-apis-vs-data-apis/), the hypermedia API you produce for your hypermedia-driven application *should* feature end-points specialized for your particular application’s UI needs.

Because hypermedia APIs are [not designed to be consumed by general-purpose clients](https://htmx.org/essays/hypermedia-clients/) you can set aside the pressure to keep them generalized and produce the content specifically needed for your application.\
Your end-points should be optimized to support your particular applications UI/UX needs, not for a general-purpose data-access model for your domain model.

### <a href="#tip-4-aggressively-refactor-your-api-end-points" class="zola-anchor" aria-label="Anchor link for: tip-4-aggressively-refactor-your-api-end-points">Tip 4: Aggressively Refactor Your API End Points</a>

A related tip is that, when you have a hypermedia-based API, you can aggressively refactor your API in a way that is heavily discouraged when writing JSON API-based SPAs. Because hypermedia-based applications use [Hypermedia As The Engine Of Application State](https://htmx.org/essays/hateoas/), you are able and, in fact, encouraged, to change the shape of them as your application developers and as use cases change.

A great strength of the hypermedia approach is that you can completely rework your API to adapt to new needs over time without needing to version the API or even document it.

### <a href="#tip-5-take-advantage-of-direct-access-to-the-data-store" class="zola-anchor" aria-label="Anchor link for: tip-5-take-advantage-of-direct-access-to-the-data-store">Tip 5: Take Advantage of Direct Access To The Data Store</a>

When an application is built using the SPA approach, the data store typically lives behind a JSON API. This level of indirection often prevents front end developers from being able to take full advantage of the tools available in the data store. GraphQL can help address this issue, but comes with <a href="https://intercoolerjs.org/2016/02/17/api-churn-vs-security.html" rel="noopener" target="_blank">security-related issues</a> that do not appear to be well understood by many developers.

When you produce your HTML on the server side, on the other hand, the developer creating that HTML can have full access to the data store and take advantage of, for example, <a href="https://www.sqltutorial.org/sql-left-join/" rel="noopener" target="_blank">joins</a> and <a href="https://www.sqltutorial.org/sql-aggregate-functions/" rel="noopener" target="_blank">aggregation functions</a> in SQL stores.

This puts far more expressive power directly in the hands of the developer producing the HTML. Because your hypermedia API can be structured around your UI needs, you can tune each endpoint to issue as few data store requests as possible.

A good rule of thumb is that every request should shoot to have three or fewer data-store accesses.

### <a href="#tip-6-avoid-modals" class="zola-anchor" aria-label="Anchor link for: tip-6-avoid-modals">Tip 6: Avoid Modals</a>

<a href="https://en.wikipedia.org/wiki/Modal_window" rel="noopener" target="_blank">Modal windows</a> have become popular, almost standard, in many web applications today.

Unfortunately, <a href="https://youdontneedamodalwindow.dev/" rel="noopener" target="_blank">modal windows do not play well with much of the infrastructure of the web</a> and introduce client-side state that can be difficult (though not impossible) to integrate cleanly with the hypermedia-based approach.

Consider using alternatives such as <a href="https://htmx.org/examples/click-to-edit/" rel="noopener" target="_blank">inline editing</a>, rather than modals.

### <a href="#tip-7-accept-good-enough-ux" class="zola-anchor" aria-label="Anchor link for: tip-7-accept-good-enough-ux">Tip 7: Accept “Good Enough” UX</a>

A problem many SPA developers face when coming to the HDA approach is that they look at their current SPA application and imagine implementing it *exactly* using hypermedia. While htmx and other hypermedia-oriented libraries significantly close the interactivity gap between hypermedia-based applications and SPAs, that gap still exists.

As Roy Fielding <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_5" rel="noopener" target="_blank">said</a> with respect to the web’s REST-ful network architecture:

> The trade-off, though, is that a uniform interface degrades efficiency, since information is transferred in a standardized form rather than one which is specific to an application’s needs.

Accepting a slightly less efficient and interactive solution to a particular UX can save you a tremendous amount of [complexity](https://htmx.org/essays/complexity-budget/) when building a web application.

Do not let the perfect be the enemy of the good.

### <a href="#tip-8-when-necessary-create-islands-of-interactivity" class="zola-anchor" aria-label="Anchor link for: tip-8-when-necessary-create-islands-of-interactivity">Tip 8: When Necessary, Create “Islands of Interactivity”</a>

At some point in your web application, there may come a point where the hypermedia approach, on its own, just doesn’t cut it.

A good example of this is re-ordering a list of things. This can be done in “pure” hypermedia by clicking up and down arrows or having order \# drop-downs next to items. (I am ashamed to admit I have built both of these!)

But this experience stinks compared to what people are used to: drag-and-drop.

In cases like this, it is perfectly fine to use a front-end heavy approach as an “Island of Interactivity”.

Consider the [SortableJS](https://htmx.org/examples/sortable/) example. Here you have a sophisticated area of interactivity that allows for drag-and-drop, and that integrates with htmx and the broader hypermedia-driven application via events.

This is an excellent way to encapsulate richer UX within an HDA.

### <a href="#tip-9-don-t-be-afraid-to-script" class="zola-anchor" aria-label="Anchor link for: tip-9-don-t-be-afraid-to-script">Tip 9: Don’t Be Afraid To Script!</a>

Scripting is <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_7" rel="noopener" target="_blank">explicitly a part of the web architecture</a> and developers adopting the hypermedia approach shouldn’t be afraid to use it. Of course there is scripting and then there is scripting.

As much as possible, you should try to use the [hypermedia-friendly scripting](https://htmx.org/essays/hypermedia-friendly-scripting/) approach, retaining hypermedia-exchanges as the primary mechanism for communicating system state changes with the server.

Inline-style scripting, as enabled by <a href="https://alpinejs.dev/" rel="noopener" target="_blank">alpine.js</a> & <a href="https://hyperscript.org" rel="noopener" target="_blank">hyperscript</a> for example, is worth exploring as well, as it refocuses your scripting on the hypermedia (HTML) itself and imposes an aesthetic constraint on just how much code you can write.

### <a href="#tip-10-be-pragmatic" class="zola-anchor" aria-label="Anchor link for: tip-10-be-pragmatic">Tip 10: Be Pragmatic</a>

Finally, do not be dogmatic about using hypermedia. At the end of the day, it is just another technology with its own [strengths & weaknesses](https://htmx.org/essays/when-to-use-hypermedia/). If a particular part of an app, or if an entire app, demands something more interactive than what hypermedia can deliver, then go with a technology that can.

Just be familiar with [what hypermedia can do](https://htmx.org/examples/), so you can make that decision as an informed developer.

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

Hopefully these tips help you adopt hypermedia and server-side rendering as a tool more effectively and smoothly. It isn’t a perfect client-server architecture, and it involves explicit tradeoffs, but it can be extremely effective for many web applications (far more than most web developers today suspect) and provides a much simpler overall development experience in those cases.

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

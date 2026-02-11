# the-fetchening__34a9a060

- Source URL: https://htmx.org/essays/the-fetchening/
- Source file: `fetch/htmx_org_34a9a060.html`
- Hash: `34a9a060`
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

# The fetch()ening

Carson Gross

November 01, 2025

![Stop trying to make fetch() happen](/img/fetch.png)

OK, I said there would never be a version three of htmx.

But, *technically*, I never said anything about a version *four*…

## <a href="#htmx-4-the-fetch-ening" class="zola-anchor" aria-label="Anchor link for: htmx-4-the-fetch-ening">htmx 4: The fetch()ening</a>

In [The Future of htmx](https://htmx.org/essays/hypermedia-driven-applications/) I said the following:

> We are going to work to ensure that htmx is extremely stable in both API & implementation. This means accepting and documenting the <a href="https://htmx.org/quirks/" rel="noopener" target="_blank">quirks</a> of the current implementation.

Earlier this year, on a whim, I created <a href="https://github.com/bigskysoftware/fixi" rel="noopener" target="_blank">fixi.js</a>, a hyperminimalist implementation of the ideas in htmx. That work gave me a chance to get a lot more familiar with the `fetch()` and, especially, the <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function" rel="noopener" target="_blank">async</a> infrastructure available in JavaScript.

In doing that work I began to wonder if that, while the htmx <a href="https://htmx.org/reference/#attributes" rel="noopener" target="_blank">API</a> is (at least reasonably) correct, maybe there was room for a more dramatic change of the implementation that took advantage of these features in order to simplify the library.

Further, changing from ye olde <a href="https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest" rel="noopener" target="_blank"><code>XMLHttpRequest</code></a> (a legacy of htmx 1.0 IE support) to <a href="https://developer.mozilla.org/en-US/docs/Web/API/Window/fetch" rel="noopener" target="_blank"><code>fetch()</code></a> would be a pretty violent change, guaranteed to break at least *some* stuff.

So I began thinking: if we are going to consider moving to fetch, then maybe we should *also* use this update as a chance address at least *some* of the <a href="https://htmx.org/quirks/" rel="noopener" target="_blank">quirks &amp; cruft</a> that htmx has acquired over its lifetime.

So, eventually & reluctantly, I have changed my mind: there *will* be another major version of htmx.

However, in order to keep my word that there will not be a htmx 3.0, the next release will instead be htmx 4.0.

## <a href="#project-goals" class="zola-anchor" aria-label="Anchor link for: project-goals">Project Goals</a>

With htmx 4.0 we are rebuilding the internals of htmx, based on the lessons learned from fixi.js and <a href="https://www.npmjs.com/package/htmx.org/v/0.0.1" rel="noopener" target="_blank">five+ years</a> of supporting htmx.

There are three major simplifying changes:

### <a href="#the-fetch-ening" class="zola-anchor" aria-label="Anchor link for: the-fetch-ening">The fetch()ening</a>

The biggest internal change is that `fetch()` will replace `XMLHttpRequest` as the core ajax infrastructure. This won’t actually have a huge effect on most usages of htmx *except* that the events model will necessarily change due to the differences between `fetch()` and `XMLHttpRequest`.

### <a href="#explicit-inheritance-by-default" class="zola-anchor" aria-label="Anchor link for: explicit-inheritance-by-default">Explicit Inheritance By Default</a>

I feel that the biggest mistake in htmx 1.0 & 2.0 was making attribute inheritance implicit. I was inspired by CSS in doing this, and the results have been roughly the same as CSS: powerful & maddening.

In htmx 4.0, attribute inheritance will be explicit by default rather than implicit. Explicit inheritance will be done via the `:inherited` modifier:

``` html
  <div hx-target:inherited="#output">
    <button hx-post="/up">Like</button>
    <button hx-post="/down">Dislike</button>
  </div>
  <output id="output">Pick a button...</output>
```

Here the `hx-target` attribute is explicitly declared as `inherited` on the enclosing `div` and, if it wasn’t, the `button` elements would not inherit the target from it.

You will be able to revert to htmx 2.0 implicit inheritance behavior via a configuration variable.

### <a href="#no-locally-cached-history" class="zola-anchor" aria-label="Anchor link for: no-locally-cached-history">No Locally Cached History</a>

Another source of pain for both us and for htmx users is history support. htmx 2.0 stores history in local cache to make navigation faster. Unfortunately, snapshotting the DOM is often brittle because of third-party modifications, hidden state, etc. There is a terrible simplicity to the web 1.0 model of blowing everything away and starting over. There are also security concerns storing history information in session storage.

In htmx 2.0, we often end up recommending that people facing history-related issues simply disable the cache entirely, and that usually fixes the problems.

In htmx 4.0, history support will no longer snapshot the DOM and keep it locally. It will, rather, issue a network request for the restored content. This is the behavior of 2.0 on a history cache-miss, and it works reliably with little effort on behalf of htmx users.

We will offer an extension that enables history caching like in htmx 2.0, but it will be opt-in, rather than the default.

This tremendously simplifies the htmx codebase and should make the out-of-the-box behavior much more plug-and-play.

## <a href="#what-stays-the-same" class="zola-anchor" aria-label="Anchor link for: what-stays-the-same">What Stays The Same?</a>

Most things.

The <a href="https://dl.acm.org/doi/10.1145/3648188.3675127" rel="noopener" target="_blank">core</a> functionality of htmx will remain the same, `hx-get`, `hx-post`, `hx-target`, `hx-boost`, `hx-swap`, `hx-trigger`, etc.

With a few configuration tweaks, most htmx 2.x based applications should work with htmx 4.x.

These changes will make the long term maintenance & sustainability of the project much stronger. It will also take pressure off the 2.0 releases, which can now focus on stability rather than contemplating new features.

## <a href="#upgrading" class="zola-anchor" aria-label="Anchor link for: upgrading">Upgrading</a>

htmx 2.0 users *will* face an upgrade project when moving to 4.0 in a way that they did not have to in moving from 1.0 to 2.0.

I am sorry about that, and want to offer two things to address it:

- htmx 2.0 (like htmx 1.0 & intercooler.js 1.0) will be supported *in perpetuity*, so there is absolutely *no* pressure to upgrade your application: if htmx 2.0 is satisfying your hypermedia needs, you can stick with it.
- We will roll htmx 4.0 out slowly, over a multi-year period. As with the htmx 1.0 -\> 2.0 upgrade, there will be a long period where htmx 2.x is `latest` and htmx 4.x is `next`

## <a href="#new-features" class="zola-anchor" aria-label="Anchor link for: new-features">New Features</a>

Beyond simplifying the implementation of htmx significantly, switching to fetch also gives us the opportunity to add some nice new features to htmx

### <a href="#streaming-responses-sse-in-core" class="zola-anchor" aria-label="Anchor link for: streaming-responses-sse-in-core">Streaming Responses &amp; SSE in Core</a>

By switching to `fetch()`, we can take advantage of its support for <a href="https://developer.mozilla.org/en-US/docs/Web/API/Streams_API/Using_readable_streams" rel="noopener" target="_blank">readable streams</a>, which allow for a stream of content to be swapped into the DOM, rather than a single response.

htmx 1.0 had Server Sent Event support integrated into the library. In htmx 2.0 we pulled this functionality out as an extension. It turns out that SSE is just a specialized version of a streaming response, so in adding streaming support, it’s an almost-free free two-fer to add that back into core as well.

This will make incremental response swapping much cleaner and well-supported in htmx.

### <a href="#morphing-swap-in-core" class="zola-anchor" aria-label="Anchor link for: morphing-swap-in-core">Morphing Swap in Core</a>

<a href="https://github.com/bigskysoftware/idiomorph/commit/7760e89d9f198b43aa7d39cc4f940f606771f47b" rel="noopener" target="_blank">Three years ago</a> I had an idea for a DOM morphing algorithm that improved on the initial algorithm pioneered by <a href="https://github.com/patrick-steele-idem/morphdom" rel="noopener" target="_blank">morphdom</a>.

The idea was to use “id sets” to make smarter decisions regarding which nodes to preserve and which nodes to delete when merging changes into the DOM, and I called this idea “idiomorph”. Idiomorph has gone on to be adopted by many other web project such as <a href="https://hotwired.dev/" rel="noopener" target="_blank">Hotwire</a>.

We strongly considered including it in htmx 2.0, but I decided not too because it worked well as an extension and htmx 2.0 had already grown larger than I wanted.

In 4.0, with the complexity savings we achieved by moving to `fetch()`, we can now comfortably fit a `morphInner` and `morphOuter` swap into core, thanks to the excellent work of Michael West.

### <a href="#explicit-htmx-partial-tag-support" class="zola-anchor" aria-label="Anchor link for: explicit-htmx-partial-tag-support">Explicit &lt;htmx-partial&gt; Tag Support</a>

htmx has, since very early on, supported a concept of “Out-of-band” swaps: content that is removed from the main HTML response and swapped into the DOM elsewhere. I have always been a bit ambivalent about them, because they move away from <a href="https://htmx.org/essays/locality-of-behaviour/" rel="noopener" target="_blank">Locality of Behavior</a>, but there is no doubt that they are useful and often crucial for achieving certain UI patterns.

Out-of-band swaps started off very simply: if you marked an element as `hx-swap-oob='true'`, htmx would swap the element as the outer HTML of any existing element already in the DOM with that id. Easy-peasy.

However, over time, people started asking for different functionality around Out-of-band swaps: prepending, appending, etc. and the feature began acquiring some fairly baroque syntax to handle all these needs.

We have come to the conclusion that the problem is that there are really *two* use cases, both currently trying to be filled by Out-of-band swaps:

- A simple, id-based replacement
- A more elaborate swap of partial content

Therefore, we are introducing the notion of `<htmx-partial>`s in htmx 4.0

A partial element is, under the covers, a template element and, thus, can contain any sort of content you like. It specifies on itself all the standard htmx options regarding swapping, `hx-target` and `hx-swap` in particular, allowing you full access to all the standard swapping behavior of htmx without using a specialized syntax. This tremendously simplifies the mental model for these sorts of needs, and dovetails well with the streaming support we intend to offer.

Out-of-band swaps will be retained in htmx 4.0, but will go back to their initial, simple focus of simply replacing an existing element by id.

### <a href="#improved-view-transitions-support" class="zola-anchor" aria-label="Anchor link for: improved-view-transitions-support">Improved View Transitions Support</a>

htmx 2.0 has had <a href="https://developer.mozilla.org/en-US/docs/Web/API/View_Transition_API" rel="noopener" target="_blank">View Transition</a> support since <a href="https://github.com/bigskysoftware/htmx/blob/master/CHANGELOG.md#190---2023-04-11" rel="noopener" target="_blank">April of 2023</a>. In the interceding two years, support for the feature has grown across browsers (c’mon, safari, you can do it) and we’ve gained experience with the feature.

One thing that has become apparent to us while using them is that, to use them in a stable manner, it is important to establish a *queue* of transitions, so each can complete before the other begins. If you don’t do this, you can get visually ugly transition cancellations.

So, in htmx 4.0 we have added this queue which will ensure that all view transitions complete smoothly.

CSS transitions will continue to work as before as well, although the swapping model is again made much simpler by the async runtime.

We may enable View Transitions by default, the jury is still out on that.

### <a href="#stabilized-event-ordering" class="zola-anchor" aria-label="Anchor link for: stabilized-event-ordering">Stabilized Event Ordering</a>

A wonderful thing about `fetch()` and the async support in general is that it is *much* easier to guarantee a stable order of events. By linearizing asynchronous code and allowing us to use standard language features like try/catch, the event model of htmx should be much more predictable and comprehensible.

We are going to adopt a new standard for event naming to make things even clearer:

`htmx:<phase>:<system>[:<optional-sub-action>]`

So, for example, `htmx:before:request` will be triggered before a request is made.

### <a href="#improved-extension-support" class="zola-anchor" aria-label="Anchor link for: improved-extension-support">Improved Extension Support</a>

Another opportunity we have is to take advantage of the `async` behavior of `fetch()` for much better performance in our preload extension (where we issue a speculative (`GET` only!) request in anticipation of an actual trigger). We have also added an optimistic update extension to the core extensions, again made easy by the new async features.

In general, we have opened up the internals of the htmx request/response/swap cycle much more fully to extension developers, up to and including allowing them to replace the `fetch()` implementation used by htmx for a particular request. There should not be a need for any hacks to get the behavior you want out of htmx now: the events and the open “context” object should provide the ability to do almost anything.

### <a href="#improved-hx-on-support" class="zola-anchor" aria-label="Anchor link for: improved-hx-on-support">Improved <code>hx-on</code> Support</a>

In htmx 2.0, I somewhat reluctantly added the <a href="https://htmx.org/attributes/hx-on/" rel="noopener" target="_blank"><code>hx-on</code></a> attributes to support light scripting inline on elements. I added this because HTML does not allow you to listen for arbitrary events via `on` attributes: only standard DOM events like `onclick` can be responded to.

We hemmed and hawed about the syntax and so, unfortunately, there are a few different ways to do it.

In htmx 4.0 we will adopt a single standard for the `hx-on` attributes: `hx-on:<event name>`. Additionally, we are working to improve the htmx JavaScript API (especially around async operation support) and will make those features available in `hx-on`:

``` html
<button hx-post="/like"
        hx-on:htmx:after:swap="await timeout('3s'); ctx.newContent[0].remove()">
    Get A Response Then Remove It 3 Seconds Later
</button>
```

htmx will never support a fully featured scripting mechanism in core, we recommend something like <a href="https://alpinejs.dev/" rel="noopener" target="_blank">Alpine.js</a> for that, but our hope is that we can provide a relatively minimalist API that allows for easy, light async scripting of the DOM.

I should note that htmx 4.0 will continue to work with `eval()` disabled, but you will need to forego a few features like `hx-on` if you choose to do so.

### <a href="#a-better-but-familiar-htmx" class="zola-anchor" aria-label="Anchor link for: a-better-but-familiar-htmx">A Better But Familiar htmx</a>

All in all, our hope is that htmx 4.0 will feel an awful lot like 2.0, but with better features and, we hope, with fewer bugs.

## <a href="#timeline" class="zola-anchor" aria-label="Anchor link for: timeline">Timeline</a>

As always, software takes as long as it takes.

However, our current planned timeline is:

- An alpha release is available *today*: `htmx@4.0.0-alpha1`
- A 4.0.0 release should be available in early-to-mid 2026
- 4.0 will be marked `latest` in early-2027ish

You can track our progress (and see quite a bit of dust flying around) in the `four` branch on <a href="https://github.com/bigskysoftware/htmx/tree/four" rel="noopener" target="_blank">github</a> and at:

<a href="https://four.htmx.org" rel="noopener" target="_blank">https://four.htmx.org</a>

Thank you for your patience and pardon our dust!

> “Well, when events change, I change my mind. What do you do?” –Paul Samuelson or John Maynard Keynes

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

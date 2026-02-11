# hypermedia-on-whatever-youd-like__e6374c5d

- Source URL: https://htmx.org/essays/hypermedia-on-whatever-youd-like/
- Source file: `fetch/htmx_org_e6374c5d.html`
- Hash: `e6374c5d`
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

# Hypermedia On Whatever you'd Like

Carson Gross

May 23, 2023

> The one big remaining (advantage of MPAs) is (server side programming) language choice. If you’re already part of the anti-JavaScript resistance, then nothing I say in the rest of this talk is going to matter that much.
>
> But, I’m going to get into this later: that ship might have sailed…
>
> Rich Harris - <a href="https://youtubetranscript.com/?v=860d8usGC0o&amp;t=440" rel="noopener" target="_blank">Have SPA’s Ruined The Web?</a>

A concept we like to talk about is “The HOWL Stack”. HOWL stands for *Hypermedia On Whatever you’d Like*.

This is a joke-but-not-really <a href="https://en.wikipedia.org/wiki/Solution_stack" rel="noopener" target="_blank">software stack</a>, and a reference to more well known stacks like <a href="https://en.wikipedia.org/wiki/LAMP_%28software_bundle%29" rel="noopener" target="_blank">The LAMP Stack</a> or <a href="https://en.wikipedia.org/wiki/MEAN_(solution_stack)" rel="noopener" target="_blank">The MEAN Stack</a>.

The TLDR of The HOWL Stack is this: when you use a [hypermedia-driven approach](/essays/hypermedia-driven-applications) for your web application, you free yourself up to choose *whatever* server-side technology best fits your problem and your own technical tastes.

## <a href="#feeling-the-javascript-pressure" class="zola-anchor" aria-label="Anchor link for: feeling-the-javascript-pressure">Feeling The JavaScript Pressure</a>

If you decide to use an SPA framework for your web application you will, naturally, have a large front-end codebase that is written in JavaScript.

Given that, the following question inevitably will come up:

> “Well, why aren’t we doing the back-end in JavaScript too?”

This is a reasonable question to ask and there are a lot of advantages to adopting the same programming language on both sides of the wire:

- You can share application logic between the two code-bases. A good example here is validation logic.
- You can share data structures between the two code-bases.
- You can build up expertise in a single language, JavaScript, making it easier for developers to work in various parts of your application.
- You can reuse the build system & dependency management knowledge you’ve acquired for the front end

This *pressure* to adopt JavaScript will only grow as your investment in the JavaScript front end ecosystem grows.

Furthermore, JavaScript has improved dramatically in the last five years and there are now multiple excellent server-side runtimes for executing it. Many of the older arguments about the messiness of the language can be waved off as preventable via linting, developer discipline, and so forth.

JavaScript is the dominant language among the web development thought leaders and there are massive numbers of tutorials, code camps, etc. that strongly emphasize the language. Nothing succeeds like success, and JavaScript (as well as React) have succeeded.

Let’s call the result of this *The JavaScript Pressure* and acknowledge that nearly every developer working with the web feels it at least to some extent.

## <a href="#hypermedia-our-only-hope" class="zola-anchor" aria-label="Anchor link for: hypermedia-our-only-hope">Hypermedia: Our Only Hope</a>

What hope do non-JavaScript developers have in web development?

Well, there is one older technology sitting there in the browser alongside JavaScript: *hypermedia*.

Browsers offer excellent HTML support (and the related Document Object Model, or DOM). In fact, even if you are using an SPA framework, you will be working with that hypermedia infrastructure in some form (via JSX templates, for example) if only to create UIs that a browser can understand.

So you are going to be using HTML or the related DOM APIs in some manner in your web application.

Well, what if we made HTML a more powerful hypermedia?

That’s the idea of [htmx](/), which makes it possible to implement [common modern web application patterns](/examples) using the hypermedia approach. This closes the UX gap between traditional MPAs and SPAs, making taking the hypermedia route feasible for a much larger set of web applications.

Once you adopt this hypermedia approach (and remember, you are going to be using hypermedia infrastructure *anyway*, so why not leverage it as much as possible?) a surprising side effect occurs:

Suddenly, the advantage of server-side language choice that Harris attributed to MPAs is *back on the table*.

If your application’s front end is mainly written in terms of HTML, maybe with a bit of client-side scripting, and with no large JavaScript code-base, you’ve suddenly dramatically diminished (or entirely eliminated) The JavaScript Pressure on the back end.

You can now make your server-side language (and framework) choice based on other considerations: technical, aesthetic or otherwise:

- Perhaps you are working in AI and want to use a Lisp variant for your project
- Perhaps you are working in big data and want to use Python
- Perhaps you know Django really well and love the batteries-included approach it takes
- Perhaps you prefer Flask and the stripped-down approach it takes
- Perhaps you like the raw, close-to-the-HTML feel of PHP
- Perhaps you have an existing Java codebase that needs some sprucing up
- Perhaps you are learning Cobol, <a href="https://twitter.com/htmx_org/status/1656381761188954113" rel="noopener" target="_blank">and want to use htmx to make a nice front end for it</a>.
- Perhaps you just really like Rust, Ocaml, Kotlin, Haskell, .NET, Clojure, Ada, ColdFusion, Ruby… whatever!

These are all perfectly reasonable technical, philosophical and aesthetic perspectives.

And, by adopting hypermedia as your primary front-end technology, you pursue any of these goals without a bicameral code-base. Hypermedia doesn’t care what you use to produce it: you can use hypermedia on whatever you’d like.

## <a href="#an-open-web-for-everyone" class="zola-anchor" aria-label="Anchor link for: an-open-web-for-everyone">An Open Web for Everyone</a>

And when we say “whatever”, we really mean it.

Here is a screenshot of the [htmx discord](/discord)’s HOWL subsection recently. Note that these are just the channels that happen to have active traffic, there are many more.

<div style="text-align: center; padding: 16px">

![Django, alpine, bash, clojure, cobol, deno, dotnet, go, java, node, ocaml, php, ruby, rust -- all active.](/img/howl-channels.png)

</div>

You can see we have ongoing conversations in a bunch of different programming languages and frameworks: Java, Go, .NET, Rust, Clojure, PHP, Ruby, Python, Ocaml. We even have some folks talking about using htmx with Bash and Cobol!

This is exactly the future that we want to see: a rich and vibrant Web in which *every* back-end language and framework can play as an equal & interesting alternative. Each language and framework has their own unique strengths & cultures and each can contribute to the magical <a href="https://hypermedia.systems" rel="noopener" target="_blank">hypermedia system</a> that is The Web.

## <a href="#but-is-it-an-anti-javascript-resistance" class="zola-anchor" aria-label="Anchor link for: but-is-it-an-anti-javascript-resistance">But, Is it An <em>Anti</em>-JavaScript Resistance?</a>

Before we finish this essay, we do want to address the idea that the resistance to JavaScript *everywhere* is necessarily *Anti*-JavaScript.

Now, admittedly, we have laughed at our fair share of [jokes about JavaScript](/img/js-the-good-parts.jpeg), and we have gone so far as to create an alternative scripting language for the web, <a href="https://hyperscript.org" rel="noopener" target="_blank">hyperscript</a>.

So it might seem like we should be card-carrying anti-javascriptites.

But, to the contrary, we are deeply appreciative of JavaScript.

After all, both htmx and hyperscript are *built in JavaScript*. We couldn’t have created these libraries without JavaScript, which, whatever else one might say, has the great virtue of <a href="https://en.wikipedia.org/wiki/Being_There" rel="noopener" target="_blank"><em>being there</em></a>.

And we even go so far as to *recommend using* JavaScript for front-end scripting needs in a hypermedia-driven application, so long as you script in a [hypermedia-friendly](/essays/hypermedia-friendly-scripting/) way.

Further, we wouldn’t steer someone away from using JavaScript (or TypeScript) on the *server side* for a hypermedia-driven application, if that language is the best option for your team. As we said earlier, JavaScript now has multiple excellent server-side runtimes and many excellent server-side libraries available.

It might be the best option for you and your team, and there is no reason not to use it in that case.

Hypermedia On Whatever you’d Like means just that: whatever you’d like.

But JavaScript is not, and it should not be, the *only* server-side option for your team.

## <a href="#turning-the-ship-around" class="zola-anchor" aria-label="Anchor link for: turning-the-ship-around">Turning The Ship Around</a>

With the resurgence of interest in (and improvements of) hypermedia, an open and diverse future for The Web is now a real possibility, if not an emerging reality.

The Web was designed to be an open, polyglot & participative hypermedia system.

And the ship *hasn’t sailed* on that dream, at least not yet!

We can keep that dream alive by re-learning and re-embracing the foundational technology of the web: hypermedia.

> I hate that the htmx community has devolved into builders helping each other without regard for likes, engaging those who don’t follow the hype, expanding sound bytes into nuance. It may not score cheap social media points, but it’s healthy. The web used to be worse than this.
>
> <a href="https://twitter.com/teej_dv/status/1655668643840098304" rel="noopener" target="_blank">@teej_dv</a>

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

# a-real-world-nextjs-to-htmx-port__49b1fe6e

- Source URL: https://htmx.org/essays/a-real-world-nextjs-to-htmx-port/
- Source file: `fetch/htmx_org_49b1fe6e.html`
- Hash: `49b1fe6e`
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

# Next.js to htmx — A Real World Example

Pouria Ezzati

November 07, 2024

Over 6 years ago, I created <a href="https://github.com/thedevs-network/kutt" rel="noopener" target="_blank">an open source URL shortener</a> with Next.js and after years of working on it, I found Next.js to be much more of a burden than a help. Over the years, Next.js has changed, and so did my code so it can be compatible with those changes.

My Next.js codebase grew bigger, and its complexity increased by greater size. I had dozens of components and a list of dependencies to manage. I ended up maintaining the code constantly just to keep it alive. Sure, Next.js helped here and there, but at what cost?

I asked myself, what am I doing on my website that is so complex that needs all that JavaScript code to decide what to render and how to render on my webpage? Next.js was trying to render the webpage from the server side, so why won’t I send the HTML directly myself?

So I decided to try a new route—some might say the good ol’ route—and choose plain HTML and use the help of htmx for that.

## <a href="#video" class="zola-anchor" aria-label="Anchor link for: video">Video</a>

Watch me go full in details here:

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

## <a href="#the-process" class="zola-anchor" aria-label="Anchor link for: the-process">The process</a>

Replacing my components with the equivalent HTML elements powered by htmx wasn’t exactly an easy task, but one that was worth the time. I had to view things from a different angle, and I sometimes felt strict in what user interactions I can implement, but what I created was reliable and fast.

All the build steps were gone; no more transpiling and compiling the code. What you see is what you get. Most of the dependencies became redundant and have been removed. All the main logic of the website was moved to the server side, holding one source for the truth.

In the Next.js version I had isolated components, global states, and all that JavaScript to handle the forms or update the content, and yet, everything was more intuitive with htmx. After trying it, sending and receiving HTML suddenly made sense.

## <a href="#summary" class="zola-anchor" aria-label="Anchor link for: summary">Summary</a>

- Dependencies are **reduced by 87%** (**24** to **3**!)
- I wrote **less code by 17%** (**9500 LOC** to **7900 LOC**.) In reality the total LOC of the code base is **reduced by more than 50%**, since much less code is imported from the dependencies.
- Web build time was **reduced by 100%** (there’s **no build step** anymore.)
- Size of the website **reduced by more than 85%** (**~800KB** to **~100KB**!)

These numbers signify a great improvement, however, what is important for me at the end is the user and the developer experience, which to me htmx won at both.

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

# prefer-if-statements__e454f9f1

- Source URL: https://htmx.org/essays/prefer-if-statements/
- Source file: `fetch/htmx_org_e454f9f1.html`
- Hash: `e454f9f1`
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

# Prefer If Statements To Polymorphism...

Carson Gross

December 07, 2024

## <a href="#or-watching-myself-lose-my-mind-in-real-time" class="zola-anchor" aria-label="Anchor link for: or-watching-myself-lose-my-mind-in-real-time">Or, Watching Myself Lose My Mind In Real Time…</a>

> “Invert, always invert.” –Carl Jacobi, by way of Charlie Munger

- *<a href="https://x.com/htmx_org/status/1843804410377535533" rel="noopener" target="_blank">If Statements</a>*

  > prefer if statements to polymorphism
  >
  > whenever you are tempted to create a class, ask yourself: “could this be an if statement instead?”

- *<a href="https://x.com/htmx_org/status/1843805753007845474" rel="noopener" target="_blank">The Closed/Closed Principle</a>*

  > In grug-oriented programming, the closed–closed principle (CCP) states “software entities (classes, modules, functions, etc.) should be closed for extension, but also closed for modification”
  >
  > they should just do something useful man

- *<a href="https://x.com/htmx_org/status/1843806270559793475" rel="noopener" target="_blank">The Minimize Abstractions Principle</a>*

  > The Minimize Abstractions Principle (MAP) is a computer programming principle that states that “a module should minimize the number of abstractions it contains, both in API and in implementation. Stop navel gazing nerd.”

- *<a href="https://x.com/htmx_org/status/1843807054970139139" rel="noopener" target="_blank">The Try It Out Substitution Principle</a>*

  > The “Try It Out” Substitution Principle states that you should try something out and, if that doesn’t work, think about why, and substitute something else for it instead.
  >
  > It is common to need to substitute multiple things to hit on the right thing eventually.

- *<a href="https://x.com/htmx_org/status/1843807769557909528" rel="noopener" target="_blank">The Useful Stuff Principle</a>*

  > The Useful Stuff Principle states that entities must depend on useful stuff, not overly abstract nonsense. It states that a high-level module can depend on a low-level module, because that’s how software works.

- *<a href="https://x.com/htmx_org/status/1843808113230860419" rel="noopener" target="_blank">Dependencies</a>*

  > The The Existence of Dependencies Is Not An Excuse For Destroying The Codebase Principle states that the existence of dependencies is not an excuse for destroying the codebase

- *<a href="https://x.com/htmx_org/status/1843821830207099007" rel="noopener" target="_blank">Abstraction Budget</a>*

  > consider giving your developers an abstraction budget
  >
  > when they exhaust that budget & ask for more, tell them they can have another abstraction when they remove an existing one
  >
  > when they complain, look for classes with the term “Factory”, “Lookup” or “Visitor” in their names

- *<a href="https://x.com/htmx_org/status/1843822378352291914" rel="noopener" target="_blank">Fewer Functions</a>*

  > if your function is only called in one place, consider inlining it & reducing the total number of method signatures in your module, to help people better understand it
  >
  > studies show longer methods have fewer bugs per line of code, so favor longer methods over many smaller methods

- *<a href="https://x.com/htmx_org/status/1843823231771521367" rel="noopener" target="_blank">“God” Object</a>*

  > consider creating “God” objects that wrap a lot of functionality up in a single package
  >
  > consumers of your API don’t want to learn 50 different classes to get something done, so give them a few that provide the core functionality of your module with minimal fuss

- *<a href="https://x.com/htmx_org/status/1843827082687852706" rel="noopener" target="_blank">Copy &amp; Paste Driven Development</a>*

  > copy&paste driven development is a development methodology where, when you need to reuse some code but in a slightly different manner, you copy & paste the code & then modify it to satisfy the new requirements
  >
  > this contrasts with designing an elaborate object model, for example

- *<a href="https://x.com/htmx_org/status/1843828023747063866" rel="noopener" target="_blank">Implementation Driven Development</a>*

  > implementation driven development is a development methodology where you first explore various implementations of your idea to determine the best one, then add tests for it
  >
  > no test code may be written without first having some implementation code to drive that test

- *<a href="https://x.com/htmx_org/status/1843830823113634132" rel="noopener" target="_blank">Mixing Concerns</a>*

  > Mixing of Concerns is a design methodology whereby “concerns” of various kinds are mixed into a single code unit. This improves locality in that code unit by placing all relevant logic within it. An example of this is hypermedia, which mixes control & presentation information.

- *<a href="https://x.com/htmx_org/status/1843831529300267103" rel="noopener" target="_blank">Macroservices Architecture</a>*

  > a macroservice architecture revolves around “macroservices”: network-deployed modules of code that provide a significant amount of functionality to the overall system
  >
  > by adopting a macroservice-based architecture you minimize deployment complexity & maximize resource utilization

- *<a href="https://x.com/htmx_org/status/1844005320223539524" rel="noopener" target="_blank">Sorry</a>*

  > kinda had a manic break last night my bad

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

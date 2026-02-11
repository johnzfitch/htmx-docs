# complexity-budget__2bb7c703

- Source URL: https://htmx.org/essays/complexity-budget/
- Source file: `fetch/htmx_org_2bb7c703.html`
- Hash: `2bb7c703`
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

# Complexity Budget

Carson Gross

October 29, 2020

Every software project involves managing a complexity budget.

A complexity budget can be defined as:

> An explicit or implicit allocation of complexity across the entire application

“Complexity” here is defined subjectively (rather than <a href="https://en.wikipedia.org/wiki/Programming_complexity" rel="noopener" target="_blank">formally</a>) and in <a href="https://en.wikipedia.org/wiki/I_know_it_when_I_see_it" rel="noopener" target="_blank">Stewartian Terms</a>: “I know it when I see it.”

Or, more specifically to software development: “I know it when I *feel* it.”

One of the primary jobs of an application architect is to manage a projects complexity budget:

- Decide if a given feature is “worth it”
- Decide if a given implementation is “worth it”
- Add appropriate system boundaries to limit complexity between components
- And so on

An infuriating aspect of complexity is that that attempts to address it can, in fact, add more complexity.

A good example of this from experience was when a company I worked at added <a href="https://en.wikipedia.org/wiki/OSGi" rel="noopener" target="_blank">OSGi</a> to the system to manage the increasing complexity of the project. It seemed like a reasonable approach, it offered a sophisticated <a href="https://www.osgi.org/resources/what-is-osgi/" rel="noopener" target="_blank">module</a> system, it was recommended by a newly hired architect, and it even says on the “What is OSGI page”:

> OSGi significantly reduces complexity in almost all aspects of development: code is easier to write and test, reuse is increased, build systems become significantly simpler, deployment is more manageable, bugs are detected early, and the runtime provides an enormous insight into what is running.

What’s not to like?

Unfortunately, adding OSGi to that project effectively ground the entire project to a halt: it took a few of our best engineers out of normal application development for over a year, and when they were done the codebase was even more difficult to work with than when they started. Feature velocity, already teetering, collapsed.

This is not to say OSGi is universally bad. But, in this case, rather than boosting our development teams productivity, it effectively ended it.

A good software architect is someone who manages the software budget of their project effectively, either explicitly or implicitly.

## <a href="#complexity-growth" class="zola-anchor" aria-label="Anchor link for: complexity-growth">Complexity Growth</a>

My sense, admittedly without hard evidence, is that Stewartian Application Complexity grows roughly geometrically with the size of an application. Proper <a href="https://en.wikipedia.org/wiki/Decomposition_(computer_science)" rel="noopener" target="_blank">factoring</a> by experienced developers can hold this curve down for quite some time.

However, this doesn’t change the fact that, somewhere out there, there is a Complexity Wall lurking.

And, if you aren’t careful, you will run headlong into it and grind your development velocity to a halt.

I have had multiple experiences with this: one day, inexplicably, development on a system that I was working on went from feeling “large, but manageable” to “this is impossible to deal with”.

## <a href="#spending-your-complexity-budget-wisely" class="zola-anchor" aria-label="Anchor link for: spending-your-complexity-budget-wisely">Spending Your Complexity Budget Wisely</a>

Here are some tools for managing your complexity budget:

1.  Foremost: understanding that there *is* a complexity budget that needs to be managed
2.  Focus your “complexity spend” on the areas where your application is adding value and/or differentiates itself
3.  Saying “No” - probably the easiest, best and, also, hardest tool to use in your battle with complexity
4.  Embracing <a href="https://en.wikipedia.org/wiki/KISS_principle" rel="noopener" target="_blank">KISS</a>, even if it means admitting you are stupid (Note that it’s often very good for an organization if the senior developers can admit they are fallible)
5.  Proper factoring of components - this is an art: Too many components and your complexity explodes. Too few… same.
6.  Choosing the proper balance of expressiveness and restrictions for a component

Unfortunately, experience shows that managing Stewartian Complexity is a subjective endeavor and that many talented and experience developers will disagree on the proper course of action at a given decision point.

Nonetheless, by making the concept of a complexity budget explicit in your software project, these conversations can be more productive and ultimately lead to better software outcomes.

## <a href="#a-final-note" class="zola-anchor" aria-label="Anchor link for: a-final-note">A Final Note</a>

Almost all mature applications are complex.

Finding a new codebase “complex” is *not* an excuse for tearing everything apart or aggressive refactoring. We must always bear in mind <a href="https://fs.blog/2020/03/chestertons-fence/" rel="noopener" target="_blank">Chesterton’s Fence</a>.

If an application is functioning well (or even reasonably) then we should assume that the complexity budget was well (or at least reasonably) managed.

And we must always remember that, with unfortunate frequency, big attempts at addressing complexity in existing, large applications often fail or, sadly, make things worse.

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

# move-before__6cabe356

- Source URL: https://htmx.org/examples/move-before/
- Source file: `fetch/htmx_org_6cabe356.html`
- Hash: `6cabe356`
- Category: `htmx/examples`

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

# Experimental moveBefore() Support

This page demonstrates the use of the experimental <a href="https://github.com/whatwg/dom/issues/1255" rel="noopener" target="_blank"><code>moveBefore()</code></a> DOM API available in <a href="https://www.google.com/chrome/canary/" rel="noopener" target="_blank">Chrome Canary</a>, which has been integrated into the `hx-preserve` attribute of htmx, if it is available.

### <a href="#getting-chrome-canary-enabling-movebefore" class="zola-anchor" aria-label="Anchor link for: getting-chrome-canary-enabling-movebefore">Getting Chrome Canary &amp; Enabling <code>moveBefore()</code></a>

For the demo to work properly you will need to install Chrome Canary and enable the API:

- Navigate to <chrome://flags/#atomic-move>
- Enable “Atomic DOM move”

htmx takes advantage of this API in the `hx-preserve` functionality if it is available, allowing you to mark an element as “preserved” and having all its state preserved as it moves between areas on the screen when new content is merged in. This is significantly better developer experience than current alternatives, such as morphing, which rely on the structure of the new page being “close enough” to not have to move things like video elements.

### <a href="#demo" class="zola-anchor" aria-label="Anchor link for: demo">Demo</a>

If you inspect the video below you will see that it is embedded in a `div` element. If you click the “View Details” link, which is boosted, you will transition to another page with a video element with the same id, but embedded in a `figure` element instead. Without the `moveBefore()` functionality it is impossible to keep the video playing in this situation because “reparenting” (i.e. changing the parent of an element) causes it to reset.

`moveBefore()` opens up a huge number of possibilities in web development by allowing developers to completely change the layout of a page while still preserving elements play state, focus, etc.

<div class="center">

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

<div>

<a href="/examples/move-before/details" data-hx-boost="true">View Details →</a>

</div>

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

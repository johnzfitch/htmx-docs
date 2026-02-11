# another-real-world-react-to-htmx-port__2d758f4b

- Source URL: https://htmx.org/essays/another-real-world-react-to-htmx-port/
- Source file: `fetch/htmx_org_2d758f4b.html`
- Hash: `2d758f4b`
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

# Another Real World React -\> htmx Port

Carson Gross

September 20, 2023

The [Mother of All htmx Demos](https://htmx.org/essays/a-real-world-react-to-htmx-port/) you can see the real world results of a port from a React-based front end to an htmx-powered front end. The results are very good, although we qualify the experience with the following:

> These are eye-popping numbers, and they reflect the fact that the Contexte application is extremely amenable to hypermedia: it is a content-focused application that shows lots of text and images. We would not expect every web application to see these sorts of numbers.
>
> However, we *would* expect *many* applications to see dramatic improvements by adopting the hypermedia/htmx approach, at least for part of their system.

As luck would have it, we have another application (again, based on Django on the server side) that has been ported from a React front end to an htmx front end: <a href="https://openunited.com/" rel="noopener" target="_blank">OpenUnited</a>.

Here is a graphic from the <a href="https://www.linkedin.com/feed/update/urn:li:activity:7109116330770878464/" rel="noopener" target="_blank">original LinkedIn post</a> by Adrian McPhee, showing the total Lines of Code in the code base before and after the port:

![Open United Before & After](/img/open_united_before_after_htmx.png)

### <a href="#before-after-source-code" class="zola-anchor" aria-label="Anchor link for: before-after-source-code">Before/After Source Code</a>

A very nice aspect of this port is that, because OpenUnited is open source, in contrast with Contexte, the before and after code is available to examine:

Before: <a href="https://github.com/OpenUnited/old-codebase" rel="noopener" target="_blank">https://github.com/OpenUnited/old-codebase</a>

After: <a href="https://github.com/OpenUnited/platform" rel="noopener" target="_blank">https://github.com/OpenUnited/platform</a>

## <a href="#executive-summary" class="zola-anchor" aria-label="Anchor link for: executive-summary">Executive Summary</a>

Here is a high-level summary of the port

- They reduced the **code base size** by **61%** (31237 LOC to 12044 LOC)
- They reduced the **total number of files** by **72%** (588 files to 163 files)
- They reduced the **total number of file types** by **38%** (18 file types to 11 file types)
- Subjectively, development velocity felt at least **5X** faster
- Rather than prototyping in Figma and then porting to HTML, UX development was done directly in HTML

## <a href="#analysis" class="zola-anchor" aria-label="Anchor link for: analysis">Analysis</a>

Once again we have some eye-popping results. This is because the OpenUnited application is extremely amenable to hypermedia: like Contexte, it is a content-focused application that shows lots of text and images.

This experience again demonstrates that, for at least a certain class of web applications, htmx and the hypermedia architecture can be an excellent choice.

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

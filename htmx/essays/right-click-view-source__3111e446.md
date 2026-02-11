# right-click-view-source__3111e446

- Source URL: https://htmx.org/essays/right-click-view-source/
- Source file: `fetch/htmx_org_3111e446.html`
- Hash: `3111e446`
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

# The \#ViewSource Affordance

Carson Gross

September 21, 2023

> Not for nothing, Hypercard presaged the web’s critical “#ViewSource” affordance, which allowed people to copy, modify, customize and improve on the things that they found delightful or useful. This affordance was later adapted by other human-centered projects like \#Scratch, and is a powerful tonic against \#enshittification.
>
> --<a href="https://twitter.com/doctorow/status/1701934612686196872" rel="noopener" target="_blank">Cory Doctorow @pluralistic@mamot.fr</a>

## <a href="#open-culture-the-web" class="zola-anchor" aria-label="Anchor link for: open-culture-the-web">Open Culture &amp; The Web</a>

When people talk about open source software, that conversation is often dominated by <a href="https://www.gnu.org/philosophy/free-sw.html" rel="noopener" target="_blank">the Free Software Foundation’s notion of free software</a>:

> “Free software” means software that respects users’ freedom and community. Roughly, it means that the users have the freedom to run, copy, distribute, study, change and improve the software.

This definition of free software has been a useful one and, through advocating for it, the FSF has gifted the world a lot of wonderful open source software.

Web applications, however, have always been an uncomfortable fit for this definition of free. This is mainly for technical reasons: web applications involve a web browser interacting with a web server that is, typically, running on a remote system.

At a fundamental level, the REST-ful architecture of the web was built around *hypermedia representations* of remote resources: browsers deal only with hypermedia representations provided by the server and, thus, have no visibility into the actual source of the code executing on the server side.

Now, the web has certainly *leveraged* free and open source software in its growth: browsers are typically (at least mostly) open source, server software is often open source, and so on. And there are, of course, open source web applications that users may run for things like forums and so forth.

However, from the standpoint of typical web application users, web applications are not free in the FSF sense of that term: the users are unable to see and modify the source of the server code that is being executed as they interact with the application via the browser.

### <a href="#right-click-view-source-as-culture" class="zola-anchor" aria-label="Anchor link for: right-click-view-source-as-culture">Right-Click-View-Source As Culture</a>

Despite the fact that the web has a somewhat uncomfortable relationship with the notion of free software, the early web none-the-less had a radically open *developer culture*.

In fact, in some important and practical ways, the early web had a *more* open developer culture than what was achieved by the free software movement.

The <a href="https://en.wikipedia.org/wiki/View-source_URI_scheme" rel="noopener" target="_blank">#ViewSource</a> affordance available in browsers allowed people to understand and “own”, at least in an informal way, the web in a way that even most FSF-conforming applications could not: you had direct access to the “source”, or at least *part* of the source, of the application available from *within* the application itself.

You could copy-and-paste (or save) the “source” (HTML, JavaScript & CSS) and start modifying it, without a complicated build tool chain or, indeed, without any tool chain at all.

This radical openness of the web allowed many people, often not formally trained computer programmers, to learn how to create web pages and applications in an ad hoc and informal way.

In strict free software terms, this was, of course, a compromise: as a user of a web application, you had no visibility into how a server was constructing a given hypermedia response.

But you could see *what* the server was responding with: you could download and tweak it, poke and prod at it. You could, if you were an advanced user, use browser tools to modify the application in place.

And, most importantly, you could *learn from it*, even if you couldn’t see how the HTML was being produced.

This radical openness of the client and network protocol, and the culture it produced, was a big part of the success of the early web.

## <a href="#digital-enclosure-vs-technical-enclosure" class="zola-anchor" aria-label="Anchor link for: digital-enclosure-vs-technical-enclosure">Digital Enclosure vs. Technical Enclosure</a>

The <a href="https://en.wikipedia.org/wiki/Enclosure" rel="noopener" target="_blank">Enclosure Movement</a> was a period in English history when what were previously <a href="https://en.wikipedia.org/wiki/Commons" rel="noopener" target="_blank">commons</a> were privatized.

This was a traumatic event in English history, as evidenced by this poem by an 18th century anon:

> The law locks up the man or woman
>
> Who steals the goose from off the common,
>
> But lets the greater felon loose
>
> Who steals the common from the goose.
>
> –18th century anon

In the last decade, the web has gone through a period of “Digital Enclosure”, where <a href="https://en.wikipedia.org/wiki/Closed_platform" rel="noopener" target="_blank">“Walled Gardens”</a>, such as Facebook & Twitter, have replaced the earlier, more open and more chaotic blogs and internet forums.

### <a href="#technical-enclosure" class="zola-anchor" aria-label="Anchor link for: technical-enclosure">Technical Enclosure</a>

Many (most?) web developers have decried this trend.

However, despite recognizing the danger of an increasingly closed internet, many web developers don’t consider their own technical decisions and how those decisions can also contribute to the disappearance of web’s *culture* of openness.

Inadvertently (for the most part) technical trends and decisions in web development in the last two decades have lead to what we term a “Technical Enclosure” of the web, a processes whereby technical decisions chip away at the \#ViewSource affordance that Cory Doctorow discusses in the opening quote of this article, an affordance that existed as a commons for early web developers.

To see a stark example of the decline of the <a href="https://en.wikipedia.org/wiki/View-source_URI_scheme" rel="noopener" target="_blank">#ViewSource</a> affordance in web development and Technical Enclosure in action, we can look at what is perhaps the most popular web page on the internet, <a href="https://google.com" rel="noopener" target="_blank">The Google Homepage</a>.

Here is the nearly complete source of that page from the year 2000, taken from <a href="http://web.archive.org/web/20000229040250/http://www.google.com/" rel="noopener" target="_blank">the wayback machine</a>:

### <a href="#google-in-2000" class="zola-anchor" aria-label="Anchor link for: google-in-2000">Google in 2000</a>

<img src="/img/google-2000.png" style="border-radius: 12px; margin: 12px" alt="Google Source Code in 2000" />

In contrast, here is a random snapshot of roughly 1/100th of the current source code for the website:

### <a href="#google-in-2023" class="zola-anchor" aria-label="Anchor link for: google-in-2023">Google in 2023</a>

<img src="/img/google-2023.png" style="border-radius: 12px; margin: 12px" alt="Google Source Code in 2023" />

These two screenshots dramatically demonstrate the decline in the effectiveness of the <a href="https://en.wikipedia.org/wiki/View-source_URI_scheme" rel="noopener" target="_blank">#ViewSource</a> affordance over time: yes, you can still right-click the page and view its underlying source, but making sense of the latter code would be challenging for even the most seasoned web developer.

A new web developer would have almost no chance of deriving any value from doing so.

Now, this is not to criticize the Google engineer’s technical decisions that lead to this situation *as technical decisions*: obviously, despite similar appearances, the Google homepage of 2023 is far more sophisticated than the one available in 2000.

The 2023 google homepage is going to be a lot more complicated than the 2000 page and, given the zeitgeist, it is going to involve a lot of JavaScript.

However, this is to point out that something deeply important about the early web has been lost, almost certainly unintentionally, along the way: the ability to view the source of the page, make sense of what it is doing and, most importantly, to learn from it.

## <a href="#right-click-view-source-extremism" class="zola-anchor" aria-label="Anchor link for: right-click-view-source-extremism">Right-Click-View-Source Extremism</a>

Both [htmx](/) and <a href="https://hyperscript.org" rel="noopener" target="_blank">hyperscript</a> adhere to the [Locality of Behavior](https://htmx.org/essays/locality-of-behaviour/) design principle.

This principle states that:

> The behaviour of a unit of code should be as obvious as possible by looking only at that unit of code

The main technical advantage of Locality of Behavior is ease of maintenance, as outlined in the essay above.

However, there is an important cultural benefit to the Locality of Behavior of htmx and hyperscript as well: **it restores the power of the <a href="https://en.wikipedia.org/wiki/View-source_URI_scheme" rel="noopener" target="_blank">#ViewSource</a> affordance on the web**.

Consider <a href="https://arhamjain.com/hyperwordle/" rel="noopener" target="_blank">Hyperwordle</a>, a hyperscript-based clone of the popular <a href="https://www.nytimes.com/games/wordle/index.html" rel="noopener" target="_blank">Wordle</a> game, now owned by the New York Times.

You can visit Hyperwordle, right click and view the source of it, and you will be presented with some HTML and hyperscript, all of which is, with a bit of effort, understandable.

The <a href="https://en.wikipedia.org/wiki/View-source_URI_scheme" rel="noopener" target="_blank">#ViewSource</a> affordance is effective in this case.

Contrast this with the view-source experience of the Wordle implementation at the New York Times.

Now, this is of course a bit unfair: the NYTimes version has a lot more functionality and is heavily optimized. Hyperwordle is a proof of concept and not being hammered by millions of users every day.

Despite that qualification, Hyperwordle demonstrates a potential future for the web, a future where a culture of openness, of <a href="https://en.wikipedia.org/wiki/View-source_URI_scheme" rel="noopener" target="_blank">#ViewSource</a> politeness, is once again a touchstone of the culture of the web.

## <a href="#prioritizing-viewsource" class="zola-anchor" aria-label="Anchor link for: prioritizing-viewsource">Prioritizing</a> <a href="https://en.wikipedia.org/wiki/View-source_URI_scheme" rel="noopener" target="_blank">#ViewSource</a>

Engineers who care about the open culture of the web should recognize that the threats to that culture come not only from Digital Enclosure by large, private companies of the most important pieces of the web.

They should also recognize the risks of Technical Enclosure, and the *non-technical* value of the <a href="https://en.wikipedia.org/wiki/View-source_URI_scheme" rel="noopener" target="_blank">#ViewSource</a> affordance in perpetuating the open culture of web development. They should start thinking about making this affordance a priority in their technical decisions. As with all priorities, this may involve trading off against other technical and even functional priorities during application development.

But if we don’t stand up for <a href="https://en.wikipedia.org/wiki/View-source_URI_scheme" rel="noopener" target="_blank">#ViewSource</a>, no one else will.

\
<img src="/img/memes/viewsource.png" style="border-radius: 12px; margin: 12px" alt="Right Click View Source Guy" />

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

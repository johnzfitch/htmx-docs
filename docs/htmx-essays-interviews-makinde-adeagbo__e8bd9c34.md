# interviews-makinde-adeagbo__e8bd9c34

- Source URL: https://htmx.org/essays/interviews/makinde-adeagbo/
- Source file: `fetch/htmx_org_e8bd9c34.html`
- Hash: `e8bd9c34`
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

# An interview with Makinde Adeagbo, Creator of Primer

Carson Gross

January 27, 2025

I’m delighted to be able to interview Makinde Adeagbo, one of the creators of <a href="https://www.youtube.com/watch?v=wHlyLEPtL9o" rel="noopener" target="_blank">Primer</a>, an hypermedia-oriented javascript library that was being used at Facebook in the 2000s.

Thank you for agreeing to an interview!

Q: To begin with, why don’t you give the readers a bit of your background both professionally & technically?

> I’ve always been into tech. In high school, I used to build computers for friends and family. I took the computer science classes my high school offered and went on to study computer science in college. I was always amazed by the fact that I could build cool things—games, tools, etc.—with just a computer and an internet connection.
>
> I was lucky enough to participate in Explore Microsoft, an internship that identifies underrepresented college freshmen and gives them a shot at working at Microsoft. After that experience, I was sold on software as my future. I later interned at Apple and Microsoft again. During college, I also worked at Facebook when the company was about 150 employees. It was an incredible experience where engineers had near-total freedom to build and contribute to the company’s growth. It was exactly what I needed early in my career, and I thrived. From there, I went on to work at Dropbox and Pinterest and also co-founded the nonprofit, /dev/color.

Q: Can you give me the history of how Primer came to be?

> In 2010, the Facebook website was sloooow. This wasn’t the fault of any specific person—each engineer was adding features and, along the way, small amounts of JavaScript. However, we didn’t have a coherent system for sharing libraries or tracking how much JavaScript was being shipped with each page. Over time, this led to the 90th-percentile page load time ballooning to about 10 seconds! Midway through the year, reducing that load time by half became one of the company’s three top priorities. I was on a small team of engineers tasked with making it happen.
>
> As we investigated where most of the JavaScript was coming from, we noticed the majority of it was performing simple tasks. These tasks involved either fetching additional data or markup from the server, or submitting a form and then receiving more markup to update the page. With limited time, we decided to build a small solution to abstract those patterns and reduce the amount of code needed on the page.
>
> Tom Occhino and I built the first version of Primer and converted a few use cases ourselves to ensure it worked well. Once we were confident, we brought more engineers into the effort to scale it across the codebase.

Q: Primer & React were both created at Facebook. Was there any internal competition or discussion between the teams? What did that look like?

> The two projects came from different eras, needs, and parts of the codebase. As far as I know, there was never any competition between them.
>
> Primer worked well for the type of website we were building in 2010. A key part of its success was understanding that it wasn’t meant to handle every use case. It was an 80/20 solution, and we didn’t use it for particularly complex interactions (like the interface for creating a new post).
>
> React emerged from a completely different challenge: the ads tools. Managing, composing, and tracking hundreds of ads required a highly involved, complex interface. I’m not sure if they ever attempted to use Primer for it, but it would have been a miserable experience. We didn’t have the terminology at the time, but this was a classic example of a single-page application needing purpose-built tools. The users of that site also had a very different profile from someone browsing their home feed or clicking through photos.

Q: Why do you think Primer ultimately failed at Facebook?

> I don’t think there’s any single technical solution that has spanned 15 years in Facebook’s platform. The site’s needs evolve, technology changes, and the internet’s landscape shifts over time. Primer served the site well for its time and constraints, but eventually, the product demanded richer interactivity, which wasn’t what Primer was designed for.
>
> Other tradeoffs also come into play: developer ease/speed, security, scalability. These priorities and tradeoffs change over time, especially as a company grows 10x in size.
>
> More broadly, these things tend to work in cycles in the industry. Streamlined, fast solutions give way to richer, heavier tools, which eventually cycle back to streamlined and fast. I wouldn’t be surprised if something like Primer made a comeback at some point.

Q: How much “theory” was there to Primer? Did you think much about hypermedia, REST, etc., when you were building it?

> Not much. Honestly, I was young and didn’t know a ton about the internet’s history or past research. I was drawn to the simplicity of the web’s underlying building blocks and thought it was fun to use those tools as they were designed. But, as always, the web is a layer cake of hacks and bandaids, so you have to be flexible.

Q: What were the most important technical lessons you took away from Primer?

> Honestly, the biggest lessons were about people. Building a system like Primer is one thing, but for it to succeed, you have to train hundreds of engineers to use it. You have to teach them to think differently about building things, ask questions at the right time, and avoid going too far in the wrong direction. At the end of the day, even if the system is perfect, if engineers hate using it, it won’t succeed.

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

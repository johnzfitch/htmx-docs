# interviews-mike-amundsen__78374e32

- Source URL: https://htmx.org/essays/interviews/mike-amundsen/
- Source file: `fetch/htmx_org_78374e32.html`
- Hash: `78374e32`
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

# An interview with Mike Amundsen, Author of 'RESTful Web APIs'

Carson Gross

January 27, 2025

Mike Amundsen is a computer programmer, author and speaker, and is one of the world leading experts on REST & hypermedia. He has been writing about REST and Hypermedia since 2008 and has published two books on the ideas:

- <a href="http://restfulwebapis.com/" rel="noopener" target="_blank">RESTful Web APIs</a>
- <a href="http://www.dpbolvw.net/click-7269430-11260198?sid=HP&amp;url=http%3A%2F%2Fshop.oreilly.com%2Fproduct%2F0636920020530.do%3Fcmp%3Daf-prog-book-product_cj_9781449306571_%25zp&amp;cjsku=0636920020530" rel="noopener" target="_blank">Building Hypermedia APIs with HTML and Node</a>

Mike agreed to do an interview with me on his view of the history of hypermedia and where things are today.

**Q**: The “standard” history of hypermedia is Vannevar Bush’s “As We May Think”, followed by Nelson introducing the term “hypermedia” in 1963, Englebart’s “Mother of all Demos” in 1968 and then Berners-Lee creating The Web in 1990. Are there any other important points you see along the way?

> I think starting the history of what I call the “modern web” with Bush makes a lot of sense. Primarily because you can directly link Bush to Engelbart to Nelson to Berners-Lee to Fielding. That’s more than half a century of scholarship, design, and implementation that we can study, learn from, and expand upon.
>
> At the same time, I think there is an unsung hero in the hypermedia story; one stretches back to the early 20th century. I am referring to the Belgian author and entrepreneur <a href="https://en.wikipedia.org/wiki/Paul_Otlet" rel="noopener" target="_blank">Paul Otlet</a>. Otlet had a vision of <a href="https://monoskop.org/Mundaneum_symposium" rel="noopener" target="_blank">a multimedia information system</a> he named the “World Wide Network”. He saw how we could combine text, audio, and video into a mix of live and on-demand replay of content from around the world. He even envisioned a kind of multimedia workstation that supported searching, storing, and playing content in what was the earliest instance I can find of an understanding of what we call “streaming services” today.
>
> To back all this up, he created <a href="https://daily.jstor.org/internet-before-internet-paul-otlet/" rel="noopener" target="_blank">a community of researchers</a> that would read monographs, articles, and books then summarize them to fit on a page or less. He then designed an identification system – much like our URI/URN/URLs today and created a massive card catalog system to enable searching and collating the results into a package that could be shared – even by postal service – with recipients. He created web search by mail in the 1920s!
>
> This was a man well ahead of his time that I’d like to see talked about more in hypermedia and information system circles.

**Question**: Why do you think that The Web won over other hypermedia systems (such as Xanadu)?

> The short reason is, I think, that Xanadu was a much more detailed and specific way of thinking about linking documents, documenting provenance, and compensating authors. That’s a grand vision that was difficult to implement back in the 60s and 70s when Nelson was sharing his ideas.
>
> There are, of course, lots of other factors. Berners-Lee’s vision was much smaller (he was trying to make it easy for CERN staff to share contact information!). Berners-Lee was, I think, much more pragmatic about the implementation details. He himself said he used existing tech (DNS, packet networking, etc.) to implement his ideas. That meant he attracted interest from lots of different communities (telephone, information systems, computing, networking, etc.).
>
> I would also say here that I wish <a href="https://en.wikipedia.org/wiki/Wendy_Hall" rel="noopener" target="_blank">Wendy Hall</a> ’s <a href="https://www.sciencefriday.com/articles/the-woman-who-linked-the-web-in-a-microcosm/" rel="noopener" target="_blank">Microcosm</a> had gotten more traction than it did. Hall and her colleagues built an incredibly rich hypermedia system in the 90s and released it before Berners-Lee’s version of “the Web” was available. And Hall’s Microcosm held more closely to the way Bush, Englebart, and Nelson thought hypermedia systems would be implemented – primarily by storing the hyperlinks in a separate “anchor document” instead of in the source document itself.

**Question**: What do you think of my essay “How did REST come to mean the opposite of REST”? Are there any points you disagree with in it?

> I read that piece back in 2022 when you released it and enjoyed it. While I have nothing to quibble with, really, there are a few observations I can share.
>
> I think I see most hypermedia developers/researchers go through a kind of cycle where you get exposed to “common” REST, then later learn of “Fielding’s REST” and then go back to the “common REST” world with your gained knowledge and try to get others on board; usually with only a small bit of success.
>
> I know you like memes so, I’ll add mine here. This journey away from home, into expanded knowledge and the return to the mundane life you once led is – to me – just another example of Campbell’s Hero’s Journey\<g\>. I feel this so strongly that I created <a href="http://amundsen.com/talks/2015-05-barcelona/index.html" rel="noopener" target="_blank">my own Hero’s Journey presentation</a> to deliver at API conferences over the years.
>
> On a more direct note. I think many readers of Fielding’s Dissertation (for those who actually read it) miss some key points. Fielding’s paper is about designing network architecture, not about REST. REST is offered as a real-world example but it is just that; an example of his approach to information network design. There have been other designs from the same school (UC Irvine) including Justin Erenkrantz’s Computational REST (<a href="https://www.erenkrantz.com/CREST/" rel="noopener" target="_blank">CREST</a>) and Rohit Kare’s Asynchronous REST (A-REST). These were efforts that got the message of Fielding: “Let’s design networked software systems!”
>
> But that is much more abstract work that most real-world developers need to deal with. They have to get code out the door and up and running quickly and consistently. Fielding’s work, he admitted, was on the “<a href="https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven#comment-724" rel="noopener" target="_blank">scale of decades</a>” – a scale most developers are not paid to consider.
>
> In the long run, I think it amazing that a PhD dissertation from almost a quarter-century ago has had such a strong influence on day-to-day developers. That’s pretty rare.

**Question**: Hyperview, the mobile hypermedia that Adam Stepinski created, was very explicitly based on your books. Have you looked at his system?

> I have looked over <a href="https://hyperview.org/" rel="noopener" target="_blank">Hyperview</a> and like what I see. I must admit, however, that I don’t write mobile code anymore so I’ve not actually written any hyperview code myself. But I like it.
>
> I talked to Adam in 2022 about Hyperview in general and was impressed with his thoughts. I’d like to see more people talking about and using the Hyperview approach.
>
> Something I am pretty sure I mentioned to Adam at the time is that Hyperview reminds me of Wireless Markup Language (<a href="https://en.wikipedia.org/wiki/Wireless_Markup_Language" rel="noopener" target="_blank">WML</a>). This was another XML-based document model aimed at rendering early web content on feature phones (before smartphone technology). Another XML-based hypermedia domain-specific document format is <a href="https://en.wikipedia.org/wiki/VoiceXML" rel="noopener" target="_blank">VoiceXML</a>. I still think there are great applications of hypermedia-based domain-specific markup languages (DSML) and would like to see more of them in use.

**Question**: It’s perhaps wishful thinking, but I feel there is a resurgence in interest in the ideas of hypermedia and REST (real REST.) Are you seeing this as well? Do you have a sense if businesses are starting to recognize the strengths of this approach?

> I, myself, think there is a growth in hypermedia-inspired designs and implementations and I’m glad to see it. I think much of the work of APIs in general has been leading the market to start thinking about how to lower the barrier of entry for using and interoperating with remote, independent services. And the hypermedia control paradigm (the one you and your colleagues talk about in your paper “<a href="https://dl.acm.org/doi/fullHtml/10.1145/3648188.3675127" rel="noopener" target="_blank">Hypermedia Controls: Feral to Formal</a>”) offers an excellent way to do that.
>
> I think the biggest hurdle for using more hypermedia in business is was <a href="https://www.crummy.com/writing/speaking/2015-RESTFest/" rel="noopener" target="_blank">laid out pretty conclusively</a> by <a href="https://www.crummy.com/self/" rel="noopener" target="_blank">Leonard Richardson</a> several years ago. He helped build a powerful <a href="https://opds.io/" rel="noopener" target="_blank">hypermedia-based book-sharing server and client</a> system to support public libraries around the world. He noted that, in the library domain, each site is not a competitor but a partner. That means libraries are encouraged to make it easier to loan out books and interoperate with other libraries.
>
> Most businesses operate on the opposite model. They typically succeed by creating barriers of entry and by hoarding assets, not sharing them. Hypermedia makes it easier to share and interact without the need of central control or other types of “gatekeeping.”
>
> Having said that, I think a ripe territory for increased use of hypermedia to lower the bar and increase interaction is at the enterprise level in large organizations. Most big companies spend huge amounts of money building and rebuilding interfaces in order to improve their internal information system. I can’t help but think designing and implementing hypermedia-driven solutions would yield long-term savings, and near-term sustainable interoperability.

**Question**: Are there any concepts in hypermedia that you think we are sleeping on? Or, maybe said another way, some older ideas that are worth looking at again?

> Well, as I just mentioned, I think hypermedia has a big role to play in the field of interoperability. And I think the API-era has, in some ways, distracted us from the power of hypermedia controls as a design element for service-to-service interactions.
>
> While I think Nelson, Berners-Lee and others have done a great job of laying out the possibilities for human-to-machine interaction, I think we’ve lost sight of the possibilities hypermedia gives us for machine-to-machine interactions. I am surprised we don’t have more hypermedia-driven workflow systems available today.
>
> And I think the rise in popularity of LLM-driven automation is another great opportunity to create hypermedia-based, composable services that can be “orchestrated” on the fly. I am worried that we’ll get too tied up in trying to make generative AI systems look and act like human users and miss the chance to design hypermedia workflow designed specifically to take advantage of the strengths of statistical language models.
>
> I’ve seen some interesting things in this area including <a href="https://www.linkedin.com/in/zdne/" rel="noopener" target="_blank">Zdenek Nemec</a>’s <a href="https://superface.ai/" rel="noopener" target="_blank">Superface</a> project which has been working on this hypermedia-driven workflow for several years.
>
> I just think there are lots of opportunities to apply what we’ve learned from the last 100 years (when you include Otlet) of hypermedia thinking. And I’m looking forward to seeing what comes next.

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

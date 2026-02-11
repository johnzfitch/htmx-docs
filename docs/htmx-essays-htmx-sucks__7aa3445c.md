# htmx-sucks__7aa3445c

- Source URL: https://htmx.org/essays/htmx-sucks/
- Source file: `fetch/htmx_org_7aa3445c.html`
- Hash: `7aa3445c`
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

# htmx sucks

Carson Gross

February 01, 2024

I have been following <a href="https://htmx.org" rel="noopener" target="_blank">htmx</a> for a while now. I thought it was a somewhat funny/cringey meme and that it served as some light comic relief from the real work being done in web development, things like <a href="https://react.dev/reference/react/use-server" rel="noopener" target="_blank">React Server Components</a>, <a href="https://svelte.dev/blog/runes" rel="noopener" target="_blank">Svelte Runes</a> and <a href="https://www.solidjs.com/tutorial/introduction_signals" rel="noopener" target="_blank">Signals</a> that are actually pushing the state of the art forward.

Unfortunately at some point <a href="https://star-history.com/#bigskysoftware/htmx&amp;Date" rel="noopener" target="_blank">in the middle of 2023</a> people began to actually take htmx seriously for <a href="https://www.youtube.com/watch?v=zjHHIqI9lUY" rel="noopener" target="_blank">some</a> <a href="https://www.youtube.com/watch?v=r-GSGH2RxJs" rel="noopener" target="_blank">reason</a>. This is an extremely alarming turn of events that has me deeply concerned for the future of web development.

And I’m not alone in my alarm: you can read an excellent <a href="https://archive.is/rQrl7" rel="noopener" target="_blank">dressing down of htmx here</a>:

> Basically they put their ignorance on full display, then attribute all sorts of unfounded merits to whatever they’ve done hoping that everyone else pats them on the back for it.

So true. So, so true.

Unfortunately, the language in that excellent medium post is academic and, without a solid grasp of theoretical HTML, many of the more important points in it will go over a typical web developers head.

So, in this article, I will attempt to present, in plain language for the layman web developer, why [htmx sucks](https://htmx.org/essays/htmx-sucks/).

## <a href="#the-code-is-crap" class="zola-anchor" aria-label="Anchor link for: the-code-is-crap">The Code Is Crap</a>

First of all, consider the code for htmx.

<a href="https://github.com/bigskysoftware/htmx/blob/master/src/htmx.js" rel="noopener" target="_blank">Look at this garbage.</a>

They use `var` all over the place, almost no modern JavaScript features (hello, htmx people, have you heard of <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules" rel="noopener" target="_blank">Modules</a>?), they pollute the `window` name space, and on and on and on.

Worst of all, it’s just one big ball of JavaScript! One file! It isn’t decomposed at all. If this person took one of my <a href="https://www.cs.montana.edu/directory/2256398/carson-gross" rel="noopener" target="_blank">classes at MSU</a> I would fail them based solely on this complete misunderstanding of <a href="https://en.wikipedia.org/wiki/Separation_of_concerns" rel="noopener" target="_blank">Separation of Concerns</a>, something any freshman in computer science should be able to grasp.

Good software starts with clean code, and this code is filthy.

## <a href="#no-build-tools" class="zola-anchor" aria-label="Anchor link for: no-build-tools">No Build Tools</a>

The next red flag is the lack of a build step. Not only does htmx not have a traditional build step, thereby depriving themselves of the <a href="https://vitejs.dev/guide/why.html" rel="noopener" target="_blank">benefits</a> that the rest of the JavaScript community enjoys, but they [actively brag](https://htmx.org/essays/no-build-step/) about it!

And it gets worse.

If you look closely, even though they claim to not have a build step, they <a href="https://github.com/bigskysoftware/htmx/blob/bedee219329117fff8d58e33678d82f7c34b08b5/package.json#L30" rel="noopener" target="_blank"><em>actually do</em></a> have a build step, it’s just an ad hoc set of bash scripts they wrote themselves.

Ridiculous *and* dishonest. Shameful.

## <a href="#no-typescript" class="zola-anchor" aria-label="Anchor link for: no-typescript">No Typescript</a>

Despite the <a href="https://blog.logrocket.com/understanding-typescripts-benefits-pitfalls/" rel="noopener" target="_blank">obvious benefits</a> of <a href="https://www.typescriptlang.org/" rel="noopener" target="_blank">TypeScript</a> for a project like htmx, the authors have stubbornly resisted using it. Part of this is their irrational opposition to a build step (which they actually have, btw!) but part of it is a ridiculous commitment to “shipping debuggable source code”. Of course, as any JavaScript developer who isn’t a complete idiot knows, TypeScript supports <a href="https://www.typescriptlang.org/tsconfig#sourceMap" rel="noopener" target="_blank">Source Maps</a> that make it perfectly debuggable. Despite this fact, the authors continue to insist on using an antiquated version of JavaScript for development.

In a tacit admission that they screwed up, they are now belatedly adding <a href="https://jsdoc.app/" rel="noopener" target="_blank">JSDoc</a> annotations to their codebase (I use the word loosely here). All this to make up for the fact that they didn’t do the obvious, correct thing initially and simply write the whole project in modern, modular TypeScript.

The only good news here is that at least they have a halfway-decent <a href="https://github.com/bigskysoftware/htmx/blob/master/test/index.html" rel="noopener" target="_blank">test suite</a>, and given the state of the codebase, they better damned well!

## <a href="#antiquated-technology" class="zola-anchor" aria-label="Anchor link for: antiquated-technology">Antiquated Technology</a>

OK, that covers the major (but by no means all!) issues with the htmx codebase itself. Let’s move on to more general issues with htmx.

The first glaring issue is something the authors, again, brag about: it uses <a href="https://hypermedia.systems" rel="noopener" target="_blank">hypermedia</a>. Really this is just a pretentious way of saying “it uses HTML”, I don’t know why they insist on using a different and confusing term for it, but whatever.

OK, well, if you haven’t noticed, HTML is over thirty years old now. It’s ancient. And, moreover, we have lots of experience with the approach these guys are recommending. It’s not like htmx is doing anything new: <a href="https://intercoolerjs.org" rel="noopener" target="_blank">intercooler.js</a>, <a href="https://github.com/defunkt/jquery-pjax" rel="noopener" target="_blank">PJax</a> and <a href="https://unpoly.com/" rel="noopener" target="_blank">Unpoly</a> (way better than htmx, btw) have been around literally *forever*.

Even before that, we had <a href="https://api.jquery.com/load/#load-url-data-complete" rel="noopener" target="_blank"><code>jquery.load()</code></a>.

Look at this jQuery code from 2008:

``` js
$( "#result" ).load( "ajax/test.html" );
```

And now look at the super innovative stuff the htmx folks give us:

``` html
<button hx-get="/ajax/test.html"
        hx-target="#result">
    Load
</button>
```

Wow. Amazing.

It would be funny if it weren’t so infuriating.

## <a href="#no-components" class="zola-anchor" aria-label="Anchor link for: no-components">No Components</a>

The next reason to consider not using htmx is that there aren’t any components available for it. If you go with react you get things like <a href="https://mui.com/" rel="noopener" target="_blank">MUI</a>, <a href="https://nextui.org/" rel="noopener" target="_blank">NextUI</a> & <a href="https://chakra-ui.com/" rel="noopener" target="_blank">Chakra</a>.

With htmx, you get… nothing. You have to figure out what components you want to use and then how to integrate them with htmx using events and so forth.

Do you really want to spend time figuring out how things like <a href="https://lit.dev/" rel="noopener" target="_blank">lit</a> work and then *also* how to integrate them with htmx? That doesn’t make any sense. Far better to go with a front end library with integrated, off-the-shelf components you can just use without any fuss.

## <a href="#no-front-end-back-end-split" class="zola-anchor" aria-label="Anchor link for: no-front-end-back-end-split">No Front-End/Back-End Split</a>

Another major reason to avoid htmx is that it eliminates the split between the Back-End & Front-End teams. They even have a page with a team [bragging about it as a virtue](https://htmx.org/essays/a-real-world-react-to-htmx-port/) when their company (foolishly) moved from React to htmx.

The Front-End/Back-End split has been extremely successful for many companies, allowing the Front-End engineers to focus on building a good user experience, and the Back-End engineers to focus on getting the data access layer right.

Yes, there are at times some difficulties in coordinating between the two teams, with Back-End engineers complaining that Front-End engineers change their requirements too frequently and Front-End engineers complaining that Back-End engineers move too slowly. But we have technologies like <a href="https://graphql.org/" rel="noopener" target="_blank">GraphQL</a> and <a href="https://react.dev/reference/react/use-server" rel="noopener" target="_blank">RSC</a> to help with that, it’s a solved problem at this point within the existing <a href="https://macwright.com/2020/10/28/if-not-spas.html" rel="noopener" target="_blank">standard web application model</a>.

The Front-End/Back-End split has proven a very good organizational model for companies, particularly as they scale their development team, and abandoning it for “Full Stack” (so called) development is risky and, frankly, foolish.

## <a href="#back-end-engineers-make-garbage-uis" class="zola-anchor" aria-label="Anchor link for: back-end-engineers-make-garbage-uis">Back-End Engineers Make Garbage UIs</a>

Leaving aside if the Front-End/Back-End split is good or not, we can definitively say that Back-End engineers make garbage user interfaces.

Just look at <a href="https://htmx.org" rel="noopener" target="_blank">the htmx website</a>. You’ve got inline styles, tables, a bunch of image tags didn’t have `alt` descriptions forever. Just a dogs breakfast of bad HTML, from people who are trying to tell us to use HTML!

You should leave your user interfaces in the hands of people who understand how to properly build them, and those people are, today, mostly Front-End SPA developers.

## <a href="#xss-vulnerabilities" class="zola-anchor" aria-label="Anchor link for: xss-vulnerabilities">XSS Vulnerabilities</a>

Getting back to a more technical reason why you shouldn’t use htmx, it opens you up to a class of security issues called <a href="https://owasp.org/www-community/attacks/xss/" rel="noopener" target="_blank">Cross-Site Scripting attacks</a>, abbreviated “XSS”.

The problem here is fundamental to the design of htmx: it enables & and even encourages you to put *behavior* in your markup. Once again we see a clear violation of <a href="https://en.wikipedia.org/wiki/Separation_of_concerns" rel="noopener" target="_blank">Separation of Concerns</a>. We’ve known for ages in web development that you should separate your markup, styling and behavior into HTML, CSS & JavaScript files respectively.

By violating this obvious and well known truth htmx makes you vulnerable to other people injecting behavior into your web application if you don’t <a href="https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html" rel="noopener" target="_blank">sanitize your HTML</a> properly.

Sometimes the htmx author will make a smart-alec comment like “Well, how do you feel about the <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a#href" rel="noopener" target="_blank">href</a> attribute?”, but that’s different, obviously.

## <a href="#no-jobs" class="zola-anchor" aria-label="Anchor link for: no-jobs">No Jobs</a>

Another practical reason not to use htmx is that there are, rounding off, zero htmx jobs.

I just did a search for htmx jobs on indeed and found a grand total of two: one at Microsoft and one at Oak Ridge National Laboratory.

A search for “react”, on the other hand, gives 13,758 jobs.

Seriously, developer, which of these two technologies do you want to hitch your career to?

## <a href="#no-one-to-hire" class="zola-anchor" aria-label="Anchor link for: no-one-to-hire">No One To Hire</a>

The flip side of the above problem is that, if you are a company, there are, rounding off, zero htmx developers.

Everyone goes to bootcamps and learns React. If you want to have a large potential employee pool (maybe your company has high turnover for some reason, maybe you want to keep employee wages down, maybe a small team of full stack engineers would get in the way of your kingdom building) it makes a ton more sense to go with The Big Dog in front end development.

Today, that dog is React.

## <a href="#duplicating-or-more-your-apis" class="zola-anchor" aria-label="Anchor link for: duplicating-or-more-your-apis">Duplicating (Or More!) Your APIs</a>

Getting back to the more technical side of things, if you adopt htmx and you want to *also* have a mobile app or an API for 3rd parties to use, you will need to create that API entirely separately from your web application’s end points.

Here, again, we find that, incredibly, the [htmx people brag about this fact](https://htmx.org/essays/splitting-your-apis/), completely ignoring the duplication of work involved here.

It makes far more sense to have a single API maintained by a single, Back-End team that can flexibly serve all your needs.

This is obvious and, frankly, not worth even arguing about.

## <a href="#it-won-t-scale" class="zola-anchor" aria-label="Anchor link for: it-won-t-scale">It Won’t Scale</a>

Another technical issue with htmx is that it just won’t scale. It may work for small applications, but as applications get larger the htmx model breaks down and becomes a mess. The component model of React and other front-end tools keeps everything compartmentalized and testable. This makes it much easier to keep large codebases clean.

As an example, consider <a href="https://github.com/" rel="noopener" target="_blank">GitHub</a>, which started out using technology a lot like htmx. It has recently started adopting React and is now much more stable than it was previously. They would have been better off if they had just started with React and built the whole thing in a modern, component-based way, but at least they are making the right move now. Better late than never.

## <a href="#the-creator-is-unhinged" class="zola-anchor" aria-label="Anchor link for: the-creator-is-unhinged">The Creator Is Unhinged</a>

Finally, and maybe the most important reason not to use htmx: the creator is obviously unhinged.

Just look at the <a href="https://twitter.com/htmx_org" rel="noopener" target="_blank">twitter feed</a>: unprofessional, childish, intentionally provocative.

Or consider the fact that he posts [essays he](https://htmx.org/essays/is-htmx-another-javascript-framework/)) [doesn’t agree with](https://htmx.org/essays/htmx-sucks/) to his own site.

The essays tab <a href="https://htmx.org/essays/#memes" rel="noopener" target="_blank">has a section for memes</a>, most of which are cringe-worthy and all of which have no business being on a website of a front end library that expects to be taken seriously.

Apparently he allows <a href="https://htmx.ceo" rel="noopener" target="_blank">anyone to be the CEO of htmx</a> and make one of those super-cringey job announcements on LinkedIn.

Wanton buffoonery.

When you pick a front-end library you are, to an extent, picking the author of that library as a co-worker. Do you really want to work this guy? I certainly don’t.

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

I hope this has convinced you that choosing htmx & hypermedia for your web application is an <a href="https://www.reddit.com/r/ProgrammerHumor/comments/zmyug8/edsger_dijkstra_math_and_memes/" rel="noopener" target="_blank">exceptionally bad idea</a> that could only have originated in <a href="https://bigsky.software" rel="noopener" target="_blank">Montana</a>. Don’t listen to the fanboys and fangirls with their “It’s so over”, “We’re so back” nonsense, CEO profiles and childish memes.

Software, and especially Front-End software is serious business and needs to be treated with the same gravity as things like law & politics, two other extremely serious and productive activities. We should support libraries that focus on innovation & sophistication, not broken, backwards-looking libraries whose creator spends most of his time posting ridiculous things on twitter.

It’s just common sense: htmx sucks.

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

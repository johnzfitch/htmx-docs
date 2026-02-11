# vendoring__b8ede60b

- Source URL: https://htmx.org/essays/vendoring/
- Source file: `fetch/htmx_org_b8ede60b.html`
- Hash: `b8ede60b`
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

# Vendoring

Carson Gross

January 27, 2025

“Vendoring” software is a technique where you copy the source of another project directly into your own project.

It is an old technique that has been used for time immemorial in software development, but the term “vendoring” to describe it appears to have originated in the <a href="https://stackoverflow.com/posts/72115282/revisions" rel="noopener" target="_blank">ruby community</a>.

Vendoring can be and is still used today. You can vendor htmx, for example, quite easily.

Assuming you have a `/js/vendor` directory in your project, you can just download the source into your own project like so:

``` bash
curl https://raw.githubusercontent.com/bigskysoftware/htmx/refs/tags/v2.0.4/dist/htmx.min.js > /js/vendor/htmx-2.0.4.min.js
```

You then include the library in your `head` tag:

``` html
<script src="/js/vendor/htmx-2.0.4.min.js"></script>
```

And then you check the htmx source into your own source control repository. (I would even recommend considering using the <a href="https://raw.githubusercontent.com/bigskysoftware/htmx/refs/tags/v2.0.4/dist/htmx.js" rel="noopener" target="_blank">non-minimized version</a>, so you can better understand and debug the code.)

That’s it, that’s vendoring.

## <a href="#vendoring-strengths" class="zola-anchor" aria-label="Anchor link for: vendoring-strengths">Vendoring Strengths</a>

OK, great, so what are some strengths of vendoring libraries like this?

It turns out there are quite a few:

- Your entire project is checked in to your source repository, so no external systems beyond your source control need to be involved when building it
- Vendoring dramatically improves dependency *visibility*: you can *see* all the code your project depends on, so you won’t have a situation like we have in htmx, where we feel like we only have a few development dependencies, when in fact we may have a lot
- This also means if you have a good debugger, you can step into the library code as easily as any other code. You can also read it, learn from it and even modify it if necessary.
- From a security perspective, you aren’t relying on opaque code. Even if your package manager has an integrity hash system, the actual code may be opaque to you. With vendored code it is checked in and can be analysed automatically or by a security team.
- Personally, it has always seemed crazy to me that people will often resolve dependencies at deployment time, right when your software is about to go out the door. If that bothers you, like it does me, vendoring puts a stop to it.

On the other hand, vendoring also has one massive drawback: there typically isn’t a good way to deal with what is called the <a href="https://en.wikipedia.org/wiki/Transitive_closure" rel="noopener" target="_blank">transitive dependency</a> problem.

If htmx had sub-dependencies, that is, other libraries that it depended on, then to vendor it properly you would have to start vendoring all those libraries as well. And if those dependencies had further dependencies, you’d need to install them as well… And on and on.

Worse, two dependencies might depend on the same library, and you’ll need to make sure you get the <a href="https://en.wikipedia.org/wiki/Dependency_hell" rel="noopener" target="_blank">correct version</a> of that library for everything to work.

This can get pretty difficult to deal with, but I want to make a paradoxical claim that this weakness (and, again, it’s a real one) is actually a strength in some way:

Because dealing with large numbers of dependencies is difficult, vendoring encourages a culture of *independence*.

You get more of what you make easy, and if you make dependencies easy, you get more of them. Making dependencies, *especially* transitive dependencies, more difficult would make them less common.

And, as we will see in a bit, maybe fewer dependencies isn’t such a bad thing.

## <a href="#dependency-managers" class="zola-anchor" aria-label="Anchor link for: dependency-managers">Dependency Managers</a>

That’s great and all, but there are <a href="https://gist.github.com/datagrok/8577287" rel="noopener" target="_blank">significant</a> <a href="https://web.archive.org/web/20180216205752/http://blog.bithound.io/why-we-stopped-vendoring-our-npm-dependencies/" rel="noopener" target="_blank">drawbacks</a> to vendoring, particular the transitive dependency problem.

Modern software engineering uses dependency managers to deal with the dependencies of software projects. These tools allow you to specify your projects dependencies, typically via some sort of file. They then they will install those dependencies and resolve and manage all the other dependencies that are necessary for those dependencies to work.

One of the most widely used package managers is NPM: The <a href="https://www.npmjs.com/" rel="noopener" target="_blank">Node Package Manager</a>. Despite having no runtime dependencies, htmx uses NPM to specify 16 development dependencies. Development dependencies are dependencies that are necessary for development of htmx, but not for running it. You can see the dependencies at the bottom of the NPM <a href="https://github.com/bigskysoftware/htmx/blob/master/package.json" rel="noopener" target="_blank"><code>package.json</code></a> file for the project.

Dependency managers are a crucial part of modern software development and many developers today couldn’t imagine writing software without them.

### <a href="#the-trouble-with-dependency-managers" class="zola-anchor" aria-label="Anchor link for: the-trouble-with-dependency-managers">The Trouble with Dependency Managers</a>

So dependency managers solve the transitive dependency problem that vendoring has. But, as with everything in software engineering, there are tradeoffs associated with them. To see some of these tradeoffs, let’s take a look at the <a href="https://github.com/bigskysoftware/htmx/blob/master/package-lock.json" rel="noopener" target="_blank"><code>package-lock.json</code></a> file in htmx.

NPM generates a `package-lock.json` file that contains the resolved transitive closure of dependencies for a project, with the concrete versions of those dependencies. This helps ensure that the same dependencies are used unless a user explicitly updates them.

If you take a look at the `package-lock.json` for htmx, you will find that the original 13 development dependencies have ballooned into a total of 411 dependencies when all is said and done.

htmx, it turns out, relies on a huge number of packages, despite priding itself on being a relatively lean. In fact, the `node_modules` folder in htmx is a whopping 110 megabytes!

But, beyond this bloat there are deeper problems lurking in that mass of dependencies.

While writing this essay I found that htmx apparently depends on the <a href="https://www.npmjs.com/package/array.prototype.findlastindex" rel="noopener" target="_blank"><code>array.prototype.findlastindex</code></a>, a <a href="https://en.wikipedia.org/wiki/Polyfill_(programming)" rel="noopener" target="_blank">polyfill</a> for a JavaScript feature introduced in <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLastIndex" rel="noopener" target="_blank">2022</a>.

Now, <a href="https://v1.htmx.org/" rel="noopener" target="_blank">htmx 1.x</a> is IE compatible, and I don’t *want* polyfills for *anything*: I want to write code that will work in IE without any additional library support. And yet a polyfill has snuck in via a chain of dependencies (htmx does not directly rely on it) that introduces a dangerous polyfill that would let me write code that would break in IE, as well as other older browsers.

This polyfill may or may not be available when I run the htmx <a href="https://htmx.org/test/" rel="noopener" target="_blank">test suite</a> (it’s hard to tell) but that’s the point: some dangerous code has snuck into my project without me even knowing it, due to the number and complexity of the (development) dependencies it has.

This demonstrates significant *cultural* problem with dependency managers:

They tend to foster a culture of, well, dependency.

A spectacular example of this was the infamous <a href="https://en.wikipedia.org/wiki/Npm_left-pad_incident" rel="noopener" target="_blank">left-pad incident</a>, in which an engineer took down a widely used package and broke the build at companies like Facebook, PayPal, Netflix, etc.

That was a relatively innocuous, although splashy, issue, but a more serious concern is <a href="https://en.wikipedia.org/wiki/Supply_chain_attack" rel="noopener" target="_blank">supply chain attacks</a>, where a hostile entity is able to compromise a company via code injected unwittingly via dependencies.

The larger our dependency graph gets, the worse these problems get.

## <a href="#dependencies-reconsidered" class="zola-anchor" aria-label="Anchor link for: dependencies-reconsidered">Dependencies Reconsidered</a>

I’m not the only person thinking about our culture of dependency. Here’s what some other, smarter folks have to say about it:

<a href="https://x.com/mitsuhiko" rel="noopener" target="_blank">Armin Ronacher</a>, creator of <a href="https://flask.palletsprojects.com/en/stable/" rel="noopener" target="_blank">flask</a> recently said this on <a href="https://x.com/mitsuhiko/status/1882739157120041156" rel="noopener" target="_blank">the ol’twits</a>:

> The more I build software, the more I despise dependencies. I greatly prefer people copy/pasting stuff into their own code bases or re-implement it. Unfortunately the vibe of the time does not embrace that idea much. I need that vibe shift.

He also wrote a great blog post about his <a href="https://lucumr.pocoo.org/2025/1/24/build-it-yourself/" rel="noopener" target="_blank">experience with package management</a> in the Rust ecosystem:

> It’s time to have a new perspective: we should give kudos to engineers who write a small function themselves instead of hooking in a transitive web of crates. We should be suspicious of big crate graphs. Celebrated are the minimal dependencies, the humble function that just quietly does the job, the code that doesn’t need to be touched for years because it was done right once.

Please go read it in full.

Back in 2021, <a href="https://macwright.com" rel="noopener" target="_blank">Tom Macwright</a> wrote this in <a href="https://macwright.com/2021/03/11/vendor-by-default" rel="noopener" target="_blank">Vendor by default</a>

> But one thing that I do think is sort of unusual is: I’m vendoring a lot of stuff.
>
> Vendoring, in the programming sense, means “copying the source code of another project into your project.” It’s in contrast to the practice of using dependencies, which would be adding another project’s name to your package.json file and having npm or yarn download and link it up for you.

I highly recommend reading his take on vendoring as well.

## <a href="#software-designed-to-be-vendored" class="zola-anchor" aria-label="Anchor link for: software-designed-to-be-vendored">Software Designed To Be Vendored</a>

Some good news, if you are an open source developer and like the idea of vendoring, is that there is a simple way to make your software vendor-friendly: remove as many dependencies as you can.

<a href="https://daisyui.com/" rel="noopener" target="_blank">DaisyUI</a>, for example, has been in the process of <a href="https://x.com/Saadeghi/status/1882556881253826941" rel="noopener" target="_blank">removing their dependencies</a>, going from 100 dependencies in version 3 to 0 in version 5.

There is also a set htmx-adjacent projects that are taking vendoring seriously:

- <a href="https://github.com/gnat/surreal" rel="noopener" target="_blank">Surreal</a> - a lightweight jQuery alternative
- <a href="https://github.com/kgscialdone/facet" rel="noopener" target="_blank">Facet</a> - an HTML-oriented Web Component library
- <a href="https://github.com/bigskysoftware/fixi" rel="noopener" target="_blank">fixi</a> - a minimal htmx alternative

None of these JavaScript projects are available in NPM, and all of them <a href="https://github.com/gnat/surreal#-install" rel="noopener" target="_blank">recommend</a> <a href="https://github.com/kgscialdone/facet#installation" rel="noopener" target="_blank">vendoring</a> the <a href="https://github.com/bigskysoftware/fixi#installing" rel="noopener" target="_blank">software</a> into your own project as the primary installation mechanism.

## <a href="#vendor-first-dependency-managers" class="zola-anchor" aria-label="Anchor link for: vendor-first-dependency-managers">Vendor First Dependency Managers?</a>

The last thing I want to briefly mention is a technology that combines both vendoring and dependency management: vendor-first dependency managers. I have never worked with one before, but I have been pointed to <a href="https://github.com/fosskers/vend" rel="noopener" target="_blank">vend</a>, a common lisp vendor oriented package manager (with a great README), as well as <a href="https://go.dev/ref/mod#vendoring" rel="noopener" target="_blank">go’s vendoring option</a>.

In writing this essay, I also came across <a href="https://github.com/sourcemeta/vendorpull" rel="noopener" target="_blank">vendorpull</a> and <a href="https://github.com/brettlangdon/git-vendor" rel="noopener" target="_blank">git-vendor</a>, both of which are small but interesting projects.

These all look like excellent tools, and it seems to me that there is an opportunity for some of them (and tools like them) to add additional functionality to address the traditional weaknesses of vendoring, for example:

- Managing transitive dependencies, if any
- Relatively easy updates of those dependencies
- Managing local modifications made to dependencies (and maybe help manage contributing them upstream?)

With these additional features I wonder if vendor-first dependency managers could compete with “normal” dependency managers in modern software development, perhaps combining some of the benefits of both approaches.

Regardless, I hope that this essay has helped you think a bit more about dependencies and perhaps planted the idea that maybe your software could be a little less, well, dependent on dependencies.

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

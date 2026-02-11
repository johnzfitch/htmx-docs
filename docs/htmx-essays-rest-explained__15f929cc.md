# rest-explained__15f929cc

- Source URL: https://htmx.org/essays/rest-explained/
- Source file: `fetch/htmx_org_15f929cc.html`
- Hash: `15f929cc`
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

# REST - Explained For Beginners

Carson Gross

July 13, 2021

There is no topic that generates more confusion in web development than the idea of Representational State Transfer, known as REST. This term comes from <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm" rel="noopener" target="_blank">Chapter 5</a> of <a href="https://en.wikipedia.org/wiki/Roy_Fielding" rel="noopener" target="_blank">Roy Fielding’s</a> PhD thesis at <a href="https://www.uci.edu/" rel="noopener" target="_blank">U.C. Irvine</a>.

In this essay we will go through this Chapter and summarize the important concepts for non-academic web developers. The thesis is dense and involves a lot of technical jargon that isn’t relevant to people who aren’t academics interested in formal PhD thesis writing.

By the end of this essay you should have a better handle on REST, and the concept of a <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_5" rel="noopener" target="_blank">Uniform Interface</a> in particular.

## <a href="#overview" class="zola-anchor" aria-label="Anchor link for: overview">Overview</a>

The first thing to understand about REST is that *it is a description of the original web*. Fielding describes REST as an “architectural style for distributed hypermedia systems”, which sounds fancy but just means the web we all know and love: clicking on hyperlinks, submitting forms, looking at images, reading paragraphs and all that jazz.

It was *NOT* created as a description of a particular approach for JSON APIs, although that is the context that most people hear about REST today in. Fielding was describing the early web and, in particular, how it was different from earlier client/server architectures.

## <a href="#section-5-1-deriving-rest" class="zola-anchor" aria-label="Anchor link for: section-5-1-deriving-rest">Section 5.1 Deriving Rest</a>

In <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1" rel="noopener" target="_blank">section 5.1</a>, unfortunately for non-academics, Fielding adopts the technique of deriving REST from first principles. Here I will summarize each section and clarify and add context in the important ones.

### <a href="#client-server" class="zola-anchor" aria-label="Anchor link for: client-server"></a><a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_2" rel="noopener" target="_blank">Client Server</a>

REST is, of course, a client-server architecture, since the web is a client (browser) server (http server) system.

### <a href="#stateless" class="zola-anchor" aria-label="Anchor link for: stateless"></a><a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_3" rel="noopener" target="_blank">Stateless</a>

The web, most developers know, is intended to be stateless. All requests should encapsulate all information necessary to understand that request. For example, there should not be a long running transaction implicitly associated with a series of requests, as you might have with a SQL database session.

### <a href="#cache" class="zola-anchor" aria-label="Anchor link for: cache"></a><a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_4" rel="noopener" target="_blank">Cache</a>

HTTP, you probably know, has a <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching" rel="noopener" target="_blank">caching mechanism</a> built into it. You don’t need to know the details of this now, but may explore it later.

### <a href="#uniform-interface" class="zola-anchor" aria-label="Anchor link for: uniform-interface"></a><a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_5" rel="noopener" target="_blank">Uniform Interface</a>

This section, in my mind, is the crux of the REST architecture and, unfortunately, is very brief, so we will spend some time expanding on it, rather that just summarizing it. The chapter begins:

> The central feature that distinguishes the REST architectural style from other network-based styles is its emphasis on a uniform interface between components

To clarify the discussion around exactly what the uniform interface is, let’s consider some simple HTML that I hope everyone reading this will understand:

``` html
<html>
  <body>
  <section>
    <p>
      Name: Joe Blow
    </p>
    <p>
      Email: joe@blow.com
    </p>
    <p>
      <a href="/contacts/42/edit">Edit</a>
      <a href="/contacts/42/email">Email</a>
      <a href="/contacts/42/archive">Archive</a>
    </p>
  </section>
</body>
</html>
```

Here we have a basic bit of html, with some divs, a bit of information and then some anchor tags to perform various operations on a contact. Nothing fancy. Again, for the discussion, imagine this content could be found at <a href="http://example.com/contacts/42" rel="noopener" target="_blank">http://example.com/contacts/42</a>.

Back to the dissertation:

> REST is defined by four interface constraints: identification of resources; manipulation of resources through representations; self-descriptive messages; and, hypermedia as the engine of application state.

Let’s go through each of these in turn.

#### <a href="#identification-of-resources" class="zola-anchor" aria-label="Anchor link for: identification-of-resources">Identification of Resources</a>

The first aspect of Rest is the idea of *resources* that are found somewhere via… well, <a href="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL" rel="noopener" target="_blank">Universal Resource Locators</a>, or URLs. Note that the HTML contains additional URLs for the actions that you can perform on this resource (`contacts/42`), following the conventional hierarchical arrangement of URL paths.

#### <a href="#manipulation-of-resources-through-representations" class="zola-anchor" aria-label="Anchor link for: manipulation-of-resources-through-representations">Manipulation of Resources Through Representations</a>

This sounds fancy, but it just means that you can update and mutate the resource (that is, the contact) through various representations (that is HTML pages) rather than having to issues, say, SQL, to modify it.

#### <a href="#self-descriptive-messages" class="zola-anchor" aria-label="Anchor link for: self-descriptive-messages">Self Descriptive Messages</a>

This is a key concept of REST. Note that the browser, which is the client in this client-server setup, *knows nothing about contacts*. And yet it is able to render a “Contact UI” simply by rendering the HTML returned by the server. The message itself is entirely self-describing, containing all information the client needs about both the data and the possible operations on that data (in the form of links.)

Now, contrast this with a JSON representation of the same data:

``` json
    {
      "name" : "Joe Blow",
      "email" : "joe@example.com"
    }
```

Obviously this is smaller, but a client working with this data must decide two crucial things:

- How to render it
- What actions are available to mutate it

The first part is typically done with a client side template. The second is typically done by reading the documentation for the API and encoding the interactions with the server directly in the client.

This is the crux of the difference between REST-ful systems and traditional client-server system: in the REST-ful system the client (i.e. the browser) doesn’t know anything about the resource, it just knows how to render a hypermedia. In the client-server system, knowledge about the resource is embedded in the client.

There are pros and cons to both approaches, but the REST-ful approach, in the form of the early web, proved to be extremely reliable and flexible. It hides a tremendous amount of knowledge about the resources behind this *uniform interface* of HTML, so the client doesn’t have the opportunity to break in the way the thick-client does.

Now, you may have noticed that, in the last decade, web development has trended away from the REST-ful architecture and towards a more traditional client-server setup, using JSON APIs. And you may have noticed a lot more discussion and issues around versioning APIs, providing more general query functionality and so on. This is not accidental: we are losing the flexibility of the REST-ful model as we turn the browser into a VM for hosting thick client applications.

#### <a href="#hypermedia-as-the-engine-of-application-state-hateoas" class="zola-anchor" aria-label="Anchor link for: hypermedia-as-the-engine-of-application-state-hateoas">Hypermedia As The Engine of Application State (HATEOAS)</a>

This last concept dovetails with the previous one: clients transition application state by interacting with URLs found in the hypermedia itself (via forms and links). So, in the HTML example above, the ability to edit, email and archive the contact all encoded as anchors in the HTML. If one of those actions was not available, or a new one became available, it would come down in a new bit of HTML, after a page refresh.

This is in contrast with a thick client approach where, for example, a local store may be sync’d asynchronously with a back end and, thus, the HTML is not acting as the engine of application state, but rather as a (somewhat janky) UI description language.

Somewhat hilariously, the <a href="https://en.wikipedia.org/wiki/HATEOAS" rel="noopener" target="_blank">Wikipedia article on HATEOAS</a> uses JSON, which is not a natural hypermedia. You can layer some REST-ful behavior on top of JSON if you want, but it has rarely been useful in the real world, and HATEOAS is usually ignored in JSON APIs. This makes sense because JSON APIs are useful mainly for the traditional client-server architecture and aren’t particularly amenable to the REST-ful style.

#### <a href="#uniform-interface-summary" class="zola-anchor" aria-label="Anchor link for: uniform-interface-summary">Uniform Interface Summary</a>

That’s the crux of REST and really the crux of this essay. You can read on for a bit more detail and analysis of Fieldings paper, but the core take away here is that there is a sharp distinction between a REST-ful hypermedia architecture and traditional client-server architectures, and that distinction revolves mainly around the concept of a uniform interface, and the self-describing nature of them in particular.

Again, don’t get bogged down in the jargon here, just think about this HTML and what a miracle of flexibility and ingenuity it is:

``` html
<html>
  <body>
  <div>
    <div>
      Name: Joe Blow
    </div>
    <div>
      Email: joe@blow.com
    </div>
    <div>
      <a href="/contacts/42/edit">Edit</a>
      <a href="/contacts/42/email">Email</a>
      <a href="/contacts/42/archive">Archive</a>
    </div>
  </div>
</body>
</html>
```

### <a href="#layered-system" class="zola-anchor" aria-label="Anchor link for: layered-system"></a><a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_6" rel="noopener" target="_blank">Layered System</a>

You don’t need to know much about this, except that <a href="https://en.wikipedia.org/wiki/Content_delivery_network" rel="noopener" target="_blank">CDNs exist</a>, and you should use them.

### <a href="#code-on-demand" class="zola-anchor" aria-label="Anchor link for: code-on-demand"></a><a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_7" rel="noopener" target="_blank">Code-On-Demand</a>

Again, you don’t need to know much about this, except that <a href="https://developer.mozilla.org/en-US/docs/Web/javascript" rel="noopener" target="_blank">Javascript exists</a>, and that it’s the only part that’s optional.

## <a href="#section-5-2-rest-architectural-elements" class="zola-anchor" aria-label="Anchor link for: section-5-2-rest-architectural-elements">Section 5.2 -</a> <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2" rel="noopener" target="_blank">REST Architectural Elements</a>

I won’t drill in as deeply on this section as we did others because it gets pretty technical and, frankly, is a bit boring and repetitive (as one might expect from a dissertation.) The two big ideas in this section are Resources and Representations.

## <a href="#section-5-2-1-resources-and-resource-identifiers" class="zola-anchor" aria-label="Anchor link for: section-5-2-1-resources-and-resource-identifiers">Section 5.2.1 -</a> <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2" rel="noopener" target="_blank">Resources and Resource Identifiers</a>

From the paper:

> The key abstraction of information in REST is a resource. Any information that can be named can be a resource: a document or image, a temporal service (e.g. “today’s weather in Los Angeles”), a collection of other resources, a non-virtual object (e.g. a person), and so on.

Practically, a resource is anything that can be addressed by a URL. What happens when you access a URL?

Well, you get back a *representation* of that resource, in the form of an HTTP response that may contain HTML, directives and so forth.

## <a href="#section-5-2-1-representations" class="zola-anchor" aria-label="Anchor link for: section-5-2-1-representations">Section 5.2.1 -</a> <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_2" rel="noopener" target="_blank">Representations</a>

I don’t find a lot of practical use in this section. There is some stuff on control data, media types and so forth, which are all worth learning about eventually when needed, but aren’t a commonly used aspect of web development.

The remaining sections 5.2 similarly do not offer much to the generalist.

## <a href="#section-5-3-rest-architectural-views" class="zola-anchor" aria-label="Anchor link for: section-5-3-rest-architectural-views">Section 5.3 -</a> <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_3" rel="noopener" target="_blank">REST Architectural Views</a>

In what is becoming a pattern, I again do not feel there is a lot of useful new information for the average web developer in this section, with one big exception: it lays out the benefits of REST.

From the paper:

> REST’s client-server separation of concerns simplifies component implementation, reduces the complexity of connector semantics, improves the effectiveness of performance tuning, and increases the scalability of pure server components. Layered system constraints allow intermediaries–proxies, gateways, and firewalls–to be introduced at various points in the communication without changing the interfaces between components, thus allowing them to assist in communication translation or improve performance via large-scale, shared caching. REST enables intermediate processing by constraining messages to be self-descriptive: interaction is stateless between requests, standard methods and media types are used to indicate semantics and exchange information, and responses explicitly indicate cacheability.

This is all very true, and is why the web has been so successful and will continue to be successful.

## <a href="#sections-5-4-5-5-related-work-summary" class="zola-anchor" aria-label="Anchor link for: sections-5-4-5-5-related-work-summary"></a><a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_4" rel="noopener" target="_blank">Sections 5.4</a> & <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_5" rel="noopener" target="_blank">5.5</a> - Related Work & Summary

These brief sections are not relevant to non-academics interested in REST.

## <a href="#summary" class="zola-anchor" aria-label="Anchor link for: summary">Summary</a>

So there you have it, a brief tour of Chapter 5 of Roy Fielding’s dissertation, which gave us the term REST. I have focused in on the areas that I think are most important for web developers to understand and tried to convey how REST describes the original web model. The uniform interface concept is, in my opinion, the most important and interesting aspect of REST, and is useful for web developers to understand as it is primarily responsible for the benefits described above.

Finally, I hope you can see how inappropriate REST is for describing most JSON APIs in use today.

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

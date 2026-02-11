# two-approaches-to-decoupling__53955897

- Source URL: https://htmx.org/essays/two-approaches-to-decoupling/
- Source file: `fetch/htmx_org_53955897.html`
- Hash: `53955897`
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

# Two Approaches To Decoupling

Carson Gross

May 01, 2022

> The central feature that distinguishes the REST architectural style from other network-based styles is its emphasis on a uniform interface between components. By applying the software engineering principle of generality to the component interface, the overall system architecture is simplified and the visibility of interactions is improved. Implementations are decoupled from the services they provide, which encourages independent evolvability.

*-Roy Fielding, <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_5" rel="noopener" target="_blank">https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_5</a>*

In this essay we will look at two different types of decoupling in the context of web applications:

- Decoupling at the *application level* via a generic JSON Data API
- Decoupling at the *network architecture level* via a hypermedia API

We will see that, at the application level, a hypermedia API tightly couples your front-end and back-end. Despite this fact, surprisingly, the hypermedia API is in fact more resilient in the face of change.

## <a href="#coupling" class="zola-anchor" aria-label="Anchor link for: coupling">Coupling</a>

<a href="https://en.wikipedia.org/wiki/Coupling_%28computer_programming%29" rel="noopener" target="_blank">Coupling</a> is a property of a software system in which two modules or aspects of the system have a high degree of interdependence. *Decoupling* software is the act of reducing this interdependence between unrelated modules so that they can evolve independently of one another.

The concept of coupling and decoupling is closely (and inversely) related to <a href="https://en.wikipedia.org/wiki/Cohesion_(computer_science)" rel="noopener" target="_blank">cohesion</a>. Highly cohesive software has related logic within a module or conceptual boundary, rather than spread out throughout a codebase. (A related concept is our own idea of [Locality of Behavior](/essays/locality-of-behaviour/))

Broadly, experienced developers strive for decoupled and cohesive systems.

## <a href="#json-data-apis-application-level-decoupling" class="zola-anchor" aria-label="Anchor link for: json-data-apis-application-level-decoupling">JSON Data APIs - Application Level Decoupling</a>

A common approach to building web applications today is to create a JSON Data API and then consume that JSON API using a JavaScript framework such as React. This application-level architectural decision decouples the front-end code from the back-end code, and allows the reuse of the JSON API in other contexts, such as a mobile applications, 3rd party client integrations, etc.

This is an *application-level* decoupling because the decision and implementation of the decoupling is done by the application developer themselves. The JSON API provides a “hard” interface between the two pieces of software.

Using my favorite example, consider a simple JSON for a bank that has a `GET` end point at `https://example.com/account/12345`. This API might return the following content:

``` json
HTTP/1.1 200 OK

{
    "account": {
        "account_number": 12345,
        "balance": {
            "currency": "usd",
            "value": -50.00
        },
        "status": "overdrawn"
    }
}
```

This Data API can be consumed by any client: a web application, a mobile client, a third party, etc. It is, therefore decoupled from any particular client.

### <a href="#decoupling-via-a-json-api-in-practice" class="zola-anchor" aria-label="Anchor link for: decoupling-via-a-json-api-in-practice">Decoupling Via A JSON API In Practice</a>

So far, so good. But how does this decoupling work out in practice?

In our essay <a href="https://htmx.org/essays/splitting-your-apis/" rel="noopener" target="_blank">Splitting Your Data &amp; Application APIs: Going Further</a> you will find the following quote:

> The worst part of my job these days is designing APIs for front-end developers. The conversation goes inevitably as:
>
> Dev – So, this screen has data element x,y,z… could you please create an API with the response format {x: , y:, z: }
>
> Me – Ok
>
> Jean-Jacques Dubray - <a href="https://www.infoq.com/articles/no-more-mvc-frameworks" rel="noopener" target="_blank">https://www.infoq.com/articles/no-more-mvc-frameworks</a>

This quote shows that, although we have driven coupling out with a pitchfork (or, in our case, with a JSON API) it has come back through requests for web application-specific JSON API end points. These sorts of requests end up recoupling the front-end and back-end code: the JSON API is no longer providing a generic JSON Data API, but rather a specific API for the front-end needs.

Worse, these front-end needs will often change frequently as your application evolves, necessitating the modification of your JSON API. What if other non-web application clients have come to depend on the original API?

This problem leads to the “versioning hell” that many JSON Data API developers face when supporting both web applications as well as other non-web application clients.

#### <a href="#a-solution-graphql" class="zola-anchor" aria-label="Anchor link for: a-solution-graphql">A Solution: GraphQL</a>

One potential solution to this problem is to introduce <a href="https://graphql.org/" rel="noopener" target="_blank">GraphQL</a>, which allows you to have a much more expressive JSON API. This means that you don’t need to change it as often when your API client’s needs change.

This is a reasonable approach for addressing the problem outlined above, but there are problems with it. The biggest issue that we see is security, as we outline this in <a href="https://intercoolerjs.org/2016/02/17/api-churn-vs-security.html" rel="noopener" target="_blank">The API Churn/Security Trade-off</a> essay.

Apparently facebook uses a <a href="https://twitter.com/AdamChainz/status/1392162996844212232" rel="noopener" target="_blank">whitelist</a> to deal with the security issues introduced by GraphQL, but many developers who are using GraphQL appear to not understand the security threats involved with it.

#### <a href="#another-solution-splitting-your-application-general-data-apis" class="zola-anchor" aria-label="Anchor link for: another-solution-splitting-your-application-general-data-apis">Another Solution: Splitting Your Application &amp; General Data APIs</a>

Another approach recommended by <a href="https://max.engineer/" rel="noopener" target="_blank">Max Chernyak</a> in his article <a href="https://max.engineer/server-informed-ui" rel="noopener" target="_blank">Don’t Build A General Purpose API To Power Your Own Front End</a>, is to build *two* JSON APIs:

- An application specific JSON API that can be modified as needed
- A general purpose JSON API that can be consumed by other clients such as mobile, etc.

This is a pragmatic solution to address what appears to be the *inherent* coupling between your web application’s front-end and the back-end code supporting it, and it doesn’t involve the security tradeoffs involved in a general GraphQL API.

## <a href="#hypermedia-network-architecture-decoupling" class="zola-anchor" aria-label="Anchor link for: hypermedia-network-architecture-decoupling">Hypermedia - Network Architecture Decoupling</a>

Now let us consider how a *hypermedia API* decouples software.

Consider a potential response to the same `GET` for `https://example.com/account/12345` that we saw above:

``` html
HTTP/1.1 200 OK

<html>
  <body>
    <div>Account number: 12345</div>
    <div>Balance: $100.00 USD</div>
    <div>Links:
        <a href="/accounts/12345/deposits">deposits</a>
        <a href="/accounts/12345/withdrawals">withdrawals</a>
        <a href="/accounts/12345/transfers">transfers</a>
        <a href="/accounts/12345/close-requests">close-requests</a>
    </div>
  <body>
</html>
```

(Yes, this is an API response. It just happens to be a hypermedia-formatted response, in this case HTML.)

Here we see that, at the application level, this response could not be more tightly coupled to the “front-end”. In fact, it *is* the front-end, in the sense that the API response specifies not only the data for the resource, but also provides layout information on how, exactly, to display this data to the user.

The response also contains *hypermedia controls*, in this case, links, that an end user can select from to continue navigating the hypermedia API that this <a href="https://htmx.org/essays/hypermedia-driven-applications/" rel="noopener" target="_blank">Hypermedia-Driven Application</a> provides.

So, where is the decoupling in this case?

### <a href="#rest-the-uniform-interface" class="zola-anchor" aria-label="Anchor link for: rest-the-uniform-interface">REST &amp; The Uniform Interface</a>

The decoupling in this case is occurring at a *lower level*. It is happening at the *network architecture* level, which is to say, at the system level. <a href="https://hypermedia.systems" rel="noopener" target="_blank">Hypermedia systems</a> are designed to decouple the hypermedia client (in the case of the web, the browser) from the hypermedia server.

This is accomplished primarily via the Uniform Interface constraint of REST and, in particular, by using Hypermedia As The Engine of Application State ([HATEOAS](/essays/hateoas)).

This style of decoupling allows tighter coupling at the higher application level (which we have seen may be an *inherent* coupling) while still retaining the benefits of decoupling for the overall system.

### <a href="#decoupling-via-hypermedia-in-practice" class="zola-anchor" aria-label="Anchor link for: decoupling-via-hypermedia-in-practice">Decoupling Via Hypermedia In Practice</a>

How does this sort of decoupling work in practice? Well, let’s say that we wish to remove the ability to transfer money from our bank to other banks as well as the ability to close accounts.

What does our hypermedia response for this `GET` request now look like?

``` html
HTTP/1.1 200 OK

<html>
  <body>
    <div>Account number: 12345</div>
    <div>Balance: $100.00 USD</div>
    <div>Links:
        <a href="/accounts/12345/deposits">deposits</a>
        <a href="/accounts/12345/withdrawals">withdrawals</a>
    </div>
  <body>
</html>
```

You can see that in this response, links for those two actions have been removed from the HTML. The browser simply render the new HTML to the user. To a rounding error, there are no clients sitting around using the *old* API. The API is encoded within and discovered through the hypermedia.

This means that we can dramatically change our API without breaking our clients.

This flexibility is the crux of the REST-ful network architecture and, in particular, of [HATEOAS](/essays/hateoas/).

As you can see, despite much tighter *application-level* coupling between our front-end and back-end, we actually have more flexibility due to the *network architecture* decoupling afforded to us by the Uniform Interface aspect of REST-ful <a href="https://hypermedia.systems" rel="noopener" target="_blank">hypermedia systems</a>.

### <a href="#but-that-s-a-terrible-data-api" class="zola-anchor" aria-label="Anchor link for: but-that-s-a-terrible-data-api">But That’s A Terrible (Data) API!</a>

Many people would object that, sure, this hypermedia API may be flexible for our web application, but it makes for a terrible general purpose API.

This is quite true. This hypermedia API is tuned for a specific web application. It would be cumbersome and error-prone to try to download this HTML, parse it and try to extract information from it. This hypermedia API only makes sense as part of a larger hypermedia system, being consumed by a proper hypermedia client.

This is exactly why we recommend creating a general purpose JSON API alongside your hypermedia API in <a href="https://htmx.org/essays/splitting-your-apis/" rel="noopener" target="_blank">Splitting Your Data &amp; Application APIs: Going Further</a>. You can take advantage of the flexibility of hypermedia for your own web application, while providing a general purpose JSON API for mobile applications, third party applications, etc.

(Although, we should mention, a <a href="https://hyperview.org" rel="noopener" target="_blank">hypermedia-based mobile application</a> might be a good choice too!)

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

In this essay we looked at two different types of decoupling:

- Application level decoupling via a JSON Data API
- Network-architecture decoupling via REST/HATEOAS in a hypermedia system

And we saw that, despite the tighter application-level coupling found in a hypermedia-based application, it is the hypermedia system that handles changes more gracefully.

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

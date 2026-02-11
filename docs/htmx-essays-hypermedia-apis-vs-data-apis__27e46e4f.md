# hypermedia-apis-vs-data-apis__27e46e4f

- Source URL: https://htmx.org/essays/hypermedia-apis-vs-data-apis/
- Source file: `fetch/htmx_org_27e46e4f.html`
- Hash: `27e46e4f`
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

# Hypermedia APIs vs. Data APIs

Carson Gross

July 17, 2021

A *hypermedia* API is an API that returns <a href="https://en.wikipedia.org/wiki/Hypermedia" rel="noopener" target="_blank">hypermedia</a>, typically HTML over HTTP. This style of API is distinguished from data APIs that do not return a hypermedia. The most familiar form of this latter style of API today is the ubiquitous JSON API.

These two different types of API have distinctly different design needs and, therefore, should use different design constraints and adopt different goals when being created.

Hypermedia APIs:

- Will be trivially <a href="https://en.wikipedia.org/wiki/Representational_state_transfer" rel="noopener" target="_blank">REST-ful</a>, since they are simply what <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm" rel="noopener" target="_blank">Roy Fielding was describing</a>.
- Should be driven by the needs of the underlying hypermedia application
- May change dramatically *without* versioning information, because hypermedia utilizes <a href="https://en.wikipedia.org/wiki/Representational_state_transfer#Uniform_interface" rel="noopener" target="_blank">self describing messages</a>
- Should be passed directly to humans, to maximize the flexibility of the system

Data APIs, on the other hand:

- Will not benefit dramatically from REST-fulness, beyond perhaps <a href="https://en.wikipedia.org/wiki/Richardson_Maturity_Model" rel="noopener" target="_blank">Level 2 of the Richardson Maturity Model</a>
- Should strive for both regularity and expressiveness due to the arbitrary data needs of consumers
- Should be versioned and should be very stable within a particular version of the API
- Should be consumed by code, processed and then potentially presented to a human

## <a href="#apis-today" class="zola-anchor" aria-label="Anchor link for: apis-today">APIs Today</a>

Today, APIs are typically thought of in terms of JSON-over-HTTP. These are almost always data-oriented APIs rather than hypermedia APIs, although occasionally hypermedia concepts are incorporated into them (typically to little benefit of the end users.) There has been a <a href="https://graphql.org/" rel="noopener" target="_blank">movement away</a> from REST-ful APIs as the industry has begun to <a href="https://kieranpotts.com/rebranding-rest/" rel="noopener" target="_blank">recognize the problems with fitting data APIs into the REST-ful model.</a>

This is a good thing: the industry should question REST-ful ideas in the Data API world and begin looking at older client-server technologies that did a better job of servicing that particular network architecture, leaving REST instead to the network architecture that it was coined to describe: hypermedia APIs.

## <a href="#designing-a-hypermedia-api" class="zola-anchor" aria-label="Anchor link for: designing-a-hypermedia-api">Designing a Hypermedia API</a>

To show how a hypermedia API might be designed differently than a data API, let’s consider the following situation, which came up on the [htmx discord](/discord) recently:

> I want a page with a form and a table on it. The form will add new elements to the table, and the table will also be polling every 30 seconds so that updates from other users are shown.

Let’s consider this UI in terms of a base url, `/contacts`

The first thing we will need is an end point to retrieve the form and the table of current contacts. This will live at `/contacts`, giving:

``` txt
  GET /contacts -> render the form & contacts table
```

Next, we want to be able to create contacts. This would be done via a POST to the same URL:

``` txt
  GET /contacts -> render the form & contacts table
  POST /contacts -> create the new contact, redirect to GET /contacts
```

with HTML that looks something like this:

``` html
<div>
    <form action='/contacts' method="post">
      <!-- form for adding contacts -->
    </form>
    <table>
      <!-- contacts table -->
    </table>
</div>
```

So far, so standard web 1.0 application, and thus far the data-API and hypermedia API needs haven’t diverged very much, although it is worth noteing that the hypermedia API is *self describing* and could be modified (say, changing the URL for creating contacts) without breaking the hypermedia application.

Now we get to the part where htmx is needed: polling the server for updates to the table occasionally. To do this we will add a new end point, `/contacts/table`, which renders only the table of contacts:

``` txt
  GET /contacts -> render the form & contacts table
  POST /contacts -> create the new contact, redirect to GET /contacts
  GET /contacts/table -> render the contacts table
```

and then add a poll trigger to the table:

``` html
<div>
    <form action='/contacts' method="post">
      <!-- form for adding contacts -->
    </form>
    <table hx-trigger="every 30s" hx-get="/contacts/table" hx-swap="outerHTML">
      <!-- contacts table -->
    </table>
</div>
```

Here we see the hypermedia API and data API begin to diverge. This new end point is driven entirely by hypermedia needs, not data model needs. This end point can go away if the hypermedia needs of the application change; its form may change dramatically and so on, which is entirely acceptable since the system is self-describing.

Since we have updated the HTML to use htmx for polling, we may as well make the form use htmx as well for a better UX experience:

``` html
<div>
    <form action='/contacts' method="post" hx-boost="true">
      <!-- form for adding contacts -->
    </form>
    <table hx-trigger="every 30s" hx-get="/contacts/table" hx-swap="outerHTML">
      <!-- contacts table -->
    </table>
</div>
```

We can, if we choose, add additional end points for things like server-side validation of inputs, dynamic forms and so forth. These end points would be driven by *hypermedia needs* rather than any sort of data model considerations: we think in terms of what we are trying to achieve with our application.

## <a href="#api-churn" class="zola-anchor" aria-label="Anchor link for: api-churn">API Churn</a>

The crux point of this short essay is this: API churn is fine in a hypermedia system because *the messages in a hypermedia system are self-describing*. We can thrash the API around and the application doesn’t break: human users simply see the new hypermedia (HTML) and select what actions they want to do.

Humans, compared with computers, are <a href="https://intercoolerjs.org/2016/05/08/hatoeas-is-for-humans.html" rel="noopener" target="_blank">good at deciding what to do</a> and are reasonably OK with change.

This is in contrast with data APIs. Data APIs cannot be modified without breaking client code and thus must be much more disciplined in their changes. Data APIs also face pressure to provide higher levels of expressiveness so that they can satisfy more client needs without modification.

*This latter situation is <a href="https://intercoolerjs.org/2016/02/17/api-churn-vs-security.html" rel="noopener" target="_blank">especially dangerous</a> when these data APIs are consumed in a browser, because any data-api expressiveness available to a front-end developer is also available to a potentially hostile user, who can fire up a console and begin hammering away at the API. Apparently, facebook uses a <a href="https://twitter.com/AdamChainz/status/1392162996844212232" rel="noopener" target="_blank">whitelist</a> to deal with this.*

*Do you?*

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

When designing a hypermedia API, you should use a different design mindset than you use for data APIs. Churn is much less of a concern, and providing the end points you need for a good hypermedia experience should be your primary goal.

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

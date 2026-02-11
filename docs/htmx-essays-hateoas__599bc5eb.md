# hateoas__599bc5eb

- Source URL: https://htmx.org/essays/hateoas/
- Source file: `fetch/htmx_org_599bc5eb.html`
- Hash: `599bc5eb`
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

# HATEOAS

<div class="section">

## <a href="#preface-hateoas-an-alternative-explanation" class="zola-anchor" aria-label="Anchor link for: preface-hateoas-an-alternative-explanation">Preface: <em>HATEOAS — An Alternative Explanation</em></a>

This page is a reworking on the <a href="https://en.wikipedia.org/wiki/HATEOAS" rel="noopener" target="_blank">Wikipedia Entry on HATEOAS</a>, which uses JSON. Here we use HTML to explain the concept, and contrast it with JSON APIs. It is a more opinionated explanation of the concept than would be appropriate for Wikipedia, but it is more correct in our opinion.

</div>

Hypermedia as the Engine of Application State (HATEOAS) is a constraint of the <a href="https://en.wikipedia.org/wiki/Representational_state_transfer" rel="noopener" target="_blank">REST application architecture</a> that distinguishes it from other network application architectures.

With HATEOAS, a client interacts with a network application whose application servers provide information dynamically through <a href="https://en.wikipedia.org/wiki/Hypermedia" rel="noopener" target="_blank"><em>hypermedia</em></a>. A REST client needs little to no prior knowledge about how to interact with an application or server beyond a generic understanding of hypermedia.

By contrast, today JSON-based web clients typically interact through a fixed interface shared through documentation via a tool such as <a href="https://swagger.io/" rel="noopener" target="_blank">swagger</a>.

The restrictions imposed by HATEOAS decouples client and server. This enables server functionality to evolve independently.

## <a href="#example" class="zola-anchor" aria-label="Anchor link for: example">Example</a>

A user-agent that implements HTTP makes a HTTP request of a REST end point through a simple URL. All subsequent requests the user-agent may make are discovered within the hypermedia responses to each request. The media types used for these representations, and the link relations they may contain, are standardized. The client transitions through application states by selecting from links within a hypermedia representation or by manipulating the representation in other ways afforded by its media type.

In this way, RESTful interaction is driven by hypermedia, rather than out-of-band information.

A concrete example will clarify this. Consider this GET request, issued by a web browser, which fetches a bank account resource:

``` txt
GET /accounts/12345 HTTP/1.1
Host: bank.example.com
```

The server responds with a hypermedia representation using HTML:

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

The response contains following possible follow-up actions: navigate to a UI to enter a deposit, withdrawal, transfer, or to close request (to close the account).

Consider the situation at a later point, after the account has been overdrawn. Now, a different set of links are available due to this account status change.

``` html
HTTP/1.1 200 OK

<html>
  <body>
    <div>Account number: 12345</div>
    <div>Balance: -$50.00 USD</div>
    <div>Links:
        <a href="/accounts/12345/deposits">deposits</a>
    </div>
  <body>
</html>
```

Only one link is available: to deposit more money. In the accounts current overdrawn state the other actions are not available, and this fact is reflected internally in *the hypermedia*. The web browser does not know about the concept of an overdrawn account or, indeed, even what an account is. It simply knows how to present hypermedia representations to a user.

Hence we have the notion of the Hypermedia being the Engine of Application State. What actions are possible varies as the state of the resource varies and this information is encoded in the hypermedia.

Contrast the HTML response above with a typical JSON API which, instead, might return a representation of the account with a status field:

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

Here we can see that the client must know specifically what the value of the `status` field means and how it might affect the rendering of a user interface, and what actions can be taken with it. The client must also know what URLs must be used for manipulation of this resource since they are not encoded in the response. This would typically be achieved by consulting documentation for the JSON API.

It is this requirement of out-of-band information that distinguishes this JSON API from a RESTful API that implements HATEOAS.

This shows the core difference between the two approaches: in the RESTful, HATEOAS HTML representation, all operations are encoded directly in the response. In the JSON API example, out-of-band information is necessary for processing and working with the remote resource.

## <a href="#origins" class="zola-anchor" aria-label="Anchor link for: origins">Origins</a>

The HATEOAS constraint is an essential part of the <a href="https://en.wikipedia.org/wiki/Representational_state_transfer#Uniform_interface" rel="noopener" target="_blank">“uniform interface”</a> feature of REST, as defined in Roy Fielding’s <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm" rel="noopener" target="_blank">doctoral dissertation</a>. Fielding’s dissertation was a discussion of the early web architecture, consisting mainly of HTML and HTTP at the time.

Fielding has further described the concept, and the crucial requirement of hypermedia, <a href="https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven" rel="noopener" target="_blank">on his blog</a>.

## <a href="#hateoas-and-json" class="zola-anchor" aria-label="Anchor link for: hateoas-and-json">HATEOAS and JSON</a>

*NOTE: The Neutral Tone Of This Section is Disputed*

In the early 2000s the concept of REST was appropriated from its initial conceptual environment as a description of the early web into other areas of web development: first XML API development (often using <a href="https://en.wikipedia.org/wiki/SOAP" rel="noopener" target="_blank">SOAP</a>) and then JSON API development. This, despite the fact that neither XML nor JSON was a natural hypermedia in the same manner as HTML.

In order to characterize different levels of adherence to REST in these new areas, <a href="https://en.wikipedia.org/wiki/Richardson_Maturity_Model" rel="noopener" target="_blank">The Richardson Maturity Model</a> was proposed, consisting of various levels of “maturity” of APIs, with the highest level, Level 3, consisting of “Hypermedia Controls”.

JSON is not a natural hypermedia and, therefore, hypermedia concepts can only be imposed on top of it. A JSON engineer attempting to meet Level 3 of the Richardson Maturity Model might return the following JSON corresponding to the bank account example above:

``` json
HTTP/1.1 200 OK

{
    "account": {
        "account_number": 12345,
        "balance": {
            "currency": "usd",
            "value": 100.00
        },
        "links": {
            "deposits": "/accounts/12345/deposits",
            "withdrawals": "/accounts/12345/withdrawals",
            "transfers": "/accounts/12345/transfers",
            "close-requests": "/accounts/12345/close-requests"
        }
    }
}
```

Here, the “hypermedia controls” are encoded in a `links` property on the account object.

Unfortunately, the client of this API still needs to know quite a bit of additional information:

- What http methods can be used against these URLs?
- Can it issue a `GET` to these URLs in order to get a representation of the mutation in question?
- If it can `POST` to a given URL, what values are expected?

Compare the above JSON with the following HTTP response, retrieved by a browser after a user has clicked on the link to `/accounts/12345/deposits` found in the first HTML example:

``` html
HTTP/1.1 200 OK

<html>
  <body>
    <form method="post" action="/accounts/12345/deposits">
        <input name="amount" type="number" />
        <button>Submit</button>
    </form>
  <body>
</html>
```

Note that this HTML response encodes all the information necessary to update the account balance, providing a `form` with a `method` and `action` attribute, as well as the inputs necessary for updating the resource correctly.

The JSON representation does not have the same self-contained “uniform interface” as the HTML representation does.

Labelling JSON APIs, no matter how far they stray from RESTful concepts, as ‘REST’ has lead Roy Fielding to say:

> I am getting frustrated by the number of people calling any HTTP-based interface a REST API. Today’s example is the SocialSite REST API. That is RPC. It screams RPC. There is so much coupling on display that it should be given an X rating.

While attempts have been made to impose more elaborate hypermedia controls on JSON APIs, broadly the industry has rejected this approach in favor of simpler RPC-style APIs that forego HATEOAS and other elements of the REST-ful architecture.

This fact is strong evidence for the assertion that a natural hypermedia such as HTML is a practical necessity for building RESTful systems.

<style>
  .content {
    font-family: 'Source Serif Pro', serif;
    text-align: justify;
    hyphens: auto;
    margin-bottom: 3em;
  }

  .content h1 {
    font-family: 'Lexend Zetta', Haettenschweiler, Impact, sans-serif;
    margin: 16px;
    font-size: min(10vw, 6em);
    line-height: 1em;
    margin-bottom: 5rem;
    text-align: center;
  }

  .content section:after {
    content: '< / >';
    content: '< / >' / '';
    display: block;
    margin-bottom: 32px;
    text-align: center;
    color: #aaa;
    font-weight: bold;
    letter-spacing: .5em;
  }

  .content h2 {
    font-size: 1em;
    margin: 16px;
    margin-top: 32px;
    text-transform: uppercase;
    letter-spacing: .1em;
    text-align: center;
  }
    .content h2 em {
      text-transform: none;
      letter-spacing: 0;
    }

  .content a {
    font-variant: all-small-caps;
    letter-spacing: .08em;
    font-weight: 600;
  }

  .content blockquote {
    border: none;
    font-style: italic;
    font-size: 1.1em;
  }
</style>

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

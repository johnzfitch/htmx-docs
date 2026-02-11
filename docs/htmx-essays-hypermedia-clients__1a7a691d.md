# hypermedia-clients__1a7a691d

- Source URL: https://htmx.org/essays/hypermedia-clients/
- Source file: `fetch/htmx_org_1a7a691d.html`
- Hash: `1a7a691d`
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

# Hypermedia Clients

Carson Gross

January 28, 2023

Often, when we are being insufferably pedantic in <a href="https://news.ycombinator.com/item?id=32141027" rel="noopener" target="_blank">online discussions</a> about [REST](https://htmx.org/essays/how-did-rest-come-to-mean-the-opposite-of-rest/) & [HATEOAS](https://htmx.org/essays/hateoas/), we will say something along the lines of this:

> JSON isn’t a hypermedia because it doesn’t have hypermedia controls.
>
> Look at this JSON:

``` json
{
 "account": {
   "account_number": 12345,
   "balance": {
     "currency": "usd",
     "value": 50.00
   },
   "status": "open"
 }
}
```

> See? No hypermedia controls.
>
> So this JSON isn’t a hypermedia, and, therefore, the API returning this JSON isn’t RESTful.

To this, occasionally, a smart and experienced web developer will reply with something along these lines:

> OK, mr. REST-y pants, how about this JSON?

``` json
{
  "account": {
    "account_number": 12345,
    "balance": {
      "currency": "usd",
      "value": 50.00
    },
    "status": "open",
    "links": {
      "deposits": "/accounts/12345/deposits",
      "withdrawals": "/accounts/12345/withdrawals",
      "transfers": "/accounts/12345/transfers",
      "close-requests": "/accounts/12345/close-requests"
    }
  }
}
```

> There, now there are hypermedia controls in this response (normal humans call them links, btw) so this JSON is a hypermedia.
>
> So this JSON API is now RESTful. Feel better?

😑

One must concede that, at least at a high-level, our online adversary has something of a talking point here: these do appear to be hypermedia controls, and they are, in fact, in a JSON response. So, couldn’t you call this JSON response RESTful?

Being obstinate by nature, we still wouldn’t be willing to concede the immediate point without a good <a href="https://i.imgur.com/DpQ9YJl.png" rel="noopener" target="_blank">ackchyually</a> or two:

- First, these links hold no information about what HTTP method to use to access them
- Secondly, these links aren’t a *native* part of JSON the way that, for example, anchor and form tags are with HTML
- Third, there is a lot of missing information about the hypermedia interactions at each end point (e.g. what data needs to go up with the request.)

And so on: the sorts of pedantic nit-picking that makes technical flame wars about REST on the internet such a *special* joy.

However, there is a deeper <a href="https://i.imgur.com/DpQ9YJl.png" rel="noopener" target="_blank">ackchyually</a> here, and one that doesn’t involve the *JSON API* itself, but rather the other side of the wire: the *client* that receives the JSON.

## <a href="#hypermedia-clients-presentation-information" class="zola-anchor" aria-label="Anchor link for: hypermedia-clients-presentation-information">Hypermedia Clients &amp; Presentation Information</a>

The deeper problem with this proposed fix for non-RESTful JSON APIs is that, for this JSON response to participate properly in a <a href="https://hypermedia.systems" rel="noopener" target="_blank">hypermedia system</a>, the *client* that consumes the JSON needs to *also* satisfy the <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm" rel="noopener" target="_blank">constraints</a> that the RESTful architectural style places on the entire system.

In particular, the client needs to satisfy the <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_5" rel="noopener" target="_blank">uniform interface</a>, in which the client code knows nothing about the “shape” or details of the response beyond the ability to display the given hypermedia to a user. In a properly functioning RESTful system, the client isn’t allowed to have any “out of band” knowledge about the domain that a particular hypermedia representation, er, represents.

Let’s look at the proposed JSON-as-hypermedia again:

``` json
{
  "account": {
    "account_number": 12345,
    "balance": {
      "currency": "usd",
      "value": 50.00
    },
    "status": "open",
    "links": {
      "deposits": "/accounts/12345/deposits",
      "withdrawals": "/accounts/12345/withdrawals",
      "transfers": "/accounts/12345/transfers",
      "close-requests": "/accounts/12345/close-requests"
    }
  }
}
```

Now, a client of this API *could* use a generic algorithm to transform this JSON into, for example, some HTML. It could do so via a client-side templating language that, for example, iterated over all the properties of the JSON object.

But there’s a hitch: note that there isn’t a lot of *presentation information* in the JSON response. It is a fairly raw data representation of the account in question, with a few additional URLs.

A client that wanted to satisfy the uniform interface constraint of REST doesn’t have much information on how to present this data to a user. The client would, therefore, need to adopt a very basic approach to displaying this account to an end user.

It would probably end up being roughly a set of name/value pairs and a set generic of buttons or links for actions, right?

There simply isn’t much more it could do while remaining agnostic about the form of the JSON response.

### <a href="#pushing-our-json-api-further" class="zola-anchor" aria-label="Anchor link for: pushing-our-json-api-further">Pushing Our JSON API Further</a>

We could fix this by making our JSON API more elaborate and start including more information on how to lay out the information: perhaps indications that some fields should be emphasized, or hidden, etc.

But that would only be part of the story.

We would also need to update the client side to interpret these new elements of our JSON API properly. So we are no longer just API designers: we are getting in to the hypermedia *client* creation business as well. Or, more likely, we are asking our *API clients* to get into the hypermedia client business as well.

Now, Mike Amundsen has written an <a href="https://www.oreilly.com/library/view/restful-web-clients/9781491921890/" rel="noopener" target="_blank">excellent book</a> on how to build a proper, generic hypermedia client. But what you will see in that book is that creating a good hypermedia client isn’t trivial, and, further, it is certainly not what *most* engineers would build to consume a JSON API, even if the JSON API had increasingly elaborate hypermedia controls and presentation information in their responses.

### <a href="#inefficient-representations" class="zola-anchor" aria-label="Anchor link for: inefficient-representations">“Inefficient” Representations</a>

As we begin to consider adding more information to our JSON response, a quote from Roy Fielding’s dissertation jumps to mind:

> The trade-off, though, is that a uniform interface degrades efficiency, since information is transferred in a standardized form rather than one which is specific to an application’s needs.

*-Roy Fielding, <a href="https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_5" rel="noopener" target="_blank">https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm#sec_5_1_5</a>*

A criticism of HTML is that it mixes “presentation” information with “semantic” information. This is often contrasted unfavorably with the brevity of typical JSON API responses.

It turns out, however, that it is exactly that presentation information, and the ability of a web browser (i.e. a hypermedia client) to turn it into a UI that a human can interact with, that makes HTML work so well as a component of the larger hypermedia system that is the web.

And that exactly what we find ourselves adding to our own JSON API to support a proper hypermedia client.

## <a href="#building-hypermedia-clients" class="zola-anchor" aria-label="Anchor link for: building-hypermedia-clients">Building Hypermedia Clients</a>

So, you can see, just offering hypermedia controls in a JSON API response isn’t enough. It is *part* of the REST story, but not the entire story. And, I have come to understand, it is not really the *hard* part of the story. In fact, creating the hypermedia *client* is the hard part, and creating a *good* hypermedia client is *the really hard part*.

Now, we are all used to web browsers just being there, but think for a moment about all the technology that goes in to simply parsing and rendering HTML to an end user in a normal, every day web request. It’s *extremely* complicated.

That’s why, if we want to build web-based [hypermedia-driven applications](https://htmx.org/essays/hypermedia-driven-applications/), it’s probably a good idea to use the standard, web-based hypermedia client: the browser.

It is already an extremely powerful, well tested hypermedia client. And, [with a bit of help](https://htmx.org/docs/), it can be an even better hypermedia client.

In general, building a good hypermedia client that satisfies all the constraints of REST is hard, and we should lean towards using (and extending) existing clients rather than building our own new ones.

### <a href="#hyperview" class="zola-anchor" aria-label="Anchor link for: hyperview">Hyperview</a>

That being said, there are times when building a new hypermedia client is appropriate. For example, this is what makes a technology like <a href="https://hyperview.org/" rel="noopener" target="_blank">Hyperview</a> so impressive and special. Hyperview doesn’t just provide a specification for a new, mobile-friendly hypermedia, <a href="https://hyperview.org/docs/guide_html" rel="noopener" target="_blank">HXML</a>.

It also provides developers with a hypermedia *client* that understands how to render HXML.

Without that hypermedia client, Hyperview would be just another hypermedia-in-theory, like the JSON above, rather than a compelling, practical and *complete* RESTful hypermedia solution.

A hypermedia without a hypermedia client is like a fish without a bicycle, except where the fish is really only good at bicycling.

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

It took me a long time to appreciate how important the *client* is to a proper, RESTful hypermedia system. This is understandable, since most of the early discussion around REST was around <a href="https://www.martinfowler.com/articles/richardsonMaturityModel.html" rel="noopener" target="_blank">API Design</a>, and the client simply didn’t come up much.

What I see now is that a lot of these discussions were putting the cart before the horse: the only way a RESTful hypermedia API can be useful is if it is consumed by a proper hypermedia client. Otherwise, your hypermedia controls are wasted on what is, at the end of the day, a domain-specific thick client that just wants to get things done.

Further, your hypermedia API is almost certainly going to have to carry a fair amount of presentation-layer information in it to make the whole thing usable. It turns out that “Level 3” of the <a href="https://martinfowler.com/articles/richardsonMaturityModel.html" rel="noopener" target="_blank">Richard Maturity Model</a>, Hypermedia Controls, *isn’t* enough to reach “The Glory of REST”.

In practice, you are going to need to add in a bunch of practical presentation-level technology to make your hypermedia API really work, *and* you are going to need a properly built hypermedia client to consume it.

I had a nascent sense of this when I wrote <a href="https://intercoolerjs.org/2016/05/08/hatoeas-is-for-humans.html" rel="noopener" target="_blank">HATEOAS Is For Humans</a>, but I didn’t, at that time, appreciate just how special the client/web browser was.

REST isn’t solely about APIs: as Roy Fielding makes clear in his dissertation, it is a *system* architecture.

Except for a few people like <a href="https://training.amundsen.com/" rel="noopener" target="_blank">Mike</a>, we’ve been largely ignoring a larger (really, *much* larger) part of the REST story:

<div style="text-align:center;padding-top: 24px">

<img src="/img/creating-client.png" style="max-width: 95%" alt="Creating A Hypermedia Client Is Hard Joke" />

</div>

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

# why-tend-not-to-use-content-negotiation__0e760284

- Source URL: https://htmx.org/essays/why-tend-not-to-use-content-negotiation/
- Source file: `fetch/htmx_org_0e760284.html`
- Hash: `0e760284`
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

# Why I Tend Not To Use Content Negotiation

Carson Gross

November 18, 2023

I have written a lot about Hypermedia APIs vs. Data (JSON) APIs, including [the differences between the two](https://htmx.org/essays/hypermedia-apis-vs-data-apis/), what [REST “really” means](https://htmx.org/essays/how-did-rest-come-to-mean-the-opposite-of-rest/) and why [HATEOAS](https://htmx.org/essays/hateoas/) isn’t so bad as long as your API is interacting with a [Hypermedia Client](https://htmx.org/essays/hypermedia-clients/).

Often when I am engaged in discussions with people coming from the “REST is JSON over HTTP” world (that is, the normal world) I have to navigate a lot of language and conceptual issues:

- No, I am not advocating you return HTML as a general purpose API, hypermedia makes for a bad general purpose API
- Yes, I am advocating [tightly coupling](https://htmx.org/essays/two-approaches-to-decoupling/) your web application to your hypermedia API
- No, I do not think that we will ever fix how the industry [uses the term REST](https://htmx.org/essays/how-did-rest-come-to-mean-the-opposite-of-rest/)
- Yes, I am advocating you [split your data API and your hypermedia API up](https://htmx.org/essays/splitting-your-apis/)

The last point often strikes people who are used to a single, general purpose JSON API as dumb: why have two APIs when you can have a single API that can satisfy any number of types of clients? I tried to answer that question as best I can in the essay above, but it is certainly a reasonable one to ask.

It seems like (and it is) extra work in some ways when compared to having one general API.

At this point in a conversation, someone who agrees broadly with my take on REST, [Hypermedia-Driven Applications](https://htmx.org/essays/hypermedia-driven-applications/), etc. will often jump in and say something like

> “Oh, it’s easy, you just use *content negotiation*, it’s baked into HTTP!”

Not being content with alienating only the general purpose JSON API enthusiasts, let me now proceed to also alienate my erstwhile hypermedia enthusiast allies by saying:

*I don’t think content negotiation is typically the right approach to returning both JSON and HTML for most applications.*

## <a href="#what-is-content-negotiation" class="zola-anchor" aria-label="Anchor link for: what-is-content-negotiation">What Is Content Negotiation?</a>

First things first, what is “content negotiation”?

<a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation" rel="noopener" target="_blank">Content negotiation</a> is a feature of HTTP that allows a client to negotiate the content type of the response from a server. A full treatment of the implementation in HTTP is beyond the scope of this essay, but let us consider the most well known mechanism for content negotiation in HTTP, the <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation#the_accept_header" rel="noopener" target="_blank"><code>Accept</code> Request Header</a>.

The `Accept` request header allows a client, such as a browser, to indicate the `MIME` types that it is willing to accept from the server in a response.

An example value of this header is:

``` http
Accept: text/html, application/xhtml+xml, application/xml;q=0.9, image/webp, */*;q=0.8
```

This `Accept` header tells the server what formats the client is willing to accept. Preferences are expressed via the `q` weighting factor. Wildcards are expressed with asterisks `*`.

In this case, the client is saying:

> I would most like to receive text/html, application/xhtml+xml or image/webp. Next I would prefer application/xml. Finally, I will accept whatever you give me.

The server then can take this information and determine the best content type to provide to the client.

This is the act of “content negotiation” and it is certainly an interesting feature of HTTP.

## <a href="#using-content-negotiation-in-apis" class="zola-anchor" aria-label="Anchor link for: using-content-negotiation-in-apis">Using Content Negotiation In APIs</a>

As far as I am aware, it was the <a href="https://rubyonrails.org/" rel="noopener" target="_blank">Ruby On Rails</a> community that first went in in a big way using content negotiation to provide both HTML and JSON (and other) formats from the same URL.

In Rails, this is accomplished via the <a href="https://apidock.com/rails/ActionController/MimeResponds/respond_to" rel="noopener" target="_blank"><code>respond_to</code></a> helper method available in controllers.

Leaving the gory details of Rails aside, you might have a request like an HTTP `GET` to `/contacts` that ends up invoking a function in a `ContactsController` class that looks like this:

``` ruby
def index
  @contacts = Contacts.all

  respond_to do |format|
    format.html # default rendering logic
    format.json { render json: @contacts }
  end
end
```

By making use of the `respond_to` helper method, if a client makes a request with the `Accept` header above, the controller will render an HTML response using the Rails templating systems.

However, if the `Accept` header from the client has the value `application/json` instead, Rails will render the contacts as a JSON array for the client.

A pretty neat trick: you can keep all your controller logic, like looking up the contacts, the same and just use a bit of ruby/Rails magic to render two different response types using content negotiation. Barely any additional work on top of the normal Model/View/Controller logic.

You can see why people like the idea!

## <a href="#so-what-s-the-problem" class="zola-anchor" aria-label="Anchor link for: so-what-s-the-problem">So What’s The Problem?</a>

So why don’t I think this is a good approach to splitting your JSON and HTML APIs up?

It boils down to the [differences between JSON APIs and Hypermedia (HTML) APIs](https://htmx.org/essays/hypermedia-apis-vs-data-apis/) I hinted at earlier. In particular:

- Data APIs should be versioned and should be very stable within a particular version of the API
- Data APIs should strive for both regularity and expressiveness due to the arbitrary data needs of consumers
- Data APIs typically use some sort of token-based authentication
- Data APIs should be rate limited
- Hypermedia APIs typically use some sort of session-cookie based authentication
- Hypermedia APIs should be driven by the needs of the underlying hypermedia application

While all of these differences matter and have an effect on your controller code, pulling it in two different directions, it is really the first and last items that make me often choose not to use content negotiation in my applications.

Your JSON API needs to be a stable set of endpoint that client code can rely on.

Your hypermedia API, on the other hand, can change dramatically based on the user interface needs of your applications.

These two things don’t mix well.

To give you a concrete example, consider an end point that renders a detail view of a contact, at, say `/contacts/:id` (where `:id` is a parameter containing the id of the contact to render). Let’s say that this page has a “related contacts” section of the UI and, further, computing these related contacts is expensive for some reason.

In this situation you might choose to use the <a href="https://htmx.org/examples/lazy-load/" rel="noopener" target="_blank">Lazy Loading</a> pattern to defer loading the related contacts until after the initial contact detail screen has been rendered. This improves perceived performance of the page for your users.

If you did this, you might put the lazy loaded content at the end-point `/contacts/:id/related`.

Now, later on, maybe you are able to optimize the computation of related contacts. At this point you might choose to rip the `/contacts/:id/related` end-point out and just render the related contacts information in the initial page render.

All of this is fine for your hypermedia API: hypermedia, through [the uniform interface & HATEOAS](https://htmx.org/essays/hateoas/) is *designed* to handle these sorts of changes.

However, your JSON API… not so much.

Your JSON API should remain stable. You can’t be adding and removing end-points willy-nilly. Yes, you can have *some* end-points respond with either JSON or HTML and others only respond with HTML, but it gets messy. What if you accidentally copy-and-paste in the wrong code somewhere, for example.

Taking all of this into account, as well as things like rate-limiting and so on, I think you can make a strong argument that there should be a <a href="https://en.wikipedia.org/wiki/Separation_of_concerns" rel="noopener" target="_blank">Separation Of Concerns</a> between the JSON API and the hypermedia API.

(Yes, I am aware of the irony that the person who coined the term [Locality of Behaviour](https://htmx.org/essays/locality-of-behaviour/) is making a SoC argument.)

## <a href="#so-what-s-the-alternative" class="zola-anchor" aria-label="Anchor link for: so-what-s-the-alternative">So What’s The Alternative?</a>

The alternative is, as I advocate in [Splitting Your APIs](https://htmx.org/essays/splitting-your-apis/), er, well, splitting your APIs. This means providing different paths (or subdomains, or whatever) for your JSON API and your hypermedia (HTML) API.

Going back to our contacts API, we might have the following:

- The JSON API to get all contacts is found at `/api/v1/contacts`
- The Hypermedia API to get all contacts is found at `/contacts`

This layout implies two different controllers and, I say, that’s a good thing: the JSON API controller can implement the requirements of a JSON API: rate limiting, stability, maybe an expressive query mechanism like GraphQL.

Meanwhile, your hypermedia API (really, just your Hypermedia Driven Application endpoints) can change dramatically as your user interface needs change, with highly tuned database queries, end-points to support special UI needs, etc.

By separating these two concerns, your JSON API can be stable, regular and low-maintenance, and your hypermedia API can be chaotic, specialized and flexible. Each gets its own controller environment to thrive in, without conflicting with one another.

And this is why I prefer to split my JSON and hypermedia APIs up into separate controllers, rather than use HTTP content negotiation to attempt to reuse controllers for both.

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

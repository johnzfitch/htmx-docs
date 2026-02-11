# mvc__d44eef0b

- Source URL: https://htmx.org/essays/mvc/
- Source file: `fetch/htmx_org_d44eef0b.html`
- Hash: `d44eef0b`
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

# Model/View/Controller (MVC)

Carson Gross

January 16, 2024

A common objection I see to using htmx and hypermedia is something along the lines of:

> The problem with returning HTML (and not JSON) from your server is that you’d probably also like to serve mobile apps and don’t want to duplicate your API

I have already outlined in [another essay](https://htmx.org/essays/splitting-your-apis/) that I think you should split your JSON API & your hypermedia API up into separate components.

In that essay I explicitly recommend “duplicating” (to an extent) your API, in order to disentangle your “churny” web application API endpoints that return HTML from your stable, regular & expressive JSON Data API.

In looking back at conversations I’ve had around this idea with people, I think that I have been assuming familiarity with a pattern that many people are not as familiar with as I am: the <a href="https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller" rel="noopener" target="_blank">Model/View/Controller</a> (MVC) pattern.

## <a href="#an-mvc-intro" class="zola-anchor" aria-label="Anchor link for: an-mvc-intro">An MVC Intro</a>

I was a little shocked to discover <a href="https://www.youtube.com/watch?v=9H5VK9vJ-aw" rel="noopener" target="_blank">in a recent podcast</a> that many younger web developers just don’t have much experience with MVC. This is perhaps due to the Front-end/Back-end split that occurred when Single Page Applications became the norm.

MVC is a simple pattern that predates the web and can be with nearly any program that offers a graphical interface to a user.

The rough idea is as follows:

- A “Model” layer contains your <a href="https://en.wikipedia.org/wiki/Domain_model" rel="noopener" target="_blank">“Domain Model”</a>. This layer contains the domain logic specific to the application. So, for example, a contact management application will have contact-related logic in this layer. It will not have references to visual elements in it, and should be relatively “pure”.

- A “View” layer contains the “view” or visual elements that are presented to the user. This layer often (although not always) works with model values to present visual information to the user.

- Finally, a “Controller” layer, which coordinates these two layers: for example it might receive an update from a user, update a Model and then pass the updated model to a View to display an update user interface to the user.

There are a lot of variations, but that’s the idea.

Early on in web development many server side frameworks explicitly adopted the MVC pattern. The implementation that I’m most familiar with is <a href="https://rubyonrails.org/" rel="noopener" target="_blank">Ruby On Rails</a>, which has documentation on each of these topics: <a href="https://guides.rubyonrails.org/active_record_basics.html" rel="noopener" target="_blank">Models</a> that are persisted to the database, <a href="https://guides.rubyonrails.org/action_view_overview.html" rel="noopener" target="_blank">Views</a> for generating HTML views, and <a href="https://guides.rubyonrails.org/action_controller_overview.html" rel="noopener" target="_blank">Controllers</a> that coordinate between the two.

The rough idea, in Rails, is:

- Models collect your application logic and database accesses
- Views take Models and generate HTML via a templating language (<a href="https://github.com/ruby/erb" rel="noopener" target="_blank">ERB</a>, this is where <a href="https://en.wikipedia.org/wiki/HTML_sanitization" rel="noopener" target="_blank">HTML sanitizing</a> is done, btw)
- Controllers take HTTP Requests and, typically, perform some action with a Model and then pass that Model on to a View (or redirect, etc.)

Rails has a fairly standard (although somewhat “shallow” and simplified) implementation of the MVC pattern, built on top of the underlying HTML, HTTP Request/Response lifecycle.

### <a href="#fat-model-skinny-controller" class="zola-anchor" aria-label="Anchor link for: fat-model-skinny-controller">Fat Model/Skinny Controller</a>

One concept that came up a lot in the Rails community was the notion of <a href="https://riptutorial.com/ruby-on-rails/example/9609/fat-model--skinny-controller" rel="noopener" target="_blank">“Fat Model, Skinny Controller”</a>. The idea here is that your Controllers should be relatively simple, only maybe invoking a method or two on the Model and then immediately handing the result on to a View.

The Model, on the other hand, could be much “thicker” with lots of domain specific logic. (There are objections that this leads to <a href="https://en.wikipedia.org/wiki/God_object" rel="noopener" target="_blank">God Objects</a>, but let’s set that aside for now.)

Let’s keep this idea of fat model/skinny controller in mind as we work through a simple example of the MVC pattern and why it is useful.

## <a href="#an-mvc-style-web-application" class="zola-anchor" aria-label="Anchor link for: an-mvc-style-web-application">An MVC-Style Web Application</a>

For our example, let’s take a look at one of my favorites: an online Contacts application. Here is a Controller method for that application that displays a given page of Contacts by generating an HTML page:

``` python
@app.route("/contacts")
def contacts():
    contacts = Contact.all(page=request.args.get('page', default=0, type=int))
    return render_template("index.html", contacts=contacts)
```

Here I’m using <a href="https://www.python.org/" rel="noopener" target="_blank">Python</a> and <a href="https://flask.palletsprojects.com/en/3.0.x/" rel="noopener" target="_blank">Flask</a>, since I use those in my <a href="https://hypermedia.systems/" rel="noopener" target="_blank">Hypermedia Systems</a> book.

Here you can see that the controller is very “thin”: it simply looks up contacts via the `Contact` Model object, passing a `page` argument in from the request.

This is very typical: the Controllers job is to map an HTTP request into some domain logic, pulling HTTP-specific information out and turning it into data that the Model can understand, such as a page number.

The controller then hands the paged collection of contacts on to the `index.html` template, to render them to an HTML page to send back to the user.

Now, the `Contact` Model, on the other hand, may be relatively “fat” internally: that `all()` method could have a bunch of domain logic internally that does a database lookup, pages the data somehow, maybe applies some transformations or business rules, etc. And that would be fine, that logic is encapsulated within the Contact model and the Controller doesn’t have to deal with it.

### <a href="#creating-a-json-data-api-controller" class="zola-anchor" aria-label="Anchor link for: creating-a-json-data-api-controller">Creating A JSON Data API Controller</a>

So, if we have this relatively well-developed Contact model that encapsulates our domain, you can easily create a *different* API end point/Controller that does something similar, but returns a JSON document rather than an HTML document:

``` python
@app.route("/api/v1/contacts")
def contacts():
    contacts = Contact.all(page=request.args.get('page', default=0, type=int))
    return jsonify(contacts=contacts)
```

### <a href="#but-you-are-duplicating-code" class="zola-anchor" aria-label="Anchor link for: but-you-are-duplicating-code">But You Are Duplicating Code!</a>

At this point, looking at these two controller functions, you may think “This is stupid, the methods are nearly identical”.

And you’re right, currently they are nearly identical.

But let’s consider two potential additions to our system.

#### <a href="#rate-limiting-our-json-api" class="zola-anchor" aria-label="Anchor link for: rate-limiting-our-json-api">Rate Limiting Our JSON API</a>

First, let’s add rate limiting to the JSON API to prevent DDOS or badly written automated clients from swamping our system. We’ll add the <a href="https://flask-limiter.readthedocs.io/en/stable/" rel="noopener" target="_blank">Flask-Limiter</a> library:

``` python
@app.route("/api/v1/contacts")
@limiter.limit("1 per second")
def contacts():
    contacts = Contact.all(page=request.args.get('page', default=0, type=int))
    return jsonify(contacts=contacts)
```

Easy.

But note: we don’t want that limit applying to our web application, we just want it for our JSON Data API. And, because we’ve split the two up, we can achieve that.

#### <a href="#adding-a-graph-to-our-web-application" class="zola-anchor" aria-label="Anchor link for: adding-a-graph-to-our-web-application">Adding A Graph To Our Web Application</a>

Let’s consider another change: we want to add a graph of the number of contacts added per day to the `index.html` template in our HTML-based web application. It turns out that this graph is expensive to compute.

We do not want to block the rendering of the `index.html` template on the graph generation, so we will use the [Lazy Loading](https://htmx.org/examples/lazy-load/) pattern for it instead. To do this, we need to create a new endpoint, `/graph`, that returns the HTML for that lazily loaded content:

``` python
@app.route("/graph")
def graph():
    graphInfo = Contact.computeGraphInfo(page=request.args.get('page', default=0, type=int))
    return render_template("graph.html", info=graphInfo)
```

Note that here, again, our controller is still “thin”: it just delegates out to the Model and then hands the results on to a View.

What’s easy to miss is that we’ve added a new endpoint to our web application HTML API, but *we haven’t added it to our JSON Data API*. So we are **not** committing to other non-web clients that this (specialized) endpoint, which is being driven entirely by our UI needs, will be around forever.

Since we are not committing to *all* clients that this data will be available at `/graph` forever, and since we are using [Hypermedia As The Engine of Application State](https://htmx.org/essays/hateoas/) in our HTML-based web application, we are free to remove or refactor this URL later on.

Perhaps some database optimization suddenly make the graph fast to compute and we can include it inline in the response to `/contacts`: we can remove this end point because we have not exposed it to other clients, it’s just there to support our web application.

So, we get the [flexibility we want](https://htmx.org/essays/hypermedia-apis-vs-data-apis/) for our hypermedia API, and the [features](https://htmx.org/essays/hypermedia-apis-vs-data-apis/) we want for our JSON Data API.

The most important thing to notice, in terms of MVC, is that because our domain logic has been collected in a Model, we can vary these two APIs flexibly while still achieving a significant amount of code reuse. Yes, there was a lot of initial similarity to the JSON and HTML controllers, but they diverged over time.

At the same time, we didn’t duplicate our Model logic: both controllers remained relatively “thin” and delegated out to our Model object to do most of the work.

Our two APIs are decoupled, while our domain logic remains centralized.

(Note that this also gets at [why I tend not to use content negotiation](https://htmx.org/essays/why-tend-not-to-use-content-negotiation/) and return HTML & JSON from the same endpoint.)

## <a href="#mvc-frameworks" class="zola-anchor" aria-label="Anchor link for: mvc-frameworks">MVC Frameworks</a>

Many older web frameworks such as <a href="https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/mvc.html" rel="noopener" target="_blank">Spring</a>, <a href="https://dotnet.microsoft.com/en-us/apps/aspnet/mvc" rel="noopener" target="_blank">ASP.NET</a>, Rails have very strong MVC concepts that allow you to split your logic out in this manner extremely effectively.

Django has a variation on the idea called <a href="https://www.askpython.com/django/django-mvt-architecture" rel="noopener" target="_blank">MVT</a>.

This strong support for MVC is one reason why these frameworks pair very well with htmx and those communities are excited about it.

And, while the examples above are obviously biased towards <a href="https://www.azquotes.com/picture-quotes/quote-object-oriented-programming-is-an-exceptionally-bad-idea-which-could-only-have-originated-edsger-dijkstra-7-85-25.jpg" rel="noopener" target="_blank">Object-Oriented</a> programming, the same ideas can be applied in a functional context as well.

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

I hope that, if it is new to you, that gives you to a good feel for the concept of MVC and shows how that, by adopting that organizational principle in your web applications, you can effectively decouple your APIs while at the same time avoiding significant duplication of code.

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

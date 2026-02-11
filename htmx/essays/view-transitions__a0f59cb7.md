# view-transitions__a0f59cb7

- Source URL: https://htmx.org/essays/view-transitions/
- Source file: `fetch/htmx_org_a0f59cb7.html`
- Hash: `a0f59cb7`
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

# View Transitions

We have asserted, for a while now, that a major reason that many people have adopted the SPA architecture for web applications is due to aesthetic considerations.

As we mention in our book <a href="https://hypermedia.systems" rel="noopener" target="_blank">Hypermedia Systems</a>, when discussing the Web 1.0-style contact management application we begin with, there are serious *aesthetic* issues with the application, even if it has feature-parity with an SPA version:

> From a user experience perspective: there is a noticeable refresh when you move between pages of the application, or when you create, update or delete a contact. This is because every user interaction (link click or form submission) requires a full page refresh, with a whole new HTML document to process after each action.
>
> *–Hypermedia Systems - <a href="https://hypermedia.systems/extending-html-as-hypermedia/" rel="noopener" target="_blank">Chapter 4</a>*

This jarring “ka-chunk” between webpages, often with a <a href="https://webkit.org/blog/66/the-fouc-problem/" rel="noopener" target="_blank">Flash of Unstyled Content</a> has been with us forever and, while modern browsers have improved the situation somewhat (while, unfortunately, also making it less obvious that a request is in flight) the situation is still bad, particularly when compared with what a well-crafted SPA can achieve.

Now, early on in the life of the web, this wasn’t such a big deal. We had stars flying around dinosaurs *in the browser’s toolbar*, flaming text, table-based layouts, dancing babies and so forth, and we were largely comparing the web with things like ftp clients.

The bar was *low* and the times were *good*.

Alas, the web has since put away such childish things, and now we are expected to present polished, attractive interfaces to our users, *including* smooth transitions from one view state to another.

Again, we feel this is why many teams default to the SPA approach: the old way just seems… clunky.

## <a href="#css-transitions" class="zola-anchor" aria-label="Anchor link for: css-transitions">CSS Transitions</a>

The early web engineers realized that web developers would like to provide smooth transitions between different view states and have offered various technologies for achieving this. A major one is <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/transition" rel="noopener" target="_blank">CSS Transitions</a>, which allow you to specify a mathematical *transition* from one state to another.

Unfortunately for HTML, CSS transitions are only available if you use JavaScript: you have to change elements dynamically in order to trigger the transitions, which “vanilla” HTML can’t do. In practice, this meant that only the cool kids using JavaScript to build SPAs got to use these tools, further cementing the *aesthetic superiority* of SPAs.

htmx, as you probably know, makes CSS Transitions <a href="https://htmx.org/examples/animations/" rel="noopener" target="_blank">available in plain HTML</a> via a somewhat elaborate <a href="https://htmx.org/docs/#request-operations" rel="noopener" target="_blank">swapping model</a> where we take elements that are in both the old and new content and “settle” attributes on them. It’s a neat trick and can be used to make hypermedia-driven application feel as buttery-smooth as well done SPA.

However, there is a new kid on the block: <a href="https://developer.chrome.com/docs/web-platform/view-transitions/" rel="noopener" target="_blank">The View Transition API</a>

## <a href="#the-view-transition-api" class="zola-anchor" aria-label="Anchor link for: the-view-transition-api">The View Transition API</a>

The View Transition API is much more ambitious than CSS transitions in that it is attempting to provide a simple, intuitive API for transitioning an *entire DOM* from one state to another in a way that mere mortals can take advantage of.

Furthermore, this API is supposed to be available not only in JavaScript, but also for plain old links and forms in HTML as well, making it possible to build *much nicer* user interfaces using the Web 1.0 approach.

It will be fun to revisit the Contact application in “Hypermedia Systems” when this functionality is available!

As of this writing, however, the API is, like CSS Transitions, only available in JavaScript, and its only been just released in Chrome 111+.

In JavaScript, The API could not be more simple:

``` js

  // this is all it takes to get a smooth transition from one 
  // state to another!
  document.startViewTransition(() => updateTheDOMSomehow(data));
```

Now, that’s my kind of API.

As luck would have it, it’s trivial to wrap this API around the regular htmx swapping model, which allows us to start exploring View Transitions in htmx, even before it’s generally available in HTML!

And, as of <a href="https://cdn.jsdelivr.net/npm/htmx.org@1.9.0" rel="noopener" target="_blank">htmx 1.9.0</a>, you can start experimenting with the API by adding the `transition:true` attribute to an [`hx-swap`](/attributes/hx-swap) attribute.

## <a href="#a-practical-example" class="zola-anchor" aria-label="Anchor link for: a-practical-example">A Practical Example</a>

So let’s look at a simple example of this new shiny toy coupled with htmx.

Doing so will involve two parts:

- Defining our View Transition animation via CSS
- Adding a small annotation to an htmx-powered button

### <a href="#the-css" class="zola-anchor" aria-label="Anchor link for: the-css">The CSS</a>

The first thing that we need to do is define the View Transition animation that we want.

- Define some animations using @keyframes to slide and fade content
- Define a view transition with the name `slide-it` using the `:view-transition-old()` and `:view-transition-new()` pseudo-selectors
- Tie the `.sample-transition` class to the `slide-it` view transition that we just defined, so we can bind it to elements via a that CSS class name

(Fuller details on the View Transition API can be found on the <a href="https://developer.chrome.com/docs/web-platform/view-transitions/" rel="noopener" target="_blank">Chrome Developer Page</a> documenting them.)

``` html

    <style>
       @keyframes fade-in {
         from { opacity: 0; }
       }
    
       @keyframes fade-out {
         to { opacity: 0; }
       }
    
       @keyframes slide-from-right {
         from { transform: translateX(90px); }
       }
    
       @keyframes slide-to-left {
         to { transform: translateX(-90px); }
       }
    
       /* define animations for the old and new content */
       ::view-transition-old(slide-it) {
         animation: 180ms cubic-bezier(0.4, 0, 1, 1) both fade-out,
         600ms cubic-bezier(0.4, 0, 0.2, 1) both slide-to-left;
       }
       ::view-transition-new(slide-it) {
         animation: 420ms cubic-bezier(0, 0, 0.2, 1) 90ms both fade-in,
         600ms cubic-bezier(0.4, 0, 0.2, 1) both slide-from-right;
       }
    
       /* tie the view transition to a given CSS class */
       .sample-transition {
           view-transition-name: slide-it;
       }
        
    </style>
```

This CSS sets it up such that content with the `.sample-transition` class on it will fade out and slide to the left when it is removed, and new content will fade in and slide in from the right.

### <a href="#the-html" class="zola-anchor" aria-label="Anchor link for: the-html">The HTML</a>

With our View Transition defined via CSS, the next thing to do is to tie this View Transition to an actual element that htmx will mutate, and to specify that htmx should take advantage of the View Transition API:

``` html

    <div class="sample-transition">
       <h1>Initial Content</h1>
       <button hx-get="/new-content" 
               hx-swap="innerHTML transition:true" 
               hx-target="closest div">
         Swap It!
       </button>
    </div>
```

Here we have a button that issues an `GET` to get some new content, and that replaces the closest div’s inner HTML with the response.

That div has the `sample-transition` class on it, so the View Transition defined above will apply to it.

Finally, the `hx-swap` attribute includes the option, `transition:true`, which is what tells htmx to use the internal View Transition JavaScript API when swapping.

## <a href="#demo" class="zola-anchor" aria-label="Anchor link for: demo">Demo</a>

With all that tied together, we are ready to start using the View Transition API with htmx. Here’s a demo, which should work in Chrome 111+ (other browsers will work fine, but won’t get the nice animation):

<style>
   @keyframes fade-in {
     from { opacity: 0; }
   }

   @keyframes fade-out {
     to { opacity: 0; }
   }

   @keyframes slide-from-right {
     from { transform: translateX(90px); }
   }

   @keyframes slide-to-left {
     to { transform: translateX(-90px); }
   }

   /* define animations for the old and new content */
   ::view-transition-old(slide-it) {
     animation: 180ms cubic-bezier(0.4, 0, 1, 1) both fade-out,
     600ms cubic-bezier(0.4, 0, 0.2, 1) both slide-to-left;
   }
   ::view-transition-new(slide-it) {
     animation: 420ms cubic-bezier(0, 0, 0.2, 1) 90ms both fade-in,
     600ms cubic-bezier(0.4, 0, 0.2, 1) both slide-from-right;
   }

   /* tie the view transition to a given CSS class */
   .sample-transition {
       view-transition-name: slide-it;
   }
    
</style>

<div class="sample-transition" style="padding: 24px">

# Initial Content

Swap It!

</div>

Assuming you are looking at this page in Chrome 111+, you should see the content above slide gracefully out to the left and be replaced by new content sliding in from the right. Nice!

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

Hey now, that’s pretty neat, and, once you get your head around the concept, not all that much work! This new API shows a lot of promise.

View Transitions are an exciting new technology that we feel can dramatically level the playing field between <a href="https://htmx.org/essays/hypermedia-driven-applications/" rel="noopener" target="_blank">Hypermedia Driven Applications</a> and the more prevalent SPA architecture used today.

By doing away with the ugly “ka-chunk” of Web 1.0 applications, the aesthetic advantages of the SPA approach will be diminished, and we can make decisions less around “sizzle” and focus more on the actual <a href="https://htmx.org/essays/when-to-use-hypermedia/" rel="noopener" target="_blank">technical tradeoffs</a> associated with various architectures.

We are looking forward to when View Transitions are available in vanilla HTML, but, until then, you can start playing with them in htmx, today!

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

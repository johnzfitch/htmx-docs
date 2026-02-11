# animations__d7230534

- Source URL: https://htmx.org/examples/animations/
- Source file: `fetch/htmx_org_d7230534.html`
- Hash: `d7230534`
- Category: `htmx/examples`

<div class="top-nav">

<div class="c">

<div class="menu">

<div class="logo-wrapper">

<a href="/" class="logo light">&lt;<strong>/</strong>&gt; htm<strong>x</strong></a> <img src="data:image/svg+xml;base64,PHN2ZyBfPSJvbiBjbGljayB0b2dnbGUgLnNob3cgb24gI25hdiIgY2xhc3M9ImhhbWJ1cmdlciIgdmlld2JveD0iMCAwIDEwMCA4MCIgd2lkdGg9IjI1IiBoZWlnaHQ9IjI1IiBzdHlsZT0ibWFyZ2luLWJvdHRvbTotNXB4Ij4KICAgICAgICAgICAgICAgICAgICA8cmVjdCB3aWR0aD0iMTAwIiBoZWlnaHQ9IjIwIiBzdHlsZT0iZmlsbDpyZ2IoNTIsIDEwMSwgMTY0KSIgcng9IjEwIiAvPgogICAgICAgICAgICAgICAgICAgIDxyZWN0IHk9IjMwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjIwIiBzdHlsZT0iZmlsbDpyZ2IoNTIsIDEwMSwgMTY0KSIgcng9IjEwIiAvPgogICAgICAgICAgICAgICAgICAgIDxyZWN0IHk9IjYwIiB3aWR0aD0iMTAwIiBoZWlnaHQ9IjIwIiBzdHlsZT0iZmlsbDpyZ2IoNTIsIDEwMSwgMTY0KSIgcng9IjEwIiAvPgogICAgICAgICAgICAgICAgPC9zdmc+" class="hamburger" />

</div>

<div id="nav" class="navigation">

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

# Animations

htmx is designed to allow you to use <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions" rel="noopener" target="_blank">CSS transitions</a> to add smooth animations and transitions to your web page using only CSS and HTML. Below are a few examples of various animation techniques.

htmx also allows you to use the new <a href="https://developer.mozilla.org/en-US/docs/Web/API/View_Transitions_API" rel="noopener" target="_blank">View Transitions API</a> for creating animations.

### <a href="#basic" class="zola-anchor" aria-label="Anchor link for: basic">Basic CSS Animations</a>

### <a href="#color-throb" class="zola-anchor" aria-label="Anchor link for: color-throb">Color Throb</a>

The simplest animation technique in htmx is to keep the `id` of an element stable across a content swap. If the `id` of an element is kept stable, htmx will swap it in such a way that CSS transitions can be written between the old version of the element and the new one.

Consider this div:

``` html
<style>
.smooth {
  transition: all 1s ease-in;
}
</style>
<div id="color-demo" class="smooth" style="color:red"
      hx-get="/colors" hx-swap="outerHTML" hx-trigger="every 1s">
  Color Swap Demo
</div>
```

This div will poll every second and will get replaced with new content which changes the `color` style to a new value (e.g. `blue`):

``` html
<div id="color-demo" class="smooth" style="color:blue"
      hx-get="/colors" hx-swap="outerHTML" hx-trigger="every 1s">
  Color Swap Demo
</div>
```

Because the div has a stable id, `color-demo`, htmx will structure the swap such that a CSS transition, defined on the `.smooth` class, applies to the style update from `red` to `blue`, and smoothly transitions between them.

#### <a href="#throb-demo" class="zola-anchor" aria-label="Anchor link for: throb-demo">Demo</a>

<style>
.smooth {
  transition: all 1s ease-in;
}
</style>

<div id="color-demo" class="smooth" style="color:red" hx-get="/colors" hx-swap="outerHTML" hx-trigger="every 1s">

Color Swap Demo

</div>

### <a href="#smooth-progress-bar" class="zola-anchor" aria-label="Anchor link for: smooth-progress-bar">Smooth Progress Bar</a>

The [Progress Bar](https://htmx.org/examples/progress-bar/) demo uses this basic CSS animation technique as well, by updating the `length` property of a progress bar element, allowing for a smooth animation.

## <a href="#swapping" class="zola-anchor" aria-label="Anchor link for: swapping">Swap Transitions</a>

### <a href="#fade-out-on-swap" class="zola-anchor" aria-label="Anchor link for: fade-out-on-swap">Fade Out On Swap</a>

If you want to fade out an element that is going to be removed when the request ends, you want to take advantage of the `htmx-swapping` class with some CSS and extend the swap phase to be long enough for your animation to complete. This can be done like so:

``` html
<style>
.fade-me-out.htmx-swapping {
  opacity: 0;
  transition: opacity 1s ease-out;
}
</style>
<button class="fade-me-out"
        hx-delete="/fade_out_demo"
        hx-swap="outerHTML swap:1s">
        Fade Me Out
</button>
```

#### <a href="#fade-swap-demo" class="zola-anchor" aria-label="Anchor link for: fade-swap-demo">Demo</a>

<style>
.fade-me-out.htmx-swapping {
  opacity: 0;
  transition: opacity 1s ease-out;
}
</style>

Delete Me

## <a href="#settling" class="zola-anchor" aria-label="Anchor link for: settling">Settling Transitions</a>

### <a href="#fade-in-on-addition" class="zola-anchor" aria-label="Anchor link for: fade-in-on-addition">Fade In On Addition</a>

Building on the last example, we can fade in the new content by using the `htmx-added` class during the settle phase. You can also write CSS transitions against the target, rather than the new content, by using the `htmx-settling` class.

``` html
<style>
#fade-me-in.htmx-added {
  opacity: 0;
}
#fade-me-in {
  opacity: 1;
  transition: opacity 1s ease-out;
}
</style>
<button id="fade-me-in"
        class="btn primary"
        hx-post="/fade_in_demo"
        hx-swap="outerHTML settle:1s">
        Fade Me In
</button>
```

#### <a href="#fade-settle-demo" class="zola-anchor" aria-label="Anchor link for: fade-settle-demo">Demo</a>

<style>
#fade-me-in.htmx-added {
  opacity: 0;
}
#fade-me-in {
  opacity: 1;
  transition: opacity 1s ease-out;
}
</style>

Fade Me In

## <a href="#request" class="zola-anchor" aria-label="Anchor link for: request">Request In Flight Animation</a>

You can also take advantage of the `htmx-request` class, which is applied to the element that triggers a request. Below is a form that on submit will change its look to indicate that a request is being processed:

``` html
<style>
  form.htmx-request {
    opacity: .5;
    transition: opacity 300ms linear;
  }
</style>
<form hx-post="/name" hx-swap="outerHTML">
<label>Name:</label><input name="name"><br/>
<button class="btn primary">Submit</button>
</form>
```

#### <a href="#request-demo" class="zola-anchor" aria-label="Anchor link for: request-demo">Demo</a>

<style>
  form.htmx-request {
    opacity: .5;
    transition: opacity 300ms linear;
  }
</style>

<div aria-live="polite">

Name:\

Submit

</div>

## <a href="#using-the-htmx-class-tools-extension" class="zola-anchor" aria-label="Anchor link for: using-the-htmx-class-tools-extension">Using the htmx <code>class-tools</code> Extension</a>

Many interesting animations can be created by using the <a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/class-tools/README.md" rel="noopener" target="_blank"><code>class-tools</code></a> extension.

Here is an example that toggles the opacity of a div. Note that we set the toggle time to be a bit longer than the transition time. This avoids flickering that can happen if the transition is interrupted by a class change.

``` html
<style>
.demo.faded {
  opacity:.3;
}
.demo {
  opacity:1;
  transition: opacity ease-in 900ms;
}
</style>
<div class="demo" classes="toggle faded:1s">Toggle Demo</div>
```

#### <a href="#class-tools-demo" class="zola-anchor" aria-label="Anchor link for: class-tools-demo">Demo</a>

<style>
.demo.faded {
  opacity:.3;
}
.demo {
  opacity:1;
  transition: opacity ease-in 900ms;
}
</style>

<div class="demo" classes="toggle faded:1s">

Toggle Demo

</div>

### <a href="#view-transitions" class="zola-anchor" aria-label="Anchor link for: view-transitions">Using the View Transition API</a>

htmx provides access to the new <a href="https://developer.mozilla.org/en-US/docs/Web/API/View_Transitions_API" rel="noopener" target="_blank">View Transitions API</a> via the `transition` option of the [`hx-swap`](/attributes/hx-swap) attribute.

Below is an example of a swap that uses a view transition. The transition is tied to the outer div via a `view-transition-name` property in CSS, and that transition is defined in terms of `::view-transition-old` and `::view-transition-new`, using `@keyframes` to define the animation. (Fuller details on the View Transition API can be found on the <a href="https://developer.chrome.com/docs/web-platform/view-transitions/" rel="noopener" target="_blank">Chrome Developer Page</a> on them.)

The old content of this transition should slide out to the left and the new content should slide in from the right.

Note that, as of this writing, the visual transition will only occur on Chrome 111+, but more browsers are expected to implement this feature in the near future.

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

   .slide-it {
     view-transition-name: slide-it;
   }

   ::view-transition-old(slide-it) {
     animation: 180ms cubic-bezier(0.4, 0, 1, 1) both fade-out,
     600ms cubic-bezier(0.4, 0, 0.2, 1) both slide-to-left;
   }
   ::view-transition-new(slide-it) {
     animation: 420ms cubic-bezier(0, 0, 0.2, 1) 90ms both fade-in,
     600ms cubic-bezier(0.4, 0, 0.2, 1) both slide-from-right;
   }
</style>


<div class="slide-it">
   <h1>Initial Content</h1>
   <button class="btn primary" hx-get="/new-content" hx-swap="innerHTML transition:true" hx-target="closest div">
     Swap It!
   </button>
</div>
```

#### <a href="#demo" class="zola-anchor" aria-label="Anchor link for: demo">Demo</a>

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

   .slide-it {
     view-transition-name: slide-it;
   }

   ::view-transition-old(slide-it) {
     animation: 180ms cubic-bezier(0.4, 0, 1, 1) both fade-out,
     600ms cubic-bezier(0.4, 0, 0.2, 1) both slide-to-left;
   }
   ::view-transition-new(slide-it) {
     animation: 420ms cubic-bezier(0, 0, 0.2, 1) 90ms both fade-in,
     600ms cubic-bezier(0.4, 0, 0.2, 1) both slide-from-right;
   }
</style>

<div class="slide-it">

# Initial Content

Swap It!

</div>

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

You can use the techniques above to create quite a few interesting and pleasing effects with plain old HTML while using htmx.

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

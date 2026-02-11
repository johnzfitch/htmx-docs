# index__dadb0a55

- Source URL: https://htmx.org/docs/
- Source file: `fetch/htmx_org_dadb0a55.html`
- Hash: `dadb0a55`
- Category: `htmx/docs`

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

<div class="c content wide-content">

# Documentation

<div class="row">

<div class="2 col nav">

**Contents**

<div id="contents">

- [introduction](https://htmx.org/docs/#introduction)
- [installing](https://htmx.org/docs/#installing)
- [ajax](https://htmx.org/docs/#ajax)
  - [triggers](https://htmx.org/docs/#triggers)
    - [trigger modifiers](https://htmx.org/docs/#trigger-modifiers)
    - [trigger filters](https://htmx.org/docs/#trigger-filters)
    - [special events](https://htmx.org/docs/#special-events)
    - [polling](https://htmx.org/docs/#polling)
    - [load polling](https://htmx.org/docs/#load_polling)
  - [indicators](https://htmx.org/docs/#indicators)
  - [targets](https://htmx.org/docs/#targets)
  - [swapping](https://htmx.org/docs/#swapping)
  - [synchronization](https://htmx.org/docs/#synchronization)
  - [css transitions](https://htmx.org/docs/#css_transitions)
  - [out of band swaps](https://htmx.org/docs/#oob_swaps)
  - [parameters](https://htmx.org/docs/#parameters)
  - [confirming](https://htmx.org/docs/#confirming)
- [inheritance](https://htmx.org/docs/#inheritance)
- [boosting](https://htmx.org/docs/#boosting)
- [websockets & SSE](https://htmx.org/docs/#websockets-and-sse)
- [history](https://htmx.org/docs/#history)
- [requests & responses](https://htmx.org/docs/#requests)
- [validation](https://htmx.org/docs/#validation)
- [animations](https://htmx.org/docs/#animations)
- [extensions](https://htmx.org/docs/#extensions)
- [events & logging](https://htmx.org/docs/#events)
- [debugging](https://htmx.org/docs/#debugging)
- [scripting](https://htmx.org/docs/#scripting)
  - [hx-on attribute](https://htmx.org/docs/#hx-on)
- [3rd party integration](https://htmx.org/docs/#3rd-party)
  - [Web Components](https://htmx.org/docs/#web-components)
- [caching](https://htmx.org/docs/#caching)
- [security](https://htmx.org/docs/#security)
- [configuring](https://htmx.org/docs/#config)

</div>

</div>

<div class="10 col">

## <a href="#introduction" class="zola-anchor" aria-label="Anchor link for: introduction">htmx in a Nutshell</a>

htmx is a library that allows you to access modern browser features directly from HTML, rather than using javascript.

To understand htmx, first let’s take a look at an anchor tag:

``` html
<a href="/blog">Blog</a>
```

This anchor tag tells a browser:

> “When a user clicks on this link, issue an HTTP GET request to ‘/blog’ and load the response content into the browser window”.

With that in mind, consider the following bit of HTML:

``` html
<button hx-post="/clicked"
    hx-trigger="click"
    hx-target="#parent-div"
    hx-swap="outerHTML">
    Click Me!
</button>
```

This tells htmx:

> “When a user clicks on this button, issue an HTTP POST request to ‘/clicked’ and use the content from the response to replace the element with the id `parent-div` in the DOM”

htmx extends and generalizes the core idea of HTML as a hypertext, opening up many more possibilities directly within the language:

- Now any element, not just anchors and forms, can issue an HTTP request
- Now any event, not just clicks or form submissions, can trigger requests
- Now any <a href="https://en.wikipedia.org/wiki/HTTP_Verbs" rel="noopener" target="_blank">HTTP verb</a>, not just `GET` and `POST`, can be used
- Now any element, not just the entire window, can be the target for update by the request

Note that when you are using htmx, on the server side you typically respond with *HTML*, not *JSON*. This keeps you firmly within the <a href="https://roy.gbiv.com/pubs/dissertation/rest_arch_style.htm" rel="noopener" target="_blank">original web programming model</a>, using <a href="https://en.wikipedia.org/wiki/HATEOAS" rel="noopener" target="_blank">Hypertext As The Engine Of Application State</a> without even needing to really understand that concept.

It’s worth mentioning that, if you prefer, you can use the <a href="https://html.spec.whatwg.org/multipage/dom.html#attr-data-*" rel="noopener" target="_blank"><code>data-</code></a> prefix when using htmx:

``` html
<a data-hx-post="/click">Click Me!</a>
```

If you understand the concepts around htmx and want to see the quirks of the library, please see our [QUIRKS](https://htmx.org/quirks/) page.

## <a href="#1-x-to-2-x-migration-guide" class="zola-anchor" aria-label="Anchor link for: 1-x-to-2-x-migration-guide">1.x to 2.x Migration Guide</a>

<a href="https://v1.htmx.org" rel="noopener" target="_blank">Version 1</a> of htmx is still supported and supports IE11, but the latest version of htmx is 2.x.

If you are migrating to htmx 2.x from <a href="https://v1.htmx.org" rel="noopener" target="_blank">htmx 1.x</a>, please see the [htmx 1.x migration guide](https://htmx.org/migration-guide-htmx-1/).

If you are migrating to htmx from intercooler.js, please see the [intercooler migration guide](https://htmx.org/migration-guide-intercooler/).

## <a href="#installing" class="zola-anchor" aria-label="Anchor link for: installing">Installing</a>

Htmx is a dependency-free, browser-oriented javascript library. This means that using it is as simple as adding a `<script>` tag to your document head. There is no need for a build system to use it.

### <a href="#via-a-cdn-e-g-jsdelivr" class="zola-anchor" aria-label="Anchor link for: via-a-cdn-e-g-jsdelivr">Via A CDN (e.g. jsDelivr)</a>

The fastest way to get going with htmx is to load it via a CDN. You can simply add this to your head tag and get going:

``` html
<script src="https://cdn.jsdelivr.net/npm/htmx.org@2.0.8/dist/htmx.min.js" integrity="sha384-/TgkGk7p307TH7EXJDuUlgG3Ce1UVolAOFopFekQkkXihi5u/6OCvVKyz1W+idaz" crossorigin="anonymous"></script>
```

An unminified version is also available as well:

``` html
<script src="https://cdn.jsdelivr.net/npm/htmx.org@2.0.8/dist/htmx.js" integrity="sha384-ezjq8118wdwdRMj+nX4bevEi+cDLTbhLAeFF688VK8tPDGeLUe0WoY2MZtSla72F" crossorigin="anonymous"></script>
```

While the CDN approach is extremely simple, you may want to consider <a href="https://blog.wesleyac.com/posts/why-not-javascript-cdn" rel="noopener" target="_blank">not using CDNs in production</a>.

### <a href="#download-a-copy" class="zola-anchor" aria-label="Anchor link for: download-a-copy">Download a copy</a>

The next easiest way to install htmx is to simply copy it into your project.

Download `htmx.min.js` <a href="https://cdn.jsdelivr.net/npm/htmx.org@2.0.8/dist/htmx.min.js" rel="noopener" target="_blank">from jsDelivr</a> and add it to the appropriate directory in your project and include it where necessary with a `<script>` tag:

``` html
<script src="/path/to/htmx.min.js"></script>
```

### <a href="#npm" class="zola-anchor" aria-label="Anchor link for: npm">npm</a>

For npm-style build systems, you can install htmx via <a href="https://www.npmjs.com/" rel="noopener" target="_blank">npm</a>:

``` sh
npm install htmx.org@2.0.8
```

After installing, you’ll need to use appropriate tooling to use `node_modules/htmx.org/dist/htmx.js` (or `.min.js`). For example, you might bundle htmx with some extensions and project-specific code.

### <a href="#webpack" class="zola-anchor" aria-label="Anchor link for: webpack">Webpack</a>

If you are using webpack to manage your javascript:

- Install `htmx` via your favourite package manager (like npm or yarn)
- Add the import to your `index.js`

``` js
import 'htmx.org';
```

If you want to use the global `htmx` variable (recommended), you need to inject it to the window scope:

- Create a custom JS file
- Import this file to your `index.js` (below the import from step 2)

``` js
import 'path/to/my_custom.js';
```

- Then add this code to the file:

``` js
window.htmx = require('htmx.org');
```

- Finally, rebuild your bundle

## <a href="#ajax" class="zola-anchor" aria-label="Anchor link for: ajax">AJAX</a>

The core of htmx is a set of attributes that allow you to issue AJAX requests directly from HTML:

| Attribute | Description |
|----|----|
| [hx-get](https://htmx.org/attributes/hx-get/) | Issues a `GET` request to the given URL |
| [hx-post](https://htmx.org/attributes/hx-post/) | Issues a `POST` request to the given URL |
| [hx-put](https://htmx.org/attributes/hx-put/) | Issues a `PUT` request to the given URL |
| [hx-patch](https://htmx.org/attributes/hx-patch/) | Issues a `PATCH` request to the given URL |
| [hx-delete](https://htmx.org/attributes/hx-delete/) | Issues a `DELETE` request to the given URL |

Each of these attributes takes a URL to issue an AJAX request to. The element will issue a request of the specified type to the given URL when the element is [triggered](https://htmx.org/docs/#triggers):

``` html
<button hx-put="/messages">
    Put To Messages
</button>
```

This tells the browser:

> When a user clicks on this button, issue a PUT request to the URL /messages and load the response into the button

### <a href="#triggers" class="zola-anchor" aria-label="Anchor link for: triggers">Triggering Requests</a>

By default, AJAX requests are triggered by the “natural” event of an element:

- `input`, `textarea` & `select` are triggered on the `change` event
- `form` is triggered on the `submit` event
- everything else is triggered by the `click` event

If you want different behavior you can use the [hx-trigger](https://htmx.org/attributes/hx-trigger/) attribute to specify which event will cause the request.

Here is a `div` that posts to `/mouse_entered` when a mouse enters it:

``` html
<div hx-post="/mouse_entered" hx-trigger="mouseenter">
    [Here Mouse, Mouse!]
</div>
```

#### <a href="#trigger-modifiers" class="zola-anchor" aria-label="Anchor link for: trigger-modifiers">Trigger Modifiers</a>

A trigger can also have a few additional modifiers that change its behavior. For example, if you want a request to only happen once, you can use the `once` modifier for the trigger:

``` html
<div hx-post="/mouse_entered" hx-trigger="mouseenter once">
    [Here Mouse, Mouse!]
</div>
```

Other modifiers you can use for triggers are:

- `changed` - only issue a request if the value of the element has changed
- `delay:<time interval>` - wait the given amount of time (e.g. `1s`) before issuing the request. If the event triggers again, the countdown is reset.
- `throttle:<time interval>` - wait the given amount of time (e.g. `1s`) before issuing the request. Unlike `delay` if a new event occurs before the time limit is hit the event will be discarded, so the request will trigger at the end of the time period.
- `from:<CSS Selector>` - listen for the event on a different element. This can be used for things like keyboard shortcuts. Note that this CSS selector is not re-evaluated if the page changes.

You can use these attributes to implement many common UX patterns, such as [Active Search](https://htmx.org/examples/active-search/):

``` html
<input type="text" name="q"
    hx-get="/trigger_delay"
    hx-trigger="keyup changed delay:500ms"
    hx-target="#search-results"
    placeholder="Search...">
<div id="search-results"></div>
```

This input will issue a request 500 milliseconds after a key up event if the input has been changed and inserts the results into the `div` with the id `search-results`.

Multiple triggers can be specified in the [hx-trigger](https://htmx.org/attributes/hx-trigger/) attribute, separated by commas.

#### <a href="#trigger-filters" class="zola-anchor" aria-label="Anchor link for: trigger-filters">Trigger Filters</a>

You may also apply trigger filters by using square brackets after the event name, enclosing a javascript expression that will be evaluated. If the expression evaluates to `true` the event will trigger, otherwise it will not.

Here is an example that triggers only on a Control-Click of the element

``` html
<div hx-get="/clicked" hx-trigger="click[ctrlKey]">
    Control Click Me
</div>
```

Properties like `ctrlKey` will be resolved against the triggering event first, then against the global scope. The `this` symbol will be set to the current element.

#### <a href="#special-events" class="zola-anchor" aria-label="Anchor link for: special-events">Special Events</a>

htmx provides a few special events for use in [hx-trigger](https://htmx.org/attributes/hx-trigger/):

- `load` - fires once when the element is first loaded
- `revealed` - fires once when an element first scrolls into the viewport
- `intersect` - fires once when an element first intersects the viewport. This supports two additional options:
  - `root:<selector>` - a CSS selector of the root element for intersection
  - `threshold:<float>` - a floating point number between 0.0 and 1.0, indicating what amount of intersection to fire the event on

You can also use custom events to trigger requests if you have an advanced use case.

#### <a href="#polling" class="zola-anchor" aria-label="Anchor link for: polling">Polling</a>

If you want an element to poll the given URL rather than wait for an event, you can use the `every` syntax with the [`hx-trigger`](https://htmx.org/attributes/hx-trigger/) attribute:

``` html
<div hx-get="/news" hx-trigger="every 2s"></div>
```

This tells htmx

> Every 2 seconds, issue a GET to /news and load the response into the div

If you want to stop polling from a server response you can respond with the HTTP response code <a href="https://en.wikipedia.org/wiki/86_(term)" rel="noopener" target="_blank"><code>286</code></a> and the element will cancel the polling.

#### <a href="#load_polling" class="zola-anchor" aria-label="Anchor link for: load_polling">Load Polling</a>

Another technique that can be used to achieve polling in htmx is “load polling”, where an element specifies a `load` trigger along with a delay, and replaces itself with the response:

``` html
<div hx-get="/messages"
    hx-trigger="load delay:1s"
    hx-swap="outerHTML">
</div>
```

If the `/messages` end point keeps returning a div set up this way, it will keep “polling” back to the URL every second.

Load polling can be useful in situations where a poll has an end point at which point the polling terminates, such as when you are showing the user a [progress bar](https://htmx.org/examples/progress-bar/).

### <a href="#indicators" class="zola-anchor" aria-label="Anchor link for: indicators">Request Indicators</a>

When an AJAX request is issued it is often good to let the user know that something is happening since the browser will not give them any feedback. You can accomplish this in htmx by using `htmx-indicator` class.

The `htmx-indicator` class is defined so that the opacity of any element with this class is 0 by default, making it invisible but present in the DOM.

When htmx issues a request, it will put a `htmx-request` class onto an element (either the requesting element or another element, if specified). The `htmx-request` class will cause a child element with the `htmx-indicator` class on it to transition to an opacity of 1, showing the indicator.

``` html
<button hx-get="/click">
    Click Me!
    <img class="htmx-indicator" src="/spinner.gif" alt="Loading...">
</button>
```

Here we have a button. When it is clicked the `htmx-request` class will be added to it, which will reveal the spinner gif element. (I like <a href="http://samherbert.net/svg-loaders/" rel="noopener" target="_blank">SVG spinners</a> these days.)

While the `htmx-indicator` class uses opacity to hide and show the progress indicator, if you would prefer another mechanism you can create your own CSS transition like so:

``` css
.htmx-indicator{
    display:none;
}
.htmx-request .htmx-indicator{
    display:inline;
}
.htmx-request.htmx-indicator{
    display:inline;
}
```

If you want the `htmx-request` class added to a different element, you can use the [hx-indicator](https://htmx.org/attributes/hx-indicator/) attribute with a CSS selector to do so:

``` html
<div>
    <button hx-get="/click" hx-indicator="#indicator">
        Click Me!
    </button>
    <img id="indicator" class="htmx-indicator" src="/spinner.gif" alt="Loading..."/>
</div>
```

Here we call out the indicator explicitly by id. Note that we could have placed the class on the parent `div` as well and had the same effect.

You can also add the <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/disabled" rel="noopener" target="_blank"><code>disabled</code> attribute</a> to elements for the duration of a request by using the [hx-disabled-elt](https://htmx.org/attributes/hx-disabled-elt/) attribute.

### <a href="#targets" class="zola-anchor" aria-label="Anchor link for: targets">Targets</a>

If you want the response to be loaded into a different element other than the one that made the request, you can use the [hx-target](https://htmx.org/attributes/hx-target/) attribute, which takes a CSS selector. Looking back at our Live Search example:

``` html
<input type="text" name="q"
    hx-get="/trigger_delay"
    hx-trigger="keyup delay:500ms changed"
    hx-target="#search-results"
    placeholder="Search...">
<div id="search-results"></div>
```

You can see that the results from the search are going to be loaded into `div#search-results`, rather than into the input tag.

#### <a href="#extended-css-selectors" class="zola-anchor" aria-label="Anchor link for: extended-css-selectors">Extended CSS Selectors</a>

`hx-target`, and most attributes that take a CSS selector, support an “extended” CSS syntax:

- You can use the `this` keyword, which indicates that the element that the `hx-target` attribute is on is the target
- The `closest <CSS selector>` syntax will find the <a href="https://developer.mozilla.org/docs/Web/API/Element/closest" rel="noopener" target="_blank">closest</a> ancestor element or itself, that matches the given CSS selector. (e.g. `closest tr` will target the closest table row to the element)
- The `next <CSS selector>` syntax will find the next element in the DOM matching the given CSS selector.
- The `previous <CSS selector>` syntax will find the previous element in the DOM matching the given CSS selector.
- `find <CSS selector>` which will find the first child descendant element that matches the given CSS selector. (e.g `find tr` would target the first child descendant row to the element)

In addition, a CSS selector may be wrapped in `<` and `/>` characters, mimicking the <a href="https://hyperscript.org/expressions/query-reference/" rel="noopener" target="_blank">query literal</a> syntax of hyperscript.

Relative targets like this can be useful for creating flexible user interfaces without peppering your DOM with lots of `id` attributes.

### <a href="#swapping" class="zola-anchor" aria-label="Anchor link for: swapping">Swapping</a>

htmx offers a few different ways to swap the HTML returned into the DOM. By default, the content replaces the `innerHTML` of the target element. You can modify this by using the [hx-swap](https://htmx.org/attributes/hx-swap/) attribute with any of the following values:

| Name | Description |
|----|----|
| `innerHTML` | the default, puts the content inside the target element |
| `outerHTML` | replaces the entire target element with the returned content |
| `afterbegin` | prepends the content before the first child inside the target |
| `beforebegin` | prepends the content before the target in the target’s parent element |
| `beforeend` | appends the content after the last child inside the target |
| `afterend` | appends the content after the target in the target’s parent element |
| `delete` | deletes the target element regardless of the response |
| `none` | does not append content from response ([Out of Band Swaps](https://htmx.org/docs/#oob_swaps) and [Response Headers](https://htmx.org/docs/#response-headers) will still be processed) |

#### <a href="#morphing" class="zola-anchor" aria-label="Anchor link for: morphing">Morph Swaps</a>

In addition to the standard swap mechanisms above, htmx also supports *morphing* swaps, via extensions. Morphing swaps attempt to *merge* new content into the existing DOM, rather than simply replacing it. They often do a better job preserving things like focus, video state, etc. by mutating existing nodes in-place during the swap operation, at the cost of more CPU.

The following extensions are available for morph-style swaps:

- [Idiomorph](/extensions/idiomorph) - A morphing algorithm created by the htmx developers.
- <a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/morphdom-swap/README.md" rel="noopener" target="_blank">Morphdom Swap</a> - Based on the <a href="https://github.com/patrick-steele-idem/morphdom" rel="noopener" target="_blank">morphdom</a>, the original DOM morphing library.
- <a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/alpine-morph/README.md" rel="noopener" target="_blank">Alpine-morph</a> - Based on the <a href="https://alpinejs.dev/plugins/morph" rel="noopener" target="_blank">alpine morph</a> plugin, plays well with alpine.js

#### <a href="#view-transitions" class="zola-anchor" aria-label="Anchor link for: view-transitions">View Transitions</a>

The new, experimental <a href="https://developer.mozilla.org/en-US/docs/Web/API/View_Transitions_API" rel="noopener" target="_blank">View Transitions API</a> gives developers a way to create an animated transition between different DOM states. It is still in active development and is not available in all browsers, but htmx provides a way to work with this new API that falls back to the non-transition mechanism if the API is not available in a given browser.

You can experiment with this new API using the following approaches:

- Set the `htmx.config.globalViewTransitions` config variable to `true` to use transitions for all swaps
- Use the `transition:true` option in the `hx-swap` attribute
- If an element swap is going to be transitioned due to either of the above configurations, you may catch the `htmx:beforeTransition` event and call `preventDefault()` on it to cancel the transition.

View Transitions can be configured using CSS, as outlined in <a href="https://developer.chrome.com/docs/web-platform/view-transitions/#simple-customization" rel="noopener" target="_blank">the Chrome documentation for the feature</a>.

You can see a view transition example on the [Animation Examples](/examples/animations#view-transitions) page.

#### <a href="#swap-options" class="zola-anchor" aria-label="Anchor link for: swap-options">Swap Options</a>

The [hx-swap](https://htmx.org/attributes/hx-swap/) attribute supports many options for tuning the swapping behavior of htmx. For example, by default htmx will swap in the title of a title tag found anywhere in the new content. You can turn this behavior off by setting the `ignoreTitle` modifier to true:

``` html
    <button hx-post="/like" hx-swap="outerHTML ignoreTitle:true">Like</button>
```

The modifiers available on `hx-swap` are:

| Option | Description |
|----|----|
| `transition` | `true` or `false`, whether to use the view transition API for this swap |
| `swap` | The swap delay to use (e.g. `100ms`) between when old content is cleared and the new content is inserted |
| `settle` | The settle delay to use (e.g. `100ms`) between when new content is inserted and when it is settled |
| `ignoreTitle` | If set to `true`, any title found in the new content will be ignored and not update the document title |
| `scroll` | `top` or `bottom`, will scroll the target element to its top or bottom |
| `show` | `top` or `bottom`, will scroll the target element’s top or bottom into view |

All swap modifiers appear after the swap style is specified, and are colon-separated.

See the [hx-swap](https://htmx.org/attributes/hx-swap/) documentation for more details on these options.

### <a href="#synchronization" class="zola-anchor" aria-label="Anchor link for: synchronization">Synchronization</a>

Often you want to coordinate the requests between two elements. For example, you may want a request from one element to supersede the request of another element, or to wait until the other element’s request has finished.

htmx offers a [`hx-sync`](https://htmx.org/attributes/hx-sync/) attribute to help you accomplish this.

Consider a race condition between a form submission and an individual input’s validation request in this HTML:

``` html
<form hx-post="/store">
    <input id="title" name="title" type="text"
        hx-post="/validate"
        hx-trigger="change">
    <button type="submit">Submit</button>
</form>
```

Without using `hx-sync`, filling out the input and immediately submitting the form triggers two parallel requests to `/validate` and `/store`.

Using `hx-sync="closest form:abort"` on the input will watch for requests on the form and abort the input’s request if a form request is present or starts while the input request is in flight:

``` html
<form hx-post="/store">
    <input id="title" name="title" type="text"
        hx-post="/validate"
        hx-trigger="change"
        hx-sync="closest form:abort">
    <button type="submit">Submit</button>
</form>
```

This resolves the synchronization between the two elements in a declarative way.

htmx also supports a programmatic way to cancel requests: you can send the `htmx:abort` event to an element to cancel any in-flight requests:

``` html
<button id="request-button" hx-post="/example">
    Issue Request
</button>
<button onclick="htmx.trigger('#request-button', 'htmx:abort')">
    Cancel Request
</button>
```

More examples and details can be found on the [`hx-sync` attribute page.](https://htmx.org/attributes/hx-sync/)

### <a href="#css_transitions" class="zola-anchor" aria-label="Anchor link for: css_transitions">CSS Transitions</a>

htmx makes it easy to use <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions" rel="noopener" target="_blank">CSS Transitions</a> without javascript. Consider this HTML content:

``` html
<div id="div1">Original Content</div>
```

Imagine this content is replaced by htmx via an ajax request with this new content:

``` html
<div id="div1" class="red">New Content</div>
```

Note two things:

- The div has the *same* id in the original and in the new content
- The `red` class has been added to the new content

Given this situation, we can write a CSS transition from the old state to the new state:

``` css
.red {
    color: red;
    transition: all ease-in 1s ;
}
```

When htmx swaps in this new content, it will do so in such a way that the CSS transition will apply to the new content, giving you a nice, smooth transition to the new state.

So, in summary, all you need to do to use CSS transitions for an element is keep its `id` stable across requests!

You can see the [Animation Examples](https://htmx.org/examples/animations/) for more details and live demonstrations.

#### <a href="#details" class="zola-anchor" aria-label="Anchor link for: details">Details</a>

To understand how CSS transitions actually work in htmx, you must understand the underlying swap & settle model that htmx uses.

When new content is received from a server, before the content is swapped in, the existing content of the page is examined for elements that match by the `id` attribute. If a match is found for an element in the new content, the attributes of the old content are copied onto the new element before the swap occurs. The new content is then swapped in, but with the *old* attribute values. Finally, the new attribute values are swapped in, after a “settle” delay (20ms by default). A little crazy, but this is what allows CSS transitions to work without any javascript by the developer.

### <a href="#oob_swaps" class="zola-anchor" aria-label="Anchor link for: oob_swaps">Out of Band Swaps</a>

If you want to swap content from a response directly into the DOM by using the `id` attribute you can use the [hx-swap-oob](https://htmx.org/attributes/hx-swap-oob/) attribute in the *response* html:

``` html
<div id="message" hx-swap-oob="true">Swap me directly!</div>
Additional Content
```

In this response, `div#message` would be swapped directly into the matching DOM element, while the additional content would be swapped into the target in the normal manner.

You can use this technique to “piggy-back” updates on other requests.

#### <a href="#troublesome-tables" class="zola-anchor" aria-label="Anchor link for: troublesome-tables">Troublesome Tables</a>

Table elements can be problematic when combined with out of band swaps, because, by the HTML spec, many can’t stand on their own in the DOM (e.g. `<tr>` or `<td>`).

To avoid this issue you can use a `template` tag to encapsulate these elements:

``` html
<template>
  <tr id="message" hx-swap-oob="true"><td>Joe</td><td>Smith</td></tr>
</template>
```

#### <a href="#selecting-content-to-swap" class="zola-anchor" aria-label="Anchor link for: selecting-content-to-swap">Selecting Content To Swap</a>

If you want to select a subset of the response HTML to swap into the target, you can use the [hx-select](https://htmx.org/attributes/hx-select/) attribute, which takes a CSS selector and selects the matching elements from the response.

You can also pick out pieces of content for an out-of-band swap by using the [hx-select-oob](https://htmx.org/attributes/hx-select-oob/) attribute, which takes a list of element IDs to pick out and swap.

#### <a href="#preserving-content-during-a-swap" class="zola-anchor" aria-label="Anchor link for: preserving-content-during-a-swap">Preserving Content During A Swap</a>

If there is content that you wish to be preserved across swaps (e.g. a video player that you wish to remain playing even if a swap occurs) you can use the [hx-preserve](https://htmx.org/attributes/hx-preserve/) attribute on the elements you wish to be preserved.

### <a href="#parameters" class="zola-anchor" aria-label="Anchor link for: parameters">Parameters</a>

By default, an element that causes a request will include its value if it has one. If the element is a form it will include the values of all inputs within it.

As with HTML forms, the `name` attribute of the input is used as the parameter name in the request that htmx sends.

Additionally, if the element causes a non-`GET` request, the values of all the inputs of the associated form will be included (typically this is the nearest enclosing form, but could be different if e.g. `<button form="associated-form">` is used).

If you wish to include the values of other elements, you can use the [hx-include](https://htmx.org/attributes/hx-include/) attribute with a CSS selector of all the elements whose values you want to include in the request.

If you wish to filter out some parameters you can use the [hx-params](https://htmx.org/attributes/hx-params/) attribute.

Finally, if you want to programmatically modify the parameters, you can use the [htmx:configRequest](https://htmx.org/events/#htmx:configRequest) event.

#### <a href="#files" class="zola-anchor" aria-label="Anchor link for: files">File Upload</a>

If you wish to upload files via an htmx request, you can set the [hx-encoding](https://htmx.org/attributes/hx-encoding/) attribute to `multipart/form-data`. This will use a `FormData` object to submit the request, which will properly include the file in the request.

Note that depending on your server-side technology, you may have to handle requests with this type of body content very differently.

Note that htmx fires a `htmx:xhr:progress` event periodically based on the standard `progress` event during upload, which you can hook into to show the progress of the upload.

See the [examples section](https://htmx.org/examples/) for more advanced form patterns, including [progress bars](https://htmx.org/examples/file-upload/) and [error handling](https://htmx.org/examples/file-upload-input/).

#### <a href="#extra-values" class="zola-anchor" aria-label="Anchor link for: extra-values">Extra Values</a>

You can include extra values in a request using the [hx-vals](https://htmx.org/attributes/hx-vals/) (name-expression pairs in JSON format) and [hx-vars](https://htmx.org/attributes/hx-vars/) attributes (comma-separated name-expression pairs that are dynamically computed).

### <a href="#confirming" class="zola-anchor" aria-label="Anchor link for: confirming">Confirming Requests</a>

Often you will want to confirm an action before issuing a request. htmx supports the [`hx-confirm`](https://htmx.org/attributes/hx-confirm/) attribute, which allows you to confirm an action using a simple javascript dialog:

``` html
<button hx-delete="/account" hx-confirm="Are you sure you wish to delete your account?">
    Delete My Account
</button>
```

Using events you can implement more sophisticated confirmation dialogs. The [confirm example](https://htmx.org/examples/confirm/) shows how to use <a href="https://sweetalert2.github.io/" rel="noopener" target="_blank">sweetalert2</a> library for confirmation of htmx actions.

#### <a href="#confirming-requests-using-events" class="zola-anchor" aria-label="Anchor link for: confirming-requests-using-events">Confirming Requests Using Events</a>

Another option to do confirmation with is via the [`htmx:confirm` event](https://htmx.org/events/#htmx:confirm). This event is fired on *every* trigger for a request (not just on elements that have a `hx-confirm` attribute) and can be used to implement asynchronous confirmation of the request.

Here is an example using <a href="https://sweetalert.js.org/guides/" rel="noopener" target="_blank">sweet alert</a> on any element with a `confirm-with-sweet-alert='true'` attribute on it:

``` javascript
document.body.addEventListener('htmx:confirm', function(evt) {
  if (evt.target.matches("[confirm-with-sweet-alert='true']")) {
    evt.preventDefault();
    swal({
      title: "Are you sure?",
      text: "Are you sure you are sure?",
      icon: "warning",
      buttons: true,
      dangerMode: true,
    }).then((confirmed) => {
      if (confirmed) {
        evt.detail.issueRequest();
      }
    });
  }
});
```

## <a href="#inheritance" class="zola-anchor" aria-label="Anchor link for: inheritance">Attribute Inheritance</a>

Most attributes in htmx are inherited: they apply to the element they are on as well as any children elements. This allows you to “hoist” attributes up the DOM to avoid code duplication. Consider the following htmx:

``` html
<button hx-delete="/account" hx-confirm="Are you sure?">
    Delete My Account
</button>
<button hx-put="/account" hx-confirm="Are you sure?">
    Update My Account
</button>
```

Here we have a duplicate `hx-confirm` attribute. We can hoist this attribute to a parent element:

``` html
<div hx-confirm="Are you sure?">
    <button hx-delete="/account">
        Delete My Account
    </button>
    <button hx-put="/account">
        Update My Account
    </button>
</div>
```

This `hx-confirm` attribute will now apply to all htmx-powered elements within it.

Sometimes you wish to undo this inheritance. Consider if we had a cancel button to this group, but didn’t want it to be confirmed. We could add an `unset` directive on it like so:

``` html
<div hx-confirm="Are you sure?">
    <button hx-delete="/account">
        Delete My Account
    </button>
    <button hx-put="/account">
        Update My Account
    </button>
    <button hx-confirm="unset" hx-get="/">
        Cancel
    </button>
</div>
```

The top two buttons would then show a confirm dialog, but the bottom cancel button would not.

Inheritance can be disabled on a per-element and per-attribute basis using the [`hx-disinherit`](https://htmx.org/attributes/hx-disinherit/) attribute.

If you wish to disable attribute inheritance entirely, you can set the `htmx.config.disableInheritance` configuration variable to `true`. This will disable inheritance as a default, and allow you to specify inheritance explicitly with the [`hx-inherit`](https://htmx.org/attributes/hx-inherit/) attribute.

## <a href="#boosting" class="zola-anchor" aria-label="Anchor link for: boosting">Boosting</a>

Htmx supports “boosting” regular HTML anchors and forms with the [hx-boost](https://htmx.org/attributes/hx-boost/) attribute. This attribute will convert all anchor tags and forms into AJAX requests that, by default, target the body of the page.

Here is an example:

``` html
<div hx-boost="true">
    <a href="/blog">Blog</a>
</div>
```

The anchor tag in this div will issue an AJAX `GET` request to `/blog` and swap the response into the `body` tag.

### <a href="#progressive_enhancement" class="zola-anchor" aria-label="Anchor link for: progressive_enhancement">Progressive Enhancement</a>

A feature of `hx-boost` is that it degrades gracefully if javascript is not enabled: the links and forms continue to work, they simply don’t use ajax requests. This is known as <a href="https://developer.mozilla.org/en-US/docs/Glossary/Progressive_Enhancement" rel="noopener" target="_blank">Progressive Enhancement</a>, and it allows a wider audience to use your site’s functionality.

Other htmx patterns can be adapted to achieve progressive enhancement as well, but they will require more thought.

Consider the [active search](https://htmx.org/examples/active-search/) example. As it is written, it will not degrade gracefully: someone who does not have javascript enabled will not be able to use this feature. This is done for simplicity’s sake, to keep the example as brief as possible.

However, you could wrap the htmx-enhanced input in a form element:

``` html
<form action="/search" method="POST">
    <input class="form-control" type="search"
        name="search" placeholder="Begin typing to search users..."
        hx-post="/search"
        hx-trigger="keyup changed delay:500ms, search"
        hx-target="#search-results"
        hx-indicator=".htmx-indicator">
</form>
```

With this in place, javascript-enabled clients would still get the nice active-search UX, but non-javascript enabled clients would be able to hit the enter key and still search. Even better, you could add a “Search” button as well. You would then need to update the form with an `hx-post` that mirrored the `action` attribute, or perhaps use `hx-boost` on it.

You would need to check on the server side for the `HX-Request` header to differentiate between an htmx-driven and a regular request, to determine exactly what to render to the client.

Other patterns can be adapted similarly to achieve the progressive enhancement needs of your application.

As you can see, this requires more thought and more work. It also rules some functionality entirely out of bounds. These tradeoffs must be made by you, the developer, with respect to your projects goals and audience.

<a href="https://developer.mozilla.org/en-US/docs/Learn/Accessibility/What_is_accessibility" rel="noopener" target="_blank">Accessibility</a> is a concept closely related to progressive enhancement. Using progressive enhancement techniques such as `hx-boost` will make your htmx application more accessible to a wide array of users.

htmx-based applications are very similar to normal, non-AJAX driven web applications because htmx is HTML-oriented.

As such, the normal HTML accessibility recommendations apply. For example:

- Use semantic HTML as much as possible (i.e. the right tags for the right things)
- Ensure focus state is clearly visible
- Associate text labels with all form fields
- Maximize the readability of your application with appropriate fonts, contrast, etc.

## <a href="#websockets-and-sse" class="zola-anchor" aria-label="Anchor link for: websockets-and-sse">Web Sockets &amp; SSE</a>

Web Sockets and Server Sent Events (SSE) are supported via extensions. Please see the [SSE extension](/extensions/sse) and [WebSocket extension](/extensions/ws) pages to learn more.

## <a href="#history" class="zola-anchor" aria-label="Anchor link for: history">History Support</a>

Htmx provides a simple mechanism for interacting with the <a href="https://developer.mozilla.org/en-US/docs/Web/API/History_API" rel="noopener" target="_blank">browser history API</a>:

If you want a given element to push its request URL into the browser navigation bar and add the current state of the page to the browser’s history, include the [hx-push-url](https://htmx.org/attributes/hx-push-url/) attribute:

``` html
<a hx-get="/blog" hx-push-url="true">Blog</a>
```

When a user clicks on this link, htmx will snapshot the current DOM and store it before it makes a request to /blog. It then does the swap and pushes a new location onto the history stack.

When a user hits the back button, htmx will retrieve the old content from storage and swap it back into the target, simulating “going back” to the previous state. If the location is not found in the cache, htmx will make an ajax request to the given URL, with the header `HX-History-Restore-Request` set to true, and expects back the HTML needed for the entire page. You should always set `htmx.config.historyRestoreAsHxRequest` to false to prevent the `HX-Request` header which can then be safely used to respond with partials. Alternatively, if the `htmx.config.refreshOnHistoryMiss` config variable is set to true, it will issue a hard browser refresh.

**NOTE:** If you push a URL into the history, you **must** be able to navigate to that URL and get a full page back! A user could copy and paste the URL into an email, or new tab. Additionally, htmx will need the entire page when restoring history if the page is not in the history cache.

### <a href="#specifying-history-snapshot-element" class="zola-anchor" aria-label="Anchor link for: specifying-history-snapshot-element">Specifying History Snapshot Element</a>

By default, htmx will use the `body` to take and restore the history snapshot from. This is usually the right thing, but if you want to use a narrower element for snapshotting you can use the [hx-history-elt](https://htmx.org/attributes/hx-history-elt/) attribute to specify a different one.

Careful: this element will need to be on all pages or restoring from history won’t work reliably.

### <a href="#undoing-dom-mutations-by-3rd-party-libraries" class="zola-anchor" aria-label="Anchor link for: undoing-dom-mutations-by-3rd-party-libraries">Undoing DOM Mutations By 3rd Party Libraries</a>

If you are using a 3rd party library and want to use the htmx history feature, you will need to clean up the DOM before a snapshot is taken. Let’s consider the <a href="https://tom-select.js.org/" rel="noopener" target="_blank">Tom Select</a> library, which makes select elements a much richer user experience. Let’s set up TomSelect to turn any input element with the `.tomselect` class into a rich select element.

First we need to initialize elements that have the class in new content:

``` javascript
htmx.onLoad(function (target) {
    // find all elements in the new content that should be
    // an editor and init w/ TomSelect
    var editors = target.querySelectorAll(".tomselect")
            .forEach(elt => new TomSelect(elt))
});
```

This will create a rich selector for all input elements that have the `.tomselect` class on it. However, it mutates the DOM and we don’t want that mutation saved to the history cache, since TomSelect will be reinitialized when the history content is loaded back into the screen.

To deal with this, we need to catch the `htmx:beforeHistorySave` event and clean out the TomSelect mutations by calling `destroy()` on them:

``` javascript
htmx.on('htmx:beforeHistorySave', function() {
    // find all TomSelect elements
    document.querySelectorAll('.tomSelect')
            .forEach(elt => elt.tomselect.destroy()) // and call destroy() on them
})
```

This will revert the DOM to the original HTML, thus allowing for a clean snapshot.

### <a href="#disabling-history-snapshots" class="zola-anchor" aria-label="Anchor link for: disabling-history-snapshots">Disabling History Snapshots</a>

History snapshotting can be disabled for a URL by setting the [hx-history](https://htmx.org/attributes/hx-history/) attribute to `false` on any element in the current document, or any html fragment loaded into the current document by htmx. This can be used to prevent sensitive data entering the localStorage cache, which can be important for shared-use / public computers. History navigation will work as expected, but on restoration the URL will be requested from the server instead of the local history cache.

## <a href="#requests" class="zola-anchor" aria-label="Anchor link for: requests">Requests &amp; Responses</a>

Htmx expects responses to the AJAX requests it makes to be HTML, typically HTML fragments (although a full HTML document, matched with a [hx-select](https://htmx.org/attributes/hx-select/) tag can be useful too). Htmx will then swap the returned HTML into the document at the target specified and with the swap strategy specified.

Sometimes you might want to do nothing in the swap, but still perhaps trigger a client side event ([see below](https://htmx.org/docs/#response-headers)).

For this situation, by default, you can return a `204 - No Content` response code, and htmx will ignore the content of the response.

In the event of an error response from the server (e.g. a 404 or a 501), htmx will trigger the [`htmx:responseError`](https://htmx.org/events/#htmx:responseError) event, which you can handle.

In the event of a connection error, the [`htmx:sendError`](https://htmx.org/events/#htmx:sendError) event will be triggered.

### <a href="#response-handling" class="zola-anchor" aria-label="Anchor link for: response-handling">Configuring Response Handling</a>

You can configure the above behavior of htmx by mutating or replacing the `htmx.config.responseHandling` array. This object is a collection of JavaScript objects defined like so:

``` js
    responseHandling: [
        {code:"204", swap: false},   // 204 - No Content by default does nothing, but is not an error
        {code:"[23]..", swap: true}, // 200 & 300 responses are non-errors and are swapped
        {code:"[45]..", swap: false, error:true}, // 400 & 500 responses are not swapped and are errors
        {code:"...", swap: false}    // catch all for any other response code
    ]
```

When htmx receives a response it will iterate in order over the `htmx.config.responseHandling` array and test if the `code` property of a given object, when treated as a Regular Expression, matches the current response. If an entry does match the current response code, it will be used to determine if and how the response will be processed.

The fields available for response handling configuration on entries in this array are:

- `code` - a String representing a regular expression that will be tested against response codes.
- `swap` - `true` if the response should be swapped into the DOM, `false` otherwise
- `error` - `true` if htmx should treat this response as an error
- `ignoreTitle` - `true` if htmx should ignore title tags in the response
- `select` - A CSS selector to use to select content from the response
- `target` - A CSS selector specifying an alternative target for the response
- `swapOverride` - An alternative swap mechanism for the response

#### <a href="#response-handling-examples" class="zola-anchor" aria-label="Anchor link for: response-handling-examples">Configuring Response Handling Examples</a>

As an example of how to use this configuration, consider a situation when a server-side framework responds with a <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/422" rel="noopener" target="_blank"><code>422 - Unprocessable Entity</code></a> response when validation errors occur. By default, htmx will ignore the response, since it matches the Regular Expression `[45]..`.

Using the [meta config](https://htmx.org/docs/#configuration-options) mechanism for configuring responseHandling, we could add the following config:

``` html
<!--
  * 204 No Content by default does nothing, but is not an error
  * 2xx, 3xx and 422 responses are non-errors and are swapped
  * 4xx & 5xx responses are not swapped and are errors
  * all other responses are swapped using "..." as a catch-all
-->
<meta
   name="htmx-config"
   content='{
        "responseHandling":[
            {"code":"204", "swap": false},
            {"code":"[23]..", "swap": true},
            {"code":"422", "swap": true},
            {"code":"[45]..", "swap": false, "error":true},
            {"code":"...", "swap": true}
        ]
    }'
/>
```

If you wanted to swap everything, regardless of HTTP response code, you could use this configuration:

``` html
<meta name="htmx-config" content='{"responseHandling": [{"code":".*", "swap": true}]}' /> <!--all responses are swapped-->
```

Finally, it is worth considering using the [Response Targets](/extensions/response-targets) extension, which allows you to configure the behavior of response codes declaratively via attributes.

### <a href="#cors" class="zola-anchor" aria-label="Anchor link for: cors">CORS</a>

When using htmx in a cross origin context, remember to configure your web server to set Access-Control headers in order for htmx headers to be visible on the client side.

- <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Headers" rel="noopener" target="_blank">Access-Control-Allow-Headers (for request headers)</a>
- <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Expose-Headers" rel="noopener" target="_blank">Access-Control-Expose-Headers (for response headers)</a>

[See all the request and response headers that htmx implements.](https://htmx.org/reference/#request_headers)

### <a href="#request-headers" class="zola-anchor" aria-label="Anchor link for: request-headers">Request Headers</a>

htmx includes a number of useful headers in requests:

| Header | Description |
|----|----|
| `HX-Boosted` | indicates that the request is via an element using [hx-boost](https://htmx.org/attributes/hx-boost/) |
| `HX-Current-URL` | the current URL of the browser |
| `HX-History-Restore-Request` | “true” if the request is for history restoration after a miss in the local history cache |
| `HX-Prompt` | the user response to an [hx-prompt](https://htmx.org/attributes/hx-prompt/) |
| `HX-Request` | always “true” except on history restore requests if \`htmx.config.historyRestoreAsHxRequest’ disabled |
| `HX-Target` | the `id` of the target element if it exists |
| `HX-Trigger-Name` | the `name` of the triggered element if it exists |
| `HX-Trigger` | the `id` of the triggered element if it exists |

### <a href="#response-headers" class="zola-anchor" aria-label="Anchor link for: response-headers">Response Headers</a>

htmx supports some htmx-specific response headers:

- [`HX-Location`](https://htmx.org/headers/hx-location/) - allows you to do a client-side redirect that does not do a full page reload
- [`HX-Push-Url`](https://htmx.org/headers/hx-push-url/) - pushes a new url into the history stack
- [`HX-Redirect`](https://htmx.org/headers/hx-redirect/) - can be used to do a client-side redirect to a new location
- `HX-Refresh` - if set to “true” the client-side will do a full refresh of the page
- [`HX-Replace-Url`](https://htmx.org/headers/hx-replace-url/) - replaces the current URL in the location bar
- `HX-Reswap` - allows you to specify how the response will be swapped. See [hx-swap](https://htmx.org/attributes/hx-swap/) for possible values
- `HX-Retarget` - a CSS selector that updates the target of the content update to a different element on the page
- `HX-Reselect` - a CSS selector that allows you to choose which part of the response is used to be swapped in. Overrides an existing [`hx-select`](https://htmx.org/attributes/hx-select/) on the triggering element
- [`HX-Trigger`](https://htmx.org/headers/hx-trigger/) - allows you to trigger client-side events
- [`HX-Trigger-After-Settle`](https://htmx.org/headers/hx-trigger/) - allows you to trigger client-side events after the settle step
- [`HX-Trigger-After-Swap`](https://htmx.org/headers/hx-trigger/) - allows you to trigger client-side events after the swap step

For more on the `HX-Trigger` headers, see [`HX-Trigger` Response Headers](https://htmx.org/headers/hx-trigger/).

Submitting a form via htmx has the benefit of no longer needing the <a href="https://en.wikipedia.org/wiki/Post/Redirect/Get" rel="noopener" target="_blank">Post/Redirect/Get Pattern</a>. After successfully processing a POST request on the server, you don’t need to return a <a href="https://en.wikipedia.org/wiki/HTTP_302" rel="noopener" target="_blank">HTTP 302 (Redirect)</a>. You can directly return the new HTML fragment.

Also the response headers above are not provided to htmx for processing with 3xx Redirect response codes like <a href="https://en.wikipedia.org/wiki/HTTP_302" rel="noopener" target="_blank">HTTP 302 (Redirect)</a>. Instead, the browser will intercept the redirection internally and return the headers and response from the redirected URL. Where possible use alternative response codes like 200 to allow returning of these response headers.

### <a href="#request-operations" class="zola-anchor" aria-label="Anchor link for: request-operations">Request Order of Operations</a>

The order of operations in a htmx request are:

- The element is triggered and begins a request
  - Values are gathered for the request
  - The `htmx-request` class is applied to the appropriate elements
  - The request is then issued asynchronously via AJAX
    - Upon getting a response the target element is marked with the `htmx-swapping` class
    - An optional swap delay is applied (see the [hx-swap](https://htmx.org/attributes/hx-swap/) attribute)
    - The actual content swap is done
      - the `htmx-swapping` class is removed from the target
      - the `htmx-added` class is added to each new piece of content
      - the `htmx-settling` class is applied to the target
      - A settle delay is done (default: 20ms)
      - The DOM is settled
      - the `htmx-settling` class is removed from the target
      - the `htmx-added` class is removed from each new piece of content

You can use the `htmx-swapping` and `htmx-settling` classes to create <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions" rel="noopener" target="_blank">CSS transitions</a> between pages.

## <a href="#validation" class="zola-anchor" aria-label="Anchor link for: validation">Validation</a>

Htmx integrates with the <a href="https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation" rel="noopener" target="_blank">HTML5 Validation API</a> and will not issue a request for a form if a validatable input is invalid. This is true for both AJAX requests as well as WebSocket sends.

Htmx fires events around validation that can be used to hook in custom validation and error handling:

- `htmx:validation:validate` - called before an element’s `checkValidity()` method is called. May be used to add in custom validation logic
- `htmx:validation:failed` - called when `checkValidity()` returns false, indicating an invalid input
- `htmx:validation:halted` - called when a request is not issued due to validation errors. Specific errors may be found in the `event.detail.errors` object

Non-form elements do not validate before they make requests by default, but you can enable validation by setting the [`hx-validate`](https://htmx.org/attributes/hx-validate/) attribute to “true”.

Normal browser form submission alerts the user of any validation errors automatically and auto focuses on the first invalid input. For backwards compatibility reasons htmx does not report the validation to the users by default and you should always enable this option by setting `htmx.config.reportValidityOfForms` to `true` to restore the default browser behavior.

### <a href="#validation-example" class="zola-anchor" aria-label="Anchor link for: validation-example">Validation Example</a>

Here is an example of an input that uses the [`hx-on`](/attributes/hx-on) attribute to catch the `htmx:validation:validate` event and require that the input have the value `foo`:

``` html
<form id="example-form" hx-post="/test">
    <input name="example"
           onkeyup="this.setCustomValidity('') // reset the validation on keyup"
           hx-on:htmx:validation:validate="if(this.value != 'foo') {
                    this.setCustomValidity('Please enter the value foo') // set the validation error
                    htmx.find('#example-form').reportValidity()          // report the issue
                }">
</form>
```

Note that all client side validations must be re-done on the server side, as they can always be bypassed.

## <a href="#animations" class="zola-anchor" aria-label="Anchor link for: animations">Animations</a>

Htmx allows you to use [CSS transitions](https://htmx.org/docs/#css_transitions) in many situations using only HTML and CSS.

Please see the [Animation Guide](https://htmx.org/examples/animations/) for more details on the options available.

## <a href="#extensions" class="zola-anchor" aria-label="Anchor link for: extensions">Extensions</a>

htmx provides an [extensions](/extensions) mechanism that allows you to customize the libraries’ behavior. Extensions [are defined in javascript](/extensions/building) and then enabled via the [`hx-ext`](https://htmx.org/attributes/hx-ext/) attribute.

### <a href="#core-extensions" class="zola-anchor" aria-label="Anchor link for: core-extensions">Core Extensions</a>

htmx supports a few “core” extensions, which are supported by the htmx development team:

- [head-support](/extensions/head-support) - support for merging head tag information (styles, etc.) in htmx requests
- [htmx-1-compat](/extensions/htmx-1-compat) - restores htmx 1 defaults & functionality
- [idiomorph](/extensions/idiomorph) - supports the `morph` swap strategy using idiomorph
- [preload](/extensions/preload) - allows you to preload content for better performance
- [response-targets](/extensions/response-targets) - allows you to target elements based on HTTP response codes (e.g. `404`)
- [sse](/extensions/sse) - support for <a href="https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events" rel="noopener" target="_blank">Server Sent Events</a>
- [ws](/extensions/ws) - support for <a href="https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_client_applications" rel="noopener" target="_blank">Web Sockets</a>

You can see all available extensions on the [Extensions](/extensions) page.

### <a href="#installing-extensions" class="zola-anchor" aria-label="Anchor link for: installing-extensions">Installing Extensions</a>

The fastest way to install htmx extensions created by others is to load them via a CDN. Remember to always include the core htmx library before the extensions and [enable the extension](https://htmx.org/docs/#enabling-extensions). For example, if you would like to use the [response-targets](/extensions/response-targets) extension, you can add this to your head tag:

``` HTML
<head>
    <script src="https://cdn.jsdelivr.net/npm/htmx.org@2.0.8/dist/htmx.min.js" integrity="sha384-/TgkGk7p307TH7EXJDuUlgG3Ce1UVolAOFopFekQkkXihi5u/6OCvVKyz1W+idaz" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/htmx-ext-response-targets@2.0.4" integrity="sha384-T41oglUPvXLGBVyRdZsVRxNWnOOqCynaPubjUVjxhsjFTKrFJGEMm3/0KGmNQ+Pg" crossorigin="anonymous"></script>
</head>
<body hx-ext="extension-name">
    ...
```

An unminified version is also available at `https://cdn.jsdelivr.net/npm/htmx-ext-extension-name/dist/extension-name.js` (replace `extension-name` with the name of the extension).

While the CDN approach is simple, you may want to consider <a href="https://blog.wesleyac.com/posts/why-not-javascript-cdn" rel="noopener" target="_blank">not using CDNs in production</a>. The next easiest way to install htmx extensions is to simply copy them into your project. Download the extension from `https://cdn.jsdelivr.net/npm/htmx-ext-extension-name` (replace `extension-name` with the name of the extension) e.g., https://cdn.jsdelivr.net/npm/htmx-ext-response-targets. Then add it to the appropriate directory in your project and include it where necessary with a `<script>` tag.

For npm-style build systems, you can install htmx extensions via <a href="https://www.npmjs.com/" rel="noopener" target="_blank">npm</a> (replace `extension-name` with the name of the extension):

``` shell
npm install htmx-ext-extension-name
```

After installing, you’ll need to use appropriate tooling to bundle `node_modules/htmx-ext-extension-name/dist/extension-name.js` (or `.min.js`). For example, you might bundle the extension with htmx core from `node_modules/htmx.org/dist/htmx.js` and project-specific code.

If you are using a bundler to manage your javascript (e.g. Webpack, Rollup):

- Install `htmx.org` and `htmx-ext-extension-name` via npm (replace `extension-name` with the name of the extension)
- Import both packages to your `index.js`

``` JS
import `htmx.org`;
import `htmx-ext-extension-name`; // replace `extension-name` with the name of the extension
```

Note: [Idiomorph](/extensions/idiomorph) does not follow the naming convention of htmx extensions. Use `idiomorph` instead of `htmx-ext-idiomorph`. For example, `https://cdn.jsdelivr.net/npm/idiomorph` or `npm install idiomorph`.

Note: Community extensions hosted outside this repository might have different installation instructions. Please check the corresponding repository for set-up guidance.

### <a href="#enabling-extensions" class="zola-anchor" aria-label="Anchor link for: enabling-extensions">Enabling Extensions</a>

To enable an extension, add a `hx-ext="extension-name"` attribute to `<body>` or another HTML element (replace `extension-name` with the name of the extension). The extension will be applied to all child elements.

The following example shows how to enable [response-targets](/extensions/response-targets) extension, allowing you to specify different target elements to be swapped based on HTTP response code.

``` html
<body hx-ext="response-targets">
    ...
    <button hx-post="/register" hx-target="#response-div" hx-target-404="#not-found">
        Register!
    </button>
    <div id="response-div"></div>
    <div id="not-found"></div>
    ...
</body>
```

### <a href="#creating-extensions" class="zola-anchor" aria-label="Anchor link for: creating-extensions">Creating Extensions</a>

If you are interested in adding your own extension to htmx, please [see the extension docs](/extensions/building).

## <a href="#events" class="zola-anchor" aria-label="Anchor link for: events">Events &amp; Logging</a>

Htmx has an extensive [events mechanism](https://htmx.org/reference/#events), which doubles as the logging system.

If you want to register for a given htmx event you can use

``` js
document.body.addEventListener('htmx:load', function(evt) {
    myJavascriptLib.init(evt.detail.elt);
});
```

or, if you would prefer, you can use the following htmx helper:

``` javascript
htmx.on("htmx:load", function(evt) {
    myJavascriptLib.init(evt.detail.elt);
});
```

The `htmx:load` event is fired every time an element is loaded into the DOM by htmx, and is effectively the equivalent to the normal `load` event.

Some common uses for htmx events are:

### <a href="#init_3rd_party_with_events" class="zola-anchor" aria-label="Anchor link for: init_3rd_party_with_events">Initialize A 3rd Party Library With Events</a>

Using the `htmx:load` event to initialize content is so common that htmx provides a helper function:

``` javascript
htmx.onLoad(function(target) {
    myJavascriptLib.init(target);
});
```

This does the same thing as the first example, but is a little cleaner.

### <a href="#config_request_with_events" class="zola-anchor" aria-label="Anchor link for: config_request_with_events">Configure a Request With Events</a>

You can handle the [`htmx:configRequest`](https://htmx.org/events/#htmx:configRequest) event in order to modify an AJAX request before it is issued:

``` javascript
document.body.addEventListener('htmx:configRequest', function(evt) {
    evt.detail.parameters['auth_token'] = getAuthToken(); // add a new parameter into the request
    evt.detail.headers['Authentication-Token'] = getAuthToken(); // add a new header into the request
});
```

Here we add a parameter and header to the request before it is sent.

### <a href="#modifying_swapping_behavior_with_events" class="zola-anchor" aria-label="Anchor link for: modifying_swapping_behavior_with_events">Modifying Swapping Behavior With Events</a>

You can handle the [`htmx:beforeSwap`](https://htmx.org/events/#htmx:beforeSwap) event in order to modify the swap behavior of htmx:

``` javascript
document.body.addEventListener('htmx:beforeSwap', function(evt) {
    if(evt.detail.xhr.status === 404){
        // alert the user when a 404 occurs (maybe use a nicer mechanism than alert())
        alert("Error: Could Not Find Resource");
    } else if(evt.detail.xhr.status === 422){
        // allow 422 responses to swap as we are using this as a signal that
        // a form was submitted with bad data and want to rerender with the
        // errors
        //
        // set isError to false to avoid error logging in console
        evt.detail.shouldSwap = true;
        evt.detail.isError = false;
    } else if(evt.detail.xhr.status === 418){
        // if the response code 418 (I'm a teapot) is returned, retarget the
        // content of the response to the element with the id `teapot`
        evt.detail.shouldSwap = true;
        evt.detail.target = htmx.find("#teapot");
    }
});
```

Here we handle a few <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client_error_responses" rel="noopener" target="_blank">400-level error response codes</a> that would normally not do a swap in htmx.

### <a href="#event_naming" class="zola-anchor" aria-label="Anchor link for: event_naming">Event Naming</a>

Note that all events are fired with two different names

- Camel Case
- Kebab Case

So, for example, you can listen for `htmx:afterSwap` or for `htmx:after-swap`. This facilitates interoperability with other libraries. <a href="https://github.com/alpinejs/alpine/" rel="noopener" target="_blank">Alpine.js</a>, for example, requires kebab case.

### <a href="#logging" class="zola-anchor" aria-label="Anchor link for: logging">Logging</a>

If you set a logger at `htmx.logger`, every event will be logged. This can be very useful for troubleshooting:

``` javascript
htmx.logger = function(elt, event, data) {
    if(console) {
        console.log(event, elt, data);
    }
}
```

## <a href="#debugging" class="zola-anchor" aria-label="Anchor link for: debugging">Debugging</a>

Declarative and event driven programming with htmx (or any other declarative language) can be a wonderful and highly productive activity, but one disadvantage when compared with imperative approaches is that it can be trickier to debug.

Figuring out why something *isn’t* happening, for example, can be difficult if you don’t know the tricks.

Well, here are the tricks:

The first debugging tool you can use is the `htmx.logAll()` method. This will log every event that htmx triggers and will allow you to see exactly what the library is doing.

``` javascript
htmx.logAll();
```

Of course, that won’t tell you why htmx *isn’t* doing something. You might also not know *what* events a DOM element is firing to use as a trigger. To address this, you can use the <a href="https://developers.google.com/web/updates/2015/05/quickly-monitor-events-from-the-console-panel" rel="noopener" target="_blank"><code>monitorEvents()</code></a> method available in the browser console:

``` javascript
monitorEvents(htmx.find("#theElement"));
```

This will spit out all events that are occurring on the element with the id `theElement` to the console, and allow you to see exactly what is going on with it.

Note that this *only* works from the console, you cannot embed it in a script tag on your page.

Finally, push come shove, you might want to just debug `htmx.js` by loading up the unminimized version. It’s about 2500 lines of javascript, so not an insurmountable amount of code. You would most likely want to set a break point in the `issueAjaxRequest()` and `handleAjaxResponse()` methods to see what’s going on.

And always feel free to jump on the <a href="https://htmx.org/discord" rel="noopener" target="_blank">Discord</a> if you need help.

### <a href="#creating-demos" class="zola-anchor" aria-label="Anchor link for: creating-demos">Creating Demos</a>

Sometimes, in order to demonstrate a bug or clarify a usage, it is nice to be able to use a javascript snippet site like <a href="https://jsfiddle.net/" rel="noopener" target="_blank">jsfiddle</a>. To facilitate easy demo creation, htmx hosts a demo script site that will install:

- htmx
- hyperscript
- a request mocking library

Simply add the following script tag to your demo/fiddle/whatever:

``` html
<script src="https://demo.htmx.org"></script>
```

This helper allows you to add mock responses by adding `template` tags with a `url` attribute to indicate which URL. The response for that url will be the innerHTML of the template, making it easy to construct mock responses. You can add a delay to the response with a `delay` attribute, which should be an integer indicating the number of milliseconds to delay

You may embed simple expressions in the template with the `${}` syntax.

Note that this should only be used for demos and is in no way guaranteed to work for long periods of time as it will always be grabbing the latest versions htmx and hyperscript!

#### <a href="#demo-example" class="zola-anchor" aria-label="Anchor link for: demo-example">Demo Example</a>

Here is an example of the code in action:

``` html
<!-- load demo environment -->
<script src="https://demo.htmx.org"></script>

<!-- post to /foo -->
<button hx-post="/foo" hx-target="#result">
    Count Up
</button>
<output id="result"></output>

<!-- respond to /foo with some dynamic content in a template tag -->
<script>
    globalInt = 0;
</script>
<template url="/foo" delay="500"> <!-- note the url and delay attributes -->
    ${globalInt++}
</template>
```

## <a href="#scripting" class="zola-anchor" aria-label="Anchor link for: scripting">Scripting</a>

While htmx encourages a hypermedia approach to building web applications, it offers many options for client scripting. Scripting is included in the REST-ful description of web architecture, see: <a href="https://roy.gbiv.com/pubs/dissertation/rest_arch_style.htm#sec_5_1_7" rel="noopener" target="_blank">Code-On-Demand</a>. As much as is feasible, we recommend a [hypermedia-friendly](/essays/hypermedia-friendly-scripting) approach to scripting in your web application:

- [Respect HATEOAS](/essays/hypermedia-friendly-scripting#prime_directive)
- [Use events to communicate between components](/essays/hypermedia-friendly-scripting#events)
- [Use islands to isolate non-hypermedia components from the rest of your application](/essays/hypermedia-friendly-scripting#islands)
- [Consider inline scripting](/essays/hypermedia-friendly-scripting#inline)

The primary integration point between htmx and scripting solutions is the [events](https://htmx.org/docs/#events) that htmx sends and can respond to. See the SortableJS example in the [3rd Party Javascript](https://htmx.org/docs/#3rd-party) section for a good template for integrating a JavaScript library with htmx via events.

Scripting solutions that pair well with htmx include:

- <a href="http://vanilla-js.com/" rel="noopener" target="_blank">VanillaJS</a> - Simply using the built-in abilities of JavaScript to hook in event handlers to respond to the events htmx emits can work very well for scripting. This is an extremely lightweight and increasingly popular approach.
- <a href="https://alpinejs.dev/" rel="noopener" target="_blank">AlpineJS</a> - Alpine.js provides a rich set of tools for creating sophisticated front end scripts, including reactive programming support, while still remaining extremely lightweight. Alpine encourages the “inline scripting” approach that we feel pairs well with htmx.
- <a href="https://jquery.com/" rel="noopener" target="_blank">jQuery</a> - Despite its age and reputation in some circles, jQuery pairs very well with htmx, particularly in older code-bases that already have a lot of jQuery in them.
- <a href="https://hyperscript.org" rel="noopener" target="_blank">hyperscript</a> - Hyperscript is an experimental front-end scripting language created by the same team that created htmx. It is designed to embed well in HTML and both respond to and create events, and pairs very well with htmx.

We have an entire chapter entitled <a href="https://hypermedia.systems/client-side-scripting/" rel="noopener" target="_blank">“Client-Side Scripting”</a> in <a href="https://hypermedia.systems" rel="noopener" target="_blank">our book</a> that looks at how scripting can be integrated into your htmx-based application.

### <a href="#the-hx-on-attributes" class="zola-anchor" aria-label="Anchor link for: the-hx-on-attributes"></a><span id="hx-on"></span>[The `hx-on*` Attributes](https://htmx.org/docs/#hx-on)

HTML allows the embedding of inline scripts via the <a href="https://developer.mozilla.org/en-US/docs/Web/Events/Event_handlers#using_onevent_properties" rel="noopener" target="_blank"><code>onevent</code> properties</a>, such as `onClick`:

``` html
<button onclick="alert('You clicked me!')">
    Click Me!
</button>
```

This feature allows scripting logic to be co-located with the HTML elements the logic applies to, giving good [Locality of Behaviour (LoB)](/essays/locality-of-behaviour). Unfortunately, HTML only allows `on*` attributes for a fixed number of <a href="https://www.w3schools.com/tags/ref_eventattributes.asp" rel="noopener" target="_blank">specific DOM events</a> (e.g. `onclick`) and doesn’t provide a generalized mechanism for responding to arbitrary events on elements.

In order to address this shortcoming, htmx offers [`hx-on*`](/attributes/hx-on) attributes. These attributes allow you to respond to any event in a manner that preserves the LoB of the standard `on*` properties.

If we wanted to respond to the `click` event using an `hx-on` attribute, we would write this:

``` html
<button hx-on:click="alert('You clicked me!')">
    Click Me!
</button>
```

So, the string `hx-on`, followed by a colon (or a dash), then by the name of the event.

For a `click` event, of course, we would recommend sticking with the standard `onclick` attribute. However, consider an htmx-powered button that wishes to add a parameter to a request using the `htmx:config-request` event. This would not be possible using a standard `on*` property, but it can be done using the `hx-on:htmx:config-request` attribute:

``` html
<button hx-post="/example"
        hx-on:htmx:config-request="event.detail.parameters.example = 'Hello Scripting!'">
    Post Me!
</button>
```

Here the `example` parameter is added to the `POST` request before it is issued, with the value ‘Hello Scripting!’.

Another usecase is to [reset user input](https://htmx.org/examples/reset-user-input/) on successful requests using the `afterRequest` event, avoiding the need for something like an out of band swap.

The `hx-on*` attributes are a very simple mechanism for generalized embedded scripting. It is *not* a replacement for more fully developed front-end scripting solutions such as AlpineJS or hyperscript. It can, however, augment a VanillaJS-based approach to scripting in your htmx-powered application.

Note that HTML attributes are *case insensitive*. This means that, unfortunately, events that rely on capitalization/ camel casing, cannot be responded to. If you need to support camel case events we recommend using a more fully functional scripting solution such as AlpineJS or hyperscript. htmx dispatches all its events in both camelCase and in kebab-case for this very reason.

### <a href="#3rd-party" class="zola-anchor" aria-label="Anchor link for: 3rd-party">3rd Party Javascript</a>

Htmx integrates fairly well with third party libraries. If the library fires events on the DOM, you can use those events to trigger requests from htmx.

A good example of this is the [SortableJS demo](https://htmx.org/examples/sortable/):

``` html
<form class="sortable" hx-post="/items" hx-trigger="end">
    <div class="htmx-indicator">Updating...</div>
    <div><input type='hidden' name='item' value='1'/>Item 1</div>
    <div><input type='hidden' name='item' value='2'/>Item 2</div>
    <div><input type='hidden' name='item' value='2'/>Item 3</div>
</form>
```

With Sortable, as with most javascript libraries, you need to initialize content at some point.

In jquery you might do this like so:

``` javascript
$(document).ready(function() {
    var sortables = document.body.querySelectorAll(".sortable");
    for (var i = 0; i < sortables.length; i++) {
        var sortable = sortables[i];
        new Sortable(sortable, {
            animation: 150,
            ghostClass: 'blue-background-class'
        });
    }
});
```

In htmx, you would instead use the `htmx.onLoad` function, and you would select only from the newly loaded content, rather than the entire document:

``` js
htmx.onLoad(function(content) {
    var sortables = content.querySelectorAll(".sortable");
    for (var i = 0; i < sortables.length; i++) {
        var sortable = sortables[i];
        new Sortable(sortable, {
            animation: 150,
            ghostClass: 'blue-background-class'
        });
    }
})
```

This will ensure that as new content is added to the DOM by htmx, sortable elements are properly initialized.

If javascript adds content to the DOM that has htmx attributes on it, you need to make sure that this content is initialized with the `htmx.process()` function.

For example, if you were to fetch some data and put it into a div using the `fetch` API, and that HTML had htmx attributes in it, you would need to add a call to `htmx.process()` like this:

``` js
let myDiv = document.getElementById('my-div')
fetch('http://example.com/movies.json')
    .then(response => response.text())
    .then(data => { myDiv.innerHTML = data; htmx.process(myDiv); } );
```

Some 3rd party libraries create content from HTML template elements. For instance, Alpine JS uses the `x-if` attribute on templates to add content conditionally. Such templates are not initially part of the DOM and, if they contain htmx attributes, will need a call to `htmx.process()` after they are loaded. The following example uses Alpine’s `$watch` function to look for a change of value that would trigger conditional content:

``` html
<div x-data="{show_new: false}"
    x-init="$watch('show_new', value => {
        if (show_new) {
            htmx.process(document.querySelector('#new_content'))
        }
    })">
    <button @click = "show_new = !show_new">Toggle New Content</button>
    <template x-if="show_new">
        <div id="new_content">
            <a hx-get="/server/newstuff" href="#">New Clickable</a>
        </div>
    </template>
</div>
```

#### <a href="#web-components" class="zola-anchor" aria-label="Anchor link for: web-components">Web Components</a>

Please see the [Web Components Examples](https://htmx.org/examples/web-components/) page for examples on how to integrate htmx with web components.

## <a href="#caching" class="zola-anchor" aria-label="Anchor link for: caching">Caching</a>

htmx works with standard <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching" rel="noopener" target="_blank">HTTP caching</a> mechanisms out of the box.

If your server adds the <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Last-Modified" rel="noopener" target="_blank"><code>Last-Modified</code></a> HTTP response header to the response for a given URL, the browser will automatically add the <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/If-Modified-Since" rel="noopener" target="_blank"><code>If-Modified-Since</code></a> request HTTP header to the next requests to the same URL. Be mindful that if your server can render different content for the same URL depending on some other headers, you need to use the <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching#vary" rel="noopener" target="_blank"><code>Vary</code></a> response HTTP header. For example, if your server renders the full HTML when the `HX-Request` header is missing or `false`, and it renders a fragment of that HTML when `HX-Request: true`, you need to add `Vary: HX-Request`. That causes the cache to be keyed based on a composite of the response URL and the `HX-Request` request header — rather than being based just on the response URL. Always disable `htmx.config.historyRestoreAsHxRequest` so that these history full HTML requests are not cached with partial fragment responses.

If you are unable (or unwilling) to use the `Vary` header, you can alternatively set the configuration parameter `getCacheBusterParam` to `true`. If this configuration variable is set, htmx will include a cache-busting parameter in `GET` requests that it makes, which will prevent browsers from caching htmx-based and non-htmx based responses in the same cache slot.

htmx also works with <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag" rel="noopener" target="_blank"><code>ETag</code></a> as expected. Be mindful that if your server can render different content for the same URL (for example, depending on the value of the `HX-Request` header), the server needs to generate a different `ETag` for each content.

## <a href="#security" class="zola-anchor" aria-label="Anchor link for: security">Security</a>

htmx allows you to define logic directly in your DOM. This has a number of advantages, the largest being [Locality of Behavior](https://htmx.org/essays/locality-of-behaviour/), which makes your system easier to understand and maintain.

A concern with this approach, however, is security: since htmx increases the expressiveness of HTML, if a malicious user is able to inject HTML into your application, they can leverage this expressiveness of htmx to malicious ends.

### <a href="#rule-1-escape-all-user-content" class="zola-anchor" aria-label="Anchor link for: rule-1-escape-all-user-content">Rule 1: Escape All User Content</a>

The first rule of HTML-based web development has always been: *do not trust input from the user*. You should escape all 3rd party, untrusted content that is injected into your site. This is to prevent, among other issues, <a href="https://en.wikipedia.org/wiki/Cross-site_scripting" rel="noopener" target="_blank">XSS attacks</a>.

There is extensive documentation on XSS and how to prevent it on the excellent <a href="https://owasp.org/www-community/attacks/xss/" rel="noopener" target="_blank">OWASP Website</a>, including a <a href="https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html" rel="noopener" target="_blank">Cross Site Scripting Prevention Cheat Sheet</a>.

The good news is that this is a very old and well understood topic, and the vast majority of server-side templating languages support <a href="https://docs.djangoproject.com/en/4.2/ref/templates/language/#automatic-html-escaping" rel="noopener" target="_blank">automatic escaping</a> of content to prevent just such an issue.

That being said, there are times people choose to inject HTML more dangerously, often via some sort of `raw()` mechanism in their templating language. This can be done for good reasons, but if the content being injected is coming from a 3rd party then it *must* be scrubbed, including removing attributes starting with `hx-` and `data-hx`, as well as inline `<script>` tags, etc.

If you are injecting raw HTML and doing your own escaping, a best practice is to *whitelist* the attributes and tags you allow, rather than to blacklist the ones you disallow.

### <a href="#htmx-security-tools" class="zola-anchor" aria-label="Anchor link for: htmx-security-tools">htmx Security Tools</a>

Of course, bugs happen and developers are not perfect, so it is good to have a layered approach to security for your web application, and htmx provides tools to help secure your application as well.

Let’s take a look at them.

#### <a href="#hx-disable" class="zola-anchor" aria-label="Anchor link for: hx-disable"><code>hx-disable</code></a>

The first tool htmx provides to help further secure your application is the [`hx-disable`](/attributes/hx-disable) attribute. This attribute will prevent processing of all htmx attributes on a given element, and on all elements within it. So, for example, if you were including raw HTML content in a template (again, this is not recommended!) then you could place a div around the content with the `hx-disable` attribute on it:

``` html
<div hx-disable>
    <%= raw(user_content) %>
</div>
```

And htmx will not process any htmx-related attributes or features found in that content. This attribute cannot be disabled by injecting further content: if an `hx-disable` attribute is found anywhere in the parent hierarchy of an element, it will not be processed by htmx.

#### <a href="#hx-history" class="zola-anchor" aria-label="Anchor link for: hx-history"><code>hx-history</code></a>

Another security consideration is htmx history cache. You may have pages that have sensitive data that you do not want stored in the users `localStorage` cache. You can omit a given page from the history cache by including the [`hx-history`](/attributes/hx-history) attribute anywhere on the page, and setting its value to `false`.

#### <a href="#configuration-options" class="zola-anchor" aria-label="Anchor link for: configuration-options">Configuration Options</a>

htmx also provides configuration options related to security:

- `htmx.config.selfRequestsOnly` - if set to `true`, only requests to the same domain as the current document will be allowed
- `htmx.config.allowScriptTags` - htmx will process `<script>` tags found in new content it loads. If you wish to disable this behavior you can set this configuration variable to `false`
- `htmx.config.historyCacheSize` - can be set to `0` to avoid storing any HTML in the `localStorage` cache
- `htmx.config.allowEval` - can be set to `false` to disable all features of htmx that rely on eval:
  - event filters
  - `hx-on:` attributes
  - `hx-vals` with the `js:` prefix
  - `hx-headers` with the `js:` prefix

Note that all features removed by disabling `eval()` can be reimplemented using your own custom javascript and the htmx event model.

#### <a href="#events-1" class="zola-anchor" aria-label="Anchor link for: events-1">Events</a>

If you want to allow requests to some domains beyond the current host, but not leave things totally open, you can use the `htmx:validateUrl` event. This event will have the request URL available in the `detail.url` slot, as well as a `sameHost` property.

You can inspect these values and, if the request is not valid, invoke `preventDefault()` on the event to prevent the request from being issued.

``` javascript
document.body.addEventListener('htmx:validateUrl', function (evt) {
  // only allow requests to the current server as well as myserver.com
  if (!evt.detail.sameHost && evt.detail.url.hostname !== "myserver.com") {
    evt.preventDefault();
  }
});
```

### <a href="#csp-options" class="zola-anchor" aria-label="Anchor link for: csp-options">CSP Options</a>

Browsers also provide tools for further securing your web application. The most powerful tool available is a <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP" rel="noopener" target="_blank">Content Security Policy</a>. Using a CSP you can tell the browser to, for example, not issue requests to non-origin hosts, to not evaluate inline script tags, etc.

Here is an example CSP in a `meta` tag:

``` html
    <meta http-equiv="Content-Security-Policy" content="default-src 'self';">
```

This tells the browser “Only allow connections to the original (source) domain”. This would be redundant with the `htmx.config.selfRequestsOnly`, but a layered approach to security is warranted and, in fact, ideal, when dealing with application security.

A full discussion of CSPs is beyond the scope of this document, but the <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP" rel="noopener" target="_blank">MDN Article</a> provides a good jumping-off point for exploring this topic.

### <a href="#csrf-prevention" class="zola-anchor" aria-label="Anchor link for: csrf-prevention">CSRF Prevention</a>

The assignment and checking of CSRF tokens are typically backend responsibilities, but `htmx` can support returning the CSRF token automatically with every request using the `hx-headers` attribute. The attribute needs to be added to the element issuing the request or one of its ancestor elements. This makes the `html` and `body` elements effective global vehicles for adding the CSRF token to the `HTTP` request header, as illustrated below.

Note: `hx-boost` does not update the `<html>` or `<body>` tags; if using this feature with `hx-boost`, make sure to include the CSRF token on an element that *will* get replaced. Many web frameworks support automatically inserting the CSRF token as a hidden input in HTML forms. This is encouraged whenever possible.

``` html
<html lang="en" hx-headers='{"X-CSRF-TOKEN": "CSRF_TOKEN_INSERTED_HERE"}'>
    :
</html>
```

``` html
    <body hx-headers='{"X-CSRF-TOKEN": "CSRF_TOKEN_INSERTED_HERE"}'>
        :
    </body>
```

The above elements are usually unique in an HTML document and should be easy to locate within templates.

## <a href="#config" class="zola-anchor" aria-label="Anchor link for: config">Configuring htmx</a>

Htmx has some configuration options that can be accessed either programmatically or declaratively. They are listed below:

<div class="info-table">

| Config Variable | Info |
|----|----|
| `htmx.config.historyEnabled` | defaults to `true`, really only useful for testing |
| `htmx.config.historyCacheSize` | defaults to 10 |
| `htmx.config.refreshOnHistoryMiss` | defaults to `false`, if set to `true` htmx will issue a full page refresh on history misses rather than use an AJAX request |
| `htmx.config.defaultSwapStyle` | defaults to `innerHTML` |
| `htmx.config.defaultSwapDelay` | defaults to 0 |
| `htmx.config.defaultSettleDelay` | defaults to 20 |
| `htmx.config.includeIndicatorStyles` | defaults to `true` (determines if the indicator styles are loaded) |
| `htmx.config.indicatorClass` | defaults to `htmx-indicator` |
| `htmx.config.requestClass` | defaults to `htmx-request` |
| `htmx.config.addedClass` | defaults to `htmx-added` |
| `htmx.config.settlingClass` | defaults to `htmx-settling` |
| `htmx.config.swappingClass` | defaults to `htmx-swapping` |
| `htmx.config.allowEval` | defaults to `true`, can be used to disable htmx’s use of eval for certain features (e.g. trigger filters) |
| `htmx.config.allowScriptTags` | defaults to `true`, determines if htmx will process script tags found in new content |
| `htmx.config.inlineScriptNonce` | defaults to `''`, meaning that no nonce will be added to inline scripts |
| `htmx.config.attributesToSettle` | defaults to `["class", "style", "width", "height"]`, the attributes to settle during the settling phase |
| `htmx.config.inlineStyleNonce` | defaults to `''`, meaning that no nonce will be added to inline styles |
| `htmx.config.useTemplateFragments` | defaults to `false`, HTML template tags for parsing content from the server (not IE11 compatible!) |
| `htmx.config.wsReconnectDelay` | defaults to `full-jitter` |
| `htmx.config.wsBinaryType` | defaults to `blob`, the <a href="https://developer.mozilla.org/docs/Web/API/WebSocket/binaryType" rel="noopener" target="_blank">type of binary data</a> being received over the WebSocket connection |
| `htmx.config.disableSelector` | defaults to `[hx-disable], [data-hx-disable]`, htmx will not process elements with this attribute on it or a parent |
| `htmx.config.withCredentials` | defaults to `false`, allow cross-site Access-Control requests using credentials such as cookies, authorization headers or TLS client certificates |
| `htmx.config.timeout` | defaults to 0, the number of milliseconds a request can take before automatically being terminated |
| `htmx.config.scrollBehavior` | defaults to ‘instant’, the scroll behavior when using the [show](https://htmx.org/attributes/hx-swap/#scrolling-scroll-show) modifier with `hx-swap`. The allowed values are `instant` (scrolling should happen instantly in a single jump), `smooth` (scrolling should animate smoothly) and `auto` (scroll behavior is determined by the computed value of <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/scroll-behavior" rel="noopener" target="_blank">scroll-behavior</a>). |
| `htmx.config.defaultFocusScroll` | if the focused element should be scrolled into view, defaults to false and can be overridden using the [focus-scroll](https://htmx.org/attributes/hx-swap/#focus-scroll) swap modifier. |
| `htmx.config.getCacheBusterParam` | defaults to false, if set to true htmx will append the target element to the `GET` request in the format `org.htmx.cache-buster=targetElementId` |
| `htmx.config.globalViewTransitions` | if set to `true`, htmx will use the <a href="https://developer.mozilla.org/en-US/docs/Web/API/View_Transitions_API" rel="noopener" target="_blank">View Transition</a> API when swapping in new content. |
| `htmx.config.methodsThatUseUrlParams` | defaults to `["get", "delete"]`, htmx will format requests with these methods by encoding their parameters in the URL, not the request body |
| `htmx.config.selfRequestsOnly` | defaults to `true`, whether to only allow AJAX requests to the same domain as the current document |
| `htmx.config.ignoreTitle` | defaults to `false`, if set to `true` htmx will not update the title of the document when a `title` tag is found in new content |
| `htmx.config.disableInheritance` | disables attribute inheritance in htmx, which can then be overridden by the [`hx-inherit`](https://htmx.org/attributes/hx-inherit/) attribute |
| `htmx.config.scrollIntoViewOnBoost` | defaults to `true`, whether or not the target of a boosted element is scrolled into the viewport. If `hx-target` is omitted on a boosted element, the target defaults to `body`, causing the page to scroll to the top. |
| `htmx.config.triggerSpecsCache` | defaults to `null`, the cache to store evaluated trigger specifications into, improving parsing performance at the cost of more memory usage. You may define a simple object to use a never-clearing cache, or implement your own system using a <a href="https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy" rel="noopener" target="_blank">proxy object</a> |
| `htmx.config.responseHandling` | the default [Response Handling](https://htmx.org/docs/#response-handling) behavior for response status codes can be configured here to either swap or error |
| `htmx.config.allowNestedOobSwaps` | defaults to `true`, whether to process OOB swaps on elements that are nested within the main response element. See [Nested OOB Swaps](https://htmx.org/attributes/hx-swap-oob/#nested-oob-swaps). |
| `htmx.config.historyRestoreAsHxRequest` | defaults to `true`, Whether to treat history cache miss full page reload requests as a “HX-Request” by returning this response header. This should always be disabled when using HX-Request header to optionally return partial responses |

</div>

You can set them directly in javascript, or you can use a `meta` tag:

``` html
<meta name="htmx-config" content='{"defaultSwapStyle":"outerHTML"}'>
```

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

And that’s it!

Have fun with htmx! You can accomplish [quite a bit](https://htmx.org/examples/) without writing a lot of code!

</div>

</div>

</div>

<div class="c content wide-content">

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

# index__0d275230

- Source URL: https://htmx.org/api/
- Source file: `fetch/htmx_org_0d275230.html`
- Hash: `0d275230`
- Category: `htmx/api`

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

# Javascript API

While it is not a focus of the library, htmx does provide a small API of helper methods, intended mainly for <a href="https://htmx.org/extensions" rel="noopener" target="_blank">extension development</a> or for working with [events](https://htmx.org/events/).

The <a href="https://hyperscript.org" rel="noopener" target="_blank">hyperscript</a> project is intended to provide more extensive scripting support for htmx-based applications.

### <a href="#addClass" class="zola-anchor" aria-label="Anchor link for: addClass">Method - <code>htmx.addClass()</code></a>

This method adds a class to the given element.

##### <a href="#parameters" class="zola-anchor" aria-label="Anchor link for: parameters">Parameters</a>

- `elt` - the element to add the class to
- `class` - the class to add

or

- `elt` - the element to add the class to
- `class` - the class to add
- `delay` - delay (in milliseconds ) before class is added

##### <a href="#example" class="zola-anchor" aria-label="Anchor link for: example">Example</a>

``` js
  // add the class 'myClass' to the element with the id 'demo'
  htmx.addClass(htmx.find('#demo'), 'myClass');

  // add the class 'myClass' to the element with the id 'demo' after 1 second
  htmx.addClass(htmx.find('#demo'), 'myClass', 1000);
```

### <a href="#ajax" class="zola-anchor" aria-label="Anchor link for: ajax">Method - <code>htmx.ajax()</code></a>

Issues an htmx-style AJAX request. This method returns a Promise, so a callback can be executed after the content has been inserted into the DOM.

##### <a href="#parameters-1" class="zola-anchor" aria-label="Anchor link for: parameters-1">Parameters</a>

- `verb` - ‘GET’, ‘POST’, etc.
- `path` - the URL path to make the AJAX
- `element` - the element to target (defaults to the `body`)

or

- `verb` - ‘GET’, ‘POST’, etc.
- `path` - the URL path to make the AJAX
- `selector` - a selector for the target

or

- `verb` - ‘GET’, ‘POST’, etc.
- `path` - the URL path to make the AJAX
- `context` - a context object that contains any of the following
  - `source` - the source element of the request, `hx-*` attrs which affect the request will be resolved against that element and its ancestors
  - `event` - an event that “triggered” the request
  - `handler` - a callback that will handle the response HTML
  - `target` - the target to swap the response into
  - `swap` - how the response will be swapped in relative to the target
  - `values` - values to submit with the request
  - `headers` - headers to submit with the request
  - `select` - allows you to select the content you want swapped from a response
  - `selectOOB` - allows you to select content for out-of-band swaps from a response
  - `push` - can be `'true'` or a path to push a URL into browser location history
  - `replace` - can be `'true'` or a path to replace the URL in the browser location history

##### <a href="#example-1" class="zola-anchor" aria-label="Anchor link for: example-1">Example</a>

``` js
    // issue a GET to /example and put the response HTML into #myDiv
    htmx.ajax('GET', '/example', '#myDiv')

    // issue a GET to /example and replace #myDiv with the response
    htmx.ajax('GET', '/example', {target:'#myDiv', swap:'outerHTML'})

    // execute some code after the content has been inserted into the DOM
    htmx.ajax('GET', '/example', '#myDiv').then(() => {
      // this code will be executed after the 'htmx:afterOnLoad' event,
      // and before the 'htmx:xhr:loadend' event
      console.log('Content inserted successfully!');
    });
```

### <a href="#closest" class="zola-anchor" aria-label="Anchor link for: closest">Method - <code>htmx.closest()</code></a>

Finds the closest matching element in the given elements parentage, inclusive of the element

##### <a href="#parameters-2" class="zola-anchor" aria-label="Anchor link for: parameters-2">Parameters</a>

- `elt` - the element to find the selector from
- `selector` - the selector to find

##### <a href="#example-2" class="zola-anchor" aria-label="Anchor link for: example-2">Example</a>

``` js
  // find the closest enclosing div of the element with the id 'demo'
  htmx.closest(htmx.find('#demo'), 'div');
```

### <a href="#config" class="zola-anchor" aria-label="Anchor link for: config">Property - <code>htmx.config</code></a>

A property holding the configuration htmx uses at runtime.

Note that using a [meta tag](https://htmx.org/docs/#config) is the preferred mechanism for setting these properties.

##### <a href="#properties" class="zola-anchor" aria-label="Anchor link for: properties">Properties</a>

- `attributesToSettle:["class", "style", "width", "height"]` - array of strings: the attributes to settle during the settling phase
- `refreshOnHistoryMiss:false` - boolean: if set to `true` htmx will issue a full page refresh on history misses rather than use an AJAX request
- `defaultSettleDelay:20` - int: the default delay between completing the content swap and settling attributes
- `defaultSwapDelay:0` - int: the default delay between receiving a response from the server and doing the swap
- `defaultSwapStyle:'innerHTML'` - string: the default swap style to use if [`hx-swap`](https://htmx.org/attributes/hx-swap/) is omitted
- `historyCacheSize:10` - int: the number of pages to keep in `localStorage` for history support
- `historyEnabled:true` - boolean: whether or not to use history
- `includeIndicatorStyles:true` - boolean: if true, htmx will inject a small amount of CSS into the page to make indicators invisible unless the `htmx-indicator` class is present
- `indicatorClass:'htmx-indicator'` - string: the class to place on indicators when a request is in flight
- `requestClass:'htmx-request'` - string: the class to place on triggering elements when a request is in flight
- `addedClass:'htmx-added'` - string: the class to temporarily place on elements that htmx has added to the DOM
- `settlingClass:'htmx-settling'` - string: the class to place on target elements when htmx is in the settling phase
- `swappingClass:'htmx-swapping'` - string: the class to place on target elements when htmx is in the swapping phase
- `allowEval:true` - boolean: allows the use of eval-like functionality in htmx, to enable `hx-vars`, trigger conditions & script tag evaluation. Can be set to `false` for CSP compatibility.
- `allowScriptTags:true` - boolean: allows script tags to be evaluated in new content
- `inlineScriptNonce:''` - string: the <a href="https://developer.mozilla.org/docs/Web/HTML/Global_attributes/nonce" rel="noopener" target="_blank">nonce</a> to add to inline scripts
- `inlineStyleNonce:''` - string: the <a href="https://developer.mozilla.org/docs/Web/HTML/Global_attributes/nonce" rel="noopener" target="_blank">nonce</a> to add to inline styles
- `withCredentials:false` - boolean: allow cross-site Access-Control requests using credentials such as cookies, authorization headers or TLS client certificates
- `timeout:0` - int: the number of milliseconds a request can take before automatically being terminated
- `wsReconnectDelay:'full-jitter'` - string/function: the default implementation of `getWebSocketReconnectDelay` for reconnecting after unexpected connection loss by the event code `Abnormal Closure`, `Service Restart` or `Try Again Later`
- `wsBinaryType:'blob'` - string: the <a href="https://developer.mozilla.org/docs/Web/API/WebSocket/binaryType" rel="noopener" target="_blank">the type of binary data</a> being received over the WebSocket connection
- `disableSelector:"[hx-disable], [data-hx-disable]"` - array of strings: htmx will not process elements with this attribute on it or a parent
- `disableInheritance:false` - boolean: If it is set to `true`, the inheritance of attributes is completely disabled and you can explicitly specify the inheritance with the [hx-inherit](https://htmx.org/attributes/hx-inherit/) attribute.
- `scrollBehavior:'instant'` - string: the scroll behavior when using the [show](https://htmx.org/attributes/hx-swap/#scrolling-scroll-show) modifier with `hx-swap`. The allowed values are `instant` (scrolling should happen instantly in a single jump), `smooth` (scrolling should animate smoothly) and `auto` (scroll behavior is determined by the computed value of <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/scroll-behavior" rel="noopener" target="_blank">scroll-behavior</a>).
- `defaultFocusScroll:false` - boolean: if the focused element should be scrolled into view, can be overridden using the [focus-scroll](https://htmx.org/attributes/hx-swap/#focus-scroll) swap modifier
- `getCacheBusterParam:false` - boolean: if set to true htmx will append the target element to the `GET` request in the format `org.htmx.cache-buster=targetElementId`
- `globalViewTransitions:false` - boolean: if set to `true`, htmx will use the <a href="https://developer.mozilla.org/en-US/docs/Web/API/View_Transitions_API" rel="noopener" target="_blank">View Transition</a> API when swapping in new content.
- `methodsThatUseUrlParams:["get", "delete"]` - array of strings: htmx will format requests with these methods by encoding their parameters in the URL, not the request body
- `selfRequestsOnly:true` - boolean: whether to only allow AJAX requests to the same domain as the current document
- `ignoreTitle:false` - boolean: if set to `true` htmx will not update the title of the document when a `title` tag is found in new content
- `scrollIntoViewOnBoost:true` - boolean: whether or not the target of a boosted element is scrolled into the viewport. If `hx-target` is omitted on a boosted element, the target defaults to `body`, causing the page to scroll to the top.
- `triggerSpecsCache:null` - object: the cache to store evaluated trigger specifications into, improving parsing performance at the cost of more memory usage. You may define a simple object to use a never-clearing cache, or implement your own system using a <a href="https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy" rel="noopener" target="_blank">proxy object</a>
- `htmx.config.responseHandling:[...]` - HtmxResponseHandlingConfig\[\]: the default [Response Handling](https://htmx.org/docs/#response-handling) behavior for response status codes can be configured here to either swap or error
- `htmx.config.allowNestedOobSwaps:true` - boolean: whether to process OOB swaps on elements that are nested within the main response element. See [Nested OOB Swaps](https://htmx.org/attributes/hx-swap-oob/#nested-oob-swaps).
- `htmx.config.historyRestoreAsHxRequest:true` - Whether to treat history cache miss full page reload requests as a “HX-Request” by returning this response header. This should always be disabled when using HX-Request header to optionally return partial responses
- `htmx.config.reportValidityOfForms:false` - Whether to report input validation errors to the end user and update focus to the first input that fails validation. This should always be enabled as this matches default browser form submit behaviour

##### <a href="#example-3" class="zola-anchor" aria-label="Anchor link for: example-3">Example</a>

``` js
  // update the history cache size to 30
  htmx.config.historyCacheSize = 30;
```

### <a href="#createEventSource" class="zola-anchor" aria-label="Anchor link for: createEventSource">Property - <code>htmx.createEventSource</code></a>

A property used to create new <a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/sse/README.md" rel="noopener" target="_blank">Server Sent Event</a> sources. This can be updated to provide custom SSE setup.

##### <a href="#value" class="zola-anchor" aria-label="Anchor link for: value">Value</a>

- `func(url)` - a function that takes a URL string and returns a new `EventSource`

##### <a href="#example-4" class="zola-anchor" aria-label="Anchor link for: example-4">Example</a>

``` js
  // override SSE event sources to not use credentials
  htmx.createEventSource = function(url) {
    return new EventSource(url, {withCredentials:false});
  };
```

### <a href="#createWebSocket" class="zola-anchor" aria-label="Anchor link for: createWebSocket">Property - <code>htmx.createWebSocket</code></a>

A property used to create new <a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/ws/README.md" rel="noopener" target="_blank">WebSocket</a>. This can be updated to provide custom WebSocket setup.

##### <a href="#value-1" class="zola-anchor" aria-label="Anchor link for: value-1">Value</a>

- `func(url)` - a function that takes a URL string and returns a new `WebSocket`

##### <a href="#example-5" class="zola-anchor" aria-label="Anchor link for: example-5">Example</a>

``` js
  // override WebSocket to use a specific protocol
  htmx.createWebSocket = function(url) {
    return new WebSocket(url, ['wss']);
  };
```

### <a href="#defineExtension" class="zola-anchor" aria-label="Anchor link for: defineExtension">Method - <code>htmx.defineExtension()</code></a>

Defines a new htmx <a href="https://htmx.org/extensions" rel="noopener" target="_blank">extension</a>.

##### <a href="#parameters-3" class="zola-anchor" aria-label="Anchor link for: parameters-3">Parameters</a>

- `name` - the extension name
- `ext` - the extension definition

##### <a href="#example-6" class="zola-anchor" aria-label="Anchor link for: example-6">Example</a>

``` js
  // defines a silly extension that just logs the name of all events triggered
  htmx.defineExtension("silly", {
    onEvent : function(name, evt) {
      console.log("Event " + name + " was triggered!")
    }
  });
```

### <a href="#find" class="zola-anchor" aria-label="Anchor link for: find">Method - <code>htmx.find()</code></a>

Finds an element matching the selector

##### <a href="#parameters-4" class="zola-anchor" aria-label="Anchor link for: parameters-4">Parameters</a>

- `selector` - the selector to match

or

- `elt` - the root element to find the matching element in, inclusive
- `selector` - the selector to match

##### <a href="#example-7" class="zola-anchor" aria-label="Anchor link for: example-7">Example</a>

``` js
    // find div with id my-div
    var div = htmx.find("#my-div")

    // find div with id another-div within that div
    var anotherDiv = htmx.find(div, "#another-div")
```

### <a href="#findAll" class="zola-anchor" aria-label="Anchor link for: findAll">Method - <code>htmx.findAll()</code></a>

Finds all elements matching the selector

##### <a href="#parameters-5" class="zola-anchor" aria-label="Anchor link for: parameters-5">Parameters</a>

- `selector` - the selector to match

or

- `elt` - the root element to find the matching elements in, inclusive
- `selector` - the selector to match

##### <a href="#example-8" class="zola-anchor" aria-label="Anchor link for: example-8">Example</a>

``` js
    // find all divs
    var allDivs = htmx.findAll("div")

    // find all paragraphs within a given div
    var allParagraphsInMyDiv = htmx.findAll(htmx.find("#my-div"), "p")
```

### <a href="#logAll" class="zola-anchor" aria-label="Anchor link for: logAll">Method - <code>htmx.logAll()</code></a>

Log all htmx events, useful for debugging.

##### <a href="#example-9" class="zola-anchor" aria-label="Anchor link for: example-9">Example</a>

``` js
    htmx.logAll();
```

### <a href="#logNone" class="zola-anchor" aria-label="Anchor link for: logNone">Method - <code>htmx.logNone()</code></a>

Log no htmx events, call this to turn off the debugger if you previously enabled it.

##### <a href="#example-10" class="zola-anchor" aria-label="Anchor link for: example-10">Example</a>

``` js
    htmx.logNone();
```

### <a href="#logger" class="zola-anchor" aria-label="Anchor link for: logger">Property - <code>htmx.logger</code></a>

The logger htmx uses to log with

##### <a href="#value-2" class="zola-anchor" aria-label="Anchor link for: value-2">Value</a>

- `func(elt, eventName, detail)` - a function that takes an element, eventName and event detail and logs it

##### <a href="#example-11" class="zola-anchor" aria-label="Anchor link for: example-11">Example</a>

``` js
    htmx.logger = function(elt, event, data) {
        if(console) {
            console.log("INFO:", event, elt, data);
        }
    }
```

### <a href="#off" class="zola-anchor" aria-label="Anchor link for: off">Method - <code>htmx.off()</code></a>

Removes an event listener from an element

##### <a href="#parameters-6" class="zola-anchor" aria-label="Anchor link for: parameters-6">Parameters</a>

- `eventName` - the event name to remove the listener from
- `listener` - the listener to remove

or

- `target` - the element to remove the listener from
- `eventName` - the event name to remove the listener from
- `listener` - the listener to remove

##### <a href="#example-12" class="zola-anchor" aria-label="Anchor link for: example-12">Example</a>

``` js
    // remove this click listener from the body
    htmx.off("click", myEventListener);

    // remove this click listener from the given div
    htmx.off("#my-div", "click", myEventListener)
```

### <a href="#on" class="zola-anchor" aria-label="Anchor link for: on">Method - <code>htmx.on()</code></a>

Adds an event listener to an element

##### <a href="#parameters-7" class="zola-anchor" aria-label="Anchor link for: parameters-7">Parameters</a>

- `eventName` - the event name to add the listener for
- `listener` - the listener to add
- `options` - an <a href="https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#options" rel="noopener" target="_blank">options</a> object (or a <a href="https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#usecapture" rel="noopener" target="_blank">useCapture</a> boolean) to add to the event listener (optional)

or

- `target` - the element to add the listener to
- `eventName` - the event name to add the listener for
- `listener` - the listener to add
- `options` - an <a href="https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#options" rel="noopener" target="_blank">options</a> object (or a <a href="https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#usecapture" rel="noopener" target="_blank">useCapture</a> boolean) to add to the event listener (optional)

##### <a href="#example-13" class="zola-anchor" aria-label="Anchor link for: example-13">Example</a>

``` js
    // add a click listener to the body
    var myEventListener = htmx.on("click", function(evt){ console.log(evt); });

    // add a click listener to the given div
    var myEventListener = htmx.on("#my-div", "click", function(evt){ console.log(evt); });

    // add a click listener to the given div that should only be invoked once
    var myEventListener = htmx.on("#my-div", "click", function(evt){ console.log(evt); }, { once: true });
```

### <a href="#onLoad" class="zola-anchor" aria-label="Anchor link for: onLoad">Method - <code>htmx.onLoad()</code></a>

Adds a callback for the `htmx:load` event. This can be used to process new content, for example initializing the content with a javascript library

##### <a href="#parameters-8" class="zola-anchor" aria-label="Anchor link for: parameters-8">Parameters</a>

- `callback(elt)` - the callback to call on newly loaded content

##### <a href="#example-14" class="zola-anchor" aria-label="Anchor link for: example-14">Example</a>

``` js
    htmx.onLoad(function(elt){
        MyLibrary.init(elt);
    })
```

### <a href="#parseInterval" class="zola-anchor" aria-label="Anchor link for: parseInterval">Method - <code>htmx.parseInterval()</code></a>

Parses an interval string consistent with the way htmx does. Useful for plugins that have timing-related attributes.

Caution: Accepts an int followed by either `s` or `ms`. All other values use `parseFloat`

##### <a href="#parameters-9" class="zola-anchor" aria-label="Anchor link for: parameters-9">Parameters</a>

- `str` - timing string

##### <a href="#example-15" class="zola-anchor" aria-label="Anchor link for: example-15">Example</a>

``` js
    // returns 3000
    var milliseconds = htmx.parseInterval("3s");

    // returns 3 - Caution
    var milliseconds = htmx.parseInterval("3m");
```

### <a href="#process" class="zola-anchor" aria-label="Anchor link for: process">Method - <code>htmx.process()</code></a>

Processes new content, enabling htmx behavior. This can be useful if you have content that is added to the DOM outside of the normal htmx request cycle but still want htmx attributes to work.

##### <a href="#parameters-10" class="zola-anchor" aria-label="Anchor link for: parameters-10">Parameters</a>

- `elt` - element to process

##### <a href="#example-16" class="zola-anchor" aria-label="Anchor link for: example-16">Example</a>

``` js
  document.body.innerHTML = "<div hx-get='/example'>Get it!</div>"
  // process the newly added content
  htmx.process(document.body);
```

### <a href="#remove" class="zola-anchor" aria-label="Anchor link for: remove">Method - <code>htmx.remove()</code></a>

Removes an element from the DOM

##### <a href="#parameters-11" class="zola-anchor" aria-label="Anchor link for: parameters-11">Parameters</a>

- `elt` - element to remove

or

- `elt` - element to remove
- `delay` - delay (in milliseconds ) before element is removed

##### <a href="#example-17" class="zola-anchor" aria-label="Anchor link for: example-17">Example</a>

``` js
  // removes my-div from the DOM
  htmx.remove(htmx.find("#my-div"));

  // removes my-div from the DOM after a delay of 2 seconds
  htmx.remove(htmx.find("#my-div"), 2000);
```

### <a href="#removeClass" class="zola-anchor" aria-label="Anchor link for: removeClass">Method - <code>htmx.removeClass()</code></a>

Removes a class from the given element

##### <a href="#parameters-12" class="zola-anchor" aria-label="Anchor link for: parameters-12">Parameters</a>

- `elt` - element to remove the class from
- `class` - the class to remove

or

- `elt` - element to remove the class from
- `class` - the class to remove
- `delay` - delay (in milliseconds ) before class is removed

##### <a href="#example-18" class="zola-anchor" aria-label="Anchor link for: example-18">Example</a>

``` js
  // removes .myClass from my-div
  htmx.removeClass(htmx.find("#my-div"), "myClass");

  // removes .myClass from my-div after 6 seconds
  htmx.removeClass(htmx.find("#my-div"), "myClass", 6000);
```

### <a href="#removeExtension" class="zola-anchor" aria-label="Anchor link for: removeExtension">Method - <code>htmx.removeExtension()</code></a>

Removes the given extension from htmx

##### <a href="#parameters-13" class="zola-anchor" aria-label="Anchor link for: parameters-13">Parameters</a>

- `name` - the name of the extension to remove

##### <a href="#example-19" class="zola-anchor" aria-label="Anchor link for: example-19">Example</a>

``` js
  htmx.removeExtension("my-extension");
```

### <a href="#swap" class="zola-anchor" aria-label="Anchor link for: swap">Method - <code>htmx.swap()</code></a>

Performs swapping (and settling) of HTML content

##### <a href="#parameters-14" class="zola-anchor" aria-label="Anchor link for: parameters-14">Parameters</a>

- `target` - the HTML element or string selector of swap target
- `content` - string representation of content to be swapped
- `swapSpec` - swapping specification, representing parameters from `hx-swap`
  - `swapStyle` (required) - swapping style (`innerHTML`, `outerHTML`, `beforebegin` etc)
  - `swapDelay`, `settleDelay` (number) - delays before swapping and settling respectively
  - `transition` (bool) - whether to use HTML transitions for swap
  - `ignoreTitle` (bool) - disables page title updates
  - `head` (string) - specifies `head` tag handling strategy (`merge` or `append`). Leave empty to disable head handling
  - `scroll`, `scrollTarget`, `show`, `showTarget`, `focusScroll` - specifies scroll handling after swap
- `swapOptions` - additional *optional* parameters for swapping
  - `select` - selector for the content to be swapped (equivalent of `hx-select`)
  - `selectOOB` - selector for the content to be swapped out-of-band (equivalent of `hx-select-oob`)
  - `eventInfo` - an object to be attached to `htmx:afterSwap` and `htmx:afterSettle` elements
  - `anchor` - an anchor element that triggered scroll, will be scrolled into view on settle. Provides simple alternative to full scroll handling
  - `contextElement` - DOM element that serves as context to swapping operation. Currently used to find extensions enabled for specific element
  - `afterSwapCallback`, `afterSettleCallback` - callback functions called after swap and settle respectively. Take no arguments

##### <a href="#example-20" class="zola-anchor" aria-label="Anchor link for: example-20">Example</a>

``` js
    // swap #output element inner HTML with div element with "Swapped!" text
    htmx.swap("#output", "<div>Swapped!</div>", {swapStyle: 'innerHTML'});
```

### <a href="#takeClass" class="zola-anchor" aria-label="Anchor link for: takeClass">Method - <code>htmx.takeClass()</code></a>

Takes the given class from its siblings, so that among its siblings, only the given element will have the class.

##### <a href="#parameters-15" class="zola-anchor" aria-label="Anchor link for: parameters-15">Parameters</a>

- `elt` - the element that will take the class
- `class` - the class to take

##### <a href="#example-21" class="zola-anchor" aria-label="Anchor link for: example-21">Example</a>

``` js
  // takes the selected class from tab2's siblings
  htmx.takeClass(htmx.find("#tab2"), "selected");
```

### <a href="#toggleClass" class="zola-anchor" aria-label="Anchor link for: toggleClass">Method - <code>htmx.toggleClass()</code></a>

Toggles the given class on an element

##### <a href="#parameters-16" class="zola-anchor" aria-label="Anchor link for: parameters-16">Parameters</a>

- `elt` - the element to toggle the class on
- `class` - the class to toggle

##### <a href="#example-22" class="zola-anchor" aria-label="Anchor link for: example-22">Example</a>

``` js
  // toggles the selected class on tab2
  htmx.toggleClass(htmx.find("#tab2"), "selected");
```

### <a href="#trigger" class="zola-anchor" aria-label="Anchor link for: trigger">Method - <code>htmx.trigger()</code></a>

Triggers a given event on an element

##### <a href="#parameters-17" class="zola-anchor" aria-label="Anchor link for: parameters-17">Parameters</a>

- `elt` - the element to trigger the event on
- `name` - the name of the event to trigger
- `detail` - details for the event

##### <a href="#example-23" class="zola-anchor" aria-label="Anchor link for: example-23">Example</a>

``` js
  // triggers the myEvent event on #tab2 with the answer 42
  htmx.trigger("#tab2", "myEvent", {answer:42});
```

### <a href="#values" class="zola-anchor" aria-label="Anchor link for: values">Method - <code>htmx.values()</code></a>

Returns the input values that would resolve for a given element via the htmx value resolution mechanism

##### <a href="#parameters-18" class="zola-anchor" aria-label="Anchor link for: parameters-18">Parameters</a>

- `elt` - the element to resolve values on
- `request type` - the request type (e.g. `get` or `post`) non-GET’s will include the enclosing form of the element. Defaults to `post`

##### <a href="#example-24" class="zola-anchor" aria-label="Anchor link for: example-24">Example</a>

``` js
  // gets the values associated with this form
  var values = htmx.values(htmx.find("#myForm"));
```

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

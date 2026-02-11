# index__25e86e98

- Source URL: https://htmx.org/events/
- Source file: `fetch/htmx_org_25e86e98.html`
- Hash: `25e86e98`
- Category: `htmx/events`

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

# Events

Htmx provides an extensive events system that can be used to modify and enhance behavior. Events are listed below.

### <a href="#htmx:abort" class="zola-anchor" aria-label="Anchor link for: htmx:abort">Event - <code>htmx:abort</code></a>

This event is different than other events: htmx does not *trigger* it, but rather *listens* for it.

If you send an `htmx:abort` event to an element making a request, it will abort the request:

``` html
<button id="request-button" hx-post="/example">Issue Request</button>
<button onclick="htmx.trigger('#request-button', 'htmx:abort')">Cancel Request</button>
```

### <a href="#htmx:afterOnLoad" class="zola-anchor" aria-label="Anchor link for: htmx:afterOnLoad">Event - <code>htmx:afterOnLoad</code></a>

This event is triggered after an AJAX `onload` has finished. Note that this does not mean that the content has been swapped or settled yet, only that the request has finished.

##### <a href="#details" class="zola-anchor" aria-label="Anchor link for: details">Details</a>

- `detail.elt` - the element that dispatched the request or if the body no longer contains the element then the closest parent
- `detail.xhr` - the `XMLHttpRequest`
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:afterProcessNode" class="zola-anchor" aria-label="Anchor link for: htmx:afterProcessNode">Event - <code>htmx:afterProcessNode</code></a>

This event is triggered after htmx has initialized a DOM node. It can be useful for extensions to build additional features onto a node.

##### <a href="#details-1" class="zola-anchor" aria-label="Anchor link for: details-1">Details</a>

- `detail.elt` - the element being initialized

### <a href="#htmx:afterRequest" class="zola-anchor" aria-label="Anchor link for: htmx:afterRequest">Event - <code>htmx:afterRequest</code></a>

This event is triggered after an AJAX request has finished either in the case of a successful request (although one that may have returned a remote error code such as a `404`) or in a network error situation. This event can be paired with [`htmx:beforeRequest`](https://htmx.org/events/#htmx:beforeRequest) to wrap behavior around a request cycle.

##### <a href="#details-2" class="zola-anchor" aria-label="Anchor link for: details-2">Details</a>

- `detail.elt` - the element that dispatched the request or if the body no longer contains the element then the closest parent
- `detail.xhr` - the `XMLHttpRequest`
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request
- `detail.successful` - true if the response has a 20x status code or is marked `detail.isError = false` in the `htmx:beforeSwap` event, else false
- `detail.failed` - true if the response does not have a 20x status code or is marked `detail.isError = true` in the `htmx:beforeSwap` event, else false

### <a href="#htmx:afterSettle" class="zola-anchor" aria-label="Anchor link for: htmx:afterSettle">Event - <code>htmx:afterSettle</code></a>

This event is triggered after the DOM has [settled](https://htmx.org/docs/#request-operations).

##### <a href="#details-3" class="zola-anchor" aria-label="Anchor link for: details-3">Details</a>

- `detail.elt` - the updated element
- `detail.xhr` - the `XMLHttpRequest`
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:afterSwap" class="zola-anchor" aria-label="Anchor link for: htmx:afterSwap">Event - <code>htmx:afterSwap</code></a>

This event is triggered after new content has been [swapped into the DOM](https://htmx.org/docs/#swapping).

##### <a href="#details-4" class="zola-anchor" aria-label="Anchor link for: details-4">Details</a>

- `detail.elt` - the swapped in element
- `detail.xhr` - the `XMLHttpRequest`
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:beforeCleanupElement" class="zola-anchor" aria-label="Anchor link for: htmx:beforeCleanupElement">Event - <code>htmx:beforeCleanupElement</code></a>

This event is triggered before htmx [disables](https://htmx.org/attributes/hx-disable/) an element or removes it from the DOM.

##### <a href="#details-5" class="zola-anchor" aria-label="Anchor link for: details-5">Details</a>

- `detail.elt` - the element to be cleaned up

### <a href="#htmx:beforeOnLoad" class="zola-anchor" aria-label="Anchor link for: htmx:beforeOnLoad">Event - <code>htmx:beforeOnLoad</code></a>

This event is triggered before any response processing occurs. If you call `preventDefault()` on the event to cancel it, no swap will occur.

##### <a href="#details-6" class="zola-anchor" aria-label="Anchor link for: details-6">Details</a>

- `detail.elt` - the element that dispatched the request
- `detail.xhr` - the `XMLHttpRequest`
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:beforeProcessNode" class="zola-anchor" aria-label="Anchor link for: htmx:beforeProcessNode">Event - <code>htmx:beforeProcessNode</code></a>

This event is triggered before htmx initializes a DOM node and has processed all of its `hx-` attributes. This gives extensions and other external code the ability to modify the contents of a DOM node before it is processed.

##### <a href="#details-7" class="zola-anchor" aria-label="Anchor link for: details-7">Details</a>

- `detail.elt` - the element being initialized

### <a href="#htmx:beforeRequest" class="zola-anchor" aria-label="Anchor link for: htmx:beforeRequest">Event - <code>htmx:beforeRequest</code></a>

This event is triggered before an AJAX request is issued. If you call `preventDefault()` on the event to cancel it, no request will occur.

##### <a href="#details-8" class="zola-anchor" aria-label="Anchor link for: details-8">Details</a>

- `detail.elt` - the element that dispatched the request
- `detail.xhr` - the `XMLHttpRequest`
- `detail.target` - the target of the request
- `detail.boosted` - true if the request is via an element using boosting
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:beforeSend" class="zola-anchor" aria-label="Anchor link for: htmx:beforeSend">Event - <code>htmx:beforeSend</code></a>

This event is triggered right before a request is sent. You may not cancel the request with this event.

##### <a href="#details-9" class="zola-anchor" aria-label="Anchor link for: details-9">Details</a>

- `detail.elt` - the element that dispatched the request
- `detail.xhr` - the `XMLHttpRequest`
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:beforeSwap" class="zola-anchor" aria-label="Anchor link for: htmx:beforeSwap">Event - <code>htmx:beforeSwap</code></a>

This event is triggered before any new content has been [swapped into the DOM](https://htmx.org/docs/#swapping). Most values on `detail` can be set to override subsequent behavior, other than where response headers take precedence. If you call `preventDefault()` on the event to cancel it, no swap will occur.

You can modify the default swap behavior by modifying the `shouldSwap`, `selectOverride`, `swapOverride` and `target` properties of the event detail. See the documentation on [configuring swapping](https://htmx.org/docs/#modifying_swapping_behavior_with_events) for more details.

##### <a href="#details-10" class="zola-anchor" aria-label="Anchor link for: details-10">Details</a>

- `detail.elt` - the target of the swap
- `detail.xhr` - the `XMLHttpRequest`
- `detail.boosted` - true if the request is via an element using boosting
- `detail.requestConfig` - the configuration of the AJAX request
- `detail.requestConfig.elt` - the element that dispatched the request
- `detail.shouldSwap` - if the content will be swapped (defaults to `false` for non-200 response codes)
- `detail.ignoreTitle` - if `true` any title tag in the response will be ignored
- `detail.isError` - whether error events should be triggered and also determines the values of `detail.successful` and `detail.failed` in later events
- `detail.serverResponse` - the server response as text to be used for the swap
- `detail.selectOverride` - add this to use instead of an [`hx-select`](https://htmx.org/attributes/hx-select/) value
- `detail.swapOverride` - add this to use instead of an [`hx-swap`](https://htmx.org/attributes/hx-swap/) value
- `detail.target` - the target of the swap

### <a href="#htmx:beforeTransition" class="zola-anchor" aria-label="Anchor link for: htmx:beforeTransition">Event - <code>htmx:beforeTransition</code></a>

This event is triggered before a <a href="https://developer.mozilla.org/en-US/docs/Web/API/View_Transitions_API" rel="noopener" target="_blank">View Transition</a> wrapped swap occurs. If you call `preventDefault()` on the event to cancel it, the View Transition will not occur and the normal swapping logic will happen instead.

##### <a href="#details-11" class="zola-anchor" aria-label="Anchor link for: details-11">Details</a>

- `detail.elt` - the element that dispatched the request
- `detail.xhr` - the `XMLHttpRequest`
- `detail.boosted` - true if the request is via an element using boosting
- `detail.requestConfig` - the configuration of the AJAX request
- `detail.shouldSwap` - if the content will be swapped (defaults to `false` for non-200 response codes)
- `detail.target` - the target of the swap

### <a href="#htmx:configRequest" class="zola-anchor" aria-label="Anchor link for: htmx:configRequest">Event - <code>htmx:configRequest</code></a>

This event is triggered after htmx has collected parameters for inclusion in the request. It can be used to include or update the parameters that htmx will send:

``` javascript
document.body.addEventListener('htmx:configRequest', function(evt) {
    evt.detail.parameters['auth_token'] = getAuthToken(); // add a new parameter into the mix
});
```

Note that if an input value appears more than once the value in the `parameters` object will be an array, rather than a single value.

##### <a href="#details-12" class="zola-anchor" aria-label="Anchor link for: details-12">Details</a>

- `detail.parameters` - the parameters that will be submitted in the request
- `detail.unfilteredParameters` - the parameters that were found before filtering by [`hx-params`](https://htmx.org/attributes/hx-params/)
- `detail.headers` - the request headers
- `detail.elt` - the element that triggered the request
- `detail.target` - the target of the request
- `detail.verb` - the HTTP verb in use

### <a href="#htmx:confirm" class="zola-anchor" aria-label="Anchor link for: htmx:confirm">Event - <code>htmx:confirm</code></a>

This event is fired on every trigger for a request (not just on elements that have a hx-confirm attribute). It allows you to cancel (or delay) issuing the AJAX request. If you call `preventDefault()` on the event, it will not issue the given request. The `detail` object contains a function, `evt.detail.issueRequest(skipConfirmation=false)`, that can be used to issue the actual AJAX request at a later point. Combining these two features allows you to create an asynchronous confirmation dialog.

Here is a basic example that shows the basic usage of the `htmx:confirm` event without altering the default behavior:

``` javascript
document.body.addEventListener('htmx:confirm', function(evt) {
  // 0. To modify the behavior only for elements with the hx-confirm attribute,
  //    check if evt.detail.target.hasAttribute('hx-confirm')

  // 1. Prevent the default behavior (this will prevent the request from being issued)
  evt.preventDefault();
  
  // 2. Do your own logic here
  console.log(evt.detail)

  // 3. Manually issue the request when you are ready
  evt.detail.issueRequest(); // or evt.detail.issueRequest(true) to skip the built-in window.confirm()
});
```

And here is an example using <a href="https://sweetalert.js.org/guides/" rel="noopener" target="_blank">sweet alert</a> on any element with a `confirm-with-sweet-alert="{question}"` attribute on it:

``` javascript
document.body.addEventListener('htmx:confirm', function(evt) {
  // 1. The requirement to show the sweet alert is that the element has a confirm-with-sweet-alert
  //    attribute on it, if it doesn't we can return early and let the default behavior happen
  if (!evt.detail.target.hasAttribute('confirm-with-sweet-alert')) return

  // 2. Get the question from the attribute
  const question = evt.detail.target.getAttribute('confirm-with-sweet-alert');

  // 3. Prevent the default behavior (this will prevent the request from being issued)
  evt.preventDefault();

  // 4. Show the sweet alert
  swal({
    title: "Are you sure?",
    text: question || "Are you sure you want to continue?",
    icon: "warning",
    buttons: true,
    dangerMode: true,
  }).then((confirmed) => {
    if (confirmed) {
      // 5. If the user confirms, we can manually issue the request
      evt.detail.issueRequest(true); // true to skip the built-in window.confirm()
    }
  });
});
```

##### <a href="#details-13" class="zola-anchor" aria-label="Anchor link for: details-13">Details</a>

- `detail.elt` - the element in question
- `detail.etc` - additional request information (mostly unused)
- `detail.issueRequest(skipConfirmation=false)` - a function that can be invoked to issue the request (should be paired with `evt.preventDefault()`!), if skipConfirmation is `true` the original `window.confirm()` is not executed
- `detail.path` - the path of the request
- `detail.target` - the element that triggered the request
- `detail.triggeringEvent` - the original event that triggered this request
- `detail.verb` - the verb of the request (e.g. `GET`)
- `detail.question` - the question passed to `hx-confirm` attribute (only available if `hx-confirm` attribute is present)

### <a href="#htmx:historyCacheError" class="zola-anchor" aria-label="Anchor link for: htmx:historyCacheError">Event - <code>htmx:historyCacheError</code></a>

This event is triggered when an attempt to save the cache to `localStorage` fails

##### <a href="#details-14" class="zola-anchor" aria-label="Anchor link for: details-14">Details</a>

- `detail.cause` - the `Exception` that was thrown when attempting to save history to `localStorage`

### <a href="#htmx:historyCacheHit" class="zola-anchor" aria-label="Anchor link for: htmx:historyCacheHit">Event - <code>htmx:historyCacheHit</code></a>

This event is triggered when a cache hit occurs when restoring history

You can prevent the history restoration via `preventDefault()` to allow alternative restore handling. You can also override the details of the history restoration request in this event if required

##### <a href="#details-15" class="zola-anchor" aria-label="Anchor link for: details-15">Details</a>

- `detail.historyElt` - the history element or body that will get replaced
- `detail.item.content` - the content of the cache that will be swapped in
- `detail.item.title` - the page title to update from the cache
- `detail.path` - the path and query of the page being restored
- `detail.swapSpec` - the swapSpec to be used containing the defatul swapStyle=‘innerHTML’

### <a href="#htmx:historyCacheMiss" class="zola-anchor" aria-label="Anchor link for: htmx:historyCacheMiss">Event - <code>htmx:historyCacheMiss</code></a>

This event is triggered when a cache miss occurs when restoring history

You can prevent the history restoration via `preventDefault()` to allow alternative restore handling. You can also modify the xhr request or other details before it makes the the request to restore history

##### <a href="#details-16" class="zola-anchor" aria-label="Anchor link for: details-16">Details</a>

- `detail.historyElt` - the history element or body that will get replaced
- `detail.xhr` - the `XMLHttpRequest` that will retrieve the remote content for restoration
- `detail.path` - the path and query of the page being restored
- `detail.swapSpec` - the swapSpec to be used containing the defatul swapStyle=‘innerHTML’

### <a href="#htmx:historyCacheMissLoadError" class="zola-anchor" aria-label="Anchor link for: htmx:historyCacheMissLoadError">Event - <code>htmx:historyCacheMissLoadError</code></a>

This event is triggered when a cache miss occurs and a response has been retrieved from the server for the content to restore, but the response is an error (e.g. `404`)

##### <a href="#details-17" class="zola-anchor" aria-label="Anchor link for: details-17">Details</a>

- `detail.xhr` - the `XMLHttpRequest`
- `detail.path` - the path and query of the page being restored

### <a href="#htmx:historyCacheMissLoad" class="zola-anchor" aria-label="Anchor link for: htmx:historyCacheMissLoad">Event - <code>htmx:historyCacheMissLoad</code></a>

This event is triggered when a cache miss occurs and a response has been retrieved successfully from the server for the content to restore

You can modify the details before it makes the swap to restore the history

##### <a href="#details-18" class="zola-anchor" aria-label="Anchor link for: details-18">Details</a>

- `detail.historyElt` - the history element or body that will get replaced
- `detail.xhr` - the `XMLHttpRequest`
- `detail.path` - the path and query of the page being restored
- `detail.response` - the response text that will be swapped in
- `detail.swapSpec` - the swapSpec to be used containing the defatul swapStyle=‘innerHTML’

### <a href="#htmx:historyRestore" class="zola-anchor" aria-label="Anchor link for: htmx:historyRestore">Event - <code>htmx:historyRestore</code></a>

This event is triggered when htmx handles a history restoration action

##### <a href="#details-19" class="zola-anchor" aria-label="Anchor link for: details-19">Details</a>

- `detail.path` - the path and query of the page being restored
- `detail.cacheMiss` - set `true` if restore was a cache miss
- `detail.serverResponse` - with cache miss has the response text replaced
- `detail.item` - with cache hit the cache details that was restored

### <a href="#htmx:beforeHistorySave" class="zola-anchor" aria-label="Anchor link for: htmx:beforeHistorySave">Event - <code>htmx:beforeHistorySave</code></a>

This event is triggered before the content is saved in the history cache.

You can modify the contents of the historyElt to remove 3rd party javascript changes so a clean copy of the content can be backed up to the history cache

##### <a href="#details-20" class="zola-anchor" aria-label="Anchor link for: details-20">Details</a>

- `detail.path` - the path and query of the page being saved
- `detail.historyElt` - the history element about to be saved

### <a href="#htmx:load" class="zola-anchor" aria-label="Anchor link for: htmx:load">Event - <code>htmx:load</code></a>

This event is triggered when a new node is loaded into the DOM by htmx. Note that this event is also triggered when htmx is first initialized, with the document body as the target.

##### <a href="#details-21" class="zola-anchor" aria-label="Anchor link for: details-21">Details</a>

- `detail.elt` - the newly added element

### <a href="#htmx:noSSESourceError" class="zola-anchor" aria-label="Anchor link for: htmx:noSSESourceError">Event - <code>htmx:noSSESourceError</code></a>

This event is triggered when an element refers to an SSE event in its trigger, but no parent SSE source has been defined

##### <a href="#details-22" class="zola-anchor" aria-label="Anchor link for: details-22">Details</a>

- `detail.elt` - the element with the bad SSE trigger

### <a href="#htmx:oobAfterSwap" class="zola-anchor" aria-label="Anchor link for: htmx:oobAfterSwap">Event - <code>htmx:oobAfterSwap</code></a>

This event is triggered as part of an [out of band swap](https://htmx.org/docs/#oob_swaps) and behaves identically to an [after swap event](https://htmx.org/events/#htmx:afterSwap)

##### <a href="#details-23" class="zola-anchor" aria-label="Anchor link for: details-23">Details</a>

- `detail.elt` - the swapped in element
- `detail.shouldSwap` - if the content will be swapped (defaults to `true`)
- `detail.target` - the target of the swap
- `detail.fragment` - the response fragment

### <a href="#htmx:oobBeforeSwap" class="zola-anchor" aria-label="Anchor link for: htmx:oobBeforeSwap">Event - <code>htmx:oobBeforeSwap</code></a>

This event is triggered as part of an [out of band swap](https://htmx.org/docs/#oob_swaps) and behaves identically to a [before swap event](https://htmx.org/events/#htmx:beforeSwap)

##### <a href="#details-24" class="zola-anchor" aria-label="Anchor link for: details-24">Details</a>

- `detail.elt` - the target of the swap
- `detail.shouldSwap` - if the content will be swapped (defaults to `true`)
- `detail.target` - the target of the swap
- `detail.fragment` - the response fragment

### <a href="#htmx:oobErrorNoTarget" class="zola-anchor" aria-label="Anchor link for: htmx:oobErrorNoTarget">Event - <code>htmx:oobErrorNoTarget</code></a>

This event is triggered when an [out of band swap](https://htmx.org/docs/#oob_swaps) does not have a corresponding element in the DOM to switch with.

##### <a href="#details-25" class="zola-anchor" aria-label="Anchor link for: details-25">Details</a>

- `detail.content` - the element with the bad oob `id`
- `detail.target` - the bad CSS selector

### <a href="#htmx:onLoadError" class="zola-anchor" aria-label="Anchor link for: htmx:onLoadError">Event - <code>htmx:onLoadError</code></a>

This event is triggered when an error occurs during the `load` handling of an AJAX call

##### <a href="#details-26" class="zola-anchor" aria-label="Anchor link for: details-26">Details</a>

- `detail.xhr` - the `XMLHttpRequest`
- `detail.elt` - the element that triggered the request
- `detail.target` - the target of the request
- `detail.exception` - the exception that occurred
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:prompt" class="zola-anchor" aria-label="Anchor link for: htmx:prompt">Event - <code>htmx:prompt</code></a>

This event is triggered after a prompt has been shown to the user with the [`hx-prompt`](https://htmx.org/attributes/hx-prompt/) attribute. If this event is cancelled, the AJAX request will not occur.

##### <a href="#details-27" class="zola-anchor" aria-label="Anchor link for: details-27">Details</a>

- `detail.elt` - the element that triggered the request
- `detail.target` - the target of the request
- `detail.prompt` - the user response to the prompt

### <a href="#htmx:beforeHistoryUpdate" class="zola-anchor" aria-label="Anchor link for: htmx:beforeHistoryUpdate">Event - <code>htmx:beforeHistoryUpdate</code></a>

This event is triggered before a history update is performed. It can be used to modify the `path` or `type` used to update the history.

##### <a href="#details-28" class="zola-anchor" aria-label="Anchor link for: details-28">Details</a>

- `detail.history` - the `path` and `type` (push, replace) for the history update
- `detail.xhr` - the `XMLHttpRequest`
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:pushedIntoHistory" class="zola-anchor" aria-label="Anchor link for: htmx:pushedIntoHistory">Event - <code>htmx:pushedIntoHistory</code></a>

This event is triggered after a URL has been pushed into history.

##### <a href="#details-29" class="zola-anchor" aria-label="Anchor link for: details-29">Details</a>

- `detail.path` - the path and query of the URL that has been pushed into history

### <a href="#htmx:replacedInHistory" class="zola-anchor" aria-label="Anchor link for: htmx:replacedInHistory">Event - <code>htmx:replacedInHistory</code></a>

This event is triggered after a URL has been replaced in history.

##### <a href="#details-30" class="zola-anchor" aria-label="Anchor link for: details-30">Details</a>

- `detail.path` - the path and query of the URL that has been replaced in history

### <a href="#htmx:responseError" class="zola-anchor" aria-label="Anchor link for: htmx:responseError">Event - <code>htmx:responseError</code></a>

This event is triggered when an HTTP error response occurs

##### <a href="#details-31" class="zola-anchor" aria-label="Anchor link for: details-31">Details</a>

- `detail.xhr` - the `XMLHttpRequest`
- `detail.elt` - the element that triggered the request
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:sendAbort" class="zola-anchor" aria-label="Anchor link for: htmx:sendAbort">Event - <code>htmx:sendAbort</code></a>

This event is triggered when a request is aborted

##### <a href="#details-32" class="zola-anchor" aria-label="Anchor link for: details-32">Details</a>

- `detail.xhr` - the `XMLHttpRequest`
- `detail.elt` - the element that triggered the request
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:sendError" class="zola-anchor" aria-label="Anchor link for: htmx:sendError">Event - <code>htmx:sendError</code></a>

This event is triggered when a network error prevents an HTTP request from occurring

##### <a href="#details-33" class="zola-anchor" aria-label="Anchor link for: details-33">Details</a>

- `detail.xhr` - the `XMLHttpRequest`
- `detail.elt` - the element that triggered the request
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:sseError" class="zola-anchor" aria-label="Anchor link for: htmx:sseError">Event - <code>htmx:sseError</code></a>

This event is triggered when an error occurs with an SSE source

##### <a href="#details-34" class="zola-anchor" aria-label="Anchor link for: details-34">Details</a>

- `detail.elt` - the element with the bad SSE source
- `detail.error` - the error
- `detail.source` - the SSE source

### <a href="#htmx:swapError" class="zola-anchor" aria-label="Anchor link for: htmx:swapError">Event - <code>htmx:swapError</code></a>

This event is triggered when an error occurs during the swap phase

##### <a href="#details-35" class="zola-anchor" aria-label="Anchor link for: details-35">Details</a>

- `detail.xhr` - the `XMLHttpRequest`
- `detail.elt` - the element that triggered the request
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:targetError" class="zola-anchor" aria-label="Anchor link for: htmx:targetError">Event - <code>htmx:targetError</code></a>

This event is triggered when a bad selector is used for a [`hx-target`](https://htmx.org/attributes/hx-target/) attribute (e.g. an element ID without a preceding `#`)

##### <a href="#details-36" class="zola-anchor" aria-label="Anchor link for: details-36">Details</a>

- `detail.elt` - the element that triggered the request
- `detail.target` - the bad CSS selector

### <a href="#htmx:timeout" class="zola-anchor" aria-label="Anchor link for: htmx:timeout">Event - <code>htmx:timeout</code></a>

This event is triggered when a request timeout occurs. This wraps the typical `timeout` event of XMLHttpRequest.

Timeout time can be set using `htmx.config.timeout` or per element using [`hx-request`](https://htmx.org/attributes/hx-request/)

##### <a href="#details-37" class="zola-anchor" aria-label="Anchor link for: details-37">Details</a>

- `detail.elt` - the element that dispatched the request
- `detail.xhr` - the `XMLHttpRequest`
- `detail.target` - the target of the request
- `detail.requestConfig` - the configuration of the AJAX request

### <a href="#htmx:trigger" class="zola-anchor" aria-label="Anchor link for: htmx:trigger">Event - <code>htmx:trigger</code></a>

This event is triggered whenever an AJAX request would be, even if no AJAX request is specified. It is primarily intended to allow `hx-trigger` to execute client-side scripts; AJAX requests have more granular events available, like [`htmx:beforeRequest`](https://htmx.org/events/#htmx:beforeRequest) or [`htmx:afterRequest`](https://htmx.org/events/#htmx:afterRequest).

##### <a href="#details-38" class="zola-anchor" aria-label="Anchor link for: details-38">Details</a>

- `detail.elt` - the element that triggered the request

### <a href="#htmx:validateUrl" class="zola-anchor" aria-label="Anchor link for: htmx:validateUrl">Event - <code>htmx:validateUrl</code></a>

This event is triggered before a request is made, allowing you to validate the URL that htmx is going to request. If `preventDefault()` is invoked on the event, the request will not be made.

``` javascript
document.body.addEventListener('htmx:validateUrl', function (evt) {
  // only allow requests to the current server as well as myserver.com
  if (!evt.detail.sameHost && evt.detail.url.hostname !== "myserver.com") {
    evt.preventDefault();
  }
});
```

##### <a href="#details-39" class="zola-anchor" aria-label="Anchor link for: details-39">Details</a>

- `detail.elt` - the element that triggered the request
- `detail.url` - the URL Object representing the URL that a request will be sent to.
- `detail.sameHost` - will be `true` if the request is to the same host as the document

### <a href="#htmx:validation:validate" class="zola-anchor" aria-label="Anchor link for: htmx:validation:validate">Event - <code>htmx:validation:validate</code></a>

This event is triggered before an element is validated. It can be used with the `elt.setCustomValidity()` method to implement custom validation rules.

``` html
<form hx-post="/test">
  <input _="on htmx:validation:validate
               if my.value != 'foo'
                  call me.setCustomValidity('Please enter the value foo')
               else
                  call me.setCustomValidity('')"
         name="example">
</form>
```

##### <a href="#details-40" class="zola-anchor" aria-label="Anchor link for: details-40">Details</a>

- `detail.elt` - the element to be validated

### <a href="#htmx:validation:failed" class="zola-anchor" aria-label="Anchor link for: htmx:validation:failed">Event - <code>htmx:validation:failed</code></a>

This event is triggered when an element fails validation. If `preventDefault()` is invoked on the event, the reportValidity() enabled by `htmx.config.reportValidityOfForms` will not be called.

##### <a href="#details-41" class="zola-anchor" aria-label="Anchor link for: details-41">Details</a>

- `detail.elt` - the element that failed validation
- `detail.message` - the validation error message
- `detail.validity` - the validity object, which contains properties specifying how validation failed

### <a href="#htmx:validation:halted" class="zola-anchor" aria-label="Anchor link for: htmx:validation:halted">Event - <code>htmx:validation:halted</code></a>

This event is triggered when a request is halted due to validation errors.

##### <a href="#details-42" class="zola-anchor" aria-label="Anchor link for: details-42">Details</a>

- `detail.elt` - the element that triggered the request
- `detail.errors` - an array of error objects with the invalid elements and errors associated with them

### <a href="#htmx:xhr:abort" class="zola-anchor" aria-label="Anchor link for: htmx:xhr:abort">Event - <code>htmx:xhr:abort</code></a>

This event is triggered when an ajax request aborts

##### <a href="#details-43" class="zola-anchor" aria-label="Anchor link for: details-43">Details</a>

- `detail.elt` - the element that triggered the request

### <a href="#htmx:xhr:loadstart" class="zola-anchor" aria-label="Anchor link for: htmx:xhr:loadstart">Event - <code>htmx:xhr:loadstart</code></a>

This event is triggered when an ajax request starts

##### <a href="#details-44" class="zola-anchor" aria-label="Anchor link for: details-44">Details</a>

- `detail.elt` - the element that triggered the request

### <a href="#htmx:xhr:loadend" class="zola-anchor" aria-label="Anchor link for: htmx:xhr:loadend">Event - <code>htmx:xhr:loadend</code></a>

This event is triggered when an ajax request finishes

##### <a href="#details-45" class="zola-anchor" aria-label="Anchor link for: details-45">Details</a>

- `detail.elt` - the element that triggered the request

### <a href="#htmx:xhr:progress" class="zola-anchor" aria-label="Anchor link for: htmx:xhr:progress">Event - <code>htmx:xhr:progress</code></a>

This event is triggered periodically when an ajax request that supports progress is in flight

##### <a href="#details-46" class="zola-anchor" aria-label="Anchor link for: details-46">Details</a>

- `detail.elt` - the element that triggered the request

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

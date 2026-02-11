# ws__7b11dde6

- Source URL: https://htmx.org/extensions/ws/
- Source file: `fetch/htmx_org_7b11dde6.html`
- Hash: `7b11dde6`
- Category: `htmx/extensions`

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

# htmx Web Socket extension

The Web Sockets extension enables easy, bi-directional communication with <a href="https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_client_applications" rel="noopener" target="_blank">Web Sockets</a> servers directly from HTML. This replaces the experimental `hx-ws` attribute built into previous versions of htmx. For help migrating from older versions, see the [Migrating](https://htmx.org/extensions/ws/#migrating-from-previous-versions) guide at the bottom of this page.

Use the following attributes to configure how WebSockets behave:

- `ws-connect="<url>"` or `ws-connect="<prefix>:<url>"` - A URL to establish a `WebSocket` connection against.
- Prefixes `ws` or `wss` can optionally be specified. If not specified, HTMX defaults to adding the location’s scheme-type, host and port to have browsers send cookies via websockets.
- `ws-send` - Sends a message to the nearest websocket based on the trigger value for the element (either the natural event or the event specified by \[`hx-trigger`\])

## Installing

The fastest way to install `ws` is to load it via a CDN. Remember to always include the core htmx library before the extension and [enable the extension](https://htmx.org/extensions/ws/#usage).

``` HTML
<head>
    <script src="https://cdn.jsdelivr.net/npm/htmx.org@2.0.8/dist/htmx.min.js" integrity="sha384-/TgkGk7p307TH7EXJDuUlgG3Ce1UVolAOFopFekQkkXihi5u/6OCvVKyz1W+idaz" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/htmx-ext-ws@2.0.4" integrity="sha384-1RwI/nvUSrMRuNj7hX1+27J8XDdCoSLf0EjEyF69nacuWyiJYoQ/j39RT1mSnd2G" crossorigin="anonymous"></script>
</head>
<body hx-ext="ws">
```

An unminified version is also available at https://cdn.jsdelivr.net/npm/htmx-ext-ws/dist/ws.js.

While the CDN approach is simple, you may want to consider <a href="https://blog.wesleyac.com/posts/why-not-javascript-cdn" rel="noopener" target="_blank">not using CDNs in production</a>. The next easiest way to install `ws` is to simply copy it into your project. Download the extension from `https://cdn.jsdelivr.net/npm/htmx-ext-ws`, add it to the appropriate directory in your project and include it where necessary with a `<script>` tag.

For npm-style build systems, you can install `ws` via <a href="https://www.npmjs.com/" rel="noopener" target="_blank">npm</a>:

``` shell
npm install htmx-ext-ws
```

After installing, you’ll need to use appropriate tooling to bundle `node_modules/htmx-ext-ws/dist/ws.js` (or `.min.js`). For example, you might bundle the extension with htmx core from `node_modules/htmx.org/dist/htmx.js` and project-specific code.

If you are using a bundler to manage your javascript (e.g. Webpack, Rollup):

- Install `htmx.org` and `htmx-ext-ws` via npm
- Import both packages to your `index.js`

``` JS
import `htmx.org`;
import `htmx-ext-ws`; 
```

## Usage

``` html

<div hx-ext="ws" ws-connect="/chatroom">
    <div id="notifications"></div>
    <div id="chat_room">
        ...
    </div>
    <form id="form" ws-send>
        <input name="chat_message">
    </form>
</div>
```

### Configuration

WebSockets extension support two configuration options:

- `createWebSocket` - a factory function that can be used to create a custom WebSocket instances. Must be a function, returning `WebSocket` object
- `wsBinaryType` - a string value, that defines socket’s <a href="https://developer.mozilla.org/en-US/docs/Web/API/WebSocket/binaryType" rel="noopener" target="_blank"><code>binaryType</code></a> property. Default value is `blob`

### Receiving Messages from a WebSocket

The example above establishes a WebSocket to the `/chatroom` end point. Content that is sent down from the websocket will be parsed as HTML and swapped in by the `id` property, using the same logic as <a href="https://htmx.org/attributes/hx-swap-oob/" rel="noopener" target="_blank">Out of Band Swaps</a>.

As such, if you want to change the swapping method (e.g., append content at the end of an element or delegate swapping to an extension), you need to specify that in the message body, sent by the server.

``` html
<!-- will be interpreted as hx-swap-oob="true" by default -->
<form id="form">
    ...
</form>
<!-- will be appended to #notifications div -->
<div id="notifications" hx-swap-oob="beforeend">
    New message received
</div>
<!-- will be swapped using an extension -->
<div id="chat_room" hx-swap-oob="morphdom">
    ....
</div>
```

### Sending Messages to a WebSocket

In the example above, the form uses the `ws-send` attribute to indicate that when it is submitted, the form values should be **serialized as JSON** and send to the nearest enclosing `WebSocket`, in this case the `/chatroom` endpoint.

The serialized values will include a field, `HEADERS`, that includes the headers normally submitted with an htmx request.

### Automatic Reconnection

If the WebSocket is closed unexpectedly, due to `Abnormal Closure`, `Service Restart` or `Try Again Later`, this extension will attempt to reconnect until the connection is reestablished.

By default, the extension uses a full-jitter <a href="https://en.wikipedia.org/wiki/Exponential_backoff" rel="noopener" target="_blank">exponential-backoff algorithm</a> that chooses a randomized retry delay that grows exponentially over time. You can use a different algorithm by writing it into `htmx.config.wsReconnectDelay`. This function takes a single parameter, the number of retries, and returns the time (in milliseconds) to wait before trying again.

``` javascript
// example reconnect delay that you shouldn't use because
// it's not as good as the algorithm that's already in place
htmx.config.wsReconnectDelay = function (retryCount) {
    return retryCount * 1000 // return value in milliseconds
}
```

The extension also implements a simple queuing mechanism that keeps messages in memory when the socket is not in `OPEN` state and sends them once the connection is restored.

### Events

WebSockets extensions exposes a set of events that allow you to observe and customize its behavior.

#### Event - `htmx:wsConnecting`

This event is triggered when a connection to a WebSocket endpoint is being attempted.

##### Details

- `detail.event.type` - the type of the event (`'connecting'`)

#### Event - `htmx:wsOpen`

This event is triggered when a connection to a WebSocket endpoint has been established.

##### Details

- `detail.elt` - the element that holds the socket (the one with `ws-connect` attribute)
- `detail.event` - the original event from the socket
- `detail.socketWrapper` - the wrapper around socket object

#### Event - `htmx:wsClose`

This event is triggered when a connection to a WebSocket endpoint has been closed normally. You can check if the event was caused by an error by inspecting `detail.event` property.

##### Details

- `detail.elt` - the element that holds the socket (the one with `ws-connect` attribute)
- `detail.event` - the original event from the socket
- `detail.socketWrapper` - the wrapper around socket object

#### Event - `htmx:wsError`

This event is triggered when `onerror` event on a socket is raised.

##### Details

- `detail.elt` - the element that holds the socket (the one with `ws-connect` attribute)
- `detail.error` - the error object
- `detail.socketWrapper` - the wrapper around socket object

#### Event - `htmx:wsBeforeMessage`

This event is triggered when a message has just been received by a socket, similar to `htmx:beforeOnLoad`. This event fires before any processing occurs.

If the event is cancelled, no further processing will occur.

- `detail.elt` - the element that holds the socket (the one with `ws-connect` attribute)
- `detail.message` - raw message content
- `detail.socketWrapper` - the wrapper around socket object

#### Event - `htmx:wsAfterMessage`

This event is triggered when a message has been completely processed by htmx and all changes have been settled, similar to `htmx:afterOnLoad`.

Cancelling this event has no effect.

- `detail.elt` - the element that holds the socket (the one with `ws-connect` attribute)
- `detail.message` - raw message content
- `detail.socketWrapper` - the wrapper around socket object

#### Event - `htmx:wsConfigSend`

This event is triggered when preparing to send a message from `ws-send` element. Similarly to <a href="https://htmx.org/events#htmx:configRequest" rel="noopener" target="_blank"><code>htmx:configRequest</code></a>, it allows you to modify the message before sending.

If the event is cancelled, no further processing will occur and no messages will be sent.

##### Details

- `detail.parameters` - the parameters that will be submitted in the request
- `detail.unfilteredParameters` - the parameters that were found before filtering by <a href="https://htmx.org/attributes/hx-params" rel="noopener" target="_blank"><code>hx-params</code></a>
- `detail.headers` - the request headers. Will be attached to the body in `HEADERS` property, if not falsy
- `detail.errors` - validation errors. Will prevent sending and trigger <a href="https://htmx.org/events#htmx:validation:halted" rel="noopener" target="_blank"><code>htmx:validation:halted</code></a> event if not empty
- `detail.triggeringEvent` - the event that triggered sending
- `detail.messageBody` - raw message body that will be sent to the socket. Undefined, can be set to value of any type, supported by WebSockets. If set, will override default JSON serialization. Useful, if you want to use some other format, like XML or MessagePack
- `detail.elt` - the element that dispatched the sending (the one with `ws-send` attribute)
- `detail.socketWrapper` - the wrapper around socket object

#### Event - `htmx:wsBeforeSend`

This event is triggered just before sending a message. This includes messages from the queue. Message can not be modified at this point.

If the event is cancelled, the message will be discarded from the queue and not sent.

##### Details

- `detail.elt` - the element that dispatched the request (the one with `ws-connect` attribute)
- `detail.message` - the raw message content
- `detail.socketWrapper` - the wrapper around socket object

#### Event - `htmx:wsAfterSend`

This event is triggered just after sending a message. This includes messages from the queue.

Cancelling the event has no effect.

##### Details

- `detail.elt` - the element that dispatched the request (the one with `ws-connect` attribute)
- `detail.message` - the raw message content
- `detail.socketWrapper` - the wrapper around socket object

#### Socket wrapper

You may notice that all events expose `detail.socketWrapper` property. This wrapper holds the socket object itself and the message queue. It also encapsulates reconnection algorithm. It exposes a few members:

- `send(message, fromElt)` - sends a message safely. If the socket is not open, the message will be persisted in the queue instead and sent when the socket is ready.
- `sendImmediately(message, fromElt)` - attempts to send a message regardless of socket state, bypassing the queue. May fail
- `queue` - an array of messages, awaiting in the queue.

This wrapper can be used in your event handlers to monitor and manipulate the queue (e.g., you can reset the queue when reconnecting), and to send additional messages (e.g., if you want to send data in batches). The `fromElt` parameter is optional and, when specified, will trigger corresponding websocket events from specified element, namely `htmx:wsBeforeSend` and `htmx:wsAfterSend` events when sending your messages.

### Testing with the Demo Server

Htmx includes a demo WebSockets server written in Node.js that will help you to see WebSockets in action, and begin bootstrapping your own WebSockets code. It is located in the /test/ws-sse folder of the <a href="https://github.com/bigskysoftware/htmx-extensions" rel="noopener" target="_blank"><code>htmx-extensions</code></a> repository. Look at /test/ws-sse/README.md for instructions on running and using the test server.

### Migrating from Previous Versions

Previous versions of htmx used a built-in tag `hx-ws` to implement WebSockets. This code has been migrated into an extension instead. Here are the steps you need to take to migrate to this version:

| Old Attribute | New Attribute | Comments |
|----|----|----|
| `hx-ws=""` | `hx-ext="ws"` | Use the `hx-ext="ws"` attribute to install the WebSockets extension into any HTML element. |
| `hx-ws="connect:<url>"` | `ws-connect="<url>"` | Add a new attribute `ws-connect` to the tag that defines the extension to specify the URL of the WebSockets server you’re using. |
| `hx-ws="send"` | `ws-send=""` | Add a new attribute `ws-send` to mark any child forms that should send data to your WebSocket server |

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

# index__6d02a6d8

- Source URL: https://htmx.org/extensions/
- Source file: `fetch/htmx_org_6d02a6d8.html`
- Hash: `6d02a6d8`
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

# Extensions

htmx supports extensions to augment the core hypermedia infrastructure it provides. The extension mechanism takes pressure off the core library to add new features, allowing it to focus on its main purpose of <a href="https://dl.acm.org/doi/10.1145/3648188.3675127" rel="noopener" target="_blank">generalizing hypermedia controls</a>.

If you are interested in creating an extension for htmx, please see [Building htmx Extensions](/extensions/building).

htmx extensions are split into two categories:

- [core extensions](https://htmx.org/extensions/#core-extensions) - supported by the htmx team
- [community extensions](https://htmx.org/extensions/#community-extensions) - supported by the broader community

## Core Extensions

| Name | Description |
|----|----|
| [head-support](/extensions/head-support) | Provides support for merging head tag information (styles, etc.) in htmx requests |
| [htmx-1-compat](/extensions/htmx-1-compat) | Rolls back most of the behavioral changes of htmx 2 to the htmx 1 defaults. |
| [idiomorph](/extensions/idiomorph) | Provides a `morph` swap strategy based on the <a href="https://github.com/bigskysoftware/idiomorph/" rel="noopener" target="_blank">idiomorph</a> morphing library, which was created by the htmx team. |
| [preload](/extensions/preload) | This extension allows you to load HTML fragments into your browser’s cache before they are requested by the user, so that additional pages appear to users to load nearly instantaneously. |
| [response-targets](/extensions/response-targets) | This extension allows you to specify different target elements to be swapped when different HTTP response codes are received. |
| [sse](/extensions/sse) | Provides support for <a href="https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events" rel="noopener" target="_blank">Server Sent Events</a> directly from HTML. |
| [ws](/extensions/ws) | Provides bi-directional communication with <a href="https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_client_applications" rel="noopener" target="_blank">Web Sockets</a> servers directly from HTML |

## Community Extensions

Search Extensions:

<table>
<thead>
<tr>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/ajax-header/README.md" rel="noopener" target="_blank">ajax-header</a></td>
<td>Adds an <code>X-Requested-With</code> header to all requests made by htmx</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/alpine-morph/README.md" rel="noopener" target="_blank">alpine-morph</a></td>
<td>Alpine.js now has a lightweight <a href="https://alpinejs.dev/plugins/morph" rel="noopener" target="_blank">morph plugin</a> and this extension allows you to use it as the swapping mechanism in htmx which is necessary to retain Alpine state when you have entire Alpine components swapped by htmx.</td>
</tr>
<tr>
<td><a href="https://github.com/jamcole/htmx-ext-attribute-tools/blob/main/README.md" rel="noopener" target="_blank">attribute-tools</a></td>
<td>The <code>attribute-tools</code> extension allows you to specify attributes that will be swapped onto or off of the elements by using an <code>attributes</code> or <code>data-attributes</code> attribute. (similar to class-tools)</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/class-tools/README.md" rel="noopener" target="_blank">class-tools</a></td>
<td>The <code>class-tools</code> extension allows you to specify CSS classes that will be swapped onto or off of the elements by using a <code>classes</code> or <code>data-classes</code> attribute.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/debug/README.md" rel="noopener" target="_blank">debug</a></td>
<td>This extension will log all htmx events for the element it is on through the <code>console.debug</code> function. Note that during dev, using <code>htmx.logAll()</code> instead can often be sufficient.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/event-header/README.md" rel="noopener" target="_blank">event-header</a></td>
<td>This extension adds the <code>Triggering-Event</code> header to requests. The value of the header is a JSON serialized version of the event that triggered the request.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/loading-states/README.md" rel="noopener" target="_blank">loading-states</a></td>
<td>This extension allows you to easily manage loading states while a request is in flight, including disabling elements, and adding and removing CSS classes.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/morphdom-swap/README.md" rel="noopener" target="_blank">morphdom-swap</a></td>
<td>Provides a <code>morph</code> swap strategy based on the <a href="https://github.com/patrick-steele-idem/morphdom/" rel="noopener" target="_blank">morphdom</a> morphing library.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/multi-swap/README.md" rel="noopener" target="_blank">multi-swap</a></td>
<td>This extension allows you to swap multiple elements marked from the HTML response. You can also choose for each element which swap method should be used.</td>
</tr>
<tr>
<td><a href="https://github.com/craigharman/htmx-ext-no-cache/blob/master/README.md" rel="noopener" target="_blank">no-cache</a></td>
<td>This extension forces HTMX to bypass client caches and make a new request. An <code>hx-no-cache</code> header is also added to allow server-side caching to be bypassed.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/path-deps/README.md" rel="noopener" target="_blank">path-deps</a></td>
<td>This extension supports expressing inter-element dependencies based on paths, inspired by the <a href="http://intercoolerjs.org/docs.html#dependencies" rel="noopener" target="_blank">intercooler.js dependencies mechanism</a>.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/path-params/README.md" rel="noopener" target="_blank">path-params</a></td>
<td>This extension uses request parameters to populate path variables. Used parameters are removed so they won’t be sent in the query string or body anymore.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/remove-me/README.md" rel="noopener" target="_blank">remove-me</a></td>
<td>Allows you to remove an element after a specified interval.</td>
</tr>
<tr>
<td><a href="https://github.com/fanelfaa/htmx-ext-replace-params/blob/main/README.md" rel="noopener" target="_blank">replace-params</a></td>
<td>This extension uses request parameters to replace existing parameters. If given value is empty string then parameter will be deleted. This extension would be useful in situations like pagination, search that you only want to replace only few parameters instead of reset all parameters.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/restored/README.md" rel="noopener" target="_blank">restored</a></td>
<td>Triggers an event whenever a back button event is detected while using <code>hx-boost</code></td>
</tr>
<tr>
<td><a href="https://github.com/MichaelWest22/htmx-extensions/blob/main/src/safe-nonce/README.md" rel="noopener" target="_blank">safe-nonce</a></td>
<td>The <code>safe-nonce</code> extension can be used to improve the security of the application/web-site and help avoid XSS issues by allowing you to return known trusted inline scripts safely</td>
</tr>
<tr>
<td><a href="https://www.npmjs.com/package/hx-drag" rel="noopener" target="_blank">hx-drag</a></td>
<td>This extension allows htmx requests to be sent for drag drop</td>
</tr>
<tr>
<td><a href="https://github.com/FumingPower3925/htmx-dynamic-url/blob/main/README.md" rel="noopener" target="_blank">dynamic-url</a></td>
<td>Allows dynamic URL path templating using <code>{varName}</code> placeholders, resolved via configurable custom function or <code>window.</code> fallback. It does not rely on <code>hx-vals</code>. Useful when needing to perform requests to paths that depend on application state.</td>
</tr>
<tr>
<td>[optimistic](<a href="https://github.com/lorenseanstewart/hx-optimistic/blob/main/README.md" rel="noopener" target="_blank">https://github.com/FumingPower3925/htmx-dynamic-url</a></td>
<td>This extension provides a way to optimistically update the UI to increase perceived performance</td>
</tr>
</tbody>
<tbody>
<tr>
<th colspan="2" scope="rowgroup">Data API</th>
</tr>
&#10;<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/client-side-templates/README.md" rel="noopener" target="_blank">client-side-templates</a></td>
<td>This extension supports transforming a JSON/XML request response into HTML via a client-side template before it is swapped into the DOM.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/json-enc/README.md" rel="noopener" target="_blank">json-enc</a></td>
<td>This extension encodes parameters in JSON format instead of url format.</td>
</tr>
<tr>
<td><a href="https://github.com/xehrad/form-json/blob/main/README.md" rel="noopener" target="_blank">form-json</a></td>
<td>Similar to <code>json-enc</code>, but with <strong>type preservation</strong>. Converts form data into structured JSON while maintaining correct types for numbers, booleans, and files (Base64-encoded). Supports nested structures using dot (<code>.</code>) or bracket (<code>[]</code>) notation.</td>
</tr>
<tr>
<td><a href="https://github.com/Emtyloc/json-enc-custom/blob/main/README.md" rel="noopener" target="_blank">json-enc-custom</a></td>
<td>This extension works similarly to json-enc but allows for very complex structures, such as embedding JSON objects, lists, or handling indexes, just by using the name attribute.</td>
</tr>
<tr>
<td><a href="https://github.com/mariusGundersen/htmx-json" rel="noopener" target="_blank">htmx-json</a></td>
<td>Support JSON response by transforming the html directly. This is a slightly different approach than client-side-templates.</td>
</tr>
</tbody>
<tbody>
<tr>
<th colspan="2" scope="rowgroup">Integrations</th>
</tr>
&#10;<tr>
<td><a href="https://github.com/felipegenef/amz-content-sha256/blob/main/README.md" rel="noopener" target="_blank">amz-content-sha256</a></td>
<td>HTMX extension for interacting with AWS services that require the content hash as part of the request for data integrity verification.</td>
</tr>
<tr>
<td><a href="https://github.com/Renerick/htmx-signalr/blob/master/README.md" rel="noopener" target="_blank">signalr</a></td>
<td>Provides bidirectional real-time communication via <a href="https://github.com/dotnet/AspNetCore/tree/main/src/SignalR" rel="noopener" target="_blank">SignalR</a>.</td>
</tr>
</tbody>
<tbody>
<tr>
<th colspan="2" scope="rowgroup">Legacy</th>
</tr>
&#10;<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/disable-element/README.md" rel="noopener" target="_blank">disable-element</a></td>
<td>This extension disables an element during an htmx request, when configured on the element triggering the request. Note that this functionality is now part of the core of htmx via the <code>hx-disabled-elt</code> attribute.</td>
</tr>
<tr>
<td><a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/include-vals/README.md" rel="noopener" target="_blank">include-vals</a></td>
<td>The <code>include-vals</code> extension allows you to programmatically include values in a request with a <code>include-vals</code> attribute. Note that this functionality is now part of the core of htmx via the <code>hx-vals</code> attribute.</td>
</tr>
</tbody>
</table>

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

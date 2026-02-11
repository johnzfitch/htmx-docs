# hx-trigger__a868119d

- Source URL: https://htmx.org/headers/hx-trigger/
- Source file: `fetch/htmx_org_a868119d.html`
- Hash: `a868119d`
- Category: `htmx/headers`

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

# HX-Trigger Response Headers

These response headers can be used to trigger client side actions on the target element within a response to htmx. You can trigger a single event or as many uniquely named events as you would like.

The headers are:

- `HX-Trigger` - trigger events as soon as the response is received.
- `HX-Trigger-After-Settle` - trigger events after the [settling step](https://htmx.org/docs/#request-operations).
- `HX-Trigger-After-Swap` - trigger events after the [swap step](https://htmx.org/docs/#request-operations).

To trigger a single event with no additional details you can simply send the event name in a header like so:

`HX-Trigger: myEvent`

This will trigger `myEvent` on the triggering element and will bubble up to the body. As an example you could listen for this event like this:

``` javascript
document.body.addEventListener("myEvent", function(evt){
    alert("myEvent was triggered!");
})
```

… or like this, if you’re trying to trigger some element without using JS code:

``` html
<!-- Since it bubbles up to the <body>, we must use the `from:body` modifier below -->
<div hx-trigger="myEvent from:body" hx-get="/example"></div>
```

If you want to pass details along with the event, you can move to JSON for the value of the trigger:

`HX-Trigger: {"showMessage":"Here Is A Message"}`

To handle this event you would write the following code:

``` javascript
document.body.addEventListener("showMessage", function(evt){
    alert(evt.detail.value);
})
```

Note that the value of the message was put into the `detail.value` slot. If you wish to pass multiple pieces of data you can use a nested JSON object on the right hand side of the JSON object:

`HX-Trigger: {"showMessage":{"level" : "info", "message" : "Here Is A Message"}}`

And handle this event like so:

``` javascript
document.body.addEventListener("showMessage", function(evt){
   if(evt.detail.level === "info"){
     alert(evt.detail.message);   
   }
})
```

Each property of the JSON object on the right hand side will be copied onto the details object for the event.

### Targeting Other Elements

You can trigger events on other target elements by adding a `target` argument to the JSON object.

`HX-Trigger: {"showMessage":{"target" : "#otherElement"}}`

### Multiple Triggers

If you wish to invoke multiple events, you can simply add additional properties to the top level JSON object:

`HX-Trigger: {"event1":"A message", "event2":"Another message"}`

You may also trigger multiple events with no additional details by sending event names separated by commas, like so:

`HX-Trigger: event1, event2`

Using events gives you a lot of flexibility to add functionality to normal htmx responses.

## Notes

Response headers are not processed on 3xx response codes. see [Response Headers](https://htmx.org/docs/#response-headers)

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

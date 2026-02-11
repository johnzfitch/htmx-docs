# confirm__f83505b8

- Source URL: https://htmx.org/examples/confirm/
- Source file: `fetch/htmx_org_f83505b8.html`
- Hash: `f83505b8`
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

# A Customized Confirmation UI

htmx supports the [`hx-confirm`](https://htmx.org/attributes/hx-confirm/) attribute to provide a simple mechanism for confirming a user action. This uses the default `confirm()` function in javascript which, while trusty, may not be consistent with your applications UX.

In this example we will see how to use <a href="https://sweetalert2.github.io" rel="noopener" target="_blank">sweetalert2</a> to implement a custom confirmation dialog. Below are two examples, one using a click+custom event method, and one using the built-in `hx-confirm` attribute and the [`htmx:confirm`](https://htmx.org/events/#htmx:confirm) event.

## <a href="#using-on-click-custom-event" class="zola-anchor" aria-label="Anchor link for: using-on-click-custom-event">Using on click+custom event</a>

``` html
<script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
<button hx-get="/confirmed" 
        hx-trigger='confirmed'
        onClick="Swal.fire({title: 'Confirm', text:'Do you want to continue?'}).then((result)=>{
            if(result.isConfirmed){
              htmx.trigger(this, 'confirmed');  
            } 
        })">
  Click Me
</button>
```

Here we use javascript to show a Sweet Alert 2 on a click, asking for confirmation. If the user confirms the dialog, we then trigger the request by triggering the custom “confirmed” event which is then picked up by `hx-trigger`.

## <a href="#vanilla-js-hx-confirm" class="zola-anchor" aria-label="Anchor link for: vanilla-js-hx-confirm">Vanilla JS, hx-confirm</a>

``` html
<script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
<script>
  document.addEventListener("htmx:confirm", function(e) {
    // The event is triggered on every trigger for a request, so we need to check if the element
    // that triggered the request has a confirm question set via the hx-confirm attribute,
    // if not we can return early and let the default behavior happen
    if (!e.detail.question) return

    // This will prevent the request from being issued to later manually issue it
    e.preventDefault()

    Swal.fire({
      title: "Proceed?",
      text: `I ask you... ${e.detail.question}`
    }).then(function(result) {
      if (result.isConfirmed) {
        // If the user confirms, we manually issue the request
        e.detail.issueRequest(true); // true to skip the built-in window.confirm()
      }
    })
  })
</script>
  
<button hx-get="/confirmed" hx-confirm="Some confirm text here">
  Click Me
</button>
```

We add some javascript to invoke Sweet Alert 2 on a click, asking for confirmation. If the user confirms the dialog, we trigger the request by calling the `issueRequest` method. We pass `skipConfirmation=true` as argument to skip `window.confirm`.

This allows to use `hx-confirm`’s value in the prompt which is convenient when the question depends on the element e.g. a django list:

``` html
{% for client in clients %}
<button hx-post="/delete/{{client.pk}}" hx-confirm="Delete {{client.name}}??">Delete</button>
{% endfor %}
```

Learn more about the [`htmx:confirm`](https://htmx.org/events/#htmx:confirm) event [here](https://htmx.org/events/#htmx:confirm).

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

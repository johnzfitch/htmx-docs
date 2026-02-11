# update-other-content__3bdfa1fd

- Source URL: https://htmx.org/examples/update-other-content/
- Source file: `fetch/htmx_org_3bdfa1fd.html`
- Hash: `3bdfa1fd`
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

# Updating Other Content

A question that often comes up when people are first working with htmx is:

> “I need to update other content on the screen. How do I do this?”

There are multiple ways to do so, and in this example we will walk you through some of them.

We’ll use the following basic UI to discuss this concept: a simple table of contacts, and a form below it to add new contacts to the table using [hx-post](https://htmx.org/attributes/hx-post/).

``` html
<h2>Contacts</h2>
<table class="table">
  <thead>
    <tr>
      <th>Name</th>
      <th>Email</th>
      <th></th>
    </tr>
  </thead>
  <tbody id="contacts-table">
    ...
  </tbody>
</table>
<h2>Add A Contact</h2>
<form hx-post="/contacts">
  <label>
    Name
        <input name="name" type="text">  
  </label>
  <label>
    Email
        <input name="email" type="email">  
  </label>
</form>
```

The problem here is that when you submit a new contact in the form, you want the contact table above to refresh and include the contact that was just added by the form.

What solutions do we have?

## <a href="#expand" class="zola-anchor" aria-label="Anchor link for: expand">Solution 1: Expand the Target</a>

The easiest solution here is to “expand the target” of the form to enclose both the table *and* the form. For example, you could wrap the whole thing in a `div` and then target that `div` in the form:

``` html
<div id="table-and-form">
    <h2>Contacts</h2>
    <table class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
          <th></th>
        </tr>
      </thead>
      <tbody id="contacts-table">
        ...
      </tbody>
    </table>
    <h2>Add A Contact</h2>
    <form hx-post="/contacts" hx-target="#table-and-form">
      <label>
        Name
            <input name="name" type="text">  
      </label>
      <label>
        Email
            <input name="email" type="email">  
      </label>
    </form>
</div>
```

Note that we are targeting the enclosing div using the [hx-target](https://htmx.org/attributes/hx-target/) attribute. You would need to render both the table and the form in the response to the `POST` to `/contacts`.

This is a simple and reliable approach, although it might not feel particularly elegant.

## <a href="#oob" class="zola-anchor" aria-label="Anchor link for: oob">Solution 2: Out of Band Responses</a>

A more sophisticated approach to this problem would use [out of band swaps](https://htmx.org/attributes/hx-swap-oob/) to swap in updated content to the DOM.

Using this approach, the HTML doesn’t need to change from the original setup at all:

``` html
<h2>Contacts</h2>
<table class="table">
  <thead>
    <tr>
      <th>Name</th>
      <th>Email</th>
      <th></th>
    </tr>
  </thead>
  <tbody id="contacts-table">
    ...
  </tbody>
</table>
<h2>Add A Contact</h2>
<form hx-post="/contacts">
  <label>
    Name
        <input name="name" type="text">  
  </label>
  <label>
    Email
        <input name="email" type="email">  
  </label>
</form>
```

Instead of modifying something on the front end, in your response to the `POST` to `/contacts` you would include some additional content:

``` html
<tbody hx-swap-oob="beforeend:#contacts-table">
  <tr>
    <td>Joe Smith</td>
    <td>joe@smith.com</td>
  </tr>
</tbody>

<label>
  Name
      <input name="name" type="text">
</label>
<label>
  Email
      <input name="email" type="email">
</label>
```

This content uses the [hx-swap-oob](https://htmx.org/attributes/hx-swap-oob/) attribute to append itself to the `#contacts-table`, updating the table after a contact is added successfully.

## <a href="#events" class="zola-anchor" aria-label="Anchor link for: events">Solution 3: Triggering Events</a>

An even more sophisticated approach would be to trigger a client side event when a successful contact is created and then listen for that event on the table, causing the table to refresh.

``` html
<h2>Contacts</h2>
<table class="table">
  <thead>
    <tr>
      <th>Name</th>
      <th>Email</th>
      <th></th>
    </tr>
  </thead>
  <tbody id="contacts-table" hx-get="/contacts/table" hx-trigger="newContact from:body">
    ...
  </tbody>
</table>
<h2>Add A Contact</h2>
<form hx-post="/contacts">
  <label>
    Name
        <input name="name" type="text">  
  </label>
  <label>
    Email
        <input name="email" type="email">  
  </label>
</form>
```

We have added a new end-point `/contacts/table` that re-renders the contacts table. Our trigger for this request is a custom event, `newContact`. We listen for this event on the `body` because when it is triggered by the response to the form, it will end up hitting the body due to event bubbling.

When a successful contact creation occurs during a POST to `/contacts`, the response includes an [HX-Trigger](https://htmx.org/headers/hx-trigger/) response header that looks like this:

``` txt
HX-Trigger:newContact
```

This will trigger the table to issue a `GET` to `/contacts/table` and this will render the newly added contact row\
(in addition to the rest of the table.)

Very clean, event driven programming!

## <a href="#path-deps" class="zola-anchor" aria-label="Anchor link for: path-deps">Solution 4: Using the Path Dependencies Extension</a>

A final approach is to use REST-ful path dependencies to refresh the table. Intercooler.js, the predecessor to htmx, had <a href="https://intercoolerjs.org/docs.html#dependencies" rel="noopener" target="_blank">path-based dependencies</a> integrated into the library.

htmx dropped this as a core feature, but supports an extension, <a href="https://github.com/bigskysoftware/htmx-extensions/blob/main/src/path-deps/README.md" rel="noopener" target="_blank">path deps</a>, that gives you similar functionality.

Updating our example to use the extension would involve loading the extension javascript and then annotating our HTML like so:

``` html
<h2>Contacts</h2>
<table class="table">
  <thead>
    <tr>
      <th>Name</th>
      <th>Email</th>
      <th></th>
    </tr>
  </thead>
  <tbody id="contacts-table" hx-get="/contacts/table" hx-ext="path-deps"  hx-trigger="path-deps" path-deps="/contacts">
    ...
  </tbody>
</table>
<h2>Add A Contact</h2>
<form hx-post="/contacts">
  <label>
    Name
        <input name="name" type="text">  
  </label>
  <label>
    Email
        <input name="email" type="email">  
  </label>
</form>
```

Now, when the form posts to the `/contacts` URL, the `path-deps` extension will detect that and trigger an `path-deps` event on the contacts table, therefore triggering a request.

The advantage here is that you don’t need to do anything fancy with response headers. The downside is that a request will be issued on every `POST`, even if a contact was not successfully created.

## <a href="#which-should-i-use" class="zola-anchor" aria-label="Anchor link for: which-should-i-use">Which should I use?</a>

Generally I would recommend the first approach, expanding your target, especially if the elements that need to be updated are reasonably close to one another in the DOM. It is simple and reliable.

After that, I would say it is a tossup between the custom event and an OOB swap approaches. I would lean towards the custom event approach because I like event-oriented systems, but that’s a personal preference. Which one you choose should be dictated by your own software engineering tastes and which of the two matches up better with your server side technology of choice.

Finally, the path-deps approach is interesting, and if it fits well with your mental model and overall system architecture, it can be a fun way to avoid explicit refreshing. I would look at it last, however, unless the concept really grabs you.

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

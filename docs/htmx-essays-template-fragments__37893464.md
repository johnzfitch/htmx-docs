# template-fragments__37893464

- Source URL: https://htmx.org/essays/template-fragments/
- Source file: `fetch/htmx_org_37893464.html`
- Hash: `37893464`
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

# Template Fragments

Carson Gross

August 03, 2022

Template fragments are a relatively rare Server Side Rendering (SSR) template library feature that allow you to render a *fragment* or partial bit of the content within a template, rather than the entire template. This feature is very handy in [Hypermedia Driven Applications](https://htmx.org/essays/hypermedia-driven-applications/) because it allows you to decompose a particular view for partial updates *internally* without pulling fragments of the template out to separate files for rendering, creating a large number of individual template files.

By keeping all the HTML in a single file, it is also easier to reason about how a feature works. This follows the [Locality of Behavior](https://htmx.org/essays/locality-of-behaviour/) design principle.

## <a href="#motivation" class="zola-anchor" aria-label="Anchor link for: motivation">Motivation</a>

Let’s look at how template fragments, in an obscure templating language for java called <a href="https://github.com/bigskysoftware/chill/tree/master/chill-script" rel="noopener" target="_blank">chill templates</a>, can help us build an HDA.

Here is a simple chill template, `/contacts/detail.html` that displays a contact:

##### <a href="#contacts-detail-html" class="zola-anchor" aria-label="Anchor link for: contacts-detail-html">/contacts/detail.html</a>

``` html
<html>
    <body>
        <div hx-target="this">
          #if contact.archived
          <button hx-patch="/contacts/${contact.id}/unarchive">Unarchive</button>
          #else
          <button hx-delete="/contacts/${contact.id}">Archive</button>
          #end
        </div>
        <h3>Contact</h3>
        <p>${contact.email}</p>
    </body>
</html>
```

In the template we have an archiving feature where, depending on the archive state of the contact, we either display an “Archive” or an “Unarchive” button, both powered by htmx and issuing HTTP requests to different end points.

When we click whichever of the two buttons is being shown, we want to replace the content in the `div` that surrounds the button with an updated button. (Note the `hx-target="this"` on the div, so we are targeting that div’s innerHTML for replacement.) This will effectively flip the back and forth between “Archive” and “Unarchive”.

Now, unfortunately, if we wanted to render only the buttons and not the rest of this template, this would typically involve splitting the buttons out to their own template file and including it in this template, like so:

##### <a href="#contacts-detail-html-1" class="zola-anchor" aria-label="Anchor link for: contacts-detail-html-1">/contacts/detail.html</a>

``` html
<html>
    <body>
        <div hx-target="this">
          #include archive-ui.html
        </div>
        <h3>Contact</h3>
        <p>${contact.email}</p>
    </body>
</html>
```

##### <a href="#contacts-archive-ui-html" class="zola-anchor" aria-label="Anchor link for: contacts-archive-ui-html">/contacts/archive-ui.html</a>

``` html
#if contact.archived
<button hx-patch="/contacts/${contact.id}/unarchive">Unarchive</button>
#else
<button hx-delete="/contacts/${contact.id}">Archive</button>
#end
```

Now we have two templates. We can now render the `archive-ui.html` template separately, but this split reduces the visibility of the archiving feature: it is less obvious what is going on when you are looking just at the `detail.html` template.

When pushed to extremes, decomposing templates like this can lead to quite a few small template fragments which, in total, become difficult to manage and to reason about.

### <a href="#template-fragments-to-the-rescue" class="zola-anchor" aria-label="Anchor link for: template-fragments-to-the-rescue">Template Fragments To The Rescue</a>

To address this issue, chill templates has a `#fragment` directive. This directive allows you to specify a block of content within a template and render *just that bit of content*:

##### <a href="#contacts-detail-html-using-a-fragment" class="zola-anchor" aria-label="Anchor link for: contacts-detail-html-using-a-fragment">/contacts/detail.html Using a Fragment</a>

``` html
<html>
    <body>
        <div hx-target="this">
          #fragment archive-ui
            #if contact.archived
            <button hx-patch="/contacts/${contact.id}/unarchive">Unarchive</button>
            #else
            <button hx-delete="/contacts/${contact.id}">Archive</button>
            #end
          #end
        </div>
        <h3>Contact</h3>
        <p>${contact.email}</p>
    </body>
</html>
```

With this fragment defined in our template, we can now render either the entire template:

``` java
  Contact c = getContact();
  ChillTemplates.render("/contacts/detail.html", "contact", c);
```

Or we can render only the `archive-ui` *fragment* of the template

``` java
  Contact c = getContact();
  ChillTemplates.render("/contacts/detail.html#archive-ui", "contact", c);
```

We would use the first option when we want to render the entire detail page for the contact.

We would use the second option when we handled the archive/unarchive actions and wished only to rerender the buttons.

Note that, with fragments, we are able to keep our UI together in a single file and see exactly what is going on with the feature, without bouncing around between different template files. This provides a cleaner and more obvious implementation of the feature.

## <a href="#known-template-fragment-implementations" class="zola-anchor" aria-label="Anchor link for: known-template-fragment-implementations">Known Template Fragment Implementations</a>

Fragments (and the ability to render them directly in controllers) appear to be a relatively rare feature in templating libraries and provide an excellent opportunity for improving the developer experience when working with htmx and other hypermedia-oriented libraries.

Here are some known implementations of the fragment concept:

- Go
  - <a href="https://pkg.go.dev/text/template" rel="noopener" target="_blank">Standard Library (use block actions)</a> <a href="https://gist.github.com/benpate/f92b77ea9b3a8503541eb4b9eb515d8a" rel="noopener" target="_blank">[demo]</a>
  - <a href="https://templ.guide" rel="noopener" target="_blank">templ</a> <a href="https://templ.guide/syntax-and-usage/fragments" rel="noopener" target="_blank">[Fragment documentation]</a> <a href="https://github.com/a-h/templ" rel="noopener" target="_blank">[repo]</a>
- Java
  - <a href="https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#fragment-specification-syntax" rel="noopener" target="_blank">Thymeleaf</a>
  - <a href="https://github.com/bigskysoftware/chill/tree/master/chill-script" rel="noopener" target="_blank">Chill Templates (currently in early alpha)</a>
  - <a href="https://quarkus.io/guides/qute-reference#fragments" rel="noopener" target="_blank">Quarkus Qute</a>
  - <a href="https://jstach.io/doc/jstachio/current/apidocs/#mustache_fragments" rel="noopener" target="_blank">JStachio (mustache)</a>
- JavaScript
  - <a href="https://www.jeasx.dev" rel="noopener" target="_blank">Jeasx</a> - see <a href="https://expo.jeasx.dev/fragments" rel="noopener" target="_blank">example for htmx</a>
- PHP
  - <a href="https://latte.nette.org/en/template-inheritance#toc-blocks" rel="noopener" target="_blank">Latte</a> - Use the 3rd parameter to only render 1 block from the template - `$Latte_Engine->render('path/to/template.latte', [ 'foo' => 'bar' ], 'content');`
  - <a href="https://laravel.com/docs/10.x/blade#rendering-blade-fragments" rel="noopener" target="_blank">Laravel Blade</a> - includes built-in support for template fragments as of v9.x
  - <a href="https://twig.symfony.com/doc/3.x/api.html#rendering-templates" rel="noopener" target="_blank">Twig</a> - `$template->renderBlock('block_name', ['the' => 'variables', 'go' => 'here']);`
- Python
  - <a href="https://pypi.org/project/django-render-block/" rel="noopener" target="_blank">Django Render Block Extension</a> - see <a href="https://github.com/spookylukey/django-htmx-patterns/blob/master/inline_partials.rst" rel="noopener" target="_blank">example code for htmx</a>
  - <a href="https://github.com/sponsfreixes/jinja2-fragments" rel="noopener" target="_blank">jinja2-fragments package</a>
  - <a href="https://github.com/mikeckennedy/jinja_partials" rel="noopener" target="_blank">jinja_partials package</a> (<a href="https://github.com/mikeckennedy/jinja_partials/issues/1" rel="noopener" target="_blank">discussion</a> on motivation)
  - <a href="https://github.com/mikeckennedy/chameleon_partials" rel="noopener" target="_blank">chameleon_partials package</a>
  - <a href="https://github.com/basxsoftwareassociation/htmlgenerator" rel="noopener" target="_blank">htmlgenerator</a>
  - <a href="https://pypi.org/project/django-template-partials/" rel="noopener" target="_blank">django-template-partials</a> (<a href="https://github.com/carltongibson/django-template-partials" rel="noopener" target="_blank">repository</a>)
  - <a href="https://github.com/medihack/django-block-fragments" rel="noopener" target="_blank">django-block-fragments</a>
- .NET
  - <a href="https://github.com/bit-badger/Giraffe.Htmx/tree/main/src/ViewEngine.Htmx" rel="noopener" target="_blank">Giraffe.ViewEngine.Htmx</a>
- Rust
  - <a href="https://docs.rs/minijinja/latest/minijinja/struct.State.html#method.render_block" rel="noopener" target="_blank">MiniJinja</a>
  - <a href="https://askama.readthedocs.io/en/stable/template_syntax.html#block-fragments" rel="noopener" target="_blank">Askama</a>
- Raku
  - <a href="https://github.com/croservices/cro-website/blob/main/docs/reference/cro-webapp-template-syntax.md#fragments" rel="noopener" target="_blank">Cro Templates</a>

Please [let me know](/discord) if you know of others, so I can add them to this list.

<div style="padding-top: 120px;padding-bottom:40px;text-align: center">

\</\>

</div>

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

# you-cant__1b1b07f4

- Source URL: https://htmx.org/essays/you-cant/
- Source file: `fetch/htmx_org_1b1b07f4.html`
- Hash: `1b1b07f4`
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

# You Can't Build Interactive Web Apps Except as Single Page Applications... And Other Myths

Tony Alaribe

September 20, 2024 <style>
img, video {
  max-width: 100%;
  margin: 10px;
}
</style>

### <a href="#an-ode-to-browser-advancements" class="zola-anchor" aria-label="Anchor link for: an-ode-to-browser-advancements"><strong>An Ode to Browser Advancements.</strong></a>

I often encounter discussions on Reddit and YCombinator where newer developers seek tech stack advice. Inevitably, someone claims it’s impossible to build a high-quality application without using a single-page application (SPA) framework like React or AngularJS. This strikes me as odd because, even before the SPA revolution, many popular multi-page web applications offered excellent user experiences.

Two years ago, I set out to build an <a href="https://apitoolkit.io" rel="noopener" target="_blank">observability platform</a> and chose to experiment with a multi-page application (MPA) approach using HTMX. I wondered: Would a server-rendered MPA be inadequate for a data-heavy application, considering that most observability platforms are built on ReactJS?

What I discovered is that you can create outstanding server-rendered applications if you pay attention to certain details.

**Here are some common MPA myths and what I’ve learned about them.**

## <a href="#myth-1-mpa-page-transitions-are-slow-because-javascript-and-css-are-downloaded-on-every-page-navigation" class="zola-anchor" aria-label="Anchor link for: myth-1-mpa-page-transitions-are-slow-because-javascript-and-css-are-downloaded-on-every-page-navigation">Myth 1: MPA Page Transitions are slow because JavaScript and CSS are downloaded on every page navigation</a>

The perception that MPA page transitions are slow is widespread—and not entirely unfounded—since this is the default behavior of browsers. However, browsers have made significant improvements over the past decade to mitigate this issue.

To illustrate, in the video below, a full page reload with the cache disabled takes 2.90 seconds until the DOMContentLoaded event fires. I recorded this at a café with poor Wi-Fi, but let’s use this as a reference point. Keep that number in mind.

It is common to reduce load times in MPAs using libraries such as **PJAX, Turbolinks, and even HTMX Boost**. These libraries hijack the page reload using Javascript and swap out only the HTML body element between transitions. That way, most of the page’s head section assets don’t need to be reloaded or re-downloaded.

But there’s a lesser known way of reducing how much assets are re-downloaded or evaluated during page transitions.

### <a href="#client-side-caching-via-service-workers" class="zola-anchor" aria-label="Anchor link for: client-side-caching-via-service-workers">Client-side Caching via Service workers</a>

Frontend developers who have built Progressive Web Applications (PWA) with SPA frameworks might know about service workers.

For those of us who are not frontend or PWA developers, service workers are a built-in feature of browsers. They let you write Javascript code that sits between your users and the network, intercepting requests and deciding how the browser handles them.

![service-worker-chart.png](/img/you-cant/service-worker-chart.png)

Due to its association with the PWA trend, service workers are only ordinary among SPA developers, and developers need to realize that this technology can also be used for regular Multi-Page Applications.

In the video demonstration, we enable a service worker to cache and refresh the current page. You’ll notice that there’s no flicker when clicking the link to reload the page, resulting in a smoother user experience.

Moreover, instead of transmitting over 2 MB of static assets as before, the browser now only fetches 84 KB of HTML content—the actual page data. This optimization reduces the `DOMContentLoaded` event time from 2.9 seconds to under 500 milliseconds. Impressively, this improvement is achieved **without** using HTMX Boost, PJAX, or Turbolinks.

### <a href="#how-to-implement-service-workers-in-your-multi-page-application" class="zola-anchor" aria-label="Anchor link for: how-to-implement-service-workers-in-your-multi-page-application">How to Implement Service workers in Your Multi-Page Application</a>

You might be wondering how to replicate these performance gains in your own MPA. Here’s a simple guide:

1.  **Create a `sw.js` File**: This is your service worker script that will manage caching and network requests.
2.  **List Files to Cache**: Within the service worker, specify all the assets (HTML, CSS, JavaScript, images) that should be cached.
3.  **Define Caching Strategies**: Indicate how each type of asset should be cached—for example, whether they should be cached permanently or refreshed periodically.

By implementing a service worker, you effectively tell the browser how to handle network requests and caching, leading to faster load times and a more seamless user experience.

### <a href="#use-workbox-to-generate-service-workers" class="zola-anchor" aria-label="Anchor link for: use-workbox-to-generate-service-workers">Use Workbox to generate service workers</a>

While it’s possible to write service workers by hand—and there are excellent resources like <a href="https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers" rel="noopener" target="_blank">this MDN article</a> to help you—I prefer using Google’s <a href="https://developer.chrome.com/docs/workbox" rel="noopener" target="_blank">Workbox</a> library to automate the process.

### <a href="#steps-to-use-workbox" class="zola-anchor" aria-label="Anchor link for: steps-to-use-workbox">Steps to Use Workbox:</a>

1.  **Install Workbox**: Install Workbox via npm or your preferred package manager:

    ``` bash
    npm install workbox-cli --global
    ```

2.  Generate a Workbox Configuration file: Run the following command to create a configuration file:

    ``` bash
    workbox wizard
    ```

3.  **Configure Asset Handling**: In the generated `workbox-config.js` file, define how different assets should be cached. Use the `urlPattern` property—a regular expression—to match specific HTTP requests. For each matching request, specify a caching strategy, such as `CacheFirst` or `NetworkFirst`.

    ![workbox-cfg.png](/img/you-cant/workbox-cfg.png)

4.  **Build the Service Worker**: Run the Workbox build command to generate the `sw.js` file based on your configuration:

    ``` bash
    workbox generateSW workbox-config.js
    ```

5.  **Register the Service Worker in Your Application**: Add the following script to your HTML pages to register the service worker:

    ``` html
    <script>
      if ('serviceWorker' in navigator) {
        window.addEventListener('load', function() {
          navigator.serviceWorker.register('/sw.js').then(function(registration) {
            console.log('ServiceWorker registration successful with scope: ', registration.scope);
          }, function(err) {
            console.log('ServiceWorker registration failed: ', err);
          });
        });
      }
    </script>
    ```

By following these steps, you instruct the browser to serve cached assets whenever possible, drastically reducing load times and improving the overall performance of your multi-page application.

![Image showing the registered service worker from the Chrome browser console.](/img/you-cant/service-worker.png)

Image showing the registered service worker from the Chrome browser console.

### <a href="#speculation-rules-api-prerender-pages-for-instant-page-navigation" class="zola-anchor" aria-label="Anchor link for: speculation-rules-api-prerender-pages-for-instant-page-navigation"></a><a href="https://developer.mozilla.org/en-US/docs/Web/API/Speculation_Rules_API" rel="noopener" target="_blank"><code>Speculation Rules API</code></a>: Prerender pages for instant page navigation.

If you have used **htmx-preload** or **instantpage.js,** you’re familiar with prerendering and the problem the <a href="https://developer.mozilla.org/en-US/docs/Web/API/Speculation_Rules_API" rel="noopener" target="_blank">“Speculation Rules API”</a> aims to solve. The Speculation Rules API is designed to improve performance for future navigations. It has an expressive syntax for specifying which links should be prefetched or prerendered on the current page.

![Speculation rules configuration example](/img/you-cant/speculation-rules.png)

Speculation rules configuration example

The script above is an example of how speculation rules are configured. It is a Javascript object, and without going into detail, you can see that it uses keywords such as “where,” “and,” “not,” etc. to describe what elements should either be prefetched or prerendered.

<a href="https://developer.chrome.com/docs/web-platform/prerender-pages" rel="noopener" target="_blank">Example impact of prerendering (Chrome Team)</a>

## <a href="#myth-2-mpas-can-t-operate-offline-and-save-updates-to-retry-when-there-s-network" class="zola-anchor" aria-label="Anchor link for: myth-2-mpas-can-t-operate-offline-and-save-updates-to-retry-when-there-s-network">Myth 2: MPAs can’t operate offline and save updates to retry when there’s network</a>

From the last sections, you know that service workers can cache everything and make our apps operate entirely offline. But what if we want to save offline POST requests and retry them when there is internet?

![workbox-offline-cfg.png](/img/you-cant/workbox-offline-cfg.png)

The configuration javascript file above shows how to configure Workbox to support two common offline scenarios. Here, you see background Sync, where we ask the service worker to cache any failed requests due to the internet and retry it for up to 24 hours.

Below, we define an offline catch Handler, triggered when a request is made offline. We can return a template partial with HTML or a JSON response or dynamically build a response based on the request input. The sky is the limit here.

## <a href="#myth-3-mpas-always-flash-white-during-page-transitions" class="zola-anchor" aria-label="Anchor link for: myth-3-mpas-always-flash-white-during-page-transitions">Myth 3: MPAs always flash white during page Transitions</a>

In the service worker videos, we already saw that this will not happen if we configure caching and prerendering. However, this myth was not generally true until 2019. Since 2019, most browsers withhold painting the next screen until all the required assets for the next page are available or a timeout is reached, resulting in no flash of white while transitioning between both pages. This only works when navigating within the same origin/domain.

<a href="https://developer.chrome.com/blog/paint-holding" rel="noopener" target="_blank">Paint holding documentation on chrome.com</a>.

## <a href="#myth-4-fancy-cross-document-page-transitions-are-not-possible-with-mpas" class="zola-anchor" aria-label="Anchor link for: myth-4-fancy-cross-document-page-transitions-are-not-possible-with-mpas">Myth 4: Fancy Cross-document page transitions are not possible with MPAs.</a>

The advent of single-page application frameworks made custom transitions between pages more popular. The allure of different navigation styles comes from completely taking control of page navigation from the browsers. In practice, such transitions have mostly been popular within the demos at web dev conference talks.

<a href="https://developer.chrome.com/docs/web-platform/view-transitions" rel="noopener" target="_blank">Cross Document Transitions documentation on chrome.com</a>.

This remains a common argument for single-page applications, especially on Reddit and Hacker News comment sections. However, browsers have been working towards solving this problem natively for the last couple of years. Chrome 126 rolled out cross-document view transitions. This means we can build our MPAs to include those fancy animations and transitions between pages using CSS only or CSS and Javascript.

My favorite bit is that we might be able to create lovely cross-document transitions with CSS only:

![cross-doc-transitions-css.png](/img/you-cant/cross-doc-transitions-css.png)

You can quickly learn more on the <a href="https://developer.chrome.com/docs/web-platform/view-transitions" rel="noopener" target="_blank">Google Chrome announcement page</a>

This link hosts a <a href="https://view-transitions.netlify.app/stack-navigator/mpa-prerender/" rel="noopener" target="_blank">multi-page application demo</a>, where you can play around with a rudimentary server-rendered application using the cross-document view transitions API to simulate a stack-based animation.

## <a href="#myth-5-with-htmx-or-mpas-every-user-action-must-happen-on-the-server" class="zola-anchor" aria-label="Anchor link for: myth-5-with-htmx-or-mpas-every-user-action-must-happen-on-the-server">Myth 5: With htmx or MPAs, every user action must happen on the server.</a>

I’ve heard this a lot when HTMX is discussed. So, there might be some confusion caused by the HTMX positioning. But you don’t have to do everything server-side. Many HTMX and regular MPA users continue to use Javascript, Alpine, or Hyperscript where appropriate.

In situations where robust interactivity is helpful, you can lean into the component islands architecture using WebComponents or any javascript framework (React, Angular, etc.) of your choice. That way, instead of your entire application being an SPA, you can leverage those frameworks specifically for the bits of your application that need that interactivity.

The example above shows a very interactive search component in the <a href="https://apitoolkit.io" rel="noopener" target="_blank">APItoolkit</a>. It’s a web component implemented with lit-element, a zero-compile-step library for writing web components. So, the entire web component event fits in a Javascript file.

## <a href="#myth-6-operating-directly-on-the-dom-is-slow-therefore-it-would-be-best-to-use-react-virtual-dom" class="zola-anchor" aria-label="Anchor link for: myth-6-operating-directly-on-the-dom-is-slow-therefore-it-would-be-best-to-use-react-virtual-dom">Myth 6: Operating directly on the DOM is slow. Therefore, it would be best to use React/Virtual DOM.</a>

The speed of direct DOM operations was a major motivation for building ReactJS on and popularizing the virtual DOM technology. While virtual DOM operations can be faster than direct DOM operations, this is only true for applications that perform many complex operations and refresh in milliseconds, where that performance might be noticeable. But most of us are not building such software.

The Svelte team wrote an excellent article titled <a href="https://svelte.dev/blog/virtual-dom-is-pure-overhead" rel="noopener" target="_blank">“Virtual DOM is pure Overhead.”</a> I recommend reading it, as it better explains why Virtual DOM doesn’t matter for most applications.

## <a href="#myth-7-you-still-need-to-write-javascript-for-every-minor-interactivity" class="zola-anchor" aria-label="Anchor link for: myth-7-you-still-need-to-write-javascript-for-every-minor-interactivity">Myth 7: You still need to write JavaScript for every minor interactivity.</a>

With the advancements in browser tech, you can avoid writing a lot of client-side Javascript in the first place. For example, a standard action on the web is to show and hide things based on a button click or toggle. These days, you can show and hide elements with only CSS and HTML, for example, by using an HTML input checkbox to track state. We can style an HTML label as a button and give it a `for="checkboxID`“ attribute, so clicking the label toggles the checkbox.

``` jsx
<input id="published" class="hidden peer" type="checkbox"/>
<label for="published" class="btn">toggle content</label>

<div class="hidden peer-checked:block">
    Content to be toggled when label/btn is clicked
</div>
```

We can combine such a checkbox with HTMX intersect to fetch content from an endpoint when the button is clicked.

``` html
<input id="published" class="peer" type="checkbox" name="status"/>
<div
        class="hidden peer-checked:block"
        hx-trigger="intersect once"
        hx-get="/log-item"
>Shell/Loading text etc
</div>
```

All the classes above are vanilla <a href="https://tailwindcss.com/" rel="noopener" target="_blank">Tailwind CSS</a> classes, but you can also write the CSS by hand. Below is a video of that code being used to hide or reveal log items in the log explorer.

## <a href="#final-myth-without-a-proper-frontend-framework-your-client-side-javascript-will-be-spaghetti-and-unmaintainable" class="zola-anchor" aria-label="Anchor link for: final-myth-without-a-proper-frontend-framework-your-client-side-javascript-will-be-spaghetti-and-unmaintainable">Final Myth: Without a <em>“Proper”</em> frontend framework, your Client-side Javascript will be</a> <a href="https://www.reddit.com/r/webdev/comments/bkk0gl/avoiding_the_vanillajs_spaghetticode/" rel="noopener" target="_blank">Spaghetti and Unmaintainable</a>.

This may or may not be true.

### <a href="#who-cares-i-love-spaghetti" class="zola-anchor" aria-label="Anchor link for: who-cares-i-love-spaghetti">Who cares? I love Spaghetti.</a>

I like to argue that some of the most productive days of the web were the PHP and JQuery spaghetti days. A lot of software was built at that time, including many of the popular internet brands we know today. Most of them were built as so-called spaghetti codes, which helped them ship their products early and survive long enough to refactor and not be spaghetti.

## <a href="#conclusion" class="zola-anchor" aria-label="Anchor link for: conclusion">Conclusion</a>

The entire point of this talk is to show you that a lot is possible with browsers in 2024. While we were not looking, browsers have closed the gap and borrowed the best ideas from the single-page application revolution. For example, WebComponents exist thanks to the lessons we learned from single-page applications.

So now, we can build very interactive, even offline web applications using mostly browser tools—HTML, CSS, maybe some Javascript—and still not sacrifice much in terms of user experience.

### The browser has come a long way. Give it a chance!

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

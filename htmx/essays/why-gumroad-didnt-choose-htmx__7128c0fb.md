# why-gumroad-didnt-choose-htmx__7128c0fb

- Source URL: https://htmx.org/essays/why-gumroad-didnt-choose-htmx/
- Source file: `fetch/htmx_org_7128c0fb.html`
- Hash: `7128c0fb`
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

# Why Gumroad Didn't Choose htmx

Sahil Lavingia

September 30, 2024

At Gumroad, we recently embarked on a new project called <a href="https://helper.ai" rel="noopener" target="_blank">Helper</a>. As the CEO, I was initially quite optimistic about using <a href="https://htmx.org" rel="noopener" target="_blank">htmx</a> for this project, even though some team members were less enthusiastic.

My optimism stemmed from previous experiences with React, which often felt like overkill for our needs. I thought htmx could be a good solution to keep our front-end super light.

<figure>
<a href="/img/gumroad-red.jpeg" target="_blank"><img src="/img/gumroad-red.jpeg" style="width: 100%" alt="GitHub screenshot shows deleted files" /></a>
<figcaption>Source with htmx - Click Image To View</figcaption>
</figure>

In fact, I shared this sentiment with our team in Slack:

> “https://htmx.org/ may be a way of adding simple interactions to start”

And initially, it seemed promising! As one of our engineers at Gumroad eloquently put it:

> “HTMX is (officially) a meme to make fun of how overly complicated the JS landscape has gotten - much like tailwind is just a different syntax for inline CSS, HTMX is a different syntax for inline JS.”

However, unlike Tailwind, which has found its place in our toolkit, htmx didn’t scale for our purposes and didn’t lead to the best user experience for our customers–at least for our use case.

Here’s why:

1.  **Intuition and Developer Experience**: While it would have been possible to do the right thing in htmx, we found it much more intuitive and fun to get everything working with Next.js. The development process felt natural with Next.js, whereas with htmx, it often felt unnatural and forced. For example, when building complex forms with dynamic validation and conditional fields, we found ourselves writing convoluted server-side logic to handle what would be straightforward client-side operations in React.

2.  **UX Limitations**: htmx ended up pushing our app towards a Rails/CRUD approach, which led to a really poor (or at least, boring and generic) user experience by default. We found ourselves constantly fighting against this tendency, which was counterproductive. For instance, implementing a drag-and-drop interface for our workflow builder proved to be a significant challenge with htmx, requiring workarounds that felt clunky compared to the smooth experience we could achieve with React libraries.

3.  **AI and Tooling Support**: It’s worth noting that AI tools are intimately familiar with Next.js and not so much with htmx, due to the lack of open-source training data. This is similar to the issue Rails faces. While not a dealbreaker, it did impact our development speed and the ease of finding solutions to problems. When we encountered issues, the wealth of resources available for React/Next.js made troubleshooting much faster.

4.  **Scalability Concerns**: As our project grew in complexity, we found htmx struggling to keep up with our needs. The simplicity that initially attracted us began to feel limiting as we tried to implement more sophisticated interactions and state management. For example, as we added features like real-time collaboration and complex data visualization, managing state across multiple components became increasingly difficult with htmx’s server-centric approach.

5.  **Community and Ecosystem**: The React/Next.js ecosystem is vast and mature, offering solutions to almost any problem we encountered. With htmx, we often found ourselves reinventing the wheel or compromising on functionality. This became particularly evident when we needed to integrate third-party services and libraries, which often had React bindings but no htmx equivalents.

<figure>
<a href="/img/gumroad-green.jpeg" target="_blank"><img src="/img/gumroad-green.jpeg" style="width: 100%" alt="GitHub: 1 added file" /></a>
<figcaption>Source with Next.js - Click Image To View</figcaption>
</figure>

Ultimately, we ended up moving to React/Next.js, which has been a really great fit for building the complex UX we’ve been looking for. We’re happy with this decision–for now. It’s allowed us to move faster, create more engaging user experiences, and leverage a wealth of existing tools and libraries.

<figure>
<a href="/img/gumroad-helper-before-after.png" target="_blank"><img src="/img/gumroad-helper-before-after.png" style="width: 100%" alt="The old Gumroad Helper interface is quite basic with a single flat form, while the new one has multiple levels of navigation and editable lists." /></a>
<figcaption>Gumroad Helper Before &amp; After - Click Image To View</figcaption>
</figure>

This experience has reinforced a valuable lesson: while it’s important to consider lightweight alternatives, it’s equally crucial to choose technologies that can grow with your project and support your long-term vision. For Helper, React and Next.js have proven to be that choice.

Since we’ve moved there, we’ve been able to seriously upgrade our app’s user experience for our core customers.

1.  **Drag-and-Drop Functionality**: One of the key features of our workflow builder is the ability to reorder steps through drag-and-drop. While it’s possible to implement drag-and-drop with htmx, we found that the available solutions felt clunky and required significant custom JavaScript. In contrast, React ecosystem offers libraries like react-beautiful-dnd that provide smooth, accessible drag-and-drop with minimal setup.

2.  **Complex State Management**: Each workflow step has its own set of configurations and conditional logic. As users edit these, we need to update the UI in real-time to reflect changes and their implications on other steps. With htmx, this would require numerous server roundtrips or complex client-side state management that goes against htmx’s server-centric philosophy. React’s state management solutions (like useState or more advanced options like Redux) made this much more straightforward.

3.  **Dynamic Form Generation**: The configuration for each step type is different and can change based on user input. Generating these dynamic forms and handling their state was more intuitive with React’s component model. With htmx, we found ourselves writing more complex server-side logic to generate and validate these forms.

4.  **Real-time Collaboration**: While not visible in this screenshot, we implemented features allowing multiple users to edit a workflow simultaneously. Implementing this with WebSockets and React was relatively straightforward, whereas with htmx, it would have required more complex server-side logic and custom JavaScript to handle real-time updates.

5.  **Performance Optimization**: As workflows grew larger and more complex, we needed fine-grained control over rendering optimizations. React’s virtual DOM and hooks like useMemo and useCallback allowed us to optimize performance in ways that weren’t as readily available or intuitive with htmx.

It’s important to note that while these challenges aren’t insurmountable with htmx, we found that addressing them often led us away from htmx’s strengths and towards solutions that felt more natural in a JavaScript-heavy environment. This realization was a key factor in our decision to switch to React and Next.js.

We acknowledge that htmx may be a great fit for many projects, especially those with simpler interaction models or those built on top of existing server-rendered applications. Our experience doesn’t invalidate the benefits others have found in htmx. The key is understanding your project’s specific needs and choosing the tool that best aligns with those requirements.

In our case, the complex, stateful nature of Helper’s interface made React and Next.js a better fit. However, we continue to appreciate htmx’s approach and may consider it for future projects where its strengths align better with our needs.

That said, we’re always open to reevaluating our tech stack as our needs evolve and new technologies emerge. Who knows what the future might bring?

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

---
layout: page
title: Accessibility
group: getting-started
---

Bootstrap follows common web standards and—with minimal extra effort—can be used to create sites that are accessible to those using <abbr title="Assistive Technology" class="initialism">AT</abbr>.

## Skip navigation

If your navigation contains many links and comes before the main content in the DOM, add a `Skip to main content` link before the navigation (for a simple explanation, see this [A11Y Project article on skip navigation links](http://a11yproject.com/posts/skip-nav-links/)). Using the `.sr-only` class will visually hide the skip link, and the <code>.sr-only-focusable</code> class will ensure that the link becomes visible once focused (for sighted keyboard users).

{% callout danger %}
Due to long-standing shortcomings/bugs in Chrome (see [issue 262171 in the Chromium bug tracker](https://code.google.com/p/chromium/issues/detail?id=262171 "Chromium bug tracker - Issue 262171: Focus should cycle from named anchor")) and Internet Explorer (see this article on [in-page links and focus order](http://accessibleculture.org/articles/2010/05/in-page-links/)), you will need to make sure that the target of your skip link is at least programmatically focusable by adding `tabindex="-1"`.

In addition, you may want to explicitly suppress a visible focus indication on the target (particularly as Chrome currently also sets focus on elements with `tabindex="-1"` when they are clicked with the mouse) with `#content:focus { outline: none; }`.

Note that this bug will also affect any other in-page links your site may be using, rendering them useless for keyboard users. You may consider adding a similar stop-gap fix to all other named anchors / fragment identifiers that act as link targets.
{% endcallout %}

{% highlight html %}
<body>
  <a href="#content" class="sr-only sr-only-focusable">Skip to main content</a>
  ...
  <div class="container" id="content" tabindex="-1">
    <!-- The main page content -->
  </div>
</body>
{% endhighlight %}

## Nested headings

When nesting headings (`<h1>` - `<h6>`), your primary document header should be an `<h1>`. Subsequent headings should make logical use of `<h2>` - `<h6>` such that screen readers can construct a table of contents for your pages.

Learn more at [HTML CodeSniffer](http://squizlabs.github.io/HTML_CodeSniffer/Standards/Section508/) and [Penn State's Accessability](http://accessibility.psu.edu/headings).

## Additional resources

- ["HTML Codesniffer" bookmarklet for identifying accessibility issues](https://github.com/squizlabs/HTML_CodeSniffer)
- [The A11Y Project](http://a11yproject.com/)
- [MDN accessibility documentation](https://developer.mozilla.org/en-US/docs/Accessibility)
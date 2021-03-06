---
layout: shared/narrow
title: "Accessibility Codelab"
description: "Accessibility Codelab"
published_on: 2016-03-01
updated_on: 2016-03-01
order: 10
translation_priority: 0
authors:
  - megginkearney
  - dgash
key-takeaways:
  tldr: 
    - "Learn what accessibility means and how it applies to web development."
    - "Learn how to make web sites accessible and usable for everyone."
    - "Learn how to include basic accessibility with minimal development impace."
    - "Learn what HTML features are available and how to use them to improve accessibility."
    - "Learn about advanced accessibility techniques for creating polished accessibility experiences."
notes:
  efficiency:
    - "Understanding the accessibility issue, its scope, and its impact can make you a better web developer."
  problem-solving:
    - "Catching, identifying, and removing potential accessibility roadblocks before they happen can improve your development process and reduce maintenance requirements."
---

# DOM Order Matters

Working with native elements is a great way to learn about focus behavior because they are automatically inserted into the tab order based on their position in the DOM.

For example, you might have three button elements, one after the other in the DOM. Pressing `Tab` focuses each button in order. However, it's important to note that using CSS it's possible to have things exist in one order in the DOM but appear in a different order on screen.

If, for example, you use a CSS property like *float* to move one button to the right, the buttons appear in a different order on screen. But, because their order in the DOM remains the same, so does their tab order. When the user tabs through the page, the buttons gain focus in a non-intuitive order.

Be careful when changing the visual position of elements on screen using CSS. This can cause the tab order to jump around, seemingly at random, confusing users who rely on the keyboard. For this reason, the Web AIM checklist states in section 1.3.2 that the reading and navigation order, as determined by code order, should be logical and intuitive.

As a rule, try tabbing through your pages every so often just to make sure you haven't accidentally messed up the tab order. It's a good habit to adopt, and one that doesn't require much effort.

Here's a [page with a broken tab order](http://robdodson.github.io/udacity-a11y/lesson2-focus/02-dom-order/). 

![Navigation links](imgs/navlinks.png)

Check it out and try to navigate through the page using only `Tab`; you'll quickly find that the tab order doesn't match the visual order. If you examine the page source, you'll see that the tab order originally dictated by the DOM is rearranged by CSS, making the page confusing and difficult to use and resulting in a serious accessibility issue.

It would make more sense if the page could be navigated in this order: navigation, search, content, footer. How might you accomplish that? Grab the code and use a text editor to change the order of the elements in the DOM so that the tab order makes sense. Let's have a look.

First, you can see that the Search link is actually higher in the DOM order than the other navigation links, and that it's using a "pull-right" CSS class to float to the right. That's fine visually, but the style placement overrides the link's physical DOM order. The easiest fix is to move the Search button below the other elements in the HTML; that won't change the visual presentation, but it will change the element's DOM position so that it matches the default tab order.

No doubt you also noticed that the newsletter footer's tab order is ahead of the other elements on the page because &mdash; although it is near the top of the DOM in the HTML &mdash; the "newsletter" CSS class absolutely positions it at the bottom of the page. Just like the search link, let's move the newsletter `div`, placing it at the bottom of the document, just after the `main` element. Again, this has no visual effect, but it changes the element's DOM position so that its tab order now falls in a logical place.

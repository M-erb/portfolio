---
title: Animated CSS Accordions
author: Michael Erb
description: Animated CSS Accordions using HTML details element
date: 02-26-2026
draft: false
img:
  src: /src/imgs/postImgs/river-fx-IV4db_thdMA-unsplash.jpg
  byName: River Fx
  byUrl: https://unsplash.com/@riverfx?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
  origSrc: https://unsplash.com/photos/man-playing-blue-accordion-during-daytime-IV4db_thdMA?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText
excerpt: excerpt
category: css
tags: [css, html, details, summary, animation]
loadCodePenJs: true
---

## The past...

We have been having to use either JavaScript to create accordions or CSS hacks for far too long. The JavaScript way just feels wrong in some cases. We need to add JS to an otherwise plain website just so we can open and close and element? There have been some CSS hacks using something like a `<input type="checkbox" />` or `<input type="radio" />` to track the open and close states. Both of these these options of creating accordions do not have the same reliable structure for acessability and SEO understanding that an element specifically designed for it would have.

## Introdocing `<details>` and `<summary>`

According to baseline the `<details>` HTML element has been widely available since January 2020! [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/details#browser_compatibility). What!? I was surprised by that and needed to jump on how to use this thing.

When a screen reader, or something like google bot, finds this element it will know you have an open close / hide show content there. Then will communicate that to the viewing accordingly. So instead of a screen reader trying its best to interpret your hopefully correct `aria` attributes, it will just know that is what this is!

Lets have a look at it.

```html
<!-- open attribute will show the hidden content and when it is removed (or summary is clicked when opened) the content is hidden -->
<details open>
  <summary>
    This is the open and close element AND what is shown before opening
  </summary>
  <!-- whatever else is in the details will be considered the hidden content to be hidden and shown -->

  <p>
    This would be some hidden content to be shown when the summary above is
    clicked/ opened
  </p>
  <p>Some more content!</p>
</details>
```

The details are not pretty though...

<div style="margin-bottom: var(--size-6)">
  <p class="codepen" data-height="300" data-pen-title="Basic Details Accordion" data-preview="true" data-slug-hash="PwGwdRR" data-editable="true" data-user="merb" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
    <span>See the Pen <a href="https://codepen.io/merb/pen/PwGwdRR">
    Basic Details Accordion</a> by Michael (<a href="https://codepen.io/merb">@merb</a>)
    on <a href="https://codepen.io">CodePen</a>.</span>
  </p>
</div>

The default does not look the best but it works, lets see about styling them and adding some animation.

Here is what we want to make. Just a simple slide down animation.

<div style="margin-bottom: var(--size-6)">
  <p class="codepen" data-height="300" data-pen-title="CSS animation Accordion with JS fallback" data-preview="true" data-slug-hash="xbEbmNR" data-editable="true" data-user="merb" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
    <span>See the Pen <a href="https://codepen.io/merb/pen/xbEbmNR">
    CSS animation Accordion with JS fallback</a> by Michael (<a href="https://codepen.io/merb">@merb</a>)
    on <a href="https://codepen.io">CodePen</a>.</span>
  </p>
</div>

## How to Making it pretty

Lets start with removing that ugly arrow or carrot thingy. This can get in the way of making the accordion our own. Though if you want it, then there is no need for this.

```css
details {
  summary {
    /* Remove default marker Chromium / Firefox */
    list-style: none;
  }

  /* Remove default marker Webkit */
  & summary::-webkit-details-marker {
    display: none;
  }
}
```

<div style="margin-bottom: var(--size-6)">
  <p class="codepen" data-height="300" data-pen-title="Detials remove ugly arrow from details element" data-preview="true" data-slug-hash="YPGPRJX" data-editable="true" data-user="merb" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
    <span>See the Pen <a href="https://codepen.io/merb/pen/YPGPRJX">
    Detials remove ugly arrow from details element</a> by Michael (<a href="https://codepen.io/merb">@merb</a>)
    on <a href="https://codepen.io">CodePen</a>.</span>
  </p>
</div>

Just going to add a background color and an icon here to get the shape together. I have also put all of the content of the accordion into a `div` to make fallbacks easier. Notice that there is no animation yet, BUT they still function due to the `details` element being used!

<div style="margin-bottom: var(--size-6)">
  <p class="codepen" data-height="300" data-pen-title="Styling accordion using details+summary tags - no animation yet" data-preview="true" data-slug-hash="QwKbdyK" data-editable="true" data-user="merb" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
    <span>See the Pen <a href="https://codepen.io/merb/pen/QwKbdyK">
    Styling accordion using details+summary tags - no animation yet</a> by Michael (<a href="https://codepen.io/merb">@merb</a>)
    on <a href="https://codepen.io">CodePen</a>.</span>
  </p>
</div>

## Animation, make it come alive!

Part of the issue with animating something like an accordion is that CSS cannot animate from a specific value, like `0px`, to a named value, like `auto`. To compensate for that, us developers would need to do things like getting the height of something in JavaScript. Then set it's height to `0px`, but then transition it to it's original height again. Was a headche. If you notice in my example above I did add a JS fallback for that exacte situation when the browser does not have the nessesary CSS support.

There are two things that we need a browser to support for this to work purely in CSS.

1. `interpolate-size: allow-keywords`, <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/interpolate-size" target="_blank">MDN interpolate-size</a>
   - This tells the browser it is okay to do the math between a named value, `auto`, and a specific value, `200px` or `0px`
2. `transition-behavoir: allow-discret`, <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/transition-behavior" target="_blank">MDN transition-behavior</a>
   - This tells the browser to wait for a transition to finish before applying something like `content-visibility: hidden` or `display: none`
   - This allows us to apply a transition and then hide something for example

We will also make use of the `@supports` CSS function to detect if the browser has the proper CSS feature to apply the animation or not.

It is recommended to apply the `interpolate-size: allow-keywords` at the root level as it should not break anything and then you would not have this being applied to many different components.

```css
:root {
  interpolate-size: allow-keywords;
}

/* OR if you want to only apply it if the browser supports it
  so as to prevent CSS errors happening */
:root {
  @supports (interpolate-size: allow-keywords) {
    interpolate-size: allow-keywords;
  }
}
```

Then we can apply our transitions to the `::details-content` psudo-element.

```css
.accordion_item_details {
  &::details-content {
    display: block;
    overflow: hidden;
    height: 0;
    content-visibility: hidden;
    transition: height 0.3s, content-visibility 0.3s;

    /* Needed for transitioning with content-visibility: hidden */
    transition-behavior: allow-discrete;

    &[open]::details-content {
      display: block;
      content-visibility: visible;
      height: auto;
    }
  }
}
```

Here is the result! If you are in a browser that does not support `interpolate-size: allow-keywords` then you will not see an animation as there is not JS fallback in this example.

<div style="margin-bottom: var(--size-6)">
  <p class="codepen" data-height="300" data-pen-title="Accordion with details element and animation CSS only - no JS fallback" data-preview="true" data-slug-hash="yyaNgEp" data-editable="true" data-user="merb" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
    <span>See the Pen <a href="https://codepen.io/merb/pen/yyaNgEp">
    Accordion with details element and animation CSS only - no JS fallback</a> by Michael (<a href="https://codepen.io/merb">@merb</a>)
    on <a href="https://codepen.io">CodePen</a>.</span>
  </p>
</div>

## Conclution

You have now seen a basic example of how to create a CSS only accordion. For the browsers that this does not work in yet it will just open and close without an animation which is still perfectly fine! But if you really need that animation on other browsers then a JS fallback can be added easily. The main functionality, of it opening and closing, is all controlled by a native HTML element. So, animation or not, you still get acessebility for free!

You can checkout this pen to see how I did a JS fallback. Just ignore the `reset` and `active` parts as I added a way for it to be toggled on and off too. If you want an example without the toggle then just send me a message about this article and I can set one up.

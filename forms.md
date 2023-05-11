---
src: intro.md
---
---
layout: statement
---

# Building Superpowered Forms With JavaScript 

---

# Let's define 'powers'

<div class="grid grid-cols-2 text-left">
<v-clicks>
<div>

## Baseline
- Semantic (conveys meaning)
- Accessible (works with AT)
- Fast (nothing **unnecessary**)
- Secure (?)
- Browser built-in features
</div>
<div>

## Superpowers
- Improve existing features (a11y)
- Add nonexistant features (UX)
- Don't break the baseline
</div>
</v-clicks>
</div>

---

# A very basic example

<div class="grid grid-cols-2 gap-4">

```html
<div>Do the thing</div>
```

Make this div clickable

<v-clicks>

- `onclick="handleClick()"`
- `onkeydown="handleKeydown()"`
- `tabindex="0"`
- `role="button"`
</v-clicks>
<v-click>

- Lot's of work
- Missing features
<br>(eg. open in new tab)
- Relies on JavaScript
</v-click>

</div>

---

<img src="/img/forms/ally-mimic.jpg" class="block m-auto -mt-8" width="480" alt="button html element looking at a div element and saying to anchor element, 'Look what they need to mimic a fraction of our power'">

---

# Good rule of thumb

<v-clicks>

1. HTML is awesome. Use it as much as possible.
2. If it can't be done with HTML, use CSS
3. If it can't be done with CSS, use JavaScript

</v-clicks>

---
layout: statement
---

# What's wrong with JavaScript?

---

# Many Reasons JavaScript Fails
See: https://www.kryogenix.org/code/browser/everyonehasjs.html

<div class="grid grid-cols-2">
<div>

* Has the page loaded yet?
* Did the connection drop?
* Did the connection time out?
* Is there a corporate firewall?
* Did the ISP interfere?
* Is the client a microbrowser?
* Is JavaScript turned off?
* Is Data Saver mode on?
</div>
<div>

* Did extensions alter the DOM?
* Did Adblockers interfere?
* Is the CDN up?
* Does their browser support the JavaScript you’ve written?
* Did a library change?
* Did a library author bug?
* Did you add a bug?
</div>
</div>

---
layout: statement
---

# Progressive Enhancement
<h1>&nbsp;</h1>

---
layout: statement
---

# <strike>Progressive Enhancement</strike>
# ladders, stairs, & escalators

---
layout: image
image: /img/forms/mitch.png
---

<!-- # Escalators > Elevators -->

<!-- <iframe width="875" height="475" src="https://www.youtube.com/embed/yHopAo_Ohy0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> -->

<div class="w-1/2 pt-20 text-4xl">

> An escalator can never break...
<!--  -->
<v-clicks>

> it can only become stairs.
>
> -- <cite>Mitch Hedberg</cite>
</v-clicks>
</div>

<!-- An escalator can never break: it can only become stairs. You should never see an Escalator Temporarily Out Of Order sign, just Escalator Temporarily Stairs. Sorry for the convenience. -->

---
layout: statement
---

# Let's start with HTML
# (ladders)

---

<div class="grid grid-cols-2">

# Strengths
# Weaknesses
</div>

<div class="grid grid-cols-2">
<v-clicks>
<div>

- Semantic & Accessible
- Performance
- Makes HTTP requests
- 24 types of controls
- Built-in validation
- Keyboard support
- Inherent submit
- Extremely reliable & forgiving

</div>
<div>

- Looks like butt
- UI/UX is meh
- Validation sux

</div>
</v-clicks>
</div>

---

# Superpowers

<v-clicks>

- Better keyboard UX for mobile users (`inputmode`)
- Auto-fill form data entry (`autocomplete`)
- Auto-focus form field (`autofocus` **only if it makes sense!!!**)
</v-clicks>

---

# Utility Belt

<div class="grid grid-cols-2">

- input `type`
- Validation attributes
  - `required`
  - `min`
  - `max`
  - `minlength`
  - `maxlength`
  - `pattern`
  - `step`
<!--  -->
- `inputmode`
- `autocomplete`
- `autofocus` (**!!!**)
</div>

---

# Blog posts

## How to Build HTML Forms Right: Semantics

(https://austingil.com/how-to-build-html-forms-right-semantics/)

## How to Build HTML Forms Right: Accessibility

(https://austingil.com/how-to-build-html-forms-right-accessibility/)

---
layout: statement
---

# Sprinkle on some CSS
# (stairs)

---

<div class="grid grid-cols-2">

# Strengths
# Weaknesses
</div>

<div class="grid grid-cols-2 text-left">
<v-clicks>
<div>

- Beautiful
- Fast
- Low-resource
- Turing complete (?)
- Reliable

</div>
<div>

- Not dynamic
- Dependent on HTML
- Might require hacks
- Can't touch native validation UI

</div>
</v-clicks>
</div>

---

# Superpowers

<v-clicks>

- Customized (accessible) inputs
- Fancy parent styles when child is focused/checked/etc.
- Input validity hints
- Conditional rendering *
</v-clicks>

---

# Custom Radios & Checkboxes

<iframe height="460" style="width: 100%;" src="https://codepen.io/AustinGil/full/QWyrgPG" loading="lazy">
</iframe>

---

# Switch Control

<iframe height="460" style="width: 100%;" src="https://codepen.io/AustinGil/full/pogKYgM" loading="lazy">
</iframe>

---

# Card-like Controls

<div class="grid">
<div v-click-hide="1" class="col-span-full row-span-full text-center">
<img  src="/img/forms/cards.png" class="block m-auto" width="480">

## Default
</div>
<div v-click-hide="2" v-click="1" class="col-span-full row-span-full text-center">
<img src="/img/forms/cards-focus.png" class="block m-auto" width="480">

## Focused
</div>
<div v-click="2" class="col-span-full row-span-full text-center">
<img src="/img/forms/cards-checked.png" class="block m-auto" width="480">

## Selected
</div>
</div>

---

# Validity Hints

<div class="grid grid-cols-2 gap-4">
<div>

## On focused inputs
<img src="/img/forms/invalid.png">
<img src="/img/forms/valid.png">
</div>
<div>

## On the submit button
<img src="/img/forms/required.png">
<img src="/img/forms/required-checked.png">
</div>
</div>

---

# Conditional rendering

<div class="grid">
<div v-click-hide="1" class="col-span-full row-span-full text-center">
<img  src="/img/forms/radios.png" class="block m-auto" width="400">

## Default
</div>
<div v-click="1" class="col-span-full row-span-full text-center">
<img src="/img/forms/radios-selected.png" class="block m-auto" width="400">

## Selected
</div>
</div>

---

# Utility Belt

- pseudo-classes:
  - `:valid`
  - `:invalid`
  - `:checked`
  - `:focus`
  - `:focus-visible`
- `.visually-hidden` class
- combinator selectors: `>`, `~`, `+`
- `:has()` !!!

---

# Blog posts

## How to Build HTML Forms Right: Styling
(https://austingil.com/css-has-with-html-forms/)
## 5 ways CSS :has() can make your HTML forms even better
(https://austingil.com/build-html-forms-right-styling/)

---
layout: statement
---

# Unleash the JavaScript
# (escalators)

---

<div class="grid grid-cols-2">

# Strengths
# Weaknesses
</div>

<div class="grid grid-cols-2 text-left">
<v-clicks>
<div>

- You can do ANYTHING!!!

</div>
<div>

- More work for developers
- More to download
- More compute
- Easier for errors & bugs
- Accessibility ??
- Not as reliable

</div>
</v-clicks>
</div>

<img v-click-hide="3" v-click="2" src="/img/forms/genie1.gif" class="absolute inset-0 w-full h-full">
<img v-click="4" src="/img/forms/genie2.gif" class="absolute inset-0 w-full h-full">

---
layout: statement
---

# If you want to "improve" existing browser features
## It's a good idea not to break 🤬

---

# Inputs

<div class="grid grid-cols-2 gap-4">
<v-clicks>
<div>

Cool things we can improve:

- Multiselect
- File drop-zone
- Awesome date pickers
- Type-ahead/autosuggest

</div>
<div>

Easy things we can break:

- Actual functionality
- Accessible controls
- Keyboard navigation
- Works with or without JS

</div>
</v-clicks>
</div>

---

# Validation

<div class="grid grid-cols-2 gap-4">
<v-clicks>
<div>

Cool things we can improve:

- Custom error messages
- Better looking UI
- More immediate feedback (`onblur`, `onchange`, `oninput`)
- Accessibility improvements (`aria-invalid`, `aria-disabled`, `aria-describedby`)

</div>
<div>

Easy things we can break:

- Communicate errors to AT
- Scroll to first invalid input on submit
- Trample existing ARIA attributes
- Works with or without JS

</div>
</v-clicks>
</div>

---

# Submissions

<div class="grid grid-cols-2 gap-4">
<v-clicks>
<div>

Cool things we can improve:

- Autosave (submit)
- Keyboard shortcuts (`ctrl+enter`)
- Avoid page load (`fetch`)

</div>
<div>

Important things we mustn't break:

- Prevent spamming submit
- Using correct `Content-Type`
- Respects server redirects
- Handle server errors
- Existing keyboard shortcuts
- Works with or without JS

</div>
</v-clicks>
</div>

---
layout: statement
---
<!-- 🥵🔥 -->
# 🌶️🌶️🌶️

---

<v-clicks>

- Inputs don't need state management.
- Data doesn't need to be sent as JSON.
- You don't need custom fetch requests for every endpoint.
- You don't need fancy validation libraries.
- You don't need fancy HTTP libraries.
</v-clicks>
<!-- - Don't use JS unless it improves UX enough to offset it's cost while maintaining feature-parity. -->
<!-- - Stop breaking existing functionality
- And stop preventing copy/paste -->

---

# Instead

<v-clicks>

Use the powers HTML+CSS already have

Let forms provide declarative submission logic

Let inputs provide declarative  validation logic

Add a little JavaScript to enhance existing features (without breaking)

Use the same JavaScript abstraction across multiple forms

Relax because it's practically bulletproof

</v-clicks>

---
layout: statement
---

# HTML forms have worked for decades...

---
layout: statement
---

# HTML forms will continue to work for decades...

---
layout: statement
---

# Some JS libraries break after a minor upgrade.

---

# Blog Post

## Make Beautifully Resilient Apps With Progressive Enhancement

(https://austingil.com/resilient-applications-progressive-enhancement/)

---
layout: statement
---

# But what about the things HTML+CSS can't do...?

---

# JavaScript-ONLY superpowers

<v-clicks>

- Input masks
- Repeater fields
- Re-ordering (drag and drop)
- Client-side file manipulation
- Detect if input has been touched (soon `:user-invalid`)
- Dynamic validation (eg. password matching)
- Prevent data loss from navigation
- Support for retries
- Offline support and resumability
</v-clicks>

---

# Utility Belt

<div class="grid grid-cols-3">
<div>

## APIs
- `URLSearchParams()`
- `FormData()`
- `fetch()`
- `locaStorage`/<br>`sessionStorage`

</div>
<div>

## Events
- `submit`
- `invalid`
- `beforeunload`
- Event delegation pattern
</div>
<div>

## Properties/Methods
- `validity`
- `validationMessage`
- `checkValidity()`
- `reportValidity()`
</div>
</div>

---
src: outro.md
---
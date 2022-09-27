---
theme: default
font:
  sans: 'Manrope'
  display: 'Rock Salt'
lineNumbers: false
layout: statement
---

# Building Components With Accessiblity In Mind

---
layout: image-right
image: /img/edge-compute/austin-gil-bio.png
---

<h1 class="text-4xl mt-10">Hey Im Austin Gil 👋</h1>
<p class="-top-4">@heyAustinGIl</p>

<h4 class="mb-4">Dev Advocate <a href="https://akamai.com">akamai.com</a></h4>
<h4 class="mb-4">OSS Maintainer of <a href="https://vuetensils.austingil.com">Vuetensils</a></h4>
<h4 class="mb-4">Chiweenie enthusiast</h4>
<h4 class="mb-4">Perfect marshmallow roaster</h4>

<div class="mt-10">Come talk to me about edge compute, web development, JavaScript, Vue.js, a11y, Chiweenies, or whatever :D</div>

---

Prerequisites:
* Git
* Node/NPM
* VS Code
* GitHub account

Introduction
- To get more people on board, you have to make it easy to do the right thing, and hard to do the wrong thing. The problem with a lot of current UI libraries is they follow that principle, but require library specific knowledge. Which is just as hard to learn as ARIA. So you have to master a different skill that isn't even transferable. 

Setup

Questions

Debugging tools/audit

Development tools

Compare different types of website & semantic layout

Create components
- Layouts (skip links)
- Element with text/heading (not knowing document order)
- SVG (built in labels make it easy)
- Image (enforce alt text)
- How do you prevent invalid HTML? (eg. Buttons containing divs)
- Input (fallback ID)
- Card list (:focus-within + expando-link)
- Dialog

Styling
- Styling with semantics/aria: button[aria-expanded="true"] {}
- visually-hidden class
- focus-within
- reduced-motion
- @supports
- color-themes 
- Grid/flex ordering
- Semantic headings vs size

Questions

Keyboard only & Screen reader navigation

Continuous auditing tools

Questions

Closing

Tools:
Chrome devtools
aXe devtools
VS Code axe
axe accessibility linter / webhint
eslint-plugin-jsx-a11y / eslint-plugin-vuejs-accessibility
  React: Reach UI
  Vue: Vuetensils (I made this one)
  Web components: Lion
a11y.css
https://accesslint.com/
cypress component testing with axe

https://austingil.com/making-accessibility-more-accessible/

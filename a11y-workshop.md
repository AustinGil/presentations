<!-- Hello friends!

This is Austin Gil, and I'm very excited to have you all at my workshop tomorrow, "Make Accessibility Easier to get Right & Harder to get Wrong"

I wanted to reach out with a few things you can do now to help things run more smoothly tomorrow.

You'll want to make sure you have Git (https://git-scm.com/) and Node.js (https://nodejs.org/en) installed on your machine, as well as a code editor (https://code.visualstudio.com/) and a GitHub account (https://github.com/)

There is a repository we'll be working from (https://github.com/AustinGil/accessiblitz), so if you want to clone that and install the NPM dependencies from inside the /react folder, it could help speed things up. Here's the command to do all that from a unix terminal:

git clone https://github.com/AustinGil/accessiblitz.git && cd accessiblitz/react && npm install

We will be learning how to setup automated tests with Cypress and/or Playwright. You can choose just one or both, but there are some other terminal commands to set those up.

For Cypress users: npx cypress verify
For Playwright users: npx playwright install --with-deps

 -->

# Make Accessibility <br>Easier to Get Right 
## (& Harder to Get Wrong)

<div class="grid grid-cols-2 text-left">
<div>

Wifi:<br>
MarriotBonvoy_Conference

<br>

Board:<br>
https://bit.ly/a11y-ws

</div>
<div>

Prerequisites:
* Git
* Node/NPM
* VS Code
* GitHub account
* Headphones (please)

</div>
</div>

---
src: intro.md
---
---
layout: image-left
image: /img/a11y-workshop/michael.jpg
---

# Everyone say <br>"Hi, Michael"

<p class="pt-8 text-4xl">Michael Fairchild</p>

Accessibility Coach and Manager at Deque Systems.

Developer. Gamer. Rower. Forever learning and growing.

Built a11ysupport.io and co-chairs the W3C ARIA-AT group.

---
layout: statement
---

# To the board!!!

---

# The facts - [WebAIM Million Report](https://webaim.org/projects/million/)

<v-click>

Feb 2022 - 50,829,406 distinct errors / 50.8 errors per page
[webaim.org/projects/million](https://webaim.org/projects/million/)

</v-click>

<v-click>

* Low contrast text: 86.4%
* Missing alternative text for images: 60.6%
* Missing form input labels: 54.4%
* Empty links: 51.3%
* Missing document language: 28.9%
* Empty buttons: 26.9%

</v-click>
<v-click>

**IMPORTANT:** Based on **automated** WCAG metrics
</v-click>

---
layout: statement
---

# To the board!!!

---

<img src="/img/a11y/ally-mimic.jpg" class="block m-auto -mt-10" width="495">

---

# Screen Readers & Keyboards

Markup determines how assistive technology interact with your page:

<v-clicks>

- Order of elements
- Landmarks
- Semantic tags
- Roles
- ARIA attributes

Accessibility Tree: DevTools > Elements > Accessibility

</v-clicks>

---

# How would you code this?

<div class="grid grid-cols-2">
<v-clicks>
<img src="/img/a11y-workshop/blog.jpg">
<img src="/img/a11y-workshop/dashboard.jpg">
</v-clicks>
</div>

---
layout: statement
---

# To the board!!!

---
layout: statement
---

# Pop Quiz!


<v-clicks>

If a background color is <span style="color:#000;background:#BADA55;">&nbsp;#bada55&nbsp;</span>

And WCAG AA requires color contrast ratio of 4.5:1

What color should the foreground text be...?

🤷 (pfft)

</v-clicks>

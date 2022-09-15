---
theme: default
font:
  sans: 'Manrope'
  display: 'Rock Salt'
lineNumbers: false
layout: image-right
image: /img/vueconf/austin-gil-bio.png
---

<h1 class="text-4xl mt-10">Hey Im Austin Gil 👋</h1>
<p class="-top-4">@heyAustinGIl</p>

<h4 class="mb-4">Dev Advocate <a href="https://akamai.com">akamai.com & linode.com</a></h4>
<h4 class="mb-4">OS Maintainer of <a href="https://vuetensils.austingil.com">Vuetensils</a></h4>
<h4 class="mb-4">Chiweenie fanboi</h4>
<h4 class="mb-4">Perfect marshmallow roaster</h4>
<h4 class="mb-4">Can talk to dogs</h4>

<div class="mt-10">Come talk to me about whatever :D</div>

<!-- Round of applause for the lightning talks

the air conditioning

the folks that clap at anything -->

---
layout: statement
--- 

<div class="flex justify-center mx-auto w-50 h-50 mb-8 rounded-full overflow-hidden">
<img src="/img/vueconf/nugs (6).jpg" class="w-full h-full object-cover"/>
</div>

# Internal UI Libraries

### For maintainable and resilient projects 

---

# Vue.js is awesome

<div class="grid grid-cols-2 gap-4">
<img src="/img/vueconf/vue-trends.png" width="500">
<img src="/img/vueconf/vue-stars.png">
</div>

<!-- Helping developers build UIs for 8 years. One way it does that is componentization -->

---

# Components are awesome

Encapsulate shared logic into a reusable blocks.

- Cohesive design
- Implement best practices
- De-duplicate code
- Abstract complexity
- Maintenance/migrations

<!-- Put logic in one place and distribute it easily -->
---

# For example, LisaFrankify.vue

```html
<template>
  <LisaFrankify>
    Best childhood ever!!!
  </LisaFrankify>
</template>
```

<lisa-frankify class="mb-10">
  Best childhood ever!!!
</lisa-frankify>

<v-click>

```html
<template>
  <LisaFrankify>
    Welcome to puberty
  </LisaFrankify>
</template>
```

<lisa-frankify>
  Welcome to puberty :(
</lisa-frankify>

</v-click>

<!-- 
Use it to add some razzle dazzle.

Or deliver some tough news in a fun, playful way. -->

---
layout: statement
---

# You probably knew that

## But you can do that with external code too

---
layout: statement
---

<div class="flex justify-center mx-auto w-50 h-50 mb-8 rounded-full overflow-hidden">
<img src="/img/vueconf/nugs (14).jpg" class="w-full h-full object-cover"/>
</div>

# Scene 1

## The after-after-party 

(aka 3rd party scripts)

<!-- Imagine want to add scroll triggered animations. What do you do? Build it yourself? -->

---
layout: statement
---

# Ricky-Martintersections

### I can be your scroll-triggered hero, baby

<!-- No, you look for a 3rd party script -->

---

# Looks like this

```ts
import { scrollinLaVidaLoca } from 'ricky-martintersections'

// Sets up intersection observer watcher
const domNode = document.querySelector('#she-bangs')
const rickyInstance = scrollinLaVidaLoca(domNode, 'animation-name')

// Disconnects the intersection observer
rickyInstance.pleaseStop()
```

Requires managing DOM nodes & orchestrating events

<!-- You import the library you grab a dom node and you invoke the library with that dom node and some animation name.

A couple of problems. What if the target isnt on the page? We have to manually trigger the library at a later point. -->

---

# Componentize with Vue

With lifecycle events & DOM node references.

```js {all|9,11,12,14|10}
import { scrollinLaVidaLoca } from 'ricky-martintersections'

export default {
  name: 'your-hero-baby'
  props: ['animation']
  data: () => ({
    ricky: null,
  }),
  mounted() {
    this.ricky = scrollinLaVidaLoca(this.$el, this.animation)
  },
  beforeUnmount() {
    this.ricky.pleaseStop()
  }
}
```

<!--
Instead we can encapsulate this logic into an easy to use component?

 Vue provides easy access to lifecycle events and DOM nodes. -->
---

<style>
@keyframes shake {
  0% { transform: translate(1px, 1px) rotate(0deg); }
  10% { transform: translate(-1px, -2px) rotate(-1deg); }
  20% { transform: translate(-3px, 0px) rotate(1deg); }
  30% { transform: translate(3px, 2px) rotate(0deg); }
  40% { transform: translate(1px, -1px) rotate(1deg); }
  50% { transform: translate(-1px, 2px) rotate(-1deg); }
  60% { transform: translate(-3px, 1px) rotate(0deg); }
  70% { transform: translate(3px, 1px) rotate(-1deg); }
  80% { transform: translate(-1px, -1px) rotate(1deg); }
  90% { transform: translate(1px, 2px) rotate(0deg); }
  100% { transform: translate(1px, -2px) rotate(-1deg); }
}
img {
  animation: shake 1s linear infinite;
}
</style>

# Internalized Components

Encapsulate complexity & shared logic

```html
<template>
  <YourHeroBaby animation="shakeYourBonBon">
    <img src="/img/vueconf/bonbons.jpeg" alt="bonbons" />
  </YourHeroBaby>
</template>
```

<v-click>
<img src="/img/vueconf/bonbons.jpeg" alt="bonbons" class="animate-shake" />
</v-click>

<!-- As a result, it's now easy to add an image to a page, and for wait for it to scroll onto the page before you start shaking your bonbons. -->

---

# Relevant things

Targeting the DOM:

- [`this.$el`](https://vuejs.org/api/component-instance.html#el) 
- [`this.$refs`](https://vuejs.org/guide/essentials/template-refs.html) 
- [`ref()`](https://vuejs.org/api/reactivity-core.html#ref)

Event orchestration:

- [Options lifecycle hooks](https://vuejs.org/api/options-lifecycle.html#options-lifecycle)
- [Reactivity lifecycle hooks](https://vuejs.org/api/composition-api-lifecycle.html#composition-api-lifecycle-hooks)

---
layout: statement
---

<div class="flex justify-center mx-auto w-50 h-50 mb-8 rounded-full overflow-hidden">
<img src="/img/vueconf/nugs (4).jpg" class="w-full h-full object-cover"/>
</div>

# Scene 2

## The after-after-party with books

(aka 3rd party component libraries)

<!-- A lot of 3rd parties provide Vue libraries for you.

For example, when your manager tells you the animations are great, but the buttons look like butt.

If youre not a designer you might reach for -->
---
layout: statement
---

# Buttoney-Spears

### Buttons that will make your site POP!

---

# Before long...

<div class="grid grid-cols-2 gap-4">
<div>
<v-clicks>

```html
<BSpears>
  Click me, baby, one more time
</BSpears>
```

```html
<BSpears>
  I'm a slave 4 UIs
</BSpears>
```

```html
<BSpears>
  With a taste of your clicks, I'm on a ride
</BSpears>
```

```html
<BSpears>
  When UIs say it
</BSpears>
```

</v-clicks>
</div>
<div>
<v-clicks>

```html
<BSpears>
  It's Britney, click
</BSpears>
```

```html
<BSpears>
  Touch of my hand (or keyboard)
</BSpears>
```

```html
<BSpears>
  Click-sand
</BSpears>
```

<h2 class="mt-5">You get the idea...</h2>

</v-clicks>
</div>
</div>
<!-- And they look great. So you start adding more. And before long, you've got sexy buttons everywhere. -->
---
layout: statement
---

# Then one day...

Everything changes.

---

# Gimme More (props)

```html
<BSpears freeBritney="true">
  Click me, baby, one more time
</BSpears>
```

<v-click>

<h1 class="mt-12">Oops, I did it again (breaking changes)</h1>

```html {all|2,8}
<template>
  <BSpears freeBritney="true">
    <slot/>
  </BSpears>
</template>

<template>
  <BSpears conservatorship="false">
    <slot/>
  </BSpears>
</template>
```

</v-click>
<!-- You might decide you want to change some of the props on all your buttons.

Or maybe,they publish a breaking change 

These changes are good, but you have to make that change on every single button-->

---
layout: statement
---

# Search & replace <br> pit of despair

<!-- You ever tried to do a regex search and replace? Hows therapy going? -->
---

# Internalized Components

Allow for changes in one place to propagate.

<div class="grid grid-cols-2 gap-4">
<v-clicks>
<div>

```js
import { BSpears } from 'buttoney-spears'
export default {
  name: 'AppBtn',
  components: {
    BSpears
  }
}
```

```html
<template>
  <BSpears conservatorship="false" v-bind="$attrs">
    <slot/>
  </BSpears>
</template>
```

</div>
<div>

```html
<AppBtn>
  Click me, baby, one more time
</AppBtn>
```

```html
<AppBtn>
  I'm a slave 4 UIs
</AppBtn>
```

```html
<AppBtn>
  With a taste of your clicks, I'm on a ride
</AppBtn>
```

```html
<AppBtn>
  When UIs say it
</AppBtn>
```

</div>
</v-clicks>
</div>

<!-- By creating internal components to wrap external ones, you can control implementation details in one place and propagate them. -->
---

# Relevant things

Slots:

- [`<slot />`](https://vuejs.org/guide/components/slots.html#slots)
- [`$slots`](https://vuejs.org/api/component-instance.html#slots)
- [`context.slots`](https://vuejs.org/api/composition-api-setup.html#setup-context)
- [`useSlots()`](https://vuejs.org/api/sfc-script-setup.html#useslots-useattrs)

Attributes:

- [`v-bind`](https://vuejs.org/api/built-in-directives.html#v-bind)
- [`$attrs`](https://vuejs.org/api/component-instance.html#attrs)
- [`context.attrs`](https://vuejs.org/api/composition-api-setup.html#setup-context)
- [`useAttrs()`](https://vuejs.org/api/sfc-script-setup.html#useslots-useattrs)

---
layout: statement
---

<div class="flex justify-center mx-auto w-50 h-50 mb-8 rounded-full overflow-hidden">
<img src="/img/vueconf/nugs (13).jpg" class="w-full h-full object-cover"/>
</div>

# Scene 3

## See: intersection, juncture, terminal, etc.

(aka redefining interfaces)

---

# What's wrong with this picture...?

<div class="grid grid-cols-2">

- `on`: prop that expects a `Promise`
- `#pending`: slot for pending state 
- `#resolved`: slot for resolved state 
- `#rejected`: slot for rejected state 

```html
<AsyncAwait :on="somePromise">
  <template #pending>🥱</template>
  <template #resolved>🥳</template>
  <template #rejected>😭</template>
</AsyncAwait>
```

</div>

<!-- Imagine a component for dealing with promises. 

Accepts an 'on' prop which is a Promise, then provides several slots for various states, pending, resolved, rejected, etc -->
---

# Everything!!!

<v-clicks>

- Validation?
- Autocomplete?
- Type checking?
- Unintuitive interface?
- No puns?

</v-clicks>

<!-- 
What if you foget to bind the prop?
Wouldnt it be nice to have prop autocomplete?
Red squigglies if I do something wrong?
Wasted opportunity with the naming.
Let's make it better -->
---
layout: statement
---

# NsyncAwait

### Promises, with no strings attached

---

# NsyncAwait

Type checking, prop validation, more intuitive API, etc.

<div class="grid grid-cols-2 gap-4">

```jsx {all|1,2,5|10-15}
<script lang="ts">
import { defineComponent } from 'vue'
import AsyncAwait from 'async-await'

export default defineComponent({
  name: 'NsyncAwait',
  components: {
    AsyncAwait
  },
  props: {
    thisIPromiseYou: {
      type: Promise,
      required: true
    }
  }
})
</script>
```

```html {all|2-4,6-7,9-10}
<template>
  <AsyncAwait :on="thisIPromiseYou">
    <template #pending>
      <slot name="iWantYouBack" />
    </template>
    <template #resolved>
      <slot name="itsGonnaBeMe" />
    </template>
    <template #rejected>
      <slot name="tearinUpMyHeart" />
    </template>
  </AsyncAwait>
</template>
```

</div>

<!-- One again, a wrapper component, this time Add type checking/intellisense with TypeScript support. We also write more complete prop types for validation. Lastly provide more intuitive naming conventions -->
---

# Which is better?

<div class="grid grid-cols-2 gap-4">
<div>

<h4 class="text-2xl mt-0">Before</h4>

```html
<AsyncAwait :on="somePromise">
  <template #pending>🥱</template>
  <template #resolved>🥳</template>
  <template #rejected>😭</template>
</AsyncAwait>
```

- No prop validation
- No static analysis
- No intellisense & autocomplete
- Unintuitive interface

</div>
<v-clicks>
<div>
<lisa-frankify>After</lisa-frankify>
<div class="rainbow-box">

```html
<NsyncAwait :thisIPromiseYou="somePromise">
  <template #iWantYouBack>🥱</template>
  <template #itsGonnaBeMe>🥳</template>
  <template #tearinUpMyHeart>😭</template>
</NsyncAwait>
```

- Prop validation
- Type checking
- Intellisense & autocomplete
- Intuitive API
- Can sell over 44 million records

</div>
</div>
</v-clicks>
</div>

<!-- That LisaFrankify component strikes again.
 I want it that way. It's better. This I promise you. -->

---

# Relevant Things

Props:

- [Prop validation](https://vuejs.org/guide/components/props.html#prop-validation)


Static Analysis:

- [Vue with TypeScript](https://vuejs.org/guide/typescript/overview.html)
- [`defineComponent`](https://vuejs.org/api/general.html#definecomponent)

Slots:

- [Named slots](https://vuejs.org/guide/components/slots.html#named-slots)

---
layout: statement
---

<div class="flex justify-center mx-auto w-50 h-50 mb-8 rounded-full overflow-hidden">
<img src="/img/vueconf/nugs (5).jpg" class="w-full h-full object-cover"/>
</div>

# Scene 4

## Crossing borders

(aka migrations)

<!-- Ok, now imagine you're sitting at your computer and your PM sends you this... -->

---

<div class="mt-10">
  <span class="inline-block my-2 bg-blue-600 rounded-xl rounded-bl-none py-2 px-4 text-white ">Hey, can you make sure our website is accessible.</span>
</div>
<v-clicks>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">I'll put all my focus trap on it 😉</span>
</div>
<div>
  <span class="inline-block my-2 bg-blue-600 rounded-xl rounded-bl-none py-2 px-4 text-white ">Was that a pun?</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">ARIA upset?</span>
</div>
<div>
  <span class="inline-block my-2 bg-blue-600 rounded-xl rounded-bl-none py-2 px-4 text-white ">Now is not the time. We're being audited on Monday.</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">What can I say? I'm on a role.</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">OK, I'm sorry.</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">Please don't tell &lt;hr&gt;</span>
</div>
</v-clicks>

<!-- Of course, you respond with a confirmation and after a bit of back and forth, you get to work.

But youre not and accessibility expert. Good news is there's a library for that -->

---
layout: statement
---

# Christina-AguilARIA

### Like a genie in a bottle for a11y

<!-- After a bit of integration you respond -->
---

<div class="mt-10 flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">All done!</span>
</div>
<v-clicks>
<div>
  <span class="inline-block my-2 bg-blue-600 rounded-xl rounded-bl-none py-2 px-4 text-white ">Awesome. Wanna grab tacos.</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">Sure. Put the first round on my tabindex.</span>
</div>
<div>
  <span class="inline-block my-2 bg-blue-600 rounded-xl rounded-bl-none py-2 px-4 text-white ">Are you gonna do this the whole time?</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">Well that live region isn't very polite</span>
</div>
</v-clicks>

<!-- And you celebrate...

Then a bit of time passes before you get another message... -->
---
layout: image
image: /img/vueconf/several-months-later.jpg
notes: test
---
<!--  -->
---

<div class="mt-10">
  <span class="inline-block my-2 bg-blue-600 rounded-xl rounded-bl-none py-2 px-4 text-white ">We need you to do that accessibility thingy, but in Spanish</span>
</div>
<v-clicks>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">🤬</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">Really? You're just telling me now?</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">OK, I'll see what I can do.</span>
</div>
<div>
  <span class="inline-block my-2 bg-blue-600 rounded-xl rounded-bl-none py-2 px-4 text-white ">Don't you mean you'll <b>*sí*</b> what you can do?</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">Seriously!?</span>
</div>
<div class="flex justify-end">
  <span class="inline-block my-2 bg-green-600 rounded-xl rounded-br-none py-2 px-4 text-white ">No! I'm too upset for puns right now.</span>
</div>
</v-clicks>

<!-- Explative!!! Christina Aguilaria doesn't support i18n.
a bit complaining they never tel you feature requirements ahead of time

Fortunately, there's a different solution -->

---
layout: statement
---

# Shak-ARIA

### Whenever, wherever, we're meant to browse together

<!-- In my opinion its much better and also supports multiple languages.

And because you've learned from the past, you already made a wrapper component... -->
---

# Internalized Components

Can coordinate your migration strategy.

<div class="grid grid-cols-2 gap-4">
<div>

Christina-AguilARIA

```jsx
<script>
import { ChristinaAguilaria } from 'christina-aguilaria'

export default {
  name: 'MagicA11y',
  components: {
    ChristinaAguilaria
  }
}
</script>
```

```html
<template>
  <ChristinaAguilaria youAre="beautiful">
    <slot />
  </ChristinaAguilaria>
</template>
```

</div>
<div>

Shak-ARIA

```jsx {2,7}
<script>
import { ShakAria } from 'shak-aria'

export default {
  name: 'MagicA11y',
  components: {
    ShakAria
  }
}
</script>
```

```html {2,4}
<template>
  <ShakAria :hipsLie="false">
    <slot />
  </ShakAria>
</template>
```
</div>
</div>

<!-- So now, the migration story is much more approachable because you only need to swap out the components and implementation details. -->

---

# Component Consumers

Can't tell the difference.

<div class="grid grid-cols-2 gap-4">
<div>

#### Before

```html
<MagicA11y>
  <!-- ... -->
</MagicA11y>
```

</div>
<div>

#### After

```html
<MagicA11y>
  <!-- ... -->
</MagicA11y>
```

</div>
</div>

<div class="mt-60">(Disregard the fact that a11y doesn't actually work like this)</div>

<!--As a result, the component consumer doesn't notice a difference. Homer, does a11y work like this? -->

---
layout: statement
---

<div class="flex justify-center mx-auto w-50 h-50 mb-8 rounded-full overflow-hidden">
<img src="/img/vueconf/nugs (10).jpg" class="w-full h-full object-cover"/>
</div>

# Scene 5

## Wrap it up

(aka closing)

<!-- There's actually 3 meanings in there, closing, wrapper components, and immature sense of humor -->
---

# Design patterns

Common, tried and tested pattens used in software engineering.

<v-click>

## Specifically, "facade"

A structural design pattern that uses abstractions to simplify interfaces (library, framework, API, class, etc.).

</v-click>

<v-click>

- Control surface area
- Enforce common language
- Simplify dependency management
- Provide type definitions or validation
- BONUS: Signal to everyone else how smart you are

</v-click>

<!-- I want to take a moment to talk about design patterns.

Tried and tested patterns for writing better software.

More specifically, the facade patter. Makes applications easier to maintain and resilient to change
 -->

---

# Vue has cool features

- Props
- Slots
- Lifecycle hooks
- DOM access
- Attribute binding
- TS Support
- Single File Components (co-location)
- **Scoped slots\*\***
- **Render functions\*\***
- **Renderless components\*\***
- **Composables\*\***

---
layout: statement
---

# Nothing's perfect

---

# Obscurity

Adds layer between devs and original API

<div class="mt-20"></div>

# Bundle Size

Adds more code to final output

<!-- Wrapper components add abstraction. could introduce confusion, may be solved with type definitions / intellisense)
So when should you use them...
 -->

---
layout: statement
---

# Should I use it?

<!-- So you may be asking yourself rght now if yu should be implementing this pattern. And the good news is I have an answer for you. -->
---
layout: statement
---

# "It depends"
# 💩

<!-- Gotcha. This is another great way to sound smart, just end every conversation with 'it depends'. But it's true, you'll have to decide for yourself -->
---
layout: statement
---

# Next steps

Dig deeper into Vue.js the docs

Read about design patterns

Create sharable library

Explore monorepos

---

# This is the last slide

<div class="grid grid-cols-2 gap-4">
<div>

### About Vuetensils

A Vue library that provides functionality and markup, but no styles; build uniquely styled, accessible websites faster.

- Accessibility focused
- Built in functionality
- No fighting CSS specificity
- No unused/overwritten CSS
- Supports custom classes (atomic CSS)

[vuetensils.austingil.com](https://vuetensils.austingil.com/)
</div>
<div>

### About Me

<pepicons-internet/> [austingil.com](https://austingil.com)

<emojione-microphone/> [thefncall.com](https://thefncall.com)


<logos-twitter/> [@heyAustinGil](https://twitter.com/heyAustinGil)

<logos-twitch/> [@heyAustinGil](https://twitch.tv/heyAustinGil)

<bi-github/> [@AustinGil](https://github.com/AustinGil)

<bi-instagram/> [@NuggetTheMighty](https://instagram.com/NuggetTheMighty) (my dog)

</div>
</div>

<!-- Vuetensils a set of unstyled components. It provides functionality, accessibility, and semantics while you provide the styles. Which means totally unique websites without fighting overly specific CSS or unnecessary bloat.

Last thing to ask. Thank the organizers, other speakers, all the sponsors in the hall, and the person next to you. Let folks know you had a good time because it takes a lot of work to put these together. -->
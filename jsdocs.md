---
src: intro.md
---

---
layout: statement
---

# JSDocs
It's like TypeScript for the rest of us

(Slides: [jsdocs-talk.austingil.com](https://jsdocs-talk.austingil.com/))

---
layout: center
---

<img src="/img/jsdocs/example.png" />

---

# JavaScript is cool

- Runs everywhere
- No special tooling
- Huge community
- Forwards compatible
- It just works (well, sort of)

---

# ...except when it isn't

- Type mismatches
- Missing error hints (red squiggles)
- Code changes (internal/external)
- Difficult refactors

---
layout: statement
---

# That's why there's TypeScript

---

# TypeScript is cool

- Typos & errors (red squigglies)
- Intellisense & autocomplete
- Onboarding & collaboration
- Maintenance
- Automated Documentation
- CI/CD quality checks

---

# ...except when it isn't

- Requires Tooling
- Complexity
- Learning curve
- Doesn’t work everywhere

---
layout: statement
---

<svg xmlns="http://www.w3.org/2000/svg" width="160" height="160" viewBox="0 0 128 128" class="block m-auto"><mask id="a" width="128" height="128" x="0" y="0" maskUnits="userSpaceOnUse" style="mask-type:alpha"><path fill="#fff" fill-rule="evenodd" d="M90.767 127.126a7.968 7.968 0 0 0 6.35-.244l26.353-12.681a8 8 0 0 0 4.53-7.209V21.009a8 8 0 0 0-4.53-7.21L97.117 1.12a7.97 7.97 0 0 0-9.093 1.548l-50.45 46.026L15.6 32.013a5.328 5.328 0 0 0-6.807.302l-7.048 6.411a5.335 5.335 0 0 0-.006 7.888L20.796 64 1.74 81.387a5.336 5.336 0 0 0 .006 7.887l7.048 6.411a5.327 5.327 0 0 0 6.807.303l21.974-16.68 50.45 46.025a7.96 7.96 0 0 0 2.743 1.793Zm5.252-92.183L57.74 64l38.28 29.058V34.943Z" clip-rule="evenodd"/></mask><g mask="url(#a)"><path fill="#0065A9" d="M123.471 13.82 97.097 1.12A7.973 7.973 0 0 0 88 2.668L1.662 81.387a5.333 5.333 0 0 0 .006 7.887l7.052 6.411a5.333 5.333 0 0 0 6.811.303l103.971-78.875c3.488-2.646 8.498-.158 8.498 4.22v-.306a8.001 8.001 0 0 0-4.529-7.208Z"/><g filter="url(#b)"><path fill="#007ACC" d="m123.471 114.181-26.374 12.698A7.973 7.973 0 0 1 88 125.333L1.662 46.613a5.333 5.333 0 0 1 .006-7.887l7.052-6.411a5.333 5.333 0 0 1 6.811-.303l103.971 78.874c3.488 2.647 8.498.159 8.498-4.219v.306a8.001 8.001 0 0 1-4.529 7.208Z"/></g><g filter="url(#c)"><path fill="#1F9CF0" d="M97.098 126.882A7.977 7.977 0 0 1 88 125.333c2.952 2.952 8 .861 8-3.314V5.98c0-4.175-5.048-6.266-8-3.313a7.977 7.977 0 0 1 9.098-1.549L123.467 13.8A8 8 0 0 1 128 21.01v85.982a8 8 0 0 1-4.533 7.21l-26.369 12.681Z"/></g><path fill="url(#d)" fill-rule="evenodd" d="M90.69 127.126a7.968 7.968 0 0 0 6.349-.244l26.353-12.681a8 8 0 0 0 4.53-7.21V21.009a8 8 0 0 0-4.53-7.21L97.039 1.12a7.97 7.97 0 0 0-9.093 1.548l-50.45 46.026-21.974-16.68a5.328 5.328 0 0 0-6.807.302l-7.048 6.411a5.336 5.336 0 0 0-.006 7.888L20.718 64 1.662 81.386a5.335 5.335 0 0 0 .006 7.888l7.048 6.411a5.328 5.328 0 0 0 6.807.303l21.975-16.681 50.45 46.026a7.959 7.959 0 0 0 2.742 1.793Zm5.252-92.184L57.662 64l38.28 29.057V34.943Z" clip-rule="evenodd" opacity=".25"/></g><defs><filter id="b" width="144.744" height="113.408" x="-8.411" y="22.594" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feColorMatrix in="SourceAlpha" result="hardAlpha" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0"/><feOffset/><feGaussianBlur stdDeviation="4.167"/><feColorMatrix values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.25 0"/><feBlend in2="BackgroundImageFix" mode="overlay" result="effect1_dropShadow_1_36"/><feBlend in="SourceGraphic" in2="effect1_dropShadow_1_36" result="shape"/></filter><filter id="c" width="56.667" height="144.007" x="79.667" y="-8.004" color-interpolation-filters="sRGB" filterUnits="userSpaceOnUse"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feColorMatrix in="SourceAlpha" result="hardAlpha" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0"/><feOffset/><feGaussianBlur stdDeviation="4.167"/><feColorMatrix values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.25 0"/><feBlend in2="BackgroundImageFix" mode="overlay" result="effect1_dropShadow_1_36"/><feBlend in="SourceGraphic" in2="effect1_dropShadow_1_36" result="shape"/></filter><linearGradient id="d" x1="63.922" x2="63.922" y1=".33" y2="127.67" gradientUnits="userSpaceOnUse"><stop stop-color="#fff"/><stop offset="1" stop-color="#fff" stop-opacity="0"/></linearGradient></defs></svg>

# VS Code
Code editor with TS Language Server built in

(https://code.visualstudio.com/)

---

# Provides great Intellisense

<img src="/img/jsdocs/Intellisense.png" />

---

# But doesn't type-check by default

<img src="/img/jsdocs/function-example.png" />

---

# A JS example

```js
const input = document.querySelector('input')

const someVal = 100 / input.value
```

---

# Same code with TS

<img src="/img/jsdocs/squiggle.png"/>

---
layout: statement
---

# Which would you prefer?

---
layout: image
image: /img/jsdocs/why-not-both.gif
---
<!-- image: /img/jsdocs/both-agree.gif -->

---
layout: statement
---

# TS benefits in JS files
## TypeScript can parse JSDoc comments in JavaScript files without any need for extra tooling

---

# Enable Type Checking in JS files

```js
// @ts-check
```

---

# Helps catch errors

<img src="/img/jsdocs/type-checking.png"/>

---

# JSDocs provides more control

<img src="/img/jsdocs/type-checking-2.png"/>

---

# Also works with functions

<img src="/img/jsdocs/TypeScript-Function.png" width="600"/>

---

<v-click>

## It's great:
- Still just JS (comments).
- Easy to start.
- Incrementally adoptable.
</v-click>
<v-click>

## Could be better:
- Requires adding comments to each file.
- Adds noise to code reviews.

</v-click>

---

# Enable TS check for whole project

<img src="/img/jsdocs/checkJs-setting.png">

```json
// settings.json
{
  // ...
  "js/ts.implicitProjectConfig.checkJs": true,
}
```

---

<v-click>

## It's great:
- Less work to get type checking.
</v-click>
<v-click>

## Could be better:
- Only works on your machine.

</v-click>

---

# Enable TS check for whole team

```json
// tsconfig.json
{
  "compilerOptions": {
    "checkJs": true,
  }
}
```

---

<v-click>

## It's great:
- Everyone can start catching bugs sooner.
</v-click>
<v-click>

## Could be better:
- Only works in VS Code.

</v-click>

---

# Run type checks with a CLI

`npm install --save-dev typescript`

<div class="grid grid-cols-2 gap-2">

<v-click>

```json
// package.json
{
  "scripts": {
    "ts": "tsc"
  }
}
```
</v-click>
<v-click>

```json
// tsconfig.json
{
  "files": ["./src/index.js"],
  "compilerOptions": {
    "checkJs": true,
    "allowJs": true,
    "noEmit": true,
  }
}
```

</v-click>
</div>

---

# Now check types programmatically

`npm run ts`

<img src="/img/jsdocs/CLI-error.png" />

---

<v-click>

## It's great:
- Runs on any machine
- Great for git hooks (`pre-commit`, `pre-push`)
- Great for CI/CD
</v-click>
<v-click>

## Could be better:
- Some JSDocs syntax is awkward or not supported by TS

</v-click>

---
layout: statement
---

# So why not just use TypeScript...?

---
layout: statement
---

# You can!

<v-clicks>

TS can use both `.js` or `.ts` files

JSDocs can work as a stepping stone

Or you can keep using JSDocs
</v-clicks>

---
layout: statement
---

# I prefer JSDocs 
(highly subjective)

---

# Opinions are based on experience

<v-clicks>

- **Developer**: can copy/paste code into browser/Node
- **Writer**: people can copy/paste code into their projects
- **Teacher**: students have a simpler setup and less to learn
- **Maintainer**: people can create codesandbox reproductions
- **Team lead**: want types without the learning overhead for new devs
- **Reviewer**: easier to read with separated types (highly subjective)
</v-clicks>

---
layout: statement
---

# Next steps:
## Learn more about JSDocs
(+ TypeScript)

---

# Create complex type definitions

<img src="/img/jsdocs/object-type.png" width="400" />

---

# Import type from different file

<img src="/img/jsdocs/imported-type.png" />

---

# Import typedef from different file

<img src="/img/jsdocs/imported-type-2.png" />

---

# Import type from a library

<img src="/img/jsdocs/imported-vue.png" />

---

# Define types in `.d.ts` files

```ts
export interface Dog {
  breed: string
  age: number
  name?: string
}
```

---

# Disabling TS from checking code

- `// @ts-ignore` above line: Disable TS on that line.
- `// @ts-nocheck` top of file: Disable TS on whole file.
- `exclude` in `tsconfig.json`: Disable TS on groups of files.

---

# Caveats

TypeScript mostly understands JSDocs, but not everything.

- [Unsupported patterns](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html#unsupported-patterns)
- [Unsupported tags](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html#unsupported-tags)

---

# Type Assertions 

OK in TS

```ts
const canvas1 = 
  document.querySelector("canvas") as HTMLCanvasElement;

const canvas2 =
  <HTMLCanvasElement>document.querySelector("canvas");
```

<v-click>

Flat-out gross in JSDocs 🤮

```ts
const canvas1 = /** @type {HTMLCanvasElement} */ (
  document.querySelector("canvas")
);
```
</v-click>

---
layout: statement
---

# Closing

---

- Type checking != TypeScript
<v-clicks>

- It's not one or the other
- JSDocs is good BECAUSE TypeScript exists
- We still use `.d.ts` files and the CLI
- It's mostly just syntactical difference in authoring
- For me, verbose comments + terse code is better than verbose code
- TS is an important testing ground for JS proposals & paves cow paths

</v-clicks>

---

## Community Support for JSDocs

"My position is, types are fantastic, TypeScript is a bit of a pain … as soon as you use a .ts file, then you have to have the tooling to support that … there’s all of these points of friction when you use a non-standard language like TypeScript that I have come to believe makes it not worth it." - [Rich Harris](https://www.youtube.com/watch?v=MJHO6FSioPI)

"Like to keep the source I author the same as the source at runtime because debugging is way faster when it isn't a murder mystery." - [@brianleroux](https://twitter.com/brianleroux/status/1684571157188706304)

"verbose comment - terse code" - [@myfonj](https://twitter.com/myfonj/status/1501956653981175810)

---

# Resources

- "Working with JavaScript" by VS Code
- "JSDoc Cheatsheet" by Devhints
- "JSDoc Cheatsheet and Type Safety Tricks" by Joshua Tzucker
- "Type Safe JavaScript with JSDoc" by Robert Biggs
- "JavaScript Type Linting" by Robert Biggs
- "TypeScript without TypeScript - JSDoc superpowers" by Stefan Baumgartner

---
layout: statement
---

# Worth mentioning

"Types as comments" annotations proposal

https://tc39.es/proposal-type-annotations/

---

# Before

```js
/**
 * @param {string}  p1 - String param.
 * @param {string=} p2 - Optional param (Closure syntax)
 * @param {string} [p3] - Optional param (JSDoc syntax).
 * @param {string} [p4="test"] - Param with default value.
 * @return {string} This is the result
 */
function stringsStringStrings(p1, p2, p3, p4="test") {
    // TODO
}
```

---

# After 

```js
function stringsStringStrings(
  p1: string,
  p2? : string,
  p3?: string,
  p4 = "test"
): string {
    // TODO
}
```

---

<p>Read the blog post: <a href="https://austingil.com/typescript-the-easy-way">austingil.com/typescript-the-easy-way</a></p>

<div class="mt-10 grid grid-cols-2 gap-2">

<div>

# Let's connect

<ul>
<li><pepicons-internet/><a href="https://austingil.com">austingil.com</a></li>
<li><logos-twitter/><a href="https://twitter.com/heyAustinGil">@heyAustinGil</a></li>
<li><logos-mastodon-icon/><a href="https://mastodon.social/@Austingil">@mastodon.social/@Austingil</a></li>
<li><logos-youtube-icon/><a href="https://youtube.com/@heyAustinGil">@heyAustinGil</a></li>
<li><logos-twitch/><a href="https://twitch.tv/heyAustinGil">@heyAustinGil</a></li>
<li><bi-github/><a href="https://github.com/AustinGil">@AustinGil</a></li>
</ul>
</div>
<div class="text-4xl">

# $100 for Akamai Connected Cloud

<img src="/img/bit.ly_agilacc.png" width="260">
<a href="https://bit.ly/agilacc">bit.ly/agilacc</a>
</div>

</div>

---
layout: statement
---

# JSDocs
It's like TypeScript for the rest of us

Requirements:

Node.js + NPM
VS Code

---
src: intro.md
---

---

<div class="grid grid-cols-2 gap-8">
<div>

# JavaScript is cool

- Runs everywhere
- Minimal tooling
- Huge community
</div>
<div v-click>

# ...except when it isn't

- Missing error hints (red squiggles)
- Difficult refactors
- Type mismatches
- Code changes (internal/external)
</div>
</div>

---
layout: statement
---

# That's why there's TypeScript

---

<div class="grid grid-cols-2 gap-8">
<div>

# TypeScript is cool

- Typos & errors (red squigglies)
- Intellisense & autocomplete
- Onboarding & collaboration
- CI/CD quality checks
- Maintenance
- Automated Documentation
</div>
<div v-click>

# ...except when it isn't

- Requires Tooling
- Learning curve
- Complexity
- Doesn’t work everywhere
- Source map woes
</div>
</div>

---
layout: statement
---

# Let's write some JS

---
layout: statement
---

# VS Code
Code editor with Intellisense built in (via TypeScript)

(https://code.visualstudio.com/)

---

# Type checking a file

`npm init -y`

```js
// @ts-check
```

---

# Type checking your project

```json
"javascript.implicitProjectConfig.checkJs": true
```

---

# Type checking some team's project

```json
// tsconfig.json
{
  "compilerOptions": {
    "checkJs": true,
  }
}
```

---

# Creating complex types

```js
/**
 * @typedef {object} Dog
 * @property {string} breed
 * @property {number} age
 * @property {string?} name
 */
```

---

# Type checking whole team's project

`npm install --save-dev typescript`

<div class="grid grid-cols-2 gap-2">

```json
// tsconfig.json
{
  "compilerOptions": {
    "checkJs": true,
    "noEmit": true,
  }
}
```

```json
// package.json
{
  "scripts": {
    "ts": "tsc"
  }
}
```

</div>

---

# Integrating CI/CD
<div class="text-18px">

```yml
# ./.github/workflows/ci.yml
name: Type Check
on:
  push:
    branches: [ '**' ]
jobs:
  CI:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Install
        run: npm ci
      - name: TS
        run: npm run ts
```
</div>

---

# Adding types to libraries

<div class="grid grid-cols-2 gap-2">

```json
// tsconfig.json
{
 "compilerOptions": {
  "checkJs": true,
  "declaration": true,
  "emitDeclarationOnly": true,
  "outDir": "./types",
 }
}
```

```json
// package.json
{
  "types": "types"
}
```

</div>

---

# Why I love

- As a developer - copy/paste my code anywhere
- As a writer - people can easily use my code
- As a teacher - simpler setup and less to learn
- As an OS maintainer - quicker sandbox reproductions
- As a team lead - strong types without the learning overhead for new devs
- As a debugger - fewer issues with source maps
- As a reviewer - no mixing code and types (subjective)

---

# What I don't love

Type Assertions in TS: 🙂

```ts
const canvas1 = 
  document.querySelector("canvas") as HTMLCanvasElement;
const canvas2 =
  <HTMLCanvasElement>document.querySelector("canvas");
```

<v-click>

Type Assertions in JSDocs: 🤮

```ts
const canvas1 = /** @type {HTMLCanvasElement} */ (
  document.querySelector("canvas")
);
```
</v-click>

---

# Closing

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

# Community Support for JSDocs

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

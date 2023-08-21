---
src: intro.md
---

---
layout: statement
---

# JSDocs
It's like TypeScript for the rest of us

---

# JavaScript is cool

- Runs everywhere
- Minimal tooling
- Huge community

---

# ...except when it isn't

- Missing error hints (red squiggles)
- Difficult refactors
- Type mismatches
- Code changes (internal/external)

---
layout: statement
---

# That's why there's TypeScript

---

# TypeScript is cool

- Typos & errors (red squigglies)
- Intellisense & autocomplete
- Onboarding & collaboration
- CI/CD quality checks
- Maintenance
- Automated Documentation

---

# ...except when it isn't

- Requires Tooling
- Learning curve
- Complexity
- Doesn’t work everywhere

---
layout: statement
---

# VS Code
Code editor with Intellisense built in (via TypeScript)

(https://code.visualstudio.com/)

---
layout: statement
---

# Let's write some JS

---

# Enable TypeChecking in a file

```js
// @ts-check
```

---

# Enable TypeChecking in a project

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

# Integrating TypeScript into CI/CD

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

JSDocs benefits

Simpler to add comments and examples to type definitions
Old history means rich ecosystem

---

# Why I love JSDocs > TS

As a developer, I can copy/paste parts of my code in the browser/Node
As a writer, people can more easily use my code in their projects
As a teacher, students have a simpler setup and a bit less to learn
As an OS maintainer, people can more easily make codesandbox reproductions
As a reviewer, I prefer NOT mixing code and types (highly subjective)
As a team lead, I want strong types without the learning overhead for new devs

---

# What I don't love about JSDocs

It's verbose. `as const` is flat-out gross 🤮

```js
/**
 * @param {string}  p1 - A string param.
 * @param {string=} p2 - An optional param (Closure syntax)
 * @param {string} [p3] - Another optional param (JSDoc syntax).
 * @param {string} [p4="test"] - An optional param with a default value
 * @return {string} This is the result
 */
function stringsStringStrings(p1, p2, p3, p4="test") {
    // TODO
}
```
And here's the equivalent TypeScript syntax enabled by this proposal.
```js
function stringsStringStrings(p1: string, p2?: string, p3?: string, p4 = "test"): string {
    // TODO
}
```

---

# Arguments against TS

It's harder to set up.
- Not really
- `ts-node` is fine
- Deno is fine

---

It's not one or the other

JSDocs is only good BECAUSE TypeScript exists

It's just a different syntax for authoring

We still use `.d.ts` files and the CLI

---

Commments

"Like to keep the source I author the same as the source at runtime because debugging is way faster when it isn't a murder mystery." - @brianleroux https://twitter.com/brianleroux/status/1684571157188706304

"verbose comment - terse code" - @myfonj https://twitter.com/myfonj/status/1501956653981175810

---

TypeScript is still a good thing

I still want the CLI for checking my code

It's a great testing ground for JS proposals

It paves the cowpaths

---

https://tc39.es/proposal-type-annotations/

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

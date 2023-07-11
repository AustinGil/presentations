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

# Resources

- "Working with JavaScript" by VS Code
- "JSDoc Cheatsheet" by Devhints
- "JSDoc Cheatsheet and Type Safety Tricks" by Joshua Tsucker
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

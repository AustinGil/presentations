---
layout: statement
---

# What the heck is Edge Compute anyway?

(aka "edge functions" or "edge workers")

---
src: intro.md
---
---

# Plain and simple:

<v-clicks>

Edge compute is the result of distributing serverless functions to thousands of locations around the world to handle requests from as close to the user as possible.

The result is programmable/dynamic/customizable responses with the least amount of latency (aka more speed).
</v-clicks>

---
layout: statement
---

# That's it!

<!-- That's it. That's the pitch. And if you understand all that, then I have nothing more to add. 
Thank you for coming to my talk.
For the rest of my talk, we'll cover pros and cons as well as driving the idea home with a metaphor.
-->

---
layout: statement
---

# But that's also really boring

---
layout: statement
--- 

<img src="/img/edge-compute/puppy-hat.jpg" class="block m-auto" width="300" alt="cute dog wearing a knitted hat">

# Let's make dog hats!!!

---

# Natural progression of dog hats

1. Client wants a thing
2. You make a thing
3. You give them a thing

<v-click>

Mediocre analogy / really good photos ¯\\\_(ツ)\_/¯
</v-click>

---

# Let's start with "Compute"

<v-clicks>
<div>

## What:

Compute = bleeps & bloops -> HTML
</div>
<div>

## Where: 
- Traditional Servers
- Client-Side JavaScript
- Client-Side workers
- Static-Site-Generators
- Cloud functions
- Edge functions
</div>
</v-clicks>

---
layout: statement
---

# Traditional Servers

Machine runs software you choose to execute code you write to return HTML.

<!-- <v-clicks>

- Predictable pricing
- Unbounded run times
- You pay even for idle times
- Challenge to scale
- Distance from users add latency
- **You have complete control/responsibility**

</v-clicks> -->

---
layout: statement
--- 

# 🏭<br>Commercial workspace

<img src="/img/edge-compute/dog-beret.jpg" class="block m-auto" width="300" alt="Black pug with a knitted red beret to match its red, black, and white stripped shirt.">

---
layout: statement
--- 

# Client-Side Rendering

JavaScript (or WebAssembly) running in the user's browser generates HTML.

<!-- <div class="grid grid-cols-2">
<v-clicks>
<div>

### Pros
- No latency because it's on device
- Can work offline

</div>
<div>

### Cons
- Requires user download more JS
- Can't keep secrets ("View source")
- No control over environment (x-browser issues)
- Performance greatly dependent on user's device

</div>
</v-clicks>
</div> -->

---
layout: statement
--- 

# 🛠️<br>DIY kits

<img src="/img/edge-compute/knitting-supplies.jpg" class="block m-auto" alt="knitting supplies" width="530">

---
layout: statement
--- 

# Static-Site-Generators (SSGs)

Generate all pages ahead of time, into static folders and files.

(Technically still SSR)

<!-- <div class="grid grid-cols-2">
<v-clicks>
<div>

### Pros
- Immediate response times
- Works great with a CDN
- Very fast, cheap, secure, and easy to host

</div>
<div>

### Cons
- Can't support dynamic content (without CSR)
- Build times grow with number of pages

</div>
</v-clicks>
</div> -->

---
layout: statement
--- 

# 🐶🎩<br>Pre-knitted dog hats

<img src="/img/edge-compute/dog-hats-5.jpg" class="block m-auto" width="280" alt="Black lab wearing a blue knitted hat with a puff ball on top. He's outside in the fall time.">

---
layout: statement
--- 

# Cloud Functions

(aka "lambda", "serverless")

Service providers route requests to the functions you provide.<br>
<!-- (They manage machines and servers) -->

<!-- <div class="grid grid-cols-2">
<v-clicks>
<div>

### Pros
- Easy to provision (teams/migration)
- "Infinitely" scalable
- Only pay for what you use
- Only manage code (no hardware or servers)

</div>
<div>

### Cons
- Must follow conventions (naming, files, parameters, returns)
- "Stateless" (no shared memory/files)
- Limited resources & languages
- Can also be very far from users

</div>
</v-clicks>
</div> -->

---
layout: statement
--- 

# 🐶🎩🧶💉🤖<br>Dog-hat-knitting robots

<img src="/img/edge-compute/football-dog.jpg" class="block m-auto" width="350" alt="cute dog wearing a knitted, New England Patriots hat">

---
layout: statement
--- 

# Ok, that's compute

---

# What about "Edge"?

<div class="grid grid-cols-2 gap-4 mt-24">
<v-clicks>
<div>

## What
A network of globally distributed computers capable of handling user requests.
</div>
<div>

## Why
By putting resources as close to users as possible, we can reduce latency, thereby improving performance and user experience.
</div>
</v-clicks>
</div>

---
layout: statement
--- 

# Content Delivery Network (CDN)

Thousand of globally distributed servers to deliver static assets closer to users

<!-- <div class="grid grid-cols-2">
<v-clicks>
<div>

### Pros
- Greatly reduce latency
- Works well with CSR & SSG

</div>
<div>

### Cons
- Not ideal for dynamic contnet

</div>
</v-clicks>
</div> -->

---
layout: statement
--- 

# 🏪<br>Convenience stores

<img src="/img/edge-compute/two-hat-dogs.jpg" class="block m-auto" width="350" alt="two cute dogs wearing a knitted hats">

---
layout: statement
---

# Now let's talk performance

---

# Users experience performance in 3-D

<v-clicks>

- **Distance** request/response must travel (latency)
- **Download** size before code executes
- **Device** hardware capabilities

</v-clicks>

<!-- <v-click>

<h3 class="bottom-10" style="position: absolute !important;">
🔥🔥🔥 Hot tip: alliteration > coherence
</h3>

</v-click> -->

---

# The speed-of-light-problem

Technology continues to improve, but the speed of light remains the same.

<v-clicks>

<div>
  <p>Edge vs. Origin</p>
  <img src="/img/edge-compute/edge-redirect.svg" class="block m-auto" width="600" alt="cute dog wearing a knitted, New England Patriots hat">

  <p>Eventually, the biggest bottleneck is distance</p>
</div>

</v-clicks>

---

# With everything in mind, we should...

<v-clicks>

- Do things closer to users (like a CDN)
- Do more work on servers (like cloud servers/functions)
- Send smaller assets (???)

</v-clicks>

---
layout: statement
---

# The logical next step is...

---
layout: statement
---

# Put dog-hat-knitting robots inside convenience stores <br> 🐶🎩🧶💉🤖+🏪

<img src="/img/edge-compute/mohawk-dog.jpg" class="block m-auto" width="450" alt="cute dog wearing a knitted, New England Patriots hat">

---

# Edge compute

<p>
<v-clicks>
<span>Programmable runtimes (like cloud functions)...</span>
<span>that are globally distributed (like a CDN)...</span>
<span>and live between a client and origin.</span>
</v-clicks>
</p>
<p>
<v-clicks>
<span>Dynamic server-side functionality...</span>
<span>that executes as close to users as possible.</span>
</v-clicks>
</p>

<v-click>
<div class="mt-12">

### Plus:

- Reliable location information
- Access to key-value stores 
</div>
</v-click>

---

# For Users

Dynamic content with...

<v-clicks>

- Less latency (compared to servers/cloud functions)
- Less to download (compared to client-side rendering)
- Less work on the client (better batt. & perf.)
</v-clicks>

--- 

# For Developers

<v-clicks>

- Low barrier for POC
- Consistent execution environment (no x-browser issues)
- Location-based logic
- Secrets stay secret (compared to client-side)
- Common programming language (JavaScript)
- No servers/infrastructure to manage
</v-clicks>

--- 

# For Website owners

<v-clicks>

- Reduce load on origin servers (performance, reliability, cost)
- Automatic scaling
- Only pay for what you use
</v-clicks>

--- 

<h1>The rough edges <span class="font-sans">( ͡° ͜ʖ ͡°)</span></h1>

<v-clicks>

- Limited platform features (V8 isolates != Node.js)
- Limited compute resources
- Limited time resources
- Limited networking protocols (HTTP != TCP/IP)
</v-clicks>

---
layout: statement
---

# No one likes to talk about the hard part...

---
layout: statement
---

# Distributed data

---
layout: statement
---

# Edge compute isn't<br>always better 

💻: origin<br>
🤵: server<br>
🔪: edge<br>
🎯: target<br>

---

# Proxy service in same region 🙂

<!-- <v-clicks> -->

<div class="p-4 rounded-md bg-gray-800">

```
💻---------------🤵-🎯
```

</div>

vs.

<div class="p-4 rounded-md bg-gray-800">

```
💻-🔪---------------🎯
```

</div>

<!-- </v-clicks> -->

---

# Proxy service in distant region 😀

<!-- <v-clicks> -->

<div class="p-4 rounded-md bg-gray-800">

```
💻---------------🤵---------------🎯
```
</div>

vs.

<div class="p-4 rounded-md bg-gray-800">

```
💻-🔪---------------🎯
```

</div>

<!-- </v-clicks> -->

---

<h1>Multiple <b class="text-5xl">concurrent</b> requests 😄</h1>

(a.k.a API Orchestration)

<!-- <v-clicks> -->

<div class="p-4 rounded-md bg-gray-800">

```
                   ┌----------------🎯
💻----------------🤵-🎯
                   └------🎯
```

</div>

vs.

<div class="p-4 rounded-md bg-gray-800">

```
    ┌----------------🎯
💻-🔪---🎯
    └------🎯
```

</div>

<!-- </v-clicks> -->

---

<h1>Multiple <b class="text-5xl">sequential</b> requests 😬</h1>

(eg: Blog Post -> Catgeories -> Related Posts)

<!-- <v-clicks> -->

<div class="p-4 rounded-md bg-gray-800">

```
💻---------------🤵-🎯-🤵🎯-🤵---------------💻
```

</div>

vs.

<div class="p-4 rounded-md bg-gray-800">

```
💻-🔪---------------🎯---------------🔪---------------🎯---------------🔪-💻
```

</div>

<!-- </v-clicks> -->

---

# There are solutions

<v-clicks>

- Edge Key-Value stores
- Replica databases
- Distributed cache

</v-clicks>

---

# An addition, not a replacement

Where to run compute becomes a tough question<br>
(latency, bundle size, device capabilities, data location etc).

<v-click>

<h3 class="mt-12">Before</h3>

Client-side JS -> Client-side service worker -> Cloud functions -> Traditional servers

</v-click>
<v-click>

<h3 class="mt-12">After</h3>

Client-side JS -> Client-side service worker -> **Edge compute** -> Cloud functions -> Traditional servers

<!-- <div class="mt-12">Smart folks are exploring these issues:
<br><br>
<a href="https://astro.build/">Astro</a>, <a href="https://remix.run/">Remix</a>, <a href="https://nuxtjs.org/">Nuxt</a>, <a href="https://nextjs.org/">Next</a>, and more
</div> -->

</v-click>

---
layout: statement
---

# So maybe not for full apps
## But good at other things...

---

# Common use cases

<v-clicks>

- Modify request/response (server-side ads)
- Fast static search (auto-complete, store locator)
- Geolocation (language, policies)
- Redirect management ([blog post](https://austingil.com/optimizing-content-migrations-with-edge-compute/))
- Token-based personalization (A/B testing, feature flags)
- Stateless auth (JSON Web Tokens)
- API proxy / orchestration

</v-clicks>

---
layout: statement
---

# The next phase of web development

<img src="/img/edge-compute/white-balance.jpg" class="block m-auto" width="400" alt="cute dog wearing a knitted, New England Patriots hat">

## Dog hats for everyone!!!

---

# Available in frameworks near you 

- [Astro](https://astro.build/)
- [Remix](https://remix.run/)
- [Next.js](https://nextjs.org/)
- [Nuxt.js](https://nuxtjs.org/)
- [11ty](https://www.11ty.dev/docs/plugins/edge/)
- [Sveltekit](https://kit.svelte.dev/)
- [Fresh](https://fresh.deno.dev/)
- [SolidStart](https://start.solidjs.com/)
- [Qwik City](https://qwik.builder.io/docs/qwikcity/)
- and more

---
layout: statement
---

# It's exciting!!!

## but also...

---
layout: statement
---

# Existential crisis!!!

<h1 class="font-sans">(ಥ﹏ಥ)</h1>

<h4 class="absolute top-35 left-16">Isn't my app fast enough?</h4>

<h4 class="absolute top-32 right-16">How much does 300 milliseconds matter?</h4>

<h4 class="absolute bottom-28 left-48">Is all the effort worth it?</h4>

<h4 class="absolute bottom-40 right-12">Do dogs even like wearing hats?</h4>

---
layout: statement
---

# Does 300ms really matter?

---

# Compulsory slide with lots of stats

- 100ms delay => 7% drop in sales
- 2s delay => 103% increased bounce rate
- Over 3s load times => 53% smartphone users don't convert
- Optimal loading for most sales: 1.8-2.7s
- 28% users won’t return to slow sites
- Webpages with most sales loaded 26% faster
- 250ms faster => keeps users from visiting competitors
- Performance impact's revenue, perception, loyalty, & engagement

Source: [Akamai's 2017 Online Retail Performance Report](https://www.akamai.com/newsroom/press-release/akamai-releases-spring-2017-state-of-online-retail-performance-report)

---

# Visualization


In 2008, Amazon found 100ms in load hurt sales by 1%<br>
($513.98b annual revenue x 1% = >$5b)
<v-clicks>

They could hire **SIXTY THOUSAND** developers and still profit<br>
(2023 average = $83k)

More case studies of performance vs. UX/biz metrics at wpostats.com

</v-clicks>

---
layout: statement
---

# Is it worth it?

<v-click>

## ~~Lemme work it~~

## It depends 💩

(but when you need it, give [Akamai EdgeWorkers](https://www.akamai.com/products/serverless-computing-edgeworkers) a try)

</v-click>

---

# Akamai EdgeWorkers

- Most distributed network (>300k servers, >4k POPs)
- More customizable lifecycle hooks
  - After client request, before origin request, after origin response, before client response
- Integrates with CDN's cached content
- Protected by industry-leading security
- Canary-deployment rollouts
- No per-region/per-server limits (only per-request)

---
layout: image
image: /img/edge-compute/scared-dog.jpg
---
<!-- <img src="/img/edge-compute/scared-dog.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/bday-hat.jpg
---
<!-- <img src="/img/edge-compute/bday-hat.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/big-puff.jpg
---
<!-- <img src="/img/edge-compute/big-puff.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/cool-chihuahua.jpg
---
<!-- <img src="/img/edge-compute/cool-chihuahua.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/double-puff.jpg
---
<!-- <img src="/img/edge-compute/double-puff.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/garden-hat.jpg
---
<!-- <img src="/img/edge-compute/garden-hat.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/hippie-dog.jpg
---
<!-- <img src="/img/edge-compute/hippie-dog.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/looking-at-owner.jpg
---
<!-- <img src="/img/edge-compute/looking-at-owner.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/old-dog.jpg
---
<!-- <img src="/img/edge-compute/old-dog.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/reindog.jpg
---
<!-- <img src="/img/edge-compute/reindog.jpg" class="block m-auto" width="500"> -->
---
layout: image
image: /img/edge-compute/pretty-chihuahua.jpg
style: color:black
---

<v-click>

<div class="grid grid-cols-2">
<div>

# How'd I do?
<p class="text-4xl"><a href="https://bit.ly/thanks-austin">bit.ly/thanks-austin</a></p>
</div>
<div>

# $100 Cloud Credit
<p class="text-4xl"><a href="https://linode.com/austingil">linode.com/austingil</a></p>
</div>
</div>
<br>

## Let's talk: 
Edge compute, web development, <br>career, chiweenies, whatever :D

<!-- <span class="font-mono">ヽ(⌐■_■)ノ♪♬</span> -->

## Let's connect:

<p class="grid grid-cols-3 gap-2">
<div><pepicons-internet/><a href="https://austingil.com">austingil.com</a></div>
<div><logos-twitter/><a href="https://twitter.com/heyAustinGil">@heyAustinGil</a></div>
<div><logos-mastodon-icon/><a href="https://mastodon.social/@Austingil" class="text-[1.125rem]">@mastodon.social/@Austingil</a></div>
<div><logos-youtube-icon/><a href="https://youtube.com/@heyAustinGil">@heyAustinGil</a></div>
<div><logos-twitch/><a href="https://twitch.tv/heyAustinGil">@heyAustinGil</a></div>
<div><bi-github/><a href="https://github.com/AustinGil">@AustinGil</a></div>
</p>

</v-click>
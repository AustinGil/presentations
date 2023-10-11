---
layout: statement
---

<div class="grid grid-cols-2 gap-4">
<div class="grid place-content-center">

# What the heck is Edge Compute anyway?

(aka "edge functions" <br>or "edge workers")
</div>
<div>

<b>Slides:</b> [bit.ly/edge-compute](http://bit.ly/edge-compute)
<img src="/img/edge-compute/qr.png" alt="http://bit.ly/edge-compute" width="400">
</div>
</div>

---
src: intro.md
---
---

# Plain and simple:

Edge compute is the result of distributing serverless functions to multiple locations around the world to handle requests from as close to the user as possible.

The result is dynamic responses with the least amount of latency.

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

# How to make dog hats

1. Client asks for the thing
2. You do work to make the thing
3. You give them the thing

<v-clicks>

A mediocre analogy for delivering websites

...but really good photos ¯\\\_(ツ)\_/¯
</v-clicks>

---
layout: image
image: /img/edge-compute/cute.jpg
---

<!-- <img src="/img/edge-compute/cute.jpg"> -->

---

# Background on "Compute"

<v-clicks>
<div>

## What:

Compute = bleeps & bloops -> HTML (or other stuff)
</div>
<div>

## Where: 
- Servers-Side
- Client-Side
- Static-Site-Generators
</div>
</v-clicks>

---
layout: statement
---

# Server-Side
(on-prem, VPS, cloud functions)

User request travels to a machine (own/rent) in a specific location which runs your code and return the HTML that's rendered on the page.

<!-- <v-clicks>

- Predictable pricing
- Unbounded run times
- **You have complete control**
- pay for idle times
- Challenge to scale
- Distance from users add latency
- **You have complete responsibility**

</v-clicks> -->

---
layout: statement
--- 

# 🏭<br>Commercial workspace

<img src="/img/edge-compute/dog-beret.jpg" class="block m-auto" width="300" alt="Black pug with a knitted red beret to match its red, black, and white stripped shirt.">

---
layout: statement
--- 

# Client-Side
(JavaScript, service workers, WASM)

User downloads JavaScript that runs on **THEIR** machine to generate HTML.

<!--

- No latency
- Offline
- Bigger download
- No secrets
- Environment/ x-browser
- Users Performance

-->

---
layout: statement
--- 

# 🛠️<br>DIY kits

<img src="/img/edge-compute/knitting-supplies.jpg" class="block m-auto" alt="knitting supplies" width="530">

---
layout: statement
--- 

# Static-Site-Generators
(aka SSG, technically still SSR)

Machine you control builds website ahead of time into static folders and files, allowing for immediate HTML response.

<!--

- Immediate response
- CDN
- fast, cheap, secure, easy
- Not dynamic
- Build times

-->

---
layout: statement
--- 

# 🐶🎩<br>Pre-knitted dog hats

<img src="/img/edge-compute/dog-hats-5.jpg" class="block m-auto" width="280" alt="Black lab wearing a blue knitted hat with a puff ball on top. He's outside in the fall time.">

---
layout: statement
--- 

# Ok, that's compute

---
layout: statement
---

# What about "Edge"?

<!-- <div class="grid grid-cols-2 gap-4 mt-24">
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
</div> -->

---
layout: statement
--- 

# Content Delivery Network
(CDN)

Network of globally distributed computers that deliver **STATIC** assets closer to users, reducing latency and improving performance.

<!--
- Greatly reduce latency
- Works well with CSR & SSG
- Not ideal for dynamic contnet
-->

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

# Performance: Now in 3-D!

<v-clicks>

- **Distance**: How far does the payload have to travel?
- **Device**: How fast can the hardware build the payload?
- **Download**: How big is the payload is being sent?
</v-clicks>

<!-- <v-click>

<h3 class="bottom-10" style="position: absolute !important;">
🔥🔥🔥 Hot tip: alliteration > coherence
</h3>

</v-click> -->

---

# With that in mind, we should...

<v-clicks>

- Move things closer to users (like a CDN)
- Do work on servers (like cloud servers/functions)
- Build smaller apps (pfft)

</v-clicks>

---

# But we're often left picking 2 of 3:

1. Fast Device
2. Low Latency
3. Dynamic Data

<div class="grid grid-cols-3 gap-4 mt-12">
<v-clicks>
<div>

## SSR
😀 Device + Data

😟 Latency
</div>
<div>

## CSR + CDN
😀 Latency + Data

😟 Device
</div>
<div>

## SSG + CDN
😀 Device + Latency

😟 Data
</div>
</v-clicks>
</div>

---
layout: statement
---

# But what if...

---
layout: statement
---

# 🐶🎩🧶💉🤖+🏪<br>Dog-hat-knitting robots inside convenience stores 

<img src="/img/edge-compute/mohawk-dog.jpg" class="block m-auto" width="450" alt="cute dog wearing a knitted, New England Patriots hat">

---

# Edge compute

<p>
<v-clicks>
<span>Programmable runtimes (like cloud functions)...</span>
<span>that are globally distributed (within a CDN)...</span>
<span>and can integrate with caches (like SSG).</span>
</v-clicks>
</p>
<p>
<v-clicks>
<span>Dynamic server-side functionality...</span>
<span>that executes as close to users as possible...</span>
<span>and <b>CAN</b> reduce repeat work.</span>
</v-clicks>
</p>

<v-click>
<div class="mt-12">

## Plus:

- Reliable location information
- Access to key-value stores 
</div>
</v-click>

---

# For Users

Dynamic content with...

<v-clicks>

- Less latency (compared to SSR)
- Less data usage (compared to CSR)
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

<h1>The rough edges 😏</h1>

<v-clicks>

- Limited platform features (V8 isolates != Node.js)
- Limited compute resources
- Limited time resources
- Limited networking protocols (HTTP != TCP/IP)
</v-clicks>

---
layout: statement
---

# The big thing no one likes to talk about...

---
layout: statement
---

<span class="text-8xl">🤮</span>

# Accessing data from distributed compute

---
layout: statement
---

# Edge compute isn't<br>always the right choice

💻: client<br>
🤵: origin server<br>
🔪: edge node<br>
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

<br>

---

# There are solutions

<v-clicks>

- Edge Key-Value stores
- Read-replica DB instances
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
-->

</v-click>

---
layout: statement
---

# Maybe not full edge apps
## But there's several **GREAT** use-cases...

---

# Example use cases

- Modify request/response
- Fast static search (auto-complete, store locator)
- Geolocation (language, policies)
- Redirect management ([blog post](https://austingil.com/optimizing-content-migrations-with-edge-compute/))
- Token-based personalization
- A/B testing & Feature flags
- Stateless auth (JSON Web Tokens)
- API proxy / orchestration
- Upstream software patches
- Dynamic content assembly from static/cached templates

---
layout: statement
---

# It gets sweeter

---
layout: statement
---

# C.R.E.A.M.

<v-clicks>
<span>Cache</span>
&nbsp;<span>Rules!</span>
&nbsp;<span>Everyone</span>
&nbsp;<span>Attending</span>
&nbsp;<span>My</span>
<p>(talk is about to have their mind blown)</p>
</v-clicks>

---
layout: statement
---

# Caching: Only Origin Server + Static Response

<img src="/img/edge-compute/cache1.svg">

---
layout: statement
---

# Caching: Only Origin Server + Dynamic Response

<img src="/img/edge-compute/cache2.svg">

---
layout: statement
---

# Caching: Origin Server + CDN

<img src="/img/edge-compute/cache3.svg">

---
layout: statement
---

# Caching: Origin Server + CDN + Edge Compute

<img src="/img/edge-compute/cache4.svg">

---
layout: statement
---

<img src="/img/edge-compute/white-balance.jpg" class="block m-auto" width="400" alt="cute dog wearing a knitted, New England Patriots hat">

# Look to the future

Edge compute will continue to grow and become a major factor in the next phase of web development

---

# Already see adoption by these folks

<div class="grid grid-cols-2">

- [Astro](https://astro.build/)
- [Remix](https://remix.run/)
- [Next.js](https://nextjs.org/)
- [Nuxt.js](https://nuxtjs.org/)
- [11ty](https://www.11ty.dev/docs/plugins/edge/)
<!--  -->
- [Sveltekit](https://kit.svelte.dev/)
- [Fresh](https://fresh.deno.dev/)
- [SolidStart](https://start.solidjs.com/)
- [Qwik City](https://qwik.builder.io/docs/qwikcity/)
- and more

</div>

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

<h4 class="absolute top-32 right-16">How much does 100 milliseconds matter?</h4>

<h4 class="absolute bottom-28 left-48">Is all the effort worth it?</h4>

<h4 class="absolute bottom-40 right-12">Do dogs even like wearing hats?</h4>

---
layout: statement
---

# Does 100ms really matter?

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
layout: statement
---

# Is it worth it?

---

# It depends 😘
<v-clicks>

Building for distributed systems is hard.

Edge compute adds complexity.

Small projects may not benefit from tradeoffs.

The important thing is to understand distributed systems and architecture.

Build applications for **today**, in such a way that can scale tomorrow.

And if tomorrow you tip those scales, give [Akamai EdgeWorkers](https://www.akamai.com/products/serverless-computing-edgeworkers) a try.

</v-clicks> 

---

# Akamai EdgeWorkers

- Largest distributed network (>300k servers, >4k POPs)
- Fine-tuned lifecycle hooks
  - On client request
  - Before origin request
  - On origin response
  - Before client response
- Integrates with CDN's cache
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
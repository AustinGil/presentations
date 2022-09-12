---
theme: default
font:
  sans: 'Manrope'
  display: 'Rock Salt'
lineNumbers: false
layout: image-right
image: /img/edge-compute/austin-gil-bio.png
---

<h1 class="text-4xl mt-10">Hey Im Austin Gil 👋</h1>
<p class="-top-4">@heyAustinGIl</p>

<h4 class="mb-4">Dev Advocate <a href="https://akamai.com">akamai.com</a></h4>
<h4 class="mb-4">OSS Maintainer of <a href="https://vuetensils.austingil.com">Vuetensils</a></h4>
<h4 class="mb-4">Chiweenie enthusiast</h4>

<div class="mt-10">Come talk to me about edge compute, JavaScript, Chiweenies, or whatever :D</div>

---
layout: statement
---

# What the heck is Edge Compute anyway?

(aka "edge functions" or "edge workers")

---

# Plain and simple:

Edge compute is the result of distributing the serverless functions to thousands of locations around the world to handle requests from as close to the user as possible.

The result is programmable/dynamic/customizable responses with the least amount of latency (aka more speed).

<v-click>

## But that's really boring

</v-click>

<!-- That's it. That's the pitch. And if you understand all that, then I have nothing more to add. 
Thank you for coming to my talk.
For the rest of my talk, we'll cover pros and cons as well as driving the idea home with a metaphor.
-->

---
layout: statement
--- 

<img src="/img/edge-compute/puppy-hat.jpg" class="block m-auto" width="300" alt="cute dog wearing a knitted hat">

# Dog hats!!!

(really just an ok analogy)

---

# What is "Compute"?

What: compute = bleeps & bloops -> HTML, JSON, etc.

Where: 

- Traditional Servers
<!-- - Content Delivery Networks -->
- Client-Side Rendering
- Static-Site-Generators
- Cloud functions

---

# Traditional Servers

Machine runs software you choose to execute code you write to return HTML.

<v-clicks>

- Local (machine you own) or "cloud" (machine someone else owns)
- Running 24x7 (ideally)
- You pay even with no traffic
- High traffic could expire resources (crash)
- Scaling up/down requires planning (performance vs cost)
- Distance from users add latency
- You maintain server software & application logic

</v-clicks>

---
layout: statement
--- 

# Traditional Servers

<img src="/img/edge-compute/dog-beret.jpg" class="block m-auto" width="300" alt="Black pug with a knitted red beret to match its red, black, and white stripped shirt.">

## Like commercial workspace 🏭

---

# Client-Side Rendering

JavaScript (or WebAssembly) running in the user's browser generates HTML.

<v-clicks>

- No latency because it's on device
- Can work offline
- Requires more JS for users to download
- Can't keep secrets ("View source")
- Performance greatly impacted by user's device
- Seeing movements away from CSR (SEO, perf, a11y)

</v-clicks>

---
layout: statement
--- 

# Client-Side Rendering

<img src="/img/edge-compute/knitting-supplies.jpg" class="block m-auto" width="300" alt="knitting supplies">

## Like DIY dog-hat kits 🛠
<div>(dog sold separately)</div>

---

# Static-Site-Generators (SSGs)

Generate all pages (HTML, CSS, JavaScript, etc.) ahead of time, into static folders and files.

- Technically still SSR (not client)
- Result is technically similar to hand-coding HTML
- Immediate response times
- Works great with a CDN
- Very fast, cheap, secure, and easy to host
- Can't support dynamic content (without client-side)
- Build times grow with number of pages

---
layout: statement
--- 

# Static-Site-Generators

<img src="/img/edge-compute/dog-hats-5.jpg" class="block m-auto" width="200" alt="Black lab wearing a blue knitted hat with a puff ball on top. He's outside in the fall time.">

## Like pre-made dog hats 🐶🎩

---

# Cloud Functions (aka "lambda", "serverless")

Service providers route requests to the functions you provide.<br>
(They manage machines and servers)

<v-clicks>

- Must follow conventions (naming, files, parameters, returns)
- Your function may run in various machine
- "Stateless" (no shared memory/file system)
- "Infinitely" scalable automatically
- Very easy to provision (teams, migration)
- Only pay for what you use
- Limited resources & languages
- Can also be very far from users
- Only manage code (no hardware or servers)

</v-clicks>

---
layout: statement
--- 

# Cloud Functions

<img src="/img/edge-compute/football-dog.jpg" class="block m-auto" width="300" alt="cute dog wearing a knitted, New England Patriots hat">

## Like robots trained to knit dog-hats 🤖🧶💉🐶🎩

---
layout: statement
--- 

# Horses for courses

---

# What is "Edge"?

What: A network of globally distributed computers capable of handling user requests.

Why: By putting devices as close to users as possible, we can reduce latency, thereby improving performance and user experience.

---

# Content Delivery Network (CDN)

Thousand of globally distributed servers to deliver your static assets (css, js, img, fonts, etc)

<v-clicks>

- Each server has it's own copy of your assets
- Asset served from nearest server to users
- Can greatly reduce latency (distance assets travel)
- Also great for pre-rendered HTML (SSG)

</v-clicks>

---
layout: statement
--- 

# Content Delivery Network

<img src="/img/edge-compute/two-hat-dogs.jpg" class="block m-auto" width="300" alt="two cute dogs wearing a knitted hats">

## Like convenience stores 🏪

---
layout: statement
---

# Now let's talk performance

---

# Users experience performance in 3-D

(what does that even mean!?)

<v-clicks>

- **Distance** request/response must travel (latency)
- **Download** size before code executes
- **Device** hardware capabilities

</v-clicks>

<v-click>

<h3 class="bottom-10" style="position: absolute !important;">
🔥🔥🔥 Hot tip: alliteration > coherence
</h3>

</v-click>

---

# The speed-of-light-problem

Technology will continue to improve, but speed of light will remain the same.

<v-clicks>

<div>
  <p>Edge vs. Origin</p>
  <img src="/img/edge-compute/edge-redirect.svg" class="block m-auto" width="600" alt="cute dog wearing a knitted, New England Patriots hat">
</div>

</v-clicks>

---

# In an ideal 3-D world...

<v-clicks>

- Do things closer to users (like a CDN)
- Do more work on servers (like cloud servers/functions)
- Send smaller assets, pweez 🥺 (it's subjective)

</v-clicks>

<v-click>

# In reality...

CSR is low-latency, but slow.

SSR is fast, but high-latency.

</v-click>

---
layout: statement
---

# Can you guess where we're going...?

---
layout: statement
---

# Edge compute

<img src="/img/edge-compute/mohawk-dog.jpg" class="block m-auto" width="400" alt="cute dog wearing a knitted, New England Patriots hat">

## Like robots trained to knit dog-hats at convenience stores <br> 🤖🧶💉🐶🎩+🏪

---

# Edge compute

<v-clicks>

<p class="inline-block">Programmable runtimes (like cloud functions)...</p>

<p class="inline-block">that are globally distributed (like a CDN).</p>


<p class="inline-block">Dynamic server-side functionality...</p>

<p class="inline-block">that executes as close to users as possible.</p>

Additionally can provide reliable location information 

</v-clicks>

---

# An addition, not a replacement

Where to run compute is difficult<br>
(latency, bundle size, device capabilities, etc).

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

# Benefits - Users

<v-clicks>

- Less latency (compared to servers/cloud functions)
- Less to download (compared to client-side rendering)
- Keeps work off device (batt. & perf.)

</v-clicks>

--- 

# Benefits - Developers

<v-clicks>

- Low barrier for POC
- Consistent execution environment (no x-browser issues)
- Teams own their respective responsibilities
- Location-based logic (no GDPR)
- No servers/infrastructure to manage
- Secrets stay secret (compared to client-side)
- Common programming language (JavaScript)

</v-clicks>

--- 

# Benefits - Website owners

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
- Limited networking protocols (TCP/IP)

</v-clicks>

---

# When it might make sense 🐱‍🏍

<v-clicks>

- Stateless computation
- Doesn't take a long time
- Latency-sensitive
- Hyper-local

</v-clicks>

---

# When it may not make sense 🚩

<v-clicks>

- Requires shared memory or file system
- Requires high computational resources
- Long-running operations
- Sequential/waterfall requests (may add latency)
- Direct DB access

</v-clicks>

---

# Common use cases

<v-clicks>

- Geolocation
- Fast auto-suggest / type-ahead
- Modify request/response
- Cookie-based personalization
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

# Coming to frameworks near you 

- [Astro](https://astro.build/)
- [Remix](https://remix.run/)
- [Next.js](https://nextjs.org/)
- [Nuxt.js](https://nuxtjs.org/)
- [11ty](https://www.11ty.dev/docs/plugins/edge/)
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

<h4 class="absolute -top-20 left-16">It's just about speed?</h4>

<h4 class="absolute -top-32 right-16">How much does 300 milliseconds matter?</h4>

<h4 class="absolute -bottom-28 left-48">Is even it worth it?</h4>

<h4 class="absolute -bottom-40 right-12">Do dogs even like wearing hats?</h4>

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

[Akamai's 2017 Online Retail Performance Report](https://www.akamai.com/newsroom/press-release/akamai-releases-spring-2017-state-of-online-retail-performance-report)

<v-clicks>

For every 1s faster load, Walmart increased sales by 2%<br>
(2021 = $500b x 2% = $10b)

They could hire 133,000 developers and still profit<br>
(2020 average = $75k)

</v-clicks>

---

# Why is it always about money? 😒

Money is easy to quantify, but are there are other reasons to care?

<v-clicks>

Speed and reliability

Importance of access to information

In times of crisis (disease, war, etc)

People are scared

Information is critical

## For some people, not about money at all

</v-clicks>

---
layout: statement
---

# So is it worth it?

<v-click>

# It depends 💩

(but when you need it, give [Akamai EdgeWorkers](https://www.akamai.com/products/serverless-computing-edgeworkers) a try)

</v-click>

---

# EdgeWorkers

- Largest number of locations (over 250,000)
- More customizable lifecycle hooks
  - After client request
  - Before origin request
  - After origin response
  - Before client response
- No per-region/per-server limits (only per-request)
- Run on same servers as cached content
- Protected by industry-leading firewall

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
---

<div class="text-gray-900">

<v-clicks>

# Thanks 😘

<div>

### Info on Akamai's edge:

[akamai.com](https://www.akamai.com/products/serverless-computing-edgeworkers)

[developer.akamai.com](https://developer.akamai.com/akamai-edgeworkers-overview)

[techdocs.akamai.com](https://techdocs.akamai.com/edgeworkers/docs/welcome-to-edgeworkers)

</div>
<div>

### Info on me:

<p><pepicons-internet/> <a href="https://austingil.com">austingil.com</a></p>

<p><logos-twitter/> <a href="https://twitter.com/heyAustinGil">@heyAustinGil</a></p>

<p><logos-twitch/> <a href="https://twitch.tv/heyAustinGil">@heyAustinGil</a></p>

<p><bi-github/> <a href="https://github.com/AustinGil">@AustinGil</a></p>

<p><bi-instagram/> <a href="https://instagram.com/NuggetTheMighty">@NuggetTheMighty</a> (my dog)</p>

</div>

</v-clicks>

</div>

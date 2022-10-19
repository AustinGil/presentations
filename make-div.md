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
<p class="mt-0 !mb-8">austingil.com | @heyAustinGIl</p>

<h4 class="mb-4">Dev Advocate <a href="https://akamai.com">akamai.com</a></h4>
<h4 class="mb-4">OSS Maintainer of <a href="https://vuetensils.austingil.com">Vuetensils</a></h4>
<h4 class="mb-4">Chiweenie enthusiast</h4>

---

# Story time

- Junior developer code changes not showing in the browser.
- I noticed the issue was not the code, but how the tooling worked.
- "How does that div get to the browser"
- "The browser opens up the vue app, the router finds the right component, and loads the .vue component."

Which is kind right, but missing some steps.

---

# But it's not their fault...

---
layout: statement
---

# What does it take <br> to make a \<div\>?

A journey following your code from the editor
through build processes <br> 
into deployment pipelines
out to the public internet <br>
and finally rendered in a user's browser

---

# You may answer

<div class="mt-10 text-10xl font-mono text-center">
  <v-clicks>
    <span>&lt;</span>
    <span>d</span>
    <span>i</span>
    <span>v</span>
    <span>&gt;</span>
  </v-clicks>
</div>

---

# But there's more to it

Before we can dig into that, let's travel back in time to a better day

When you'd play outside, scrape your knee, and your dad would literally rub dirt in it.

You get home and run upstairs.

Sit down at the computer and use your big toe to hit the power button on your GATEWAY 2000 PENTIUM II

As the 64 MB of RAM kick in and the fans start whining, you yell down the stairs

"Get off the phone! I need to use the internet."

Then you get that sweet, sweet sound 

<!-- Give me that sound, concentrated, straight to the vein -->

---

In this beautiful world, you needed Two tools:

FileZilla

Notepad++

There was no version control.

CI/CD? CD was the thing the internet came on.

Deploy previews? We didn't even have staging sites. We just edited code in production. It's called cowboy coding and it was the most alive I've ever felt.

But things have changed...

The internet has changed...

Things have become more complex...

And so we needed more complex tools...

---
layout: statement
---

# What have we done!?!?

---
layout: image
image: /img/make-div/logos.svg
---

---
layout: statement
---

# Alright, let's do this.

---

# What Happens When You Hit Save? <span class="font-mono">✍(▀̿Ĺ̯▀̿ ̿)</span>

File watchers & dev servers!!!!

Modern applications are made up of several small files instead of one massive thing.

These files are called modules that all have to be stitched together by a bundler.

```jsx
import a from './a.js'
import b from './b.js'
import c from './c.js'

export function jackson5() {
  console.log(a, b, c, 'easy as 1, 2, 3')
}
```

(bundlers can also handle CSS and other assets, but that's a talk for another today)

---

# Step 1: Map the Dependency Graph

The first thing a module bundler does is generate a relationship map of all the served files.

This process is called Dependency Resolution.

Now you know in which order to process the application

---

# Just one problem...

<div class="grid grid-cols-2">
<v-clicks>
<div>

### What you see:
- .jsx
- .tsx
- .vue
- .svelte
- .astro
- .webc
</div>
<div>

### What the browser sees:
<div class="mt-10 text-5xl font-mono">¯\_(ツ)_/¯</div>
</div>
</v-clicks>
</div>

---
layout: image
image: /img/make-div/spongebob.jpg
---

<h1 class="text-center"><span class="text-8xl" style="-webkit-text-stroke: 1px black;">Transpilation</span></h1>

---

# Transpilation

What 

Why 

How...

The first step starts with generating tokens from the source code. 

Then, the tokens are transformed into a syntax tree called AST.

---


<div class="grid grid-cols-2 gap-4">
<div>

JS program:
```js
console.log('poop')
```
</div>
<div>

AST out ([shift-js](https://github.com/shift-js/shift-js)):
<div style="font-size: 10px;">

```json {all|2|6-8,16,23|11-14|15|17-22}
{
  "type": "Module",
  "directives": [],
  "items": [
    {
      "type": "ExpressionStatement",
      "expression": {
        "type": "CallExpression",
        "callee": {
          "type": "StaticMemberExpression",
          "object": {
            "type": "IdentifierExpression",
            "name": "console"
          },
          "property": "log"
        },
        "arguments": [
          {
            "type": "LiteralStringExpression",
            "value": "poop"
          }
        ]
      }
    }
  ]
}
```
</div>
</div>
</div>

<div>More languages/transpilers at [astexplorer.net](https://astexplorer.net/)</div>

---

# What can you do with an AST?

Developers can create parsers called "Visitors"

Visitors walk each part of the AST can do something with it. 

Add, remove, transform, pass to another function.

For example, .tsx => .js

---

Bundling
After receiving inputs and traversing its dependencies during the Dependency Resolution phase, a bundler delivers static assets that the browser can successfully process. This output stage is called Packing.

---

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'

ReactDOM.createRoot(document.getElementById('root')).render(
  <div className="App">
    Hello world
  </div>
)
```

143kb - 143,082 characters

---

This assumes client-side JS. What about server side? Or static generators?

If they're based on JS, the process is similar, but with a slightly different build steps. We'll look at that later.

---

Also worth noting that most modern frontend tooling is more than just loading files in your browser.

You need a local web server for your browser to load your website properly. And in addition to that, you probably want a file watcher that will reload the browser automatically any time you make a change.

You young bucks don't know the pain of reloading the website every time you want to see how your changes look.

The reason this matters is because your dev server probably isn't 100% in alignment with your production server.

---

# Deploying

<div class="mt-20 font-mono text-3xl">(╯°□°）╯︵ ┻━┻ ┳━┳ ノ(゜-゜ノ)</div>

---

Once you've tested your code, it's time to ship it. In the old days, we'd just drag that sucker over the FileZilla GUI and drop it on the server. Of course, that's assuming we weren't just live editing the file on the server.

Not anymore. Today, thing look a bit different.

1. Commit changes in Git
2. Push commit to GitHub
3. (...something something something...)
4. Make sure nothings broken in production

What the heck is that octocat up to? Let's find out.

---

Most repository hosts provide some sort of mechanism that can respond to new commits. Today we'll focus on GitHub Actions.

With GitHub Actions, you can create a folder called `/.github/workflows/`. Inside of it you can place a `.yml` file (like `ci.yml`). It may look like this:

---

```yml {all|3|5|7-14|16-20}
jobs:
  deploy:
    runs-on: ubuntu-latest # With all the NPM goodness
    steps:
      - uses: actions/checkout@v2

      - name: Cache node modules
        uses: actions/cache@v2
        with:
          path: '**/node_modules'
          key: ${{ runner.os }}-modules-${{ hashFiles('**/package-lock.json') }}

      - name: Install modules
        run: npm ci

      - name: Build
        run: npm run build

      - name: Deploy
        run: npm run deploy
```

---

1. A machine that lives on GitHub's servers
2. and running Ubuntu software (with NPM installed)
3. is checking out your repo's code
4. installing NPM dependencies
5. Then running the `build` and `deploy` commands from your `package.json` file.

---

# What are those build and deploy commands?

It depends!

- Build production artifacts then send them to your production server.
- Create a docker image using the source code an env variables and send it to a registry.
- Run predefined checks (TypeScript, ESLint, Vitest) before code can be deployed.
- For static sites, this might mean generating tons of HTML pages then pushing them to a CDN like Akamai.

---

# Why does this matter?

Your dev environment (your computer) and your build environment (GitHub's computers) are probably slightly different. Remembering this can avoid some heartache.

Build artifacts are not the same as dev artifacts.

---
layout: statement
---

# It's the final question
(dee doo dee doo)

(dee doo dee doo doo)

---

<div class="grid grid-cols-2">
  <v-clicks>
    <div class="aspect-square	">
      <p class="m-0">How do we get user from this...</p>
      <img class="w-full h-full object-cover" src="/img/make-div/internet1.jpg">
    </div>
    <div class="aspect-square	">
      <p class="m-0">to this?</p>
      <img class="w-full h-full object-cover" src="/img/make-div/internet2.png">
    </div>
  </v-clicks>
</div>

---

Move this to end:
URL -> Browser -> OS -> Wifi -> Router -> Modem -> ISP -> NS -> DNS -> CDN -> IP -> TCP handshake -> TLS handshake -> HTTP request -> Proxy -> web server -> cache -> valid HTTP response -> download html -> download CSS -> download JS -> document.createElement('div')) -> hydration (optional

# Part 1: Networking <span class="font-mono">(👉ﾟヮﾟ)👉   👈(ﾟヮﾟ👈)</span>

User types [austingil.com](https://austingil.com) into their browser
Browser does a DNS lookup involving series of places to look.
* Check browser cache.
* Check local hosts file.
* Check DNS server in the network stack (local router cache or ISP cache).
  * received by a DNS recursive resolver.
  * The resolver then queries a DNS root nameserver (.).
  The root server then responds to the resolver with the address of a Top Level Domain (TLD) DNS server (such as .com or .net), which stores the information for its domains. 
  The resolver then makes a request to the .com TLD.
  The TLD server then responds with the IP address of the domain’s nameserver, example.com.
  Lastly, the recursive resolver sends a query to the domain’s nameserver.
  The IP address for example.com is then returned to the resolver from the nameserver.
  The DNS resolver then responds to the web browser with the IP address of the domain requested initially.


Note that DNS caching occur can occur:
- Browser
- Operating system
- Router
- ISP
- Edge
- Server

---

# Part 2: Connecting <span class="font-mono">💗(¯ з¯) (¯ε ¯)💗</span>


Browser prepares a data packet to be transmitted through either:
    Ethernet -> modem -> ISP
    WiFi -> router -> modem -> ISP
    Cellular data network
    (Packet: a small segment of a larger message. Each packet contains both data and information about that data)
Browser requests a TCP over IP socket stream (handshake)
  * First, the source send an SYN “initial request” packet to the target server
  * server then sends a SYN-ACK packet to agree to the process
  * source sends an ACK packet to the target to confirm the process, after which the message contents can be sent.
pass from your computer, possibly through a local network, and then through a modem
Ping pongs through network nodes until reaching destination server
TLS (SSL) handshake: Your browser also set up encryption between
- Specify which version of TLS (TLS 1.0, 1.2, 1.3, etc.) they will use
- Decide on which cipher suites (see below) they will use
- Authenticate the identity of the server via the server’s public key and the SSL certificate authority’s digital signature
- Generate session keys in order to use symmetric encryption after the handshake is complete

HTTP request: Your browser requested the content that appears on this webpage.
```
GET / HTTP/1.1
Host: austingil.com
Connection: close
[...other headers]
```
Akamai EdgeWorkers Modify the request
Linode server does some work to prepare HTML response
HTTP response: Server sends content (HTML, CSS, and JavaScript) broken up into a series of data packets. Once your device received the packets and verified it had received all of them
```
200 OK
[response headers]
```
Akamai EdgeWorkers Modify the response

Browser parses HTML and the above process is repeated for every resource (image, CSS, favicon.ico, etc) referenced by the HTML page

If the HTML referenced a resource on a different domain than austingil.com, the web browser goes back to the steps involved in resolving the other domain, and follows all steps up to this point for that domain.

For example, if you're using a CDN such as Akamai

---

# Part 3: Rendering 🏗🧱🎨📖
(ﾉ◕ヮ◕)ﾉ*:･ﾟ✧ 📦
(∩^o^)⊃━☆ *:･ﾟ✧ 📦

(。･_･)ノ”【】
ヽ(⌐■_■)ノ♪♬

Critical rendering path
- Construct the DOM Tree (Object representation of HTML)
- Construct the CSSOM Tree (Object representation of DOM styles)
- Run JavaScript
- Create Render Tree (DOM + CSSOM for RENDERED nodes)
- Calculate Styles
- Generate Layout
- Create layers in case of animations
- Paint content as px to respective layer
- Composite (flatten layers onto the screen)

Explore Critical render path in Chrome’s performance panel 

# Caveats

Render blocking resources?
- CSS is render blocking except when it isn't
- JS is a parser blocking except when it isn't

SSR vs Client vs SSG

---

So when you take down production just say, hay man, it's complicated

---

# Resources: 

[Transpilers: How They Work and How To Build Your Own JS Transpiler](https://daily.dev/blog/transpilers-how-they-work) by [Chidume Nnamdi](https://twitter.com/ngArchangel)

[What happens when](https://github.com/alex/what-happens-when) by [Alex Gaynor](https://alexgaynor.net/)

---
layout: image-right
image: /img/edge-compute/austin-gil-bio.png
---

<h1 class="text-4xl mt-10 !mb-0">Hey Im Austin Gil 👋</h1>
<p class="mt-0">austingil.com | @heyAustinGIl</p>

<h4 class="mb-2">Dev Advocate <a href="https://akamai.com">akamai.com</a></h4>
<h4 class="mb-2">OSS Maintainer of <a href="https://vuetensils.austingil.com">Vuetensils</a></h4>
<h4 class="mb-2">Chiweenie enthusiast</h4>

I want to help you build better websites.

Over the last ten years, I’ve built projects for award-winning agencies, innovative tech start-ups, and government organizations.

Today, I create cool stuff for the web and share what I learn through writing, open-source, YouTube and Twitch, The Function Call, speaking and workshops.

Twitter

GitHub

YouTube

Twitch

LinkedIn

<div class="mt-10">Come talk to me about edge compute, JavaScript, Chiweenies, or whatever :D</div>

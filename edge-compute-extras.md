
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

# Requests to a service in same region 🙂

<v-clicks>

<div class="p-4 rounded-md bg-gray-800">

```
💻---------------📡-🛢
```

</div>

vs.

<div class="p-4 rounded-md bg-gray-800">

```
💻-📡---------------🛢
```

</div>

</v-clicks>

---

# Request to service in distant region 😀

<v-clicks>

<div class="p-4 rounded-md bg-gray-800">

```
💻---------------📡---------------🛢
```
</div>

vs.

<div class="p-4 rounded-md bg-gray-800">

```
💻-📡---------------🛢
```

</div>

</v-clicks>

---

<h1>Multiple <b class="text-5xl">concurrent</b> requests 😄</h1>

<v-clicks>

<div class="p-4 rounded-md bg-gray-800">

```
                   ┌----------------🛢
💻----------------📡-🛢
                   └------🛢
```

</div>

vs.

<div class="p-4 rounded-md bg-gray-800">

```
    ┌----------------🛢
💻-📡---🛢
    └------🛢
```

</div>

</v-clicks>

---

<h1>Multiple <b class="text-5xl">sequential</b> requests 😬</h1>

<v-clicks>

<div class="p-4 rounded-md bg-gray-800">

```
💻---------------📡-🛢-📡🛢-📡---------------💻
```

</div>

vs.

<div class="p-4 rounded-md bg-gray-800">

```
💻-📡---------------🛢---------------📡---------------🛢---------------📡-💻
```

</div>

</v-clicks>

---

---
layout: statement
---

# Thanks 😘

<div class="grid grid-cols-2 mt-16">
<div>

### Info on Akamai's edge:

[akamai.com](https://www.akamai.com/products/serverless-computing-edgeworkers)

[developer.akamai.com](https://developer.akamai.com/akamai-edgeworkers-overview)

[techdocs.akamai.com](https://techdocs.akamai.com/edgeworkers/docs/welcome-to-edgeworkers)

</div>
<div>

### Info on me:

<pepicons-internet/> [austingil.com](https://austingil.com)

<logos-twitter/> [@heyAustinGil](https://twitter.com/heyAustinGil)

<logos-twitch/> [@heyAustinGil](https://twitch.tv/heyAustinGil)

<bi-github/> [@AustinGil](https://github.com/AustinGil)

</div>
</div>

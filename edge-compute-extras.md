
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

# The speed-of-light-problem

Technology continues to get faster, but the speed of light remains the same.

<v-clicks>

<div>
  <p>Edge vs. Origin</p>
  <img src="/img/edge-compute/edge-redirect.svg" class="block m-auto" width="600" alt="cute dog wearing a knitted, New England Patriots hat">

  <p>Eventually, the biggest bottleneck is distance</p>
</div>

</v-clicks>

---

# How many locations make it "edge"?

<v-clicks>

2 (You & your friend)

~10 (Netlify/Deno)

~100 (Fastly)

~300 (Cloudflare)

~4,000 (Akamai)

~10,000 (IoT)

</v-clicks>

---
layout: statement
--- 

# Cloud Functions

(aka "lambda", "serverless")

Service providers route requests to the functions you provide.<br>
<!-- (They manage machines and servers) -->

<!--

- Easy to provision
- "Infinitely" scalable
- Pay for use
- Only manage code
- follow conventions
- "Stateless" 
- Limited resources & languages
- far from users

-->

---
layout: statement
--- 

# 🐶🎩🧶💉🤖<br>Dog-hat-knitting robots

<img src="/img/edge-compute/football-dog.jpg" class="block m-auto" width="350" alt="cute dog wearing a knitted, New England Patriots hat">

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

<v-clicks>

Money is easy to quantify, but there are other reasons to care

Speed and reliability

Importance of access to information

In times of crisis (disease, war, etc)

People are scared

Information is critical

## For some people, not about money at all

</v-clicks>

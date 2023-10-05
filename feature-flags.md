---
layout: statement
---

<!-- <div class="grid grid-cols-2 gap-4">
<div class="grid place-content-center"> -->

# Edge Feature Flags:
## Blending Static Cache & Dynamic Compute

<!-- </div>
<div> -->

<!-- <b>Slides:</b> [bit.ly/edge-compute](http://bit.ly/edge-compute)
<img src="/img/edge-compute/qr.png" alt="http://bit.ly/edge-compute" width="400">
</div>
</div> -->

---
layout: statement
---

# What are feature flags?

---
layout: center
---

Tools that allow us to toggle features on/off without deploying new code.

<!-- <img src="/img/feature-flags/ld-rule.png"> -->
<img src="/img/feature-flags/flags.png">

---

# Good for

- Gradual release
- A/B testing
- Test internal features
- Beta testers
- Personalization
- Kill switches (roll back)

---
layout: statement
---

# How do feature flags work?

---
layout: center
---

```js
if (featureFlagIsEnabled("new-ui-flag")) {
  // show new UI
} else {
  // show old UI
}
```

---

# Benefits

<v-clicks>

- Faster Release Cycles
- Reduced Risk
- Improved User Experience
- Greater Flexibility
</v-clicks>

<!-- 
Can roll out features before ready
Able to turn things off
Users can get newer features sooner
Not dependent on code changes
 -->

---
layout: statement
---

# Where do feature flags run?

---

# Client-Side

Frontend contains client-side SDK, which commincates to admin and updates the UI accordingly.

<v-click>
<img src="/img/feature-flags/client.svg" width="600">
</v-click>

---

# Client-Side

<div class="grid grid-cols-2 gap-4">
<div>

## Pros
- Easy to implement
- Update to DOM after initial render
</div>
<v-clicks>
<div>

## Cons
- UI flash after changes
- Render can be delayed until after flags are checked
- Script blockers can prevent loading SDK
</div>
</v-clicks>
</div>

---

# Server-Side

Server pulls feature flag config from admin during request and constructs HTML response dynamically.

<v-click>
<img src="/img/feature-flags/server.svg" width="500">
</v-click>

---

# Server-Side

<div class="grid grid-cols-2 gap-4">
<div>

## Pros
- Improved performance
- No script blocking

</div>
<v-clicks>
<div>

## Cons
- More load on origin server
- Can remove ability to cache
</div>
</v-clicks>
</div>

---

# Edge-Side

CDN node between client and origin server, capable of running dynamic compute and integrating CDN cache.
<v-clicks>

Have access to key-value stores, geolocation, and device information.

<img src="/img/feature-flags/ekv.svg" width="700">
</v-clicks>

---

# Edge-Side

<div class="grid grid-cols-2 gap-4">
<div>

## Pros
- Super low latency
- Reduced origin load
- Geolocation logic
- Dynamic content + Cache

</div>
<v-clicks>
<div>

## Cons
- Limited time & memory resources
- More complex architecture
</div>
</v-clicks>
</div>

---
layout: statement
---

# Generic Example
A/B testing logic with dynamic content assembly

---

# How it might work

User requests a web page

<v-clicks>

Edge node pulls HTML from origin & feature flags from KV store

Possible to cache origin response for future requests

Edge node assembles HTML based on flags & context

Possible to cache Edge responses as well 
</v-clicks>

<!-- ---

# "Possible" to cache...?

Caching strategy depends largely on:
- Is personalization generalized or per unique user?
- Can personalization logic run at the edge or must be origin?
- In other words, it depends -->

---

<div style="overflow: auto; max-block-size: 100%;">

```js
import { HtmlRewritingStream } from 'html-rewriter';
import { httpRequest } from 'http-request';
import { createResponse } from 'create-response';
import { init } from '@launchdarkly/akamai-server-edgekv-sdk';

export async function responseProvider(request) {
  // Instantiate LaunchDarkly client
  const client = init({
    sdkKey: 'client-id',
    namespace: 'namespace-key',
    group: 'group-id'
  });

  // Create context for feature flagging logic
  const context = {
    kind: 'multi',
    location: {
      key: 'context-key',
      country: request.userLocation.country,
    },
  }

  // Check if flag is enabled/disabled
  const showAlternate = 
    await client.variation('flag-key', context, false);

  // Go get original HTML (or template)
  const htmlResponse = await httpRequest("/original.html", {
    headers: { "X-Subrequest": ["true"] }
  });

  const rewriter = new HtmlRewritingStream();

  // If flag is enabled, modify HTML
  if (showAlternate) {
    rewriter.onElement('h1', el => {
      el.replaceWith("<h1>New page title</h1>")
    });
  }

  // Respond with personalized HTML
  return createResponse(
    200,
    {},
    htmlResponse.body.pipeThrough(rewriter)
  );
}
```
</div>

---
layout: statement
---

# Enterprise Example

Incrementally upgrade beta users to Akamai [Image & Video Manager](https://www.akamai.com/products/image-and-video-manager)
<br>
(automatic media optimizer & CDN)

---

# Toolkit

- [Akamai Image & Video Manager](https://www.akamai.com/products/image-and-video-manager): Feature to toggle
- [Akamai User-defined variables](https://techdocs.akamai.com/property-mgr/docs/user-defined-vars): To implement toggle logic
- [Akamai EdgeWorkers](https://www.akamai.com/products/serverless-computing-edgeworkers): Dynamic runtime where checks happen
- [Akamai EdgeKV](https://www.akamai.com/products/edgekv): Distributed storage where config is saved
- [LaunchDarkly Akamai integration](https://docs.launchdarkly.com/integrations/akamai): Connector for LaunchDarkly and Akamai
- [LaunchDarkly Context Attributes](https://docs.launchdarkly.com/home/contexts/attributes): For applying toggle logic

---

# The Recipe

<v-clicks>

- Create a user-defined variable in Akamai dashboard to use in feature flagging logic & cache key
- Create a flag rule in LaunchDarkly dashboard (synced to EdgeKV)
- EdgeWorker uses LaunchDarkly SDK to read EdgeKV and LaunchDarkly Context Attributes to analyze feature flag status
- Pre-cache (`onClientRequest`) modify request to origin, update user-defined variable & set cache key based on feature flags
- Post-cache (`responseProvider`) resolve with assembled HTML
- Use Akamai Property Manager match conditions to enable Image Manager and apply caching logic
</v-clicks>

---

# The Result 

<v-clicks>

Safe & incremental roll-out of enhanced media delivery via Image Manager.

Reduced data costs for users and bandwidth costs for image delivery.

Caching also reduces server workload, costs, and improves reliability.

And users have better performance from optimized images, caching, and CDN.

Also, features can easily be turned on/off or rolled back without code changes.

Engineers have less work, less stress, less responsibility, and faster releases.
</v-clicks>

---
layout: statement
---

# 🤟<span style="font-size: 100px">😝</span><span style="display: inline-block; scale: -1 1;">🤟</span>

---
src: outro.md
---

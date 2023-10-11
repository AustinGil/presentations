---
layout: statement
---

<!-- <div class="grid grid-cols-2 gap-4">
<div class="grid place-content-center"> -->

# Supercharge User Experience 
## with Akamai EdgeWorkers & LaunchDarkly
<!-- ## Blending Static Cache & Dynamic Compute -->

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

Tools that allow us to toggle specific features on/off for targeted customer segments without deploying new code.

<!-- <img src="/img/feature-flags/ld-rule.png"> -->
<img src="/img/feature-flags/flags.png">

---

# Good for

- Gradual release
- A/B testing
- Beta testers
- Personalization
- Preview internal features
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

- Faster release cycles
- Reduced risk
- Improved user experience
- Greater flexibility
- Decouple deployments & features

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

<img src="/img/feature-flags/client.svg" width="600">

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

<img src="/img/feature-flags/server.svg" width="500">

---

# Server-Side

<div class="grid grid-cols-2 gap-4">
<div>

## Pros
- No UI content flash
- Less data for client to download
- Less work for client device
- No script blocking

</div>
<v-clicks>
<div>

## Cons
- More load on origin server
- Can remove option to cache results
</div>
</v-clicks>
</div>

---

# Edge-Side

CDN node between client and origin server, capable of running dynamic compute and integrating CDN cache.

Have access to key-value stores, geolocation, and device information.

<img src="/img/feature-flags/ekv.svg" width="700">

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
Dynamic content assembly

---

# How it might work

- User requests a web page
<v-clicks>

- Edge node pulls HTML from origin & feature flags from KV store
- Possible to cache origin response for future requests
- Edge node assembles HTML based on flags & context
- Possible to cache Edge responses as well 
</v-clicks>

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

<!-- ---

# Caveat on caching

Although you **can** cache responses from subrequests (eg. origin) and edge responses, strategy depends largely on:
- Is personalization generalized or per unique user?
- Can personalization logic run at the edge or must be origin?

<v-click>

In other words, it depends
</v-click> -->

---
layout: statement
---

# Mad Science Example

Upgrade beta users to improved features

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
- EdgeWorker uses LaunchDarkly SDK to determine feature flag status based on EdgeKV config Context Attributes (beta user cookie)
- Pre-cache (`onClientRequest`) update user-defined variable based on flag status & use as cache key for origin request
- Post-cache (`responseProvider`) resolve with assembled HTML
- Akamai Property Manager match conditions enable Image Manager when cache key is present, even when cached
</v-clicks>

---

# The Result 

<v-clicks>

Safe & incremental roll-out of enhanced media delivery via Image Manager.

Reduced data costs for users and bandwidth costs for image delivery.

Caching reduces server workload, costs, and improves reliability.

Cache + optimized images + CDN greatly improves performance.

Also, features can easily be turned on/off or rolled back without code changes.

Engineers have less work, less stress, less responsibility, and faster releases.
</v-clicks>

---
layout: statement
---

# Cache + Compute

# 🤟<span style="font-size: 100px">😝</span><span style="display: inline-block; scale: -1 1;">🤟</span>

---
src: outro.md
---

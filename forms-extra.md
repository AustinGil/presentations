
---

In 2013, GOV.UK found that 1.1% of users were not running JavaScript.
(https://gds.blog.gov.uk/2013/10/21/how-many-people-are-missing-out-on-javascript-enhancement/)

<v-clicks>

> "Surprisingly, the proportion of people that have explicitly disabled JavaScript or use a browser that doesn't support JavaScript, only makes up a small slice of people that don't run JavaScript."

Only 0.2% had JavaScript explicitly disabled.


</v-clicks>


---
layout: statement
---

# Pop Quiz:
## Using only HTML, how many different ways can you submit a form?

---

```html
<form>
  Assume everything lives in here
</form>
```

<v-clicks>

```html
<button>Submit</button>
```
```html
<input type="submit">
```
```html
<input type="image">
```
```html
<input>
(user presses "enter")
```
</v-clicks>

---

```html
<form id="formid">
</form>
But things can also live out here
```

```html
<button form="formid">Submit</button>
```
```html
<input form="formid" type="submit">
```
```html
<input form="formid" type="image">
```
```html
<input form="formid">
(user presses "enter")
```



---
layout: statement
---

# Pop Quiz:
## How many pseudo-classes deal exclusively (or closely) with forms?

---

<div class="grid grid-cols-3">
<v-clicks>

- `:autofill`
- `:checked`
- `:default`
- `:disabled`
- `:enabled`
- `:focus`
<!--  -->
- `:focus-visible`
- `:focus-within`
- `:hover`
- `:in-range`
- `:indeterminate`
- `:invalid`
<!--  -->
- `:optional`
- `:out-of-range`
- `:placeholder-shown`
- `:read-only`
- `:read-write`
- `:required`
</v-clicks>
</div>

---
layout: statement
---

# Pop Quiz:
## What is the 'content-type' for each request?

---

<div class="flex gap-6 text-xs">
  <span>1. "text/plain"</span>
  <span>2. "application/x-www-form-urlencoded"</span>
  <span>3. "multipart/form-data"</span>
  <span>4. "application/json"</span>
  <span>5. undefined</span>
</div>
<div class="grid grid-cols-2 gap-4">
<div>

<div v-click="1">

```html
<form>
```
<!-- 2 -->
</div>

<div v-click="3">

```html
<form method="post">
```
<!-- 2 -->
</div>

<div v-click="5">

```js
fetch('/', { 
  method: 'post',
  body: new URLSearchParams()  
})
```
<!-- 2 -->
</div>

<div v-click="7">

```js
fetch('/', { 
  method: 'post',
  body: new FormData()  
})
```
<!-- 3 -->
</div>
</div>
<div>

<div v-click="2">

```js
fetch('/')
```
<!-- 5 -->
</div>

<div v-click="4">

```js
fetch('/', { 
  method: 'post'
})
```
<!-- 5 -->
</div>

<div v-click="6">

```js
fetch('/', { 
  method: 'post',
  body: JSON.stringify()  
})
```
<!-- 5 -->
</div>

<div v-click="8" class="text-sm">

```html
<form method="post" enctype="multipart/form-data">
```
<!-- 3 -->
</div>
</div>
</div>

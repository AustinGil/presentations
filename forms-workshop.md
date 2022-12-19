---
src: intro.md
---
---

# Super Powered Forms With JS

<div class="grid grid-cols-2 text-left">
<div>

Miro board: **bit.ly/js-forms**

Wifi: // TODO

Prerequisites:
* Git
* Node/NPM
* Editor

</div>
<img src="img/forms-workshop/qr-miro.png">
</div>

---

# Ordinary vs Super powers

- Ordinary powers
  - Semantic (conveys meaning)
  - Accessible (works with AT & keyboards)
  - Performance baseline (nothing **unnecessary**)
  - Secure
- Super powers
  - Don't break existing features
  - Enhance existing features (a11y)
  - Add new features
  - Progressive Enhancement

---

# The Problem with JS

- More work for developers
- More data for users
- Worse for performance
- Double-edge for a11y
- Doesn't work for everyone

---

# Click Example

<!-- ```
<div id="click-me">Click me!</div>

const clickMe = document.querySelector('#click-me');
function onClick() {
  alert('Thanks!');
}
clickMe?.addEventListener('click', onClick);
``` -->

---

Some things we don't need JS for
- Sending data over HTTP
- Some inline validation hints
- Submitting forms on 'enter'
- Nested data structures

A search input

<!-- ```
<div class="control__input">
  <input id="search" placeholder="Search" />
  <span>🔎</span>
</div>

const input = document.querySelector('#search');
input?.addEventListener('keydown', (event) => {
  if (event.key !== 'Enter') return;
  fetch('/', {
    method: 'post',
    body: JSON.stringify({ search: event.target.value }),
  });
});
``` -->

---

# But JS can make things better

Progressive Enhancement

- Why build for no-js
- How to detect no-js
- Before we enhance, take stock of what we have

<!-- <html lang="en" class="no-js">
  <head>
    other stuff
		<script type="module">
      document.documentElement.classList.remove('no-js');
      document.documentElement.classList.add('js');
		</script>
  </head>
  <body>...</body>
</html> -->

---

# The Perfect Input

<!-- <div class="control">
  <label for="email">Email</label>
  <div class="control__input">
    <input id="email" type="email" name="email" required />
  </div>
</div> -->

---

# Non-JS Examples

<!-- 
["Elon Musk","Jeff Bezos","Bernard Arnault","Gautam Adani","Bill Gates","Warren Buffett","Larry Page","Sergey Brin","Larry Ellison","Steve Ballmer"]

<label for="ice-cream-choice">Choose a flavor:</label>
<input list="ice-cream-flavors" id="ice-cream-choice" name="ice-cream-choice">

<datalist id="ice-cream-flavors">
  <option value="Chocolate">
  <option value="Coconut">
  <option value="Mint">
  <option value="Strawberry">
  <option value="Vanilla">
</datalist>



[{
  id: 'html',
  name: 'HTML',
  description: 'The bones of any good website',
},
{
  id: 'css',
  name: 'CSS',
  description: 'Styles to make your mamma proud',
},
{
  id: 'js',
  name: 'JavaScript',
  description: 'Fancy-pantsy movements and stuff',
}] -->

<!-- <fieldset>
  <legend>What's your fave frontend language</legend>
  <div class="cards">
    <div class="card">
      <img src="/img/html.svg" alt="HTML logo" width="48" height="48" />
      <label for="html">HTML</label>
      <input
        id="html"
        type="radio"
        name="fe-fave"
        aria-describedby="html-description"
        class="visually-hidden"
      />
      <p id="html-description">The bones of any good website</p>
    </div>
    <div class="card">
      <img src="/img/css.svg" alt="CSS logo" width="48" height="48" />
      <label for="css">CSS</label>
      <input
        id="css"
        type="radio"
        name="fe-fave"
        aria-describedby="css-description"
        class="visually-hidden"
      />
      <p id="css-description">Styles to make your mamma proud</p>
    </div>
    <div class="card">
      <img
        src="/img/javascript.svg"
        alt="JavaScript logo"
        width="48"
        height="48"
      />
      <label for="js">JavaScript</label>
      <input
        id="js"
        type="radio"
        name="fe-fave"
        aria-describedby="js-description"
        class="visually-hidden"
      />
      <p id="js-description">Fancy-pantsy movements and stuff</p>
    </div>
  </div>
</fieldset> 

<fieldset>
  <legend>Favorite Starter Pokemon</legend>

  <div>
    <input
      id="bulbasaur"
      type="radio"
      name="selection"
      value="bulbasaur"
    />
    <label for="bulbasaur">Bulbasaur</label>
  </div>

  <div>
    <input
      id="charmander"
      type="radio"
      name="selection"
      value="charmander"
    />
    <label for="charmander">Charmader</label>
  </div>

  <div>
    <input
      id="squirtle"
      type="radio"
      name="selection"
      value="squirtle"
    />
    <label for="squirtle">Squirtle</label>
  </div>

  <div class="pokemon pokemon--bulbasaur">
    <img
      src="img/bulbasaur.png"
      width="300"
      height="300"
      alt="Bulbasaur"
    />
    <p>
      Bulbasaur can be seen napping in bright sunlight. There is a seed on
      its back. By soaking up the sun's rays, the seed grows progressively
      larger.
    </p>
    <ul>
      <li>Height: 2' 04"</li>
      <li>Weight: 15.2 lbs</li>
      <li>Type: Grass/Poison</li>
      <li>Weaknesses: Fire, Psychic, Flying, Ice</li>
    </ul>
  </div>

  <div class="pokemon pokemon--charmander">
    <img
      src="img/charmander.png"
      width="300"
      height="300"
      alt="Charmander"
    />
    <p>
      The flame that burns at the tip of its tail is an indication of its
      emotions. The flame wavers when Charmander is enjoying itself. If
      the Pokémon becomes enraged, the flame burns fiercely.
    </p>
    <ul>
      <li>Height:1' 08"</li>
      <li>Weight: 19.8 lbs</li>
      <li>Type: Water</li>
      <li>Weaknesses: Grass, Electric</li>
    </ul>
  </div>

  <div class="pokemon pokemon--squirtle">
    <img src="img/squirtle.png" width="300" height="300" alt="Squirtle" />
    <p>
      Squirtle's shell is not merely used for protection. The shell's
      rounded shape and the grooves on its surface help minimize
      resistance in water, enabling this Pokémon to swim at high speeds.
    </p>
    <ul>
      <li>Height: 2' 00"</li>
      <li>Weight: 18.7 lbs</li>
      <li>Type: Fire</li>
      <li>Weaknesses: Water, Ground, Rock</li>
    </ul>
  </div>
</fieldset>
-->

---

# Enhance form

<!-- const form = document.querySelector('form');
if (!form) return;
enhanceForm(form); -->

Existing Form powers
- Inherent submit
- HTTP requests (method & action)
- Triggers HTML input validation
  - Prevents form submission
  - Focuses first invalid input
  - Communicates error message

---

# Enhance submission with fetch

<!-- 
/** @type {HTMLFormElement} */
const url = new URL(form.action || window.location.href);
const formData = new FormData(form);
const searchParameters = new URLSearchParams(formData);
const options = {
  method: form.method
};

if (options.method.toUpperCase() === 'GET') {
  url.search = searchParameters;
} else {
  options.body = searchParameters;
}

event.preventDefault();
const request = fetch(url, options);
return request;
-->

---

# Trigger Validation

<!-- 
form.noValidate = true;
form.addEventListener('submit', (event) => {
  if (!form.checkValidity()) {
    form.reportValidity()
    event.preventDefault();
    return;
  }
-->

---

# Custom input validation UI

<!-- 
if (!form.checkValidity()) {
  for (const input of form.querySelectorAll(FORM_CONTROLS)) {
    input.dataset.validateme = true;
    validateInput(input);
  }
-->
---

## Check validity state

<!-- 
const { validity } = input;
if (!validity.valid) {
-->
---

## Toggle aria-invalid

<!-- 
if (!validity.valid) {
input.setAttribute('aria-invalid', true);
-->
---

## Get or generate input ID

<!-- 
const inputId = input.id || Math.random().toString(36).slice(2);
input.id = inputId;
-->
---

## Create .control__errors div with errors

<!-- 
const errorsId = `${inputId}-input-errors`;
if (!validity.valid) {
    const errors = [];
    const errorContainer = document.createElement('div');
    errorContainer.id = errorsId;
    errorContainer.classList.add('control__errors');

    if (validity.valueMissing) {
      errors.push(`Field is required.`);
    }

    errorContainer.innerText = errors.join(' ');

    input.parentElement.before(errorContainer);
}
-->
---

## Connect with aria-describedby

<!-- 
input.setAttribute('aria-describedby', errorsId);
-->
---

## Account for pre-existing aria-describedby excluding

<!-- 
let descriptors = input.getAttribute('aria-describedby');
descriptors = descriptors ? descriptors.split(' ') : [];
descriptors = descriptors.filter((s) => s !== errorsId);

if (!validity.valid) {
  descriptors.push(errorsId);
}

if (descriptors.length > 0) {
  input.setAttribute('aria-describedby', descriptors.join(' '));
}
-->
---

## Challenge: Custom error messages via config

---

## Challenge: Custom error messages via data-attrs

---

# Focus/scroll management (w/o aria live regions)

<!--
if (!form.checkValidity()) {
  // ...
  form.querySelector(':invalid:not(fieldset)').focus();
}
-->

---

# Now we can start improving!!!

---

# Validate inputs on input/blur

<!-- 
/** @param {Event} event */
function validateOnEvent(event) {
  const input = event.currentTarget;
  if (event.type === 'blur') {
    input.dataset.validateme = true;
  }
  if (!input.dataset.validateme) return;
  validateInput(input);
}
/** @param {HTMLInputElement} input */
export function enhanceInput(input) {
  input.addEventListener('input', validateOnEvent);
  input.addEventListener('blur', validateOnEvent);
}
-->

---

Enhanced fetch

<!-- 

/**
 * @param {Parameters<typeof fetch>[0]} url
 * @param {Parameters<typeof fetch>[1] & {
 * data?: string | object,
 * json?: string | object,
 * }} [init]
 */
export function enhancedFetch(url, init = {}) {
   -->

---

# Put data on response object

<!--
let response = await fetch(url, init);

// Grab response.json for JSON, otherwise use response.text
let bodyType = 'text';
if (response.headers.get('content-type')?.includes('application/json')) {
  bodyType = 'json';
}

// Append data property to response object with results
const data = await response[bodyType]();
response.data = data;

if (init.modifyResponse) {
  response = init.modifyResponse(response);
}

resolve(response);
--->

---

# Errors on bad requests

<!-- 
class FetchError extends Error {
  /**
   * @param {ConstructorParameters<ErrorConstructor>[0]} message
   * @param {ConstructorParameters<ErrorConstructor>[1]} options
   */
  constructor(message, options) {
    super(message, options);
    this.name = 'FetchError';
  }
}

// In the event of bad requests
if (!response.ok) {
    // throw custom error with access to response object
    throw new FetchError(`${response.status} ${response.statusText}`, {
      cause: response,
    });
}
  -->

---

# Retries

<!-- 
let response = await fetch()
if (!response.ok) {
const retry = init.retry;
// Check if we need to retry request more times
if (retry) {
  init.retryWait = init.retryWait || 500;
  await new Promise((r) => setTimeout(r, init.retryWait));

  const exponential =
    init.retryExponential != undefined ? init.retryExponential : true;
  init.retryWait = exponential ? init.retryWait * 2 : init.retryWait;
  return resolve(
    enhancedFetch(url, {
      ...init,
      retry: retry - 1,
    })
  );
} else {
}
 -->

---

# Timeout

<!-- 
const promise = new LazyPromise(async (resolve, reject) => {
  try {
    if (init.timeout != undefined) {
      setTimeout(() => {
        reject(new FetchError('HTTP request exceeded timeout limit.'));
      }, init.timeout);
    }
-->
---

# Abortable

<!-- 
enhancedFetch() {
  const controller = new AbortController();
  if (!init.signal) {
    init.signal = controller.signal;
  }

  const promise = new Promise() {
    try {

    } catch (error) {
      if (error.name !== 'AbortError') {
        reject(error);
      }
    }
  }
}
-->

---

# Lazy execution (optional)
<!-- 
class LazyPromise extends Promise {
  /** @param {ConstructorParameters<PromiseConstructor>[0]} fn */
  constructor(fn) {
    // eslint-disable-next-line prettier/prettier
    super(() => { });
    if (typeof fn !== 'function') {
      throw new TypeError(`Promise resolver is not a function`);
    }
    this._fn = fn;
  }
  then() {
    this.promise = this.promise || new Promise(this._fn);
    return this.promise.then.apply(this.promise, arguments);
  }
}
-->
---

# Challenge: How to handle 3XX status codes?

---

# Challenge: Resumable on network reconnect (navigator.
onLine)

---

# Prevent page navigation

<!-- 
export function enhanceForm(form, options = {}) {
  if (options.preventNav) {
    form.dataset.preventnav = true;
    form.addEventListener('change', () => {
      form.dataset.haschanges = true;
    });
    form.addEventListener('submit', () => {
      form.dataset.haschanges = false;
    });
    window.addEventListener('beforeunload', onBeforeUnload);
  }

/**
 * @param {BeforeUnloadEvent} event
 */
function onBeforeUnload(event) {
  const changedForm = document.querySelector(
    'form[data-preventnav][data-haschanges'
  );
  if (!changedForm) return;
  event.preventDefault();
  // Chrome requires returnValue to be set.
  event.returnValue = '';
}
-->

---

# Prevent spamming submit button

(bonus: onInput debouce)

<!-- 
if (form._pendingRequest) {
  form._pendingRequest?.abort && form._pendingRequest.abort();
}
const request = enhancedFetch(url, options);
form._pendingRequest = request;
request.then(() => {
  delete form._pendingRequest;
});
-->

---

# Store changes in sessionStorage

<!-- 
const form = document.querySelector('form')

form.addEventListener('change', event => {
  const formData = new FormData(form);
  sessionStorage.setItem('your-identifier', JSON.stringify(formData));
});

const previouslySavedData = sessionStorage.getItem('form-data');

if (previouslySavedData) {
  const inputValues = JSON.parse(savedData);

  for(const [name, value] of Object.entries(inputValues)) {
    const input = form.querySelector(`input[name=${name}]`);
    switch(input.type) {
      case 'checkbox':
        input.checked = !!value;
        break;
      // other input type logic
      default:
        input.value = value;
    }
  }
}

form.addEventListener('submit', () => {
  sessionStorage.removeItem('form-data');
});
-->

# Convert to Vue handlers (avoid memory leaks)

---

# Create components

---

# Enhance server 

Receive body 
Receive files
Validate
Respond with HTML/JSON

---

# Nested data structures

<!-- 
  if (headers['content-type']?.includes('application/x-www-form-urlencoded')) {
    body = qs.parse(body);
  }
 -->

---

Pop Quiz

What is the 'content-type' for each request

1. "text/plain"
2. "application/x-www-form-urlencoded"
3. "multipart/form-data"
4. "application/json"
5. undefined

```html
<form>
```
2
```js
fetch('/')
```
5
```html
<form method="post">
```
2
```js
fetch('/', { 
  method: 'post'
})
```
5
```js
fetch('/', { 
  method: 'post'
  body: JSON.stringify()  
})
```
5
```js
fetch('/', { 
  method: 'post'
  body: new URLSearchParams()  
})
```
2
```js
fetch('/', { 
  method: 'post'
  body: new FormData()  
})
```
3
```html
<form method="post" enctype="multipart/form-data">
```
3

---

# Account for file inputs (multipart/form-data)

---

# Improve with CSS

---

- Going beyond
  - CSRF
  https://owasp.org/www-community/attacks/csrf
  https://typeofnan.dev/using-cookie-based-csrf-tokens-for-your-single-page-application/
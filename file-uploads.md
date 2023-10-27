---
layout: statement
---

# Full Spectrum <br>File Uploads

---

# Background: HTTP

The Language of the Web

All website communicate over HTTP (Hypertext Transfer Protocol)

HTTP functions as a request–response protocol in the client–server model.

<div class="grid grid-cols-2">
<div>

Client:
Browser
</div>
<div>

Server:
Node.js
</div> 
</div> 

---

# Make an HTTP Request

Required: Method (`GET`, `POST`, `PUT`, etc), Path, HTTP version
Optional: Headers, Body

```http {none|1|2-5|7}
GET / HTTP/1.1
Host: austingil.com
Accept: */*
Accept-Encoding: gzip
Connection: keep-alive

Say hi to your dog for me
```

---

# Sending Data With HTTP

Must include a `POST` method and the body.

Should also include the `Conten-Type`, and the `Content-Length`.

```http {none|1|6}
POST / HTTP/1.1
Host: austingil.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

field1=value1&field2=value2
```

---
layout: statement
---

# You Don't Need To Know That

---

# Browsers are HTTP clients

Make HTTP requests on our behalf.

Convert HTTP responses into websites.

Provide tools to send files via HTML or JavaScript.

---
layout: statement
---

# Upload Files with HTML

---

# Steps

1. Construct an HTTP request
2. Set method to `POST`
2. Get access to files
3. Attach file in request body

---

# Construct an HTTP request

```html
<form>
  <button>Upload</button>
</form>
```

---

# Send Data As Request Body

```html {1}
<form method="post">
  <button>Upload</button>
</form>
```

---

# Access Files

```html {3}
<form method="post">
  File:
  <input type="file" />
  <button>Upload</button>
</form>
```

---

# Make it accessible

```html {2,3}
<form method="post">
  <label for="file">File:</label>
  <input type="file" id="file" />
  <button>Upload</button>
</form>
```

---

# Include File Contents

```html {1,3}
<form method="post" enctype="multipart/form-data">
  <label for="file">File:</label>
  <input type="file" id="file" name="file" />
  <button>Upload</button>
</form>
```

---

# Behold The HTML File Upload Form

```html
<form method="post" enctype="multipart/form-data">
  <label for="file">File:</label>
  <input type="file" id="file" name="file" />
  <button>Upload</button>
</form>
```

---

# Translated To HTTP

```http {all|2-3|6,11|7-8|10}
POST / HTTP/1.1
Content-Type: multipart/form-data;boundary=
  ---------------------------735323031399963166993862150
Content-Length: 17

-----------------------------735323031399963166993862150
Content-Disposition: form-data; name="file"; filename="nugget.txt"
Content-Type: text/plain

Who's a good boy?
-----------------------------735323031399963166993862150--
```

---

# We're Uploading Files

- Fast
- Secure (for users)
- Accessible
<!--  -->
- Browser reloads every time

---
layout: statement
---

# Improve UX with JavaScript

---

# Requirements

- Still need access to the file system
- Still need an HTTP request (`fetch` or `XMLHttpRequest`)
- Still need a POST method
- Still need to put the file in the body

---

# This Works

<div class="mb-8">
```html
<input type="file" onchange="handleFileChange">
```
</div>

```js
function handleFileChange(event) {
  fetch('/some-url', {
    method: 'post',
    body: event.target.files[0],
  });
}
```

---
layout: statement
---

# Don't do that

---
layout: statement
---

# Continue using `<form>`

---

```html {1,4,5,7}
<form
  method="post"
  enctype="multipart/form-data"
  onsumit="handleSubmit"
>
  <!-- content -->
</form>
```

```js
async function handleSubmit(event) {
  const request = submitFormWithJs(event.currentTarget)
  event.preventDefault()
  const response = await request
}
```

---

```js {all|2|3|4|6-8|10-15|12|14|16-18|20}
function submitFormWithJs(form) {
  const url = new URL(form.action);
  const formData = new FormData(form);
  const searchParams = new URLSearchParams(formData);

  const fetchOptions = {
    method: form.method,
  };

  if (form.method.toLowerCase() === 'post') {
    if (form.enctype === 'multipart/form-data') {
      fetchOptions.body = formData;
    } else {
      fetchOptions.body = searchParams;
    }
  } else {
    url.search = searchParams;
  }

  return fetch(url, fetchOptions);
}
```

---

# Why?

<v-clicks>

- Works on slow connections
- Works if JS fails
- Maintains existing browser features
- Maintains accessibility
- Makes your live easier
- Allows for declarative HTML logic
- Allows for reusable logic
</v-clicks>

---

# Next problem

What if we're not the ones sending files?

---
layout: statement
---

# Receive Files in Node.js

---

# First, some vocab

- chunks:
- streams:
- buffers: A buffer is a storage in physical memory used to temporarily store data while it is being transferred from one place to another. - MDN

---

# Parsing data in Node

```js
function processNodeRequest(request) {
  request.on("data", (data) => {
    console.log(data);
  }
}
```
<img src="/img/file-uploads/buffers.png">

---

```js {all|3|4-6|7-10}
function processNodeRequest(request) {
  return new Promise((resolve, reject) => {
    const chunks = [];
    request.on('data', (data) => {
      chunks.push(data);
    });
    request.on('end', () => {
      const payload = Buffer.concat(chunks).toString()
      resolve(payload);
    });
    request.on('error', reject);
  });
}
```

---

# Wanna see a cute pic of Nugget?

<img src="/img/file-uploads/file-contents.png" v-click>

---

# A Plain Text File

```http {all|2-3,10}
POST / HTTP/1.1
Content-Type: multipart/form-data;boundary=
  ---------------------------WebKitFormBoundary4Ay52hDeKB5x2vXP
Content-Length: 19

Content-Disposition: form-data; name="file"; filename="dear-nugget.txt"
Content-Type: text/plain

I love you, Nugget!
------WebKitFormBoundary4Ay52hDeKB5x2vXP--
```

---

# We've made a terrible mistake...

- Whole file contents in memory?
- How do we manage form boundaries?

---

# Use a library (formidable)

```js {3-10}
function processNodeRequest(request) {
  return new Promise((resolve, reject) => {
    const form = formidable({ multiples: true })
    form.parse(request, (error, fields, files) => {
      if (error) {
        reject(error);
        return;
      }
      resolve({ ...fields, ...files });
    });
  });
}
```

---

```js
{
  file: PersistentFile {
    lastModifiedDate: 2023-03-21T22:57:42.332Z,
    filepath: '/tmp/d53a9fd346fcc1122e6746600',
    newFilename: 'd53a9fd346fcc1122e6746600',
    originalFilename: 'dear-nugget.txt',
    mimetype: 'text/plain',
    hashAlgorithm: false,
    size: 19,
    hash: null,
  }
}
```

---

# Lessons

- Don't store files in memory, use streams
- Don't reinvent the wheel
- Abstractions are good
- But keep access to underlying runtime

---
layout: statement
---

# Reduce Costs with Object Storage

---

# What is Object Storage

Object Storage is a single, central place to store and access all of your uploads.

It's designed to be highly available, easily scalable, and super cost-effective.

Ideally should be S3 compatible.

---

# What is S3?

S3 stands for "Simple Storage Service", and it’s an Object Storage product originally developed at AWS.

Along with their product, AWS came up with a standard communication protocol for interacting with their Object Storage solution.

`npm install @aws-sdk/client-s3 @aws-sdk/lib-storage`

---

# Make it work with formidable

```js {all|3,6-8}
const form = formidable({
  multiples: true,
  fileWriteStreamHandler: fileWriteStreamHandler,
});

function fileWriteStreamHandler(file) {
  // TODO
}
```

---

# This gets a lil convoluted

- formidable needs a writable stream to send chunks to.
- S3 upload body needs to be a readable stream.
- So we use a passthrough stream.
- We need to store the file's location in the metadata.
- We need to track all upload requests in case of multiples.

---

```js {all|4|5-14|12|15-17|1,18}
const s3Uploads = [];

function fileWriteStreamHandler(file) {
  const body = new stream.PassThrough();
  const upload = new Upload({
    client: s3Client,
    params: {
      Bucket: 'austins-bucket',
      Key: `files/${file.newFilename}`,
      ContentType: file.mimetype,
      ACL: 'public-read',
      Body: body,
    },
  });
  const uploadRequest = upload.done().then((response) => {
    file.location = response.Location;
  });
  s3Uploads.push(uploadRequest);
  return body;
}
```

---

```js {8,11}
file: {
  lastModifiedDate: null,
  filepath: '/tmp/93374f13c6cab7a01f7cb5100',
  newFilename: '93374f13c6cab7a01f7cb5100',
  originalFilename: 'nugget.jpg',
  mimetype: 'image/jpeg',
  hashAlgorithm: false,
  createFileWriteStream: [Function: fileWriteStreamHandler],
  size: 82298,
  hash: null,
  location: 'https://austins-bucket.us-southeast-1.linodeobjects.com/files/nugget.jpg',
}
```

---

# The MAJOR Caveat

You pay twice for the bandwidth.

Once on the way in (to your server).

Once on the way out (to S3).

---

# Alternative Solution: Signed URLs

- Frontend request asks for a signed URL.
- Backend gets it from Object Storage provider.
- Backend gives signed URL to the frontend.
- Frontend uploads directly to provider.

<div class="mt-8 grid grid-cols-2">
<div>

## Pros
- Moves work off your servers.
- Moves bandwidth off your server.
- Simpler architecture.
</div>
<div>

## Cons
- Harder to coordinate database.
- Less control (malware protection, optimized images).
- No progressive enhancement.
</div>
</div>

---

# Review

Object Storage can be 10 cheaper than server upgrades

You can use either upload streams or signed URLs

But they still get saved in one region, which is slow

---
layout: statement
---

# Speed Up Delivery

---

# Content Delivery Networks (CDNs)

---

<img src="/img/file-uploads/webpagetest1.png" width="600" class="block m-auto">

---

<img src="/img/file-uploads/webpagetest2.png" width="600" class="block m-auto">

---

# CDNs are nothing new but...

- The compounding returns of CDNs
- Where to host your CDN domain? subpath vs subdomain cookies, etc

---
layout: statement
---

# Security and <br>Malware Protection

---

OWASP.org. Conveniently, they have a File Upload Cheat Sheet,

- Extension Validation
- Filename Sanitization
- Upload and Download Limits
- File Storage Location
- Content-Type Validation
- File Content Validation
- Malware Scanning Architecture
- Block Malware at the Edge

---

# Blog & Video Series

https://austingil.com/uploading-files-with-html/
---
layout: statement
---

<div class="grid grid-cols-2 gap-4">
<div class="grid place-content-center">

# Full Spectrum <br>File Uploads

</div>
<div class="text-center">

[uploads-talk.austingil.com](https://uploads-talk.austingil.com/)

<img src="/img/file-uploads/qr.png" alt="" class="w-full">
</div>
</div>

---

# HTTP: The language of the internet

Protocol for hypermedia communication between distributed computers.

Required: Method, Path, HTTP version<br>
Optional: Headers, Body

```http
GET / HTTP/1.1
Host: austingil.com
Accept: */*
Accept-Encoding: gzip
Connection: keep-alive

Say hi to your dog for me
```

---
layout: statement
---

# We don't need to worry about that

---

# Browsers are HTTP clients

- Make HTTP requests on our behalf.
- Convert HTTP responses into websites.
- Provide APIs to send files via HTML or JavaScript.

---
layout: statement
---

# Upload Files with HTML

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

# Actually Send File Contents

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

```http {all|1|2-3,6,11|7-10}
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

<div class="mt-20 grid grid-cols-2">
<div>

## Yes!
- Users can select a file
- Browser is sending the file
</div>
<div v-click>

## But...
- Browser reloads every time
</div>
</div>

---
layout: statement
---

# Improve UX with JavaScript

---

# Same same but different

- Still need access to the file system
- Still need an HTTP request (`fetch` or `XMLHttpRequest`)
- Still need a `POST` method
- Still need to put the file in the body

---

# Technically, this works

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

# ...But don't do that

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

<div class="text-16px">

```js {all|2|3|4-6|8|9,10|12|14-16|17}
function submitFormWithJs(form) {
  const url = new URL(form.action);
  const formData = new FormData(form);
  const fetchOptions = {
    method: form.method,
  };

  if (form.method.toLowerCase() === 'post') {
    if (form.enctype === 'multipart/form-data') {
      fetchOptions.body = formData; // multipart/form-data
    } else {
      fetchOptions.body = new URLSearchParams(formData); // application/x-www-form-urlencoded
    }
  } else {
    url.search = new URLSearchParams(formData);
  }
  return fetch(url, fetchOptions);
}
```
</div>

---

# Why?

<div class="grid grid-cols-2 gap-4 mt-20">
<div v-click>

## Progressive Enhancement

- Works with or without JS
- Maintains browser features
- Maintains accessibility
</div>
<div v-click>

## Simplicity

- Reusable function
- Declarative logic from HTML
- More resilient & maintainable
</div>
</div>

---

# We've improved the UX

<div class="mt-20 grid grid-cols-2">
<div>

## Yes!
- User doesn't wait for page refresh
- Progressive enhancement
</div>
<div v-click>

## But...
- What do we do with the sent files?
</div>
</div>

---
layout: statement
---

# Receive Files in Node.js

---

<!-- # First, some vocab

<v-clicks>

- "chunks": bits of data sent over HTTP as part of a larger stream.
- "streams": a sequence of data chunks made available to process over time.
- "buffers": a place in memory for temporarily storing data.
</v-clicks> -->

# Node is event-driven

During HTTP requests, each chunk triggers the `request.on()` method.

```js
function processNodeRequest(request) {
  request.on("data", (data) => {
    console.log(data);
  }
}
```
<img v-click src="/img/file-uploads/buffers.png">

---

```js {all|2,12|3|4-6|7-10}
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

```js
console.log(await processNodeRequest(request))
```
<v-click>

```http {all|2-3,6,11|7-10}
POST / HTTP/1.1
Content-Type: multipart/form-data;boundary=
  ---------------------------WebKitFormBoundary4Ay52hDeKB5x2vXP
Content-Length: 19

------WebKitFormBoundary4Ay52hDeKB5x2vXP--
Content-Disposition: form-data; name="file"; filename="dear-nugget.txt"
Content-Type: text/plain

I love you, Nugget!
------WebKitFormBoundary4Ay52hDeKB5x2vXP--
```
</v-click>

---

# We've made a terrible mistake...

<v-clicks>

- Whole file contents in memory?
- Manually parsing HTTP requests?
</v-clicks>

---

# Use streaming library (formidable)

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

```js {all|4}
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

# We're Saving Files to Disk

<div class="mt-20 grid grid-cols-2">
<div>

## Yes!
- Access to file metadata
- Using streams instead of memory
- Not reinventing the wheel
</div>
<div v-click>

## But...
- What happens when space runs out
- What if we have a distributed system
</div>
</div>

---
layout: statement
---

# Saving Files to<br>Object Storage

---

# What is Object Storage?

A single, central place to store and access all of your uploads.

<v-clicks>

Highly available, easily scalable, and often 10x cheaper than server space.

Ideally should be S3-compatible.
</v-clicks>

---

# What is S3?

S3 ("Simple Storage Service") is AWS's object storage product.

<v-clicks>

Has become a standard communication protocol for Object Storage solutions.

Libraries: `@aws-sdk/client-s3 @aws-sdk/lib-storage`
</v-clicks>

---

# Getting files to Object Storage

1. Signed URLs
2. Stream through proxy

---

# Signed URLs

<v-clicks>

- Frontend request asks for a signed URL.
- Backend gets it from Object Storage provider.
- Backend gives signed URL to the frontend.
- Frontend uploads directly to provider.
</v-clicks>

<div class="mt-8 grid grid-cols-2">
<v-clicks>
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
</v-clicks>
</div>

---

# Streaming through formidable

```js
const form = formidable({
  multiples: true,
  fileWriteStreamHandler: fileWriteStreamHandler,
});

function fileWriteStreamHandler(file) {
  // TODO
}
```

---

# Getting into the weeds

<v-clicks>

- formidable wants to write chunks to a stream.
- S3 upload wants to read chunks from a stream.
- We need to store the file's location somewhere.
- We need to track pending upload requests.
</v-clicks>

---

<div class="text-17px">

```js {all|4-13|3,11,18|14-16|1,17}
const s3Uploads = [];
function fileWriteStreamHandler(file) {
  const fileStream = new PassThrough(); // from 'stream' module
  const upload = new Upload({
    client: s3Client,
    params: {
      Bucket: 'austins-bucket',
      Key: `files/${file.newFilename}`,
      ContentType: file.mimetype,
      ACL: 'public-read',
      Body: fileStream,
    },
  });
  const uploadRequest = upload.done().then((response) => {
    file.location = response.Location;
  });
  s3Uploads.push(uploadRequest);
  return fileStream;
}
```
</div>

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
layout: statement
---

# The MAJOR Caveat

## 🚨 Double the bandwidth 🚨

In to your server and out to Object Storage.

---

# We're Using Object Storage

<div class="mt-20 grid grid-cols-2">
<div>

## Yes!
- Get more space for much less cost
- All files stored in single place
- Separation between server and files 
</div>
<div v-click>

## But...
- Object Storage exists in one region
- Could cause latency issues
</div>
</div>

---
layout: statement
---

# Put Files Closer

---

# Content Delivery Networks (CDNs)

Globally distributed network of servers that caches content close to users.

<v-clicks>

Initial requests pass through CDN node, pull content from origin server, and cache it. Subsequent requests get cached content.

Faster deliver of static assets (HTML, CSS, JavaScript, images, fonts, etc.)
</v-clicks>

---

<img src="/img/file-uploads/webpagetest1.png" width="600" class="block m-auto">
<div class="absolute right-45 bottom-38 w-20 h-20 border border-8 border-red-600"></div>

---

<img src="/img/file-uploads/webpagetest2.png" width="600" class="block m-auto">
<div class="absolute right-48 bottom-10 w-50 h-45 border border-8 border-red-600"></div>

---

# Things to consider...

<v-clicks>

- Multiplied impact for render blocking resources
- Caching strategy is really hard to get right
  - Duration
  - Invalidation
  - URL (subpath vs subdomain)
- CDNs have learned some new tricks 
  - DDoS protection
  - Automatic media optimization
  - Edge compute
</v-clicks>

<!-- cookies, caching, route rules -->

---

# We're Delivering Files Quickly

<div class="mt-20 grid grid-cols-2">
<div>

## Yes!
- Faster responses
- Less bandwidth
- Higher availability
</div>
<div v-click>

## But...
- What about malware
</div>
</div>

---
layout: statement
---

# Secure our application

---

# [OWASP.org File Upload Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html)

- Extension Validation
- Filename Sanitization
- Upload and Download Limits
- File Storage Location
- Content-Type Validation
- File Content Validation
- Malware Scanning Architecture
- Block Malware at the Edge

---

# Filename Sanitization

Prevent long file names or dangerous characters for OS.  

<v-click>

```js
const form = formidable({
  // other config options
  filename(file) {
    // return some random string
  },
});
```

(formidable does this by default)
</v-click>

---

# Upload and Download Limits

Reasonable file size limits can avoid storage and bandwidth issues/costs.

<v-click>

```js
const form = formidable({
  // other config options
  maxFileSize: 1024 * 1024 * 10, // 10mb
});
```

(formidable defaults to 200mb max file size)
</v-click>
---

# File Storage Location

Quarantine files away from running application and with limited permissions.

<v-click>

```js
const form = formidable({
  // other config options
  uploadDir: './uploads',
});
```

(formidable defaults to OS's temp folder)
</v-click>

---

# Extension Validation **

Only allow files with allowed extensions into your system.

<v-click>

```js
const form = formidable({
  // other config options
  filter(file) {
    const allowed = /\.(jpe?g|png|gif|avif|webp|svg)$/i;
    return allowed.test(file.originalFilename)
  }
});
```
</v-click>

---

# Content-Type Validation **

Only allow files with allowed [MIME-types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types) into your system.

<v-click>

```js
const form = formidable({
  // other config options
  filter(file) {
    const mimetype = file.mimetype ?? '';
    return Boolean(mimetype.includes('image'));
  }
});
```

(formidable bases `file.mimetype` from file extension)
</v-click>

---

# File Content Validation **

Scanning files for malware is one of the more important security steps you can take when accepting file uploads.

<v-clicks>

- The file must already be on our server to scan.
- Scans take too long for the reqquest/response cycle.
- This requires a whole new architecture.
</v-clicks>

---

# Malware Scanning Architecture

<v-clicks>

1. Store files in quatantine
2. Save file metadata and scan status in DB
3. Respond to user with upload pending info
4. Allow users to view file metadata
5. Background process scans pending files
6. Clean files get updated in DB
7. Decided on strategy for dirty files
</v-clicks>

---
layout: image
image: /img/file-uploads/malware.svg
---

---
layout: statement
---

# Block Malware at the Edge

---

# App & API Protector

Akamai customers have access to [App & API Protector](https://www.akamai.com/products/app-and-api-protector) which provides:
- IP/Geo Firewall
- Denial of Service (DoS) protection
- Web Application Firewall (WAF)
- **Malware Protection**

---

<img src="/img/file-uploads/malware-dash.png">

<!-- I configured the Malware Protection policy to just deny any request containing malware or a content type mismatch. -->

---

<img src="/img/file-uploads/malware-example.png">
<!-- Logic I didn't actually write into my application. -->

---

# App & API Protector Review

<div class="grid grid-cols-2 mt-20">
<div>

## Pros
- Convenient to set up and modify
- No changes to application
- Files scanned at the edge
- Does its job well
- I don't have to maintain it
</div>
<div>
<v-click>

## Cons
- Limited max file size
</v-click>
</div>
</div>

---

# We've secured our files

<div class="mt-20 grid grid-cols-2">
<div>

## Yes!
- Files are quarantined
- Users still have fast responses
- Scans happen in the background
</div>
<div v-click>

## But...
- You weren't paying attention
</div>
</div>

---
layout: statement
---

# Blog & Video Series

[austingil.com/uploading-files-with-html](https://austingil.com/uploading-files-with-html/)

---
src: outro.md
---
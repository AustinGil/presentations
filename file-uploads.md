---
layout: statement
---

# Full Spectrum <br>File Uploads

---

# Start With Communication: HTTP

The Language of the Web

The vast majority of website communicate over HTTP (Hypertext Transfer Protocol)

HTTP functions as a request–response protocol in the client–server model. A web browser, for example, may be the client whereas a process, named web server, running on a computer hosting one or more websites may be the server. 

---

HTTP version type
a URL
an HTTP method
HTTP request headers
Optional HTTP body.

```http
GET / HTTP/1.1
Host: www.example.com
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
```

```http
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 155
ETag: "3f80f-1b6-3e1cb03b"
Connection: close

<html>
  <head>
    <title>An Example Page</title>
  </head>
  <body>
    <p>Hello World, this is a very simple HTML document.</p>
  </body>
</html>
```

---

```http
POST / HTTP/1.1
[[ Less interesting headers ... ]]
Content-Type: multipart/form-data; boundary=---------------------------735323031399963166993862150
Content-Length: 834

-----------------------------735323031399963166993862150
Content-Disposition: form-data; name="text1"

text default
-----------------------------735323031399963166993862150
Content-Disposition: form-data; name="text2"

aωb
-----------------------------735323031399963166993862150
Content-Disposition: form-data; name="file1"; filename="a.txt"
Content-Type: text/plain

Content of a.txt.

-----------------------------735323031399963166993862150
Content-Disposition: form-data; name="file2"; filename="a.html"
Content-Type: text/html

<!DOCTYPE html><title>Content of a.html.</title>

-----------------------------735323031399963166993862150
Content-Disposition: form-data; name="file3"; filename="binary"
Content-Type: application/octet-stream

aωb
-----------------------------735323031399963166993862150--
```

---

# You Don't Need to know HTTP

On your computer is an application called a browser.

It makes HTTP requests on your behalf, and renders HTML into nice pictures and text and cat memes and flamewars.

---

How to Upload Files with HTML
- Access Files
 - `<input type="file" />`
```html
<form>
  <label for="file">File</label>
  <input id="file" type="file" />
  <button>Upload</button>
</form>
```

- Include a Request Body
  - method="post"
- Set the Content-Type
  - `application/x-www-form-urlencoded`
  - `multipart/form-data`
  - enctype="multipart/form-data"

How to Upload Files with JavaScript
- Still need to do the same steps
  - Access to the file system using a file type input.
  - Construct an HTTP request using the Fetch (or XMLHttpRequest) API.
  - Set the request method to POST.
  - Include the file in the request body.
  - Set the HTTP Content-Type header to multipart/form-data.
- Still good to use forms
  - Progressive enhancement
  - `FormData`
- event handler
  - prevent default
  - Fetch API
- Request body

```js
/** @param {SubmitEvent} event */
function handleSubmit(event) {
  const url = new URL(form.action);
  const formData = new FormData(form);

  /** @type {Parameters<fetch>[1]} */
  const fetchOptions = {
    method: form.method,
    body: formData,
  };

  event.preventDefault();

  return fetch(url, fetchOptions);
}
```
- Make it reusable
```js
/** @param {Event} event */
function handleSubmit(event) {
  /** @type {HTMLFormElement} */
  const form = event.currentTarget;
  const url = new URL(form.action);
  const formData = new FormData(form);
  const searchParams = new URLSearchParams(formData);

  /** @type {Parameters<fetch>[1]} */
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

  event.preventDefault();

  return fetch(url, fetchOptions);
}
```

Handling File Uploads on the Backend in Node.js
- Dealing with multipart/form-data in Node.js
  - “chunks”
  - “stream“
```js
  /**
 * @param {import('http').IncomingMessage} req
 */
function doSomethingWithNodeRequest(req) {
  req.on("data", (data) => {
    console.log(data);
  }
}
```
  - “buffers”:
  <img src="/img/file-uploads/buffers.png">
  > A buffer is a storage in physical memory used to temporarily store data while it is being transferred from one place to another.
  MDN

```js
/**
 * @param {import('http').IncomingMessage} req
 */
function doSomethingWithNodeRequest(req) {
  return new Promise((resolve, reject) => {
    /** @type {any[]} */
    const chunks = [];
    req.on('data', (data) => {
      chunks.push(data);
    });
    req.on('end', () => {
      const payload = Buffer.concat(chunks).toString()
      resolve(payload);
    });
    req.on('error', reject);
  });
}
```
<img src="/img/file-uploads/file-contents.png">

If I upload a more basic example, like a .txt file with some plain text in it, the body might look like this:

Content-Disposition: form-data; name="file"; filename="dear-nugget.txt"
Content-Type: text/plain

I love you!
------WebKitFormBoundary4Ay52hDeKB5x2vXP--
- Use a library to stream data onto disk: formidable
```js
/**
 * @param {import('http').IncomingMessage} req
 */
function doSomethingWithNodeRequest(req) {
  return new Promise((resolve, reject) => {
    /** @see https://github.com/node-formidable/formidable/ */
    const form = formidable({ multiples: true })
    form.parse(req, (error, fields, files) => {
      if (error) {
        reject(error);
        return;
      }
      resolve({ ...fields, ...files });
    });
  });
}
```

Stream File Uploads to S3 Object Storage and Reduce Costs
- What is Object Storage
  - It’s a single, central place to store and access all of your uploads.
  - It’s designed to be highly available, easily scalable, and super cost-effective.
- What is S3
  - `npm install @aws-sdk/client-s3 @aws-sdk/lib-storage`
- Modify formidable
```js
/** @param {import('formidable').File} file */
function fileWriteStreamHandler(file) {
  // TODO
}
const form = formidable({
  multiples: true,
  fileWriteStreamHandler: fileWriteStreamHandler,
});
```
- Caveats
  - signed URLs
  Here’s how the flow generally works:

Frontend makes a request to the backend for a signed URL.
Backend makes an authenticated request to the Object Storage provider for a signed URL with a given expiry.
Object Storage provider provides a signed URL to the backend.
Backend returns the signed URL to the frontend.
Frontend uploads the file directly to Object Storage thanks to the signed URL.
Optional: Frontend may make another request to the Backend if you need to update a database that the upload completed.
This flow requires a little more choreography than Frontend -> Backend -> Object Storage, but it has some benefits.

It moves work off your servers, which can reduce load and improve performance.
It moves the file upload bandwidth off your server. If you pay for ingress and have several large file uploads all the time, this could add up.
It also comes with its own costs.

You have much less control over what users can upload. This might include malware.
If you need to perform functions on the files like optimizing, you can’t do that with signed URLs.
The complex flow makes it much harder to build an upload flow with progressive enhancement in mind.


CDNs: Speed Up Performance by Reducing Latency
- What is a CDN?
<img src="/img/file-uploads/webpagetest1.png">
<img src="/img/file-uploads/webpagetest2.png">

- The compounding returns of CDNs
- Where to host your CDN domain? subpath vs subdomain cookies, etc


File Upload Security and Malware Protection
-  OWASP.org. Conveniently, they have a File Upload Cheat Sheet,
  - Extension Validation
  - Filename Sanitization
  - Upload and Download Limits
  - File Storage Location
  - Content-Type Validation
  - File Content Validation
  - Malware Scanning Architecture
  - Block Malware at the Edge
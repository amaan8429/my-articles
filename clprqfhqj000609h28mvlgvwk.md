---
title: "Understanding CORS Errors and How to Address Them"
datePublished: Tue Dec 05 2023 02:39:44 GMT+0000 (Coordinated Universal Time)
cuid: clprqfhqj000609h28mvlgvwk
slug: understanding-cors-errors-and-how-to-address-them
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701743837289/b91667ac-902d-4809-9f90-1e1ca380942e.webp
tags: express, programming-blogs, javascript, html5, cors, cors-errors

---

### What is CORS ?

CORS, or Cross-Origin Resource Sharing, stands for the policy that controls how web pages can request resources from a different domain. Let's break it down with an example involving two companies, Company A and Company B, each with their own frontend and back-end.

**Company A:**

* Frontend A
    
* Backend A
    

**Company B:**

* Frontend B
    
* Backend B
    

Imagine Company A wants to get data from Company B's backend. If Company A tries to make requests directly to Company B's backend, CORS steps in. CORS prevents requests from the frontend of Company A to the backend of Company B.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701743348731/763474a7-85d6-43fa-84cf-8a7498cc487b.png align="center")

### How to fix CORS ?

Now that we understand CORS, let's see how to fix CORS issues on our websites. Suppose we have an **Express Server** running and a frontend in `index.html` for that backend.

```javascript
const express = require("express");
const app = express();
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```

When we deploy index.html, how does the backend know to allow requests from index.html without causing a CORS error? There are two ways to solve this problem:

**Method 1: Serving the Frontend from the Backend** In this method, both the backend and frontend are hosted on the same port. Basically, the frontend and backend connect, allowing the backend to let the frontend fetch data.

**This is how you do it in Express :-**

* you tell your backend to serve the `index.html` file from the backend
    

```javascript
app.get("/", (req, res) => {
  res.sendFile(path.join(__dirname, "index.html"));
});
```

Make sure you '`path`' in your code on the top

```javascript
const path = require("path");
```

* Your entire code might look like this in method 1
    

```javascript
const express = require("express");
const app = express();
const port = 3000;
const path = require("path");

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.get("/", (req, res) => {
  res.sendFile(path.join(__dirname, "index.html"));
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```

**Method 2: Using the CORS Package** In this method, you install a package called "cors" on your backend. This tells the backend to allow requests from any frontend targeting that specific backend.

**This is how is it is implemented in Express:-**

* First install the package for "`cors`"
    

```bash
npm install cors
```

* Now require that package in your backend code
    

```javascript
const express = require('express');
const app = express();
const cors = require('cors');

app.use(cors());
```

* Your entire code might look like this in method 2
    

```javascript
const express = require("express");
const app = express();
const port = 3000;
const cors = require('cors');

app.use(cors());


app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```

While Method 2 may seem simple, it's not commonly used in real-life applications for security reasons.
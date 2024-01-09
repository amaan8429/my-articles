---
title: "fetch API vs Axios"
datePublished: Tue Jan 09 2024 18:56:23 GMT+0000 (Coordinated Universal Time)
cuid: clr6pqawz000408i6chq077ew
slug: fetch-api-vs-axios
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704826525237/7668065b-0414-430d-984f-20caedd908f2.png
tags: javascript, axios, fetch-api

---

I've been using `fetch` since I began learning web development, but I recently switched to `Axios`. I've been curious about the differences between the two, so I did some research and found some significant distinctions. Honestly, you don't necessarily need to know these differences to use them, but it's still interesting and smart to learn about them.

### Introduction :

`fetch` **and** `axios` **are both JavaScript libraries used for making HTTP requests in web applications.**

### Installation Steps:

### **Fetch**

`fetch` is a native browser API, and you don't need to install it separately. It is available in modern browsers by default.

1. **For Browser:**
    
    * No installation is required as `fetch` is a native API in modern browsers.
        
2. **For Node.js:**
    
    * Install `node-fetch` using npm :
        
        ```bash
        npm install node-fetch
        ```
        
    * In your Node.js script, use it like this:
        
        ```javascript
        const fetch = require('node-fetch');
        ```
        

### **Axios**

Axios is a third-party library, and you need to install it separately:

1. **For Browser or Node.js:**
    
    * Install `axios` using npm :
        
        ```bash
        npm install axios
        ```
        
2. **Usage:**
    
    * In your JavaScript code, you can use `axios` as follows:
        
        ```javascript
        // CommonJS
        const axios = require('axios');
        
        // ES6 Modules
        import axios from 'axios';
        ```
        

### **Let's Discuss the Differences Now:**

1. `fetch` is a native API available in modern browsers. When we say it's **native**, it means that the browser environment itself has built-in support for the `fetch` API. Developers can use it without having to include additional libraries or scripts. It's a standard part of the environment. `fetch` is now a standard part of the Web Platform API, which modern browsers aim to support.
    
    Axios on the other hand is a popular third-party HTTP client library. **It does not come natively and adds dependency to your project.**
    
2. **Promise Handling:**
    
    `fetch`: `fetch` uses Promises for handling asynchronous operations. This means you can use `.then()` and `.catch()` to handle the success or failure of the request.
    
    `axios`: Axios also uses Promises and provides a clean and consistent API. It allows you to use `.then()` and `.catch()` as well, but it also supports the async/await syntax, making the code more readable and concise.
    
3. **Syntax:**
    
    **Syntax for** `fetch`
    
    ```javascript
    //FETCH
    async function fetchData() {
      try {
        const response = await fetch('https:/localhost:3000/data');
        const data = await response.json();
        console.log(data);
      } catch (error) {
        console.error(error);
      }
    }
    // Call the async function
    fetchData();
    ```
    
    **Syntax of** `Axios`
    
    ```javascript
    //AXIOS
    async function fetchData() {
      try {
        const response = await axios.get('https://localhost:3000/data');    
        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    }
    // Call the async function
    fetchData();
    ```
    
    * `fetch`: `fetch` has a basic API, and if you need to transform the request or response, you need to use additional functions like `JSON.stringify()` and `response.json()` manually.
        
    * `axios`: Axios provides built-in support for request and response transformation. You can easily send JSON data in the request body or automatically parse JSON responses without additional manual steps.
        
4. **Browser Compatibility:**
    
    `fetch`: `fetch` is built into modern browsers but may require a polyfill for older browsers.
    
    `axios`: Axios is a standalone library that works consistently across different browsers, including older ones.
    

1. **Various features of Axios make it famous, some of them are:**
    
    * **Automatic JSON Parsing**: Automatically parses JSON data from responses.
        
    * **Transforms**: Allows data to be transformed before it's sent or after it's received.
        
    * **Cancellable Requests**: Supports request cancellation using the CancelToken feature.
        
    
    **Features: Some advanced features (like request timeout, and request cancellation) are not natively supported or require additional work.**
    

That's a quick overview of the difference between fetch and Axios. I hope it was informative.
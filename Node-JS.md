<h1 align="center">🚀 Node JS</h1>

## 📚 Table of Contents

1. [Introduction](#1-introduction)  
2. [Node.js Architecture](#2-nodejs-architecture)  
3. [Node.js Modules](#3-nodejs-modules)  
4. [NPM (Node Package Manager)](#4-npm-node-package-manager)  
5. [Core Node.js APIs](#5-core-nodejs-apis)
6. [Asynchronous Programming](#6-asynchronous-programming)  
8. [Express.js Framework](#expressjs-framework)  
9. [RESTful APIs](#restful-apis)  
10. [Authentication & Authorization](#authentication--authorization)  
11. [Database Integration](#database-integration)  
12. [Error Handling & Debugging](#error-handling--debugging)  
13. [Node.js with Middleware & Libraries](#nodejs-with-middleware--libraries)  
14. [Streams & Buffers](#streams--buffers)  
15. [Event-Driven Programming](#event-driven-programming)  
16. [Scaling & Performance](#scaling--performance)  
17. [Testing](#testing)  
18. [Deployment](#deployment)  
19. [Security Best Practices](#security-best-practices)

## 1. Introduction

### 🧠 What is Node.js?
Node.js is an **open-source, cross-platform JavaScript runtime environment** that allows  to run JavaScript **outside the browser**, mainly on the **server side**.  
It built on  **Google Chrome V8 engine** to execute code at lightning speed and provides an single-thread, non-blocking event-driven architecture .

### ⚡ Why Node.js? (Advantages over Traditional Backend Tech)
- **Single Language:** Use JavaScript for both frontend and backend.  
- **High Performance:** Built on V8 engine boosts execution speed.
- **REST SAME AS FEATURE**

### 🌟 Features of Node.js

| **Feature** | **Description** |
|--------------|-----------------|
| **Single Threaded** | Uses an event loop to handle multiple concurrent requests efficiently without creating new threads for each. |
| **Asynchronous & Non-Blocking I/O** | Handles multiple operations(file read,db query) without waiting for any to finish by using callbacks, promises, or async/await. |
| **Event-Driven** | Uses an event loop that listens for events and executes corresponding callbacks. |
| **Rich npm Library** | Provides access to over a million reusable open-source packages. |
| **Cross-Platform Support** | Compatible with major operating systems including Windows, macOS, and Linux. |
| **Community Support** | Backed by a large and active open-source community contributing to continuous improvement. |

### 🌍 Where Node.js is Used (Real-World Use Cases)

| **Use Case** | **Description / Examples** |
|---------------|-----------------------------|
| **Real-time Applications** | Ideal for chat apps, collaboration tools, and gaming servers (e.g., Socket.io, Slack). |
| **Streaming Services** | Used by platforms like Netflix, YouTube, and Twitch for seamless video/audio streaming. |
| **API Development** | Commonly used for building RESTful and GraphQL APIs due to its lightweight and fast nature. |
| **Microservices Architecture** | Perfect for developing modular, scalable microservices-based backends. |
| **IoT Applications** | Handles multiple device connections efficiently using event-driven architecture. |
| **Serverless Computing** | Widely supported in cloud platforms like AWS Lambda and Azure Functions. |

---

## 2. Node.js Architecture

Node.js follows an **single thread, event-driven, non-blocking architecture** that allows it to handle thousands of concurrent connections efficiently — all within a **single thread** without creating new thread for each request.  
It is built on the **Google Chrome V8  Engine** and uses **libuv** to manage asynchronous operations like file system access, networking, and more.

<p align="center">
  <img src="https://d11qzsb0ksp6iz.cloudfront.net/assets/b2c610ff35_img-nodejs-architecture0.webp" width="600px"/>
</p>

### 🧩 Core Components

| Component | Description |
|------------|-------------|
| **V8  Engine** | Executes JavaScript code outside the browser by compiling it into machine code. |
| **Event Loop** | Continuously checks the call stack and event queues to process callbacks asynchronously. |
| **Call Stack** | Executes synchronous code in a single thread. |
| **Event Queue (Callback Queue)** | Stores callbacks of completed asynchronous operations waiting for execution. |
| **Microtask Queue** | Executes promises and `process.nextTick()` before the next event loop tick. |
| **libuv (Thread Pool)** | Handles heavy I/O tasks (file system, DNS, compression) in background threads. |
| **Non-Blocking I/O** | Allows multiple operations to run concurrently without blocking the main thread. |

### ⚙️ Workflow

1. **Client Request:** A user or system sends a request to the Node.js server.  
2. **Call Stack Execution:** Synchronous tasks are executed immediately.  
3. **Async Task Delegation:** Asynchronous operations (like DB queries, file reads) are sent to **libuv thread pool**.  
4. **Event Loop Monitoring:** The event loop checks if the call stack is empty.  
5. **Callback Handling:** Completed async operations push their callbacks into the **event queue**.  
6. **Execution:** Event loop picks callbacks from the queue and executes them on the stack.  
7. **Response Sent:** The result is sent back to the client without blocking other requests.

> 🔁 This event-driven cycle enables Node.js to achieve **high concurrency and scalability** with a **single thread**.

---
## 3. Node.js Modules

### 🧠 What are Modules?
Modules in Node.js are **reusable blocks of code** that encapsulate specific functionality and can be imported or exported across files.  
They help organize code, improve maintainability, and promote reusability.

> 🧩 Every file in Node.js is treated as a separate **module**.

### 🔀 CommonJS vs ES Modules

| Feature | CommonJS (CJS) | ES Modules (ESM) |
|----------|----------------|------------------|
| **Syntax** | `require()` and `module.exports` | `import` and `export` |
| **Default Type** | Used by Node.js by default (till v12) | Supported natively in newer Node.js versions |
| **Loading Type** | Synchronous | Asynchronous |
| **File Extension** | `.js` | `.mjs` or `"type": "module"` in package.json |
| **Example** | `const fs = require('fs')` | `import fs from 'fs'` |

> 🧠 **Tip:** Use **CommonJS** for traditional Node.js apps, and **ESM** for modern projects or frontend-backend shared codebases.

### ⚙️ Built-in Modules

| Module | Description |
|---------|-------------|
| **fs** | File System – read/write files (`fs.readFile`, `fs.writeFile`). |
| **http** | Creates web servers and handles HTTP requests/responses. |
| **path** | Handles file and directory paths (`path.join`, `path.resolve`). |
| **os** | Provides system-related info (CPU, memory, OS type). |
| **events** | Enables event-driven programming (`EventEmitter`). |
| **util** | Contains utility functions (e.g., `util.promisify`). |
| **stream** | Handles streaming data efficiently (read/write streams). |
| **crypto** | Provides cryptographic functionality (hashing, encryption). |

> ✅ No need to install these — they come **preloaded** with Node.js.

### 🧩 Creating Your Own Module
You can create a custom module by exporting functions, objects, or variables and importing them in other files.

**Example:**
```js
// math.js
function add(a, b) {
  return a + b;
}
module.exports = add;

// app.js
const add = require('./math');
console.log(add(5, 3)); // Output: 8
```
---

## 4. NPM (Node Package Manager)

### 🧠 What is NPM and Why is it Important?
**NPM (Node Package Manager)** is the **default package manager for Node.js**.  
It helps developers **install, manage** reusable JavaScript packages and dependencies for their projects.

**Key Benefits:**
- Provides access to **over a million open-source libraries**.  
- Simplifies **dependency management**.  
- Enables easy **version control** and **automation scripts**.  
- Supports **global CLI tools** and local project dependencies.

> 💡 NPM is automatically installed with Node.js.

### 📘 package.json and Its Fields
The **`package.json`** file is the **heart of every Node.js project** — it defines the project metadata and dependencies.
```bash
npm init -y //create package.json
```

**Example:**
```json
{
  "name": "my-node-app", //Project name
  "version": "1.0.0",    //Current version of the project
  "description": "A sample Node.js project", //Short project summary
  "main": "index.js",  //Entry point file (e.g., index.js)
  "scripts": {   //Command shortcuts (e.g., npm start) for start entry fill
    "start": "node index.js"
  },
  "dependencies": {      //Production packages
    "express": "^4.18.2"
  },
  "devDependencies": {    //Development-only packages
    "nodemon": "^3.0.1"
  },
  "author": "Your Name",
  "license": "MIT" //License type
}
```

### 🔢 Semantic Versioning (SemVer)
NPM uses **semantic versioning** in the format:  
`MAJOR.MINOR.PATCH` → `1.4.2`

| Symbol | Meaning | Example | Update Type |
|---------|----------|----------|--------------|
| **^** | Updates to the latest **minor** or **patch** | `^1.4.2` → up to `1.x.x` | Minor & Patch updates |
| **~** | Updates to the latest **patch** only | `~1.4.2` → up to `1.4.x` | Patch updates only |
| **No Symbol** | Locks **exact version** | `1.4.2` | No auto-updates |

> ⚠️ Use `^` for stable libraries and exact versions for production-critical apps.

### ⚙️ Installing, Updating, Removing Packages

| Action | Command | Example |
|--------|----------|---------|
| **Install (local)** | `npm install <package>` | `npm install express` |
| **Install (global)** | `npm install -g <package>` | `npm install -g nodemon` |
| **Update** | `npm update <package>` | `npm update express` |
| **Uninstall** | `npm uninstall <package>` | `npm uninstall express` |
| **Install all dependencies** | `npm install` | Uses `package.json` |

### 🌐 Global vs Local Packages

| Feature | Local Package | Global Package |
|------|---------------------|--------|
| **install** | local packages are installed inside your project folder — specifically under the node_modules. | Global packages are installed system-wide|
| **Access** | They are access only within that project folder. |they can be Accessed from any project or directory using the command line. |
| **Best For** | Project dependencies (express, mongoose, etc.). |CLI tools (nodemon, eslint, typescript). |
| **Usage in Code** | Imported using require() or import. |Run directly via terminal command |
| **Added to** | dependencies or devDependencies in package.json. |Not listed (unless you add manually) |

> 💡 Prefer **local** packages for app dependencies, and **global** for reusable CLI tools.

### ⚡ npx and Its Usage
**npx** is a CLI tool that comes with npm (v5.2+) used to **execute packages without installing them globally**.

**Examples:**
```bash
npx create-react-app myApp
npx nodemon index.js
```
---

## 5. Core Node.js APIs

### 🧠 Definition
**Core Node.js APIs** are the built-in modules that come preinstalled with Node.js, allowing developers to perform essential backend tasks such as **file operations, creating servers, working with paths, encryption, and handling streams** — all without needing external packages.


### 📂 fs (File System Module)

The **fs** module enables interaction with the file system, allowing you to **read, write, update, delete, or rename files**.  
It supports both **synchronous** and **asynchronous** operations.

| Function | Description | Example |
|-----------|--------------|----------|
| `fs.readFile()` | Reads the contents of a file asynchronously. | `fs.readFile('file.txt', 'utf8', (err, data) => console.log(data));` |
| `fs.writeFile()` | Writes data to a file, creating it if it doesn’t exist. | `fs.writeFile('new.txt', 'Hello Node!', err => console.log('Saved!'));` |
| `fs.appendFile()` | Appends data to a file. | `fs.appendFile('log.txt', 'New log entry\n', () => {});` |
| `fs.unlink()` | Deletes a file. | `fs.unlink('old.txt', () => console.log('Deleted!'));` |
| `fs.existsSync()` | Checks if a file exists. | `console.log(fs.existsSync('file.txt'));` |


### 🌐 http (HTTP Module)
The **http** module is used to **create web servers and handle HTTP requests and responses**.  
It’s the foundation for frameworks like **Express.js**.

| Function | Description | Example |
|-----------|--------------|----------|
| `http.createServer()` | Creates a new HTTP server. | `http.createServer((req, res) => res.end('Hello!')).listen(3000);` |
| `res.writeHead()` | Sends response headers to the client. | `res.writeHead(200, {'Content-Type': 'text/plain'});` |
| `res.end()` | Ends the response process. | `res.end('Done');` |
| `req.url` | Returns the requested URL path. | `console.log(req.url);` |

### ⚙️ os (Operating System Module)
The **os** module provides **system-related information** such as CPU, memory, hostname, and network interfaces.

| Function | Description | Example |
|-----------|--------------|----------|
| `os.platform()` | Returns the operating system platform. | `console.log(os.platform());` |
| `os.cpus()` | Returns CPU core information. | `console.log(os.cpus());` |
| `os.totalmem()` | Returns total system memory. | `console.log(os.totalmem());` |
| `os.freemem()` | Returns free system memory. | `console.log(os.freemem());` |
| `os.hostname()` | Returns the host name of the system. | `console.log(os.hostname());` |


### 📁 path (Path Module)
The **path** module helps manage **file and directory paths** across operating systems safely and consistently.

| Function | Description | Example |
|-----------|--------------|----------|
| `path.join()` | Joins multiple path segments into one. | `path.join(__dirname, 'folder', 'file.txt');` |
| `path.basename()` | Returns the filename from a path. | `path.basename('/user/docs/file.txt');` |
| `path.extname()` | Returns the file extension. | `path.extname('index.html');` |
| `path.dirname()` | Returns the directory name. | `path.dirname('/user/docs/file.txt');` |
| `path.resolve()` | Resolves an absolute path. | `path.resolve('folder', 'file.txt');` |


### 🌍 url (URL Module)
The **url** module is used for **URL parsing, formatting, and manipulation**.

| Function | Description | Example |
|-----------|--------------|----------|
| `new URL()` | Creates a new URL object. | `const myURL = new URL('https://example.com/path?name=test');` |
| `url.hostname` | Returns the host name. | `console.log(myURL.hostname);` |
| `url.pathname` | Returns the path part of the URL. | `console.log(myURL.pathname);` |
| `url.searchParams` | Accesses query parameters. | `console.log(myURL.searchParams.get('name'));` |


### 🔄 stream (Stream Module)
The **stream** module handles **streaming data** — ideal for large files, video streaming, or network communication.  
It processes data **in chunks**, improving performance and memory usage.

| Type / Function | Description | Example |
|------------------|--------------|----------|
| **Readable Stream** | Source of data (e.g., reading a file). | `fs.createReadStream('input.txt');` |
| **Writable Stream** | Destination to write data. | `fs.createWriteStream('output.txt');` |
| **pipe()** | Transfers data between streams. | `readStream.pipe(writeStream);` |
| **Duplex Stream** | Both readable and writable. | Used in sockets. |
| **Transform Stream** | Modifies data while streaming. | Used in compression/encryption. |


### 🔐 crypto (Crypto Module)
The **crypto** module provides **encryption, decryption, and hashing** functionalities for securing data.

| Function | Description | Example |
|-----------|--------------|----------|
| `crypto.createHash()` | Creates a hash object (e.g., SHA-256). | `crypto.createHash('sha256').update('data').digest('hex');` |
| `crypto.createCipheriv()` | Encrypts data using an algorithm and key. | `crypto.createCipheriv('aes-256-cbc', key, iv);` |
| `crypto.createDecipheriv()` | Decrypts previously encrypted data. | `crypto.createDecipheriv('aes-256-cbc', key, iv);` |
| `crypto.randomBytes()` | Generates random bytes for keys/IVs. | `crypto.randomBytes(16);` |
| `crypto.pbkdf2()` | Derives a key from a password. | `crypto.pbkdf2('pass', 'salt', 1000, 64, 'sha512', cb);` |


> 🧩 These **core Node.js modules** are essential tools that power everything from simple file I/O to secure network communication, making Node.js a complete runtime for backend development.

## 6. Asynchronous Programming

### 🧠 Definition
**Asynchronous programming** in Node.js allows multiple operations (like file reads, API calls, or database queries) to run **without blocking** the main thread.  
This is achieved using **callbacks, promises, async/await, and event-driven architecture**, making Node.js fast and efficient.


### 🔁 Callback Functions
A **callback** is a function passed as an argument to another function, executed after the main task completes.

| Concept | Description | Example |
|----------|--------------|----------|
| **Callback** | Function executed after an async task completes. | ```js\nfs.readFile('data.txt', 'utf8', (err, data) => {\n  if (err) throw err;\n  console.log(data);\n});\n``` |
| **Pros** | Simple, widely used in Node.js core modules. | – |
| **Cons** | Can lead to nested callbacks → “Callback Hell”. | – |

---

### 😵 Callback Hell

Occurs when multiple asynchronous operations are **nested inside each other**, making code **hard to read and maintain**.

```js
// Callback Hell Example
getUser(id, (user) => {
  getPosts(user.id, (posts) => {
    getComments(posts[0].id, (comments) => {
      console.log(comments);
    });
  });
});
```

### 🔁 Callback Functions
A **callback** is a function passed as an argument to another function, executed after the main task completes.

| Concept | Description | Example |
|----------|--------------|----------|
| **Callback** | Function executed after an async task completes. | ```js\nfs.readFile('data.txt', 'utf8', (err, data) => {\n  if (err) throw err;\n  console.log(data);\n});\n``` |
| **Pros** | Simple, widely used in Node.js core modules. | – |
| **Cons** | Can lead to nested callbacks → “Callback Hell”. | – |

### 🧩 Promises

A Promise in JavaScript is an object used to handle asynchronous operations. It represents a value that will be available in the future — either the operation succeeds (resolved) or fails (rejected) — allowing cleaner, non-blocking code using .then(), .catch(), and .finally().

#### 🔄 Promise States

| State | Meaning |
|--------|----------|
| **Pending** | Initial state — operation not yet complete |
| **Fulfilled** | Operation completed successfully |
| **Rejected** | Operation failed |

#### ⚙️ Common Promise Methods

| Function | Description | Example |
|-----------|--------------|----------|
| `then()` | Executes after successful completion | `getData().then(data => console.log(data));` |
| `catch()` | Executes after operation failed Handles errors | `.catch(err => console.error(err));` |
| `finally()` | Executes regardless of outcome | `.finally(() => console.log('Done'));` |

#### 💡 Example

```js
const promise = new Promise((resolve, reject) => {
  // Perform some async work
  const success = true;

  if (success) {
    resolve("Task completed successfully!");
  } else {
    reject("Task failed!");
  }
});

promise
  .then(result => console.log(result))     // Handles success
  .catch(error => console.log(error))      // Handles failure
  .finally(() => console.log("Done!"));    // Runs always
```
### ⚡ async / await

`async` and `await` provide a **cleaner and more readable syntax** for handling asynchronous code, making it look and behave like synchronous code.

#### 🏷️ Keywords

| Keyword | Description | Example |
|----------|--------------|----------|
| **async** | Declares a function that always returns a Promise. | `async function fetchData() { ... }` |
| **await** | Pauses the execution until a Promise is resolved or rejected. | `const data = await getData();` |

#### 💡 Example

```js
async function fetchUser() {
  try {
    const user = await getUser();
    const posts = await getPosts(user.id);
    console.log(posts);
  } catch (err) {
    console.error('Error:', err);
  }
}
```
---
## 🧩 7. Express.js Framework

### 🧠 What is Express.js?

**Express.js** is a fast, minimalist, and flexible **web application framework** for **Node.js**.  
It simplifies building **server-side applications and APIs** by providing tools for **routing, middleware, and HTTP handling**.

> ✅ In short: Express = Node.js + Structure + Simplicity

### 🏗️ Express Architecture

Express follows a **middleware-based architecture**, where each incoming request passes through a **stack of functions (middlewares)** before reaching the final response.

**Flow:**  
`Client Request → Middleware(s) → Route Handler → Response`

| Component | Description |
|------------|--------------|
| **Application** | Created using `express()` — core of Express app |
| **Request (req)** | Represents the HTTP request data |
| **Response (res)** | Represents the HTTP response sent back |
| **Middleware** | Functions that process requests before they reach the route |
| **Router** | Handles routing for different endpoints (GET, POST, etc.) |


### 🚀 Creating a Basic Express Server

```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello Express!');
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

### ⚙️ **Middleware in Express.js**

Middleware is a function that have access to the **req**, **res**, and **next()** objects.  
They can **modify**, **log**, **validate**, or **handle** requests **before** sending the final response.


#### 🔍 Types of Middleware

| Type | Description | Example |
|------|--------------|----------|
| **Built-in** | Provided by Express itself for common tasks. | `app.use(express.json());` — Parses incoming JSON data |
| **Custom** | Created by developers for specific logic or validation. | ```js app.use((req, res, next) => { console.log('Request received'); next(); }); ``` |
| **Third-party** | Installed from npm to add features like CORS or logging. | `app.use((cors());` — Enables cross-origin requests |


#### 🧩 Note:
- Middlewares are executed **in the order they are defined** in your code.  
- Each middleware should call **next()** to pass control to the next function in the stack.


#### ✅ Example:

```js
const express = require('express');
const cors = require('cors');
const app = express();

// Built-in middleware
app.use(express.json());

// Third-party middleware
app.use(cors());

// Custom middleware
app.use((req, res, next) => {
  console.log('Middleware executed!');
  next();
});

app.get('/', (req, res) => {
  res.send('Hello Middleware!');
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

### 🧭 **Routing in Express.js**

Express provides a simple and flexible way to define **RESTful routes** to handle different HTTP methods like **GET**, **POST**, **PUT**, and **DELETE**.

#### 🔹 Common HTTP Methods

| Method | Description | Example |
|--------|--------------|----------|
| **GET** | Retrieve data from the server. | `app.get('/users', (req, res) => {...});` |
| **POST** | Create new data on the server. | `app.post('/users', (req, res) => {...});` |
| **PUT** | Update existing data by ID or key. | `app.put('/users/:id', (req, res) => {...});` |
| **DELETE** | Delete data by ID or key. | `app.delete('/users/:id', (req, res) => {...});` |


#### 💡 Example:

```js
app.get('/hello', (req, res) => {
  res.send('GET request received');
});

app.post('/data', (req, res) => {
  res.send('POST request received');
});
```
### 🧰 Error Handling in Express

Express provides a built-in way to handle errors using **error-handling middleware** i contain four parameter err first one.  
These middleware functions help catch and manage runtime or request errors **globally** in your application.


#### 🧩 Example:

```js
app.use((err, req, res, next) => {
  console.error(err.stack);          // Logs error details
  res.status(500).send('Something went wrong!');  // Sends error response
});

```
## 📦 Working with Common Middleware

Express allows integration of various middleware packages to handle tasks like parsing data, enabling CORS, logging requests, and improving security.

### 🧠 Commonly Used Middleware

| Package | Purpose | Example Usage |
|----------|----------|----------------|
| **body-parser** | Parses incoming request bodies (JSON or URL-encoded). | `app.use(express.json());`<br>`app.use(express.urlencoded({ extended: true }));` |
| **cors** | Enables Cross-Origin Resource Sharing to allow requests from different domains. | `const cors = require('cors');`<br>`app.use(cors());` |
| **morgan** | Logs incoming HTTP requests for debugging and monitoring. | `const morgan = require('morgan');`<br>`app.use(morgan('dev'));` |
| **helmet** | Adds security-related HTTP headers to protect your app. | `const helmet = require('helmet');`<br>`app.use(helmet());` |


### 💡 Tip:
> Middleware like **helmet** and **morgan** are essential in production environments for security and logging,  
> while **cors** and **body-parser** are crucial for API

---


<h1 align="center">🚀 Node JS</h1>

## 📚 Table of Contents

1. [Introduction](#1-introduction)  
2. [Node.js Architecture](#2-nodejs-architecture)  
3. [Node.js Modules](#3-nodejs-modules)  
4. [NPM (Node Package Manager)](#4-npm-node-package-manager)  
5. [Core Node.js APIs](#5-core-nodejs-apis)
6. [Asynchronous Programming](#6-asynchronous-programming)  
8. [Express.js Framework](#7-expressjs-framework)  
9. [RESTful APIs](#8-restful-apis)  
10. [Authentication & Authorization](#9-authentication--authorization)  
11. [Database Integration](#10-database-integration)  
12. [Error Handling & Debugging](#11-error-handling--debugging)  
13. [Node.js Built In Middleware Libraries](#12-nodejs-built-in-middleware-libraries) 
14. [Streams & Buffers](#13-streams--buffers)  
15. [Event-Driven Programming](#14-event-driven-programming)  
16. [Scaling & Performance](#scaling--performance)  
17. [Testing](#testing)  
18. [Deployment](#deployment)  
19. [Security Best Practices](#security-best-practices)

## 1. Introduction

### 🧠 What is Node.js?
Node.js is an **open-source, cross-platform JavaScript runtime environment** that allows  to run JavaScript **outside the browser**, mainly on the **server side**.  
It built on  **Google Chrome V8 engine** that follow an single-thread, non-blocking event-driven architecture it allows  to handle thousands of concurrent connections efficiently — all within a **single thread** without creating new thread for each request. .

### ⚡ Why Node.js? (Advantages over Traditional Backend Tech)
- **Single Language:** Use JavaScript for both frontend and backend.  
- **High Performance:** Built on V8 engine that boosts execution speed.
- **REST SAME AS FEATURE**

### 🌟 Features of Node.js

| **Feature** | **Description** |
|--------------|-----------------|
| **Single Threaded** | Uses an event loop to handle thousand of concurrent requests efficiently without creating new threads for each. |
| **Asynchronous & Non-Blocking I/O** |Allows multiple operations to run concurrently without blocking the main thread using callbacks, promises, or async/await. |
| **Event-Driven** | program react to event(user interaction or message) when event happen its  corresponding callbacks or code get executes. |
| **Rich npm Library** | Provides access to over a million of open-source libraries. |
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
| **V8 Engine** | Executes JavaScript code outside the browser by compiling it into machine code. |
| **Event Loop** | The event loop in Node.js is essentially the mechanism that handles asynchronous operations.It continuously checks the call stack and the callback queue. When the call stack is empty, it will take the first callback from the callback queue and push it onto the call stack for execution.The event loop also manages various phases, like timers, I/O operations, and more, to ensure non-blocking behavior and efficient performance.. |
| **Call Stack** | Main thread that executes synchronous code. |
| **Event Queue (Callback Queue)** | Stores callbacks of completed asynchronous operations waiting for execution. |
| **Microtask Queue** | Executes promises and `process.nextTick()` before the next event loop tick. |
| **libuv (Thread Pool)** | Handles heavy I/O tasks (file system, DNS, compression) in background threads. |
| **Non-Blocking I/O** | Allows multiple operations to run concurrently without blocking the main thread. |
| **process.nextTick()** | It executes a callback function immediately after the current operation completes,before the event loop continues to the next phase.. |
| **setImmediate()** | It schedules a callback to run on the next iteration (or tick) of the event loop,after the current I/O events are processed.. |

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
| **Readable Stream** | Read data from source (e.g., reading a file). | `fs.createReadStream('input.txt');` |
| **Writable Stream** |  Write data on destination. | `fs.createWriteStream('output.txt');` |
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

---

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
## 7. Express.js Framework

### 🧠 What is Express.js?

**Express.js** is a fast, minimalist, and flexible **web application framework** for **Node.js**.  
It simplifies building **server-side applications and APIs** by providing tools for **routing, middleware, and HTTP handling**.


### 🏗️ Express Architecture

Express follows a **middleware-based architecture**, where each incoming request passes through a **stack of middlewares** before reaching the final response.

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

Middleware in Express.js are functions that run between the client’s request and the server’s response. 
They can **modify**, **log**, **validate**, or **handle** requests then pass control to the next function using next()..


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

Routing is the process that deciding what action the server should take when a user requests a particular URL

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

Error handling in Express means using special middleware to catch and manage errors, so the app doesn’t crash and can send a proper error response to the client.

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

## 8. RESTful APIs

### 🌐 What is REST API?

A REST API is a way for the client and server to communicate using standard HTTP methods (GET, POST, PUT, DELETE), where each resource is identified by a URL
Enable
-simple
-stateless
-structured data exchange

### ⚙️ CRUD Operations with HTTP Methods

| Operation | HTTP Method | Description | Example Endpoint |
|------------|--------------|--------------|------------------|
| **Create** | `POST` | Add new data | `POST /users` |
| **Read** | `GET` | Fetch data | `GET /users` |
| **Update** | `PUT / PATCH` | Modify existing data | `PUT /users/:id` |
| **Delete** | `DELETE` | Remove data | `DELETE /users/:id` |

### 📊 Common HTTP Status Codes

| Code | Meaning | Description |
|------|----------|-------------|
| **200** | OK | Request successful |
| **201** | Created | Resource successfully created |
| **400** | Bad Request | Invalid request from client |
| **401** | Unauthorized | Authentication required or failed |
| **404** | Not Found | Resource not found |
| **500** | Internal Server Error | Server-side error |


### 🧩 API Versioning & Best Practices

| Practice | Description |
|-----------|--------------|
| **Versioning** | Use versioning to manage updates (e.g., `/api/v1/users`). |
| **Consistent Naming** | Use plural nouns for endpoints (`/users`, `/products`). |
| **Use Proper Status Codes** | Always return meaningful status codes. |
| **Handle Errors Gracefully** | Return clear error messages in JSON format. |
| **Secure Endpoints** | Use authentication (JWT, OAuth) where required. |

### 🧪 Testing with Postman

**Postman** is a popular tool used to test REST APIs by sending HTTP requests and viewing responses.

**Example Workflow:**
1. Open Postman and create a new request.
2. Choose the HTTP method (`GET`, `POST`, etc.).
3. Enter your API endpoint (e.g., `http://localhost:3000/api/v1/users`).
4. Add headers or body (if needed).
5. Click **Send** to test and view the response.


> ✅ **In Short:**  
> RESTful APIs provide a structured, consistent, and stateless way for clients and servers to communicate efficiently.

---

## 9. Authentication & Authorization

### 🧾 Authentication vs Authorization

| Concept | Meaning | Example |
|----------|----------|----------|
| **Authentication** |  Verifying who the user is. (login identity). | Logging in with email and password |
| **Authorization** | Deciding what the user can do after login.(permissions). | Admin can delete users, normal users cannot |

### Way to do 

- JSON Web Token (JWT)
- OAuth 2.0 (Basics)
- Role-Based Access Control (RBAC)

### 🔑 JSON Web Token (JWT)

#### 📘 Definition
JWT  is a token used to **verify user identity** and **securely send user information between client and server**

#### 🧩 Key Concepts

| Concept | Description | Example |
|----------|--------------|----------|
| **Structure** | JWT token has 3 parts — Header, Payload, Signature. | `xxxxx.yyyyy.zzzzz` |
| **Header** | Contains token type & algorithm used. | `{ "alg": "HS256", "typ": "JWT" }` |
| **Payload** | Stores user data (like id, role, expiry). | `{ "id": 1, "name": "Shubham" }` |
| **Signature** | Ensures token is valid and untampered. | Created using secret key & algorithm |
| **Stateless** | Server doesn’t store session — token is self-contained. | No session data on server |
| **Secure** | Signed with a secret or private key (not encrypted). | `jwt.sign(data, secret)` |
| **Expiration** | Tokens can have an expiry time for security. | `{ expiresIn: '1h' }` |

#### ⚙️ Example: Creating & Verifying JWT in Node.js

```js
const jwt = require('jsonwebtoken');

// 🔹 1. Create a Token
const user = { id: 1, name: 'Shubham', role: 'admin' };
const token = jwt.sign(user, 'mySecretKey', { expiresIn: '1h' });
console.log('Generated Token:', token);

// 🔹 2. Verify the Token
try {
  const decoded = jwt.verify(token, 'mySecretKey');
  console.log('Verified Data:', decoded);
} catch (err) {
  console.error('Invalid Token:', err.message);
}
```

### 🔐 OAuth 2.0 (Basics)

**OAuth2** is an **authorization framework** that allows users to log in using third-party services like **Google, GitHub, or Facebook** — without sharing passwords.

#### 🧭 Example Flow
1. You click **“Login with Google”**.  
2. Google verifies your identity.  
3. Your app receives a **secure access token** from Google.  
4. The token allows your app to access **limited user data** (like name or email).

✅ **Used for:** Social logins, third-party integrations, and secure delegated access.

#### 💻 Example Code (Google OAuth2 with Express)

```javascript
import express from "express";
import passport from "passport";
import { Strategy as GoogleStrategy } from "passport-google-oauth20";

const app = express();

// Configure Google OAuth2 strategy
passport.use(new GoogleStrategy({
  clientID: "GOOGLE_CLIENT_ID",
  clientSecret: "GOOGLE_CLIENT_SECRET",
  callbackURL: "/auth/google/callback"
}, (accessToken, refreshToken, profile, done) => {
  // Here you can save user info to DB
  return done(null, profile);
}));

app.use(passport.initialize());

// Route to start Google login
app.get("/auth/google", passport.authenticate("google", { scope: ["profile", "email"] }));

// Callback route after login
app.get("/auth/google/callback",
  passport.authenticate("google", { failureRedirect: "/login" }),
  (req, res) => {
    res.send("Login successful!");
  }
);

app.listen(3000, () => console.log("Server running on http://localhost:3000"));
```

### 🧩 Role-Based Access Control (RBAC)

**Role-Based Access Control (RBAC)** is a security model that allow system access permisson based on a user's **role** (e.g., admin, editor, user).  
Each role has specific **permissions** that define what actions it can perform.

### 🔑 Key Concepts

| Term | Description | Example |
|------|--------------|----------|
| **Role** | Defines a set of permissions. | `admin`, `user`, `editor` |
| **Permission** | Specific action allowed or denied. | `createUser`, `deletePost` |
| **User** | Assigned one or more roles. | `User A → admin` |
| **
Control** | Logic that checks if a user has permission. | Only `admin` can delete data. |

---

### 💻 Example (Express.js RBAC)

```javascript
// Simple RBAC middleware

const roles = {
  admin: ["read", "write", "delete"],
  editor: ["read", "write"],
  user: ["read"]
};

// Middleware to check permissions
function authorize(role, action) {
  return (req, res, next) => {
    if (roles[role] && roles[role].includes(action)) {
      next();
    } else {
      res.status(403).send("Access Denied");
    }
  };
}

// Usage in Express routes
import express from "express";
const app = express();

app.get("/data", authorize("user", "read"), (req, res) => {
  res.send("Data viewed successfully");
});

app.post("/data", authorize("editor", "write"), (req, res) => {
  res.send("Data created successfully");
});

app.delete("/data", authorize("admin", "delete"), (req, res) => {
  res.send("Data deleted successfully");
});

app.listen(3000, () => console.log("Server running on http://localhost:3000"));
```
---
## 10. Database Integration

Node.js can connect to both **NoSQL** and **SQL** databases to perform CRUD (Create, Read, Update, Delete) operations efficiently.

### ⚙️ Connecting Node.js to Databases

| Database Type | Popular Databases | Libraries/ORMs | Description |
|----------------|------------------|----------------|--------------|
| **NoSQL** | MongoDB | **Mongoose** | Stores data in flexible JSON-like documents. |
| **SQL** | MySQL, PostgreSQL | **mysql2**,**Sequelize** | Stores data in structured tables with relations. |

### 🍃 MongoDB (Using Mongoose)

**Mongoose** is an ODM (Object Data Modeling) library that helps interact with MongoDB using schemas and models.

```javascript
// Install: npm install mongoose
import mongoose from "mongoose";

// Connect to MongoDB
mongoose.connect("mongodb://localhost:27017/mydb")
  .then(() => console.log("✅ MongoDB Connected"))
  .catch(err => console.error("❌ DB Connection Error:", err));

// Define Schema & Model
const userSchema = new mongoose.Schema({
  name: String,
  email: String,
  age: Number
});

const User = mongoose.model("User", userSchema);

// CRUD Example
async function createUser() {
  const newUser = new User({ name: "John", email: "john@example.com", age: 25 });
  await newUser.save();
  console.log("User Created:", newUser);
}

createUser();

```

### MySQL / PostgreSQL (Using Sequelize)

Sequelize is an ORM for relational databases that helps define models and manage queries.
```
// Install: npm install sequelize 
import { Sequelize, DataTypes } from "sequelize";

const sequelize = new Sequelize("mydb", "root", "password", {
  host: "localhost",
  dialect: "mysql"
});

// Test connection
sequelize.authenticate()
  .then(() => console.log("✅ MySQL Connected"))
  .catch(err => console.error("❌ Connection Error:", err));

// Define Model
const User = sequelize.define("User", {
  name: DataTypes.STRING,
  email: DataTypes.STRING,
  age: DataTypes.INTEGER
});

// Sync and Create Record
(async () => {
  await sequelize.sync();
  const user = await User.create({ name: "Alice", email: "alice@mail.com", age: 22 });
  console.log("User Created:", user.toJSON());
})();

```
## (MySQL with Node.js)

**MySQL** is a popular **relational database** that organizes data in **tables** with rows and columns.  

In Node.js, you can connect to MySQL either using the **mysql2** library (for direct queries) or **Sequelize** (an ORM for structured operations).

### Connecting Node.js with MySQL (Using `mysql2`)

```javascript
// Install: npm install mysql2
import mysql from "mysql2";

// Create connection
const db = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "password",
  database: "studentDB"
});

// Connect
db.connect(err => {
  if (err) throw err;
  console.log("✅ MySQL Connected Successfully!");
});

```
---
##  11. Error Handling & Debugging

**Error Handling** in Node.js helps detect and manage issues during code execution to prevent app crashes and improve stability.


### ⚙️ Types of Errors

| Type | Description | How to Handle |
|------|--------------|----------------|
| **Synchronous Error** | Occurs during immediate code execution. | `try...catch` |
| **Asynchronous Error** | Happens in callbacks or promises. | `.catch()` or `try...catch` with `async/await` |
| **Uncaught Exception** | Unexpected runtime error not caught anywhere. | `process.on('uncaughtException')` |
| **Unhandled Rejection** | Promise rejected without a `.catch()` block. | `process.on('unhandledRejection')` |

### 💻 Example

```javascript
// Synchronous error
try {
  throw new Error("Something went wrong!");
} catch (err) {
  console.error("❌ Error:", err.message);
}

// Promise error
getData()
  .then(res => console.log(res))
  .catch(err => console.error("❌ Promise Error:", err));

// Global error handling
process.on("uncaughtException", err => console.error("🚨 Uncaught:", err));
process.on("unhandledRejection", err => console.error("🚨 Unhandled:", err));

```
---
## 12. Node.js Built In Middleware Libraries

Middleware and third-party libraries enhance the functionality, security, and maintainability of Node.js applications.

### 🧩 Common Middleware & Libraries

| Library | Purpose | Example Usage |
|----------|----------|----------------|
| **cors** | Enables Cross-Origin Resource Sharing. | `app.use(require('cors')());` |
| **helmet** | Adds security-related HTTP headers. | `app.use(require('helmet')());` |
| **morgan** | Logs incoming HTTP requests. | `app.use(require('morgan')('dev'));` |
| **dotenv** | Loads environment variables from `.env`. | `require('dotenv').config();` |
| **express-validator** | Validates and sanitizes incoming request data. | `check('email').isEmail()` |
| **express-rate-limit** | Limits repeated requests to protect from abuse. | `app.use(rateLimit({ windowMs: 60000, max: 100 }));` |


### 🧩 1. CORS (Cross-Origin Resource Sharing)

**Definition:**  
CORS allows your server to accept requests from a different domain (frontend → backend).  
Without CORS, browsers block requests for security reasons.

**Example:**
```javascript
// Install: npm install cors
import express from "express";
import cors from "cors";

const app = express();
app.use(cors()); // Enable all origins

app.get("/", (req, res) => res.send("CORS enabled!"));
app.listen(3000, () => console.log("Server running on port 3000"));
```

### 🧩 2.Helmet

**Definition:**  
Helmet secures your Express app by setting various HTTP headers (like hiding server info, preventing XSS).

**Example:**
```javascript
// Install: npm install helmet
import express from "express";
import helmet from "helmet";

const app = express();
app.use(helmet()); // Adds security headers

app.get("/", (req, res) => res.send("Helmet security active"));
app.listen(3000, () => console.log("Server secure with Helmet"));

```

### 🧩 3.Morgan

**Definition:**  
Morgan is a HTTP request logger middleware that logs incoming requests (method, URL, status, time).

**Example:**
```javascript
// Install: npm install morgan
import express from "express";
import morgan from "morgan";

const app = express();
app.use(morgan("dev")); // Logs all incoming requests

app.get("/", (req, res) => res.send("Logging with Morgan"));
app.listen(3000, () => console.log("Server running with Morgan logs"));


```

### 🧩 4.Dotenv

**Definition:**  
Dotenv loads environment variables from a .env file into process.env, keeping secrets (like DB passwords) out of your code.

**Example:**
```javascript
// Install: npm install dotenv
import express from "express";
import dotenv from "dotenv";

dotenv.config(); // Load variables from .env

const app = express();
const PORT = process.env.PORT || 4000;

app.get("/", (req, res) => res.send(`Running on port ${PORT}`));
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));

```

### 🧩 5.express-validator

**Definition:**  
A library used to validate and sanitize user input before processing requests.
**Example:**
```javascript
// Install: npm install express-validator
import express from "express";
import { body, validationResult } from "express-validator";

const app = express();
app.use(express.json());

app.post(
  "/register",
  [
    body("email").isEmail().withMessage("Invalid email"),
    body("password").isLength({ min: 5 }).withMessage("Password too short")
  ],
  (req, res) => {
    const errors = validationResult(req);
    if (!errors.isEmpty()) {
      return res.status(400).json({ errors: errors.array() });
    }
    res.send("User registered successfully!");
  }
);

app.listen(3000, () => console.log("Server running with validation"));
```
### 🧩 6. express-rate-limit

**Definition:**  
Limits the number of requests a user can make in a given time period to prevent DDoS or brute-force attacks.
**Example:**
```javascript
// Install: npm install express-rate-limit
import express from "express";
import rateLimit from "express-rate-limit";

const app = express();

// Allow max 100 requests per 15 minutes per IP
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 100,
  message: "Too many requests, please try again later."
});

app.use(limiter);

app.get("/", (req, res) => res.send("Rate limiting active!"));
app.listen(3000, () => console.log("Server running with rate limit"));
```
---
## 13. Streams & Buffers

### 🧠 What are Buffers?
**Definition:**  
A **Buffer** is a temporary memory area used to store binary data (like files, images, or video) while it’s being transferred from one place to another (i.e From disk to memory or memory to netowork).

**Example:**
```javascript
const buffer = Buffer.from("Hello");
console.log(buffer); // <Buffer 48 65 6c 6c 6f>
console.log(buffer.toString()); // Hello
```

### 🔄 stream 
The **stream** module handles **streaming data** — ideal for large files, video streaming, or network communication.  
It processes data **in chunks**, improving performance and memory usage.

| Type / Function | Description | Example |
|------------------|--------------|----------|
| **Readable Stream** | Source of data (e.g., reading a file). | `fs.createReadStream('input.txt');` |
| **Writable Stream** | Destination to write data. | `fs.createWriteStream('output.txt');` |
| **pipe()** | Transfers data between streams. | `readStream.pipe(writeStream);` |
| **Duplex Stream** | Both readable and writable. | Used in sockets. |
| **Transform Stream** | Modifies data while streaming. | Used in compression/encryption. |

---
##  14. Event-Driven Programming

### 🧩 Definition

**Event-Driven Programming** is a programming paradigm where program react to  events **like user interaction or messages**, and whenever an event happens, it corresponding code gets executed..

> In **Node.js**, this concept is the core of its architecture, as it uses an **event loop** to handle asynchronous operations efficiently.

### ⚙️ EventEmitter Class

The **EventEmitter** class (from Node’s `events` module) allows creating **custom events**.

Many Node.js core modules (like **HTTP**, **Streams**) are built on top of it.

### 🧠 Here
- `.on()` → listens for an event  
- `.emit()` → triggers the event  

### Example:
```js
import { EventEmitter } from "events";
const event = new EventEmitter();

event.on("greet", () => {
  console.log("Hello, welcome!");
});

event.emit("greet"); // Output: Hello, welcome!
```
---






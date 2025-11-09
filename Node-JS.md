<h1 align="center">🚀 Node JS</h1>

## Table Content

## 📚 Table of Contents

1. [Introduction](#1-introduction)  
2. [Node.js Architecture](#2-nodejs-architecture)  
3. [Node.js Modules](#3-nodejs-modules)  
4. [NPM (Node Package Manager)](#4-npm-node-package-manager)  
5. [Asynchronous Programming](#asynchronous-programming)  
6. [Core Node.js APIs](#core-nodejs-apis)  
7. [Express.js Framework](#expressjs-framework)  
8. [RESTful APIs](#restful-apis)  
9. [Authentication & Authorization](#authentication--authorization)  
10. [Database Integration](#database-integration)  
11. [Error Handling & Debugging](#error-handling--debugging)  
12. [Node.js with Middleware & Libraries](#nodejs-with-middleware--libraries)  
13. [Streams & Buffers](#streams--buffers)  
14. [Event-Driven Programming](#event-driven-programming)  
15. [Scaling & Performance](#scaling--performance)  
16. [Testing](#testing)  
17. [Deployment](#deployment)  
18. [Security Best Practices](#security-best-practices)

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




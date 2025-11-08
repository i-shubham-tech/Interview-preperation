<h1 align="center">🚀 Node JS</h1>

## Table Content

## 📚 Table of Contents

1. [Introduction](#1-introduction)  
2. [Node.js Architecture](#2-nodejs-architecture)  
3. [Node.js Modules](#nodejs-modules)  
4. [NPM (Node Package Manager)](#npm-node-package-manager)  
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


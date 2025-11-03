# 💡 JavaScript Interview Preparation

## 📘 Table of Contents

1. [Introduction](#introduction)
2. [Normal Feature & ES6 Feature](#normal-feature--es6-feature)
3. [Variable (let, var, const) & Their Differences](#variable-let-var-const--their-differences)
4. [Data Type & Type Casting](#data-type--type-casting)
5. [Operator](#operator)
6. [Conditional](#conditional)
7. [Loop](#loop)
8. [Function](#function)
   - [Normal Function](#normal-function)
   - [Arrow Function](#arrow-function)
   - [Pure Function](#pure-function)
   - [Impure Function](#impure-function)
   - [Currying Function](#currying-function)
   - [First Order & Higher Order Function](#first-order--higher-order-function)
9. [Built-in Methods](#built-in-methods)
   - [Array Methods](#array-methods)
   - [String Methods](#string-methods)
   - [Date Methods](#date-methods)
   - [Math Methods](#math-methods)
10. [Hoisting](#hoisting)
11. [Closure](#closure)
12. [Promise](#promise)
13. [Sync, Async & Await](#sync-async--await)
14. [setTimeout, setInterval & clearInterval](#settimeout-setinterval--clearinterval)
15. [Debouncing & Throttle](#debouncing--throttle)
16. [Lazy Loading](#lazy-loading)
17. [Memoization](#memoization)
18. [Code Splitting](#code-splitting)
19. [URL Encoding & Decoding](#url-encoding--decoding)
20. [XSS Attack](#xss-attack)
21. [Service Worker](#service-worker)

---

## Introduction

**JavaScript (JS)** is a **high-level**, **interpreted**, and **dynamic programming language** primarily used for creating interactive web pages.  
It runs in the browser and  also run on the **server side** using environments like **Node.js**.

### ⚙️ Core Characteristics

| **Feature** | **Description** |
|--------------|----------------|
| **Single-Threaded** | JavaScript executes one task at a time in a single call stack. It handles multiple tasks through asynchronous operations (like callbacks, promises, and async/await). |
| **Event-Driven** | JavaScript reacts to events (like clicks, inputs, or server responses) via the **event loop**, which manages queued tasks efficiently. |
| **Non-Blocking I/O** | Instead of waiting for a task (like reading a file) to complete, JavaScript continues executing other code and handles the result later — improving performance. |
| **Interpreted** | Code is executed line by line by the JavaScript engine (like V8 in Chrome), without the need for pre-compilation. |
| **Prototype-Based** | Objects can inherit directly from other objects — enabling flexible and reusable code structures. |
| **Dynamically Typed** | Variable types are determined at runtime, meaning a variable can hold different types of data at different times. |
| **Cross-Platform** | Runs on browsers, servers, desktops, and even IoT devices — making it one of the most versatile languages. |

---

## Normal Feature & ES6 Feature

### 🧩 Overview
Before **ES6 (ECMAScript 2015)**, JavaScript had many limitations such as function-based scoping, callback hell, and lack of modularity.  
**ES6+** introduced modern features that made JavaScript more powerful, readable, and developer-friendly.

### 🔍 Comparison Table

| **Feature** | **Pre-ES6** | **ES6+** |
|--------------|--------------|-----------|
| **Variable Declaration** | `var` | `let`, `const` |
| **Functions** | Normal functions | Arrow functions, Default parameters |
| **Strings** | Concatenation using `+` | Template literals using backticks `` ` `` |
| **Loops** | `for`, `while` | `for...of`, `for...in` |
| **Modules** | No module system | `import`, `export` |
| **Objects** | Manual key-value creation | Object shorthand, destructuring |
| **Classes** | Prototype-based functions | `class` syntax |
| **Promises** | Callback-based async handling | `Promise`, `async/await` |

---

## Variable (let, var, const) & Their Differences 
In JavaScript, variables can be declared using **`var`**, **`let`**, or **`const`**.  
The difference lies mainly in their **scope**, **hoisting behavior**, and **mutability**.

### 📊 Comparison Table

| **Feature** | **var** | **let** | **const** |
|--------------|----------|----------|------------|
| **Scope** | Function-scoped | Block-scoped | Block-scoped |
| **Hoisting** | ✅ Hoisted (initialized as `undefined`) | ✅ Hoisted (in **TDZ** – Temporal Dead Zone) | ✅ Hoisted (in **TDZ**) |
| **Reassign** | ✅ Allowed | ✅ Allowed | ❌ Not allowed |
| **Redeclare** | ✅ Allowed | ❌ Not allowed | ❌ Not allowed |
| **Initialization** | Optional | Optional | Mandatory |
| **Best Use Case** | Legacy / function-level variables | Mutable variables (loops, reassignments) | Constants / configuration values |

> ⚠️ **TDZ (Temporal Dead Zone):**  
> A period between variable hoisting and its declaration where the variable exists but **cannot be accessed**.  
> Accessing it before declaration results in a **ReferenceError**.

---

## Data Type & Type Casting

### 🧩 Overview
JavaScript data types define the **kind of value** a variable can hold.  
They are divided into **two main categories:**

### 📘 1. Primitive Data Types
Primitive types are **immutable** (cannot be changed) and stored **by value**.

| **Type** | **Example** | **Description** |
|-----------|--------------|-----------------|
| **String** | `"Hello"` | Sequence of characters |
| **Number** | `42`, `3.14` | Integer or floating point |
| **Boolean** | `true`, `false` | Logical value |
| **Null** | `null` | Intentional empty value |
| **Undefined** | `undefined` | Declared but not assigned |
| **BigInt** | `123n` | Represents integers larger than `2^53 - 1` |
| **Symbol** | `Symbol("id")` | Unique and immutable identifier |

#### 🧠 Example
```javascript
let name = "Alice";         // String
let age = 25;               // Number
let isLoggedIn = true;      // Boolean
let emptyValue = null;      // Null
let notAssigned;            // Undefined
let bigNumber = 12345678901234567890n; // BigInt
let uniqueKey = Symbol("id"); // Symbol

console.log(typeof name); // "string"
```

### 🧱 2. Non-Primitive Data Types

Non-primitives are **mutable** and stored **by reference** (pointing to memory locations).

#### 📦 Types of Non-Primitive Data

| Type | Example | Description |
|------|----------|-------------|
| **Object** | `{ name: "John", age: 30 }` | Collection of key-value pairs |
| **Array** | `[1, 2, 3]` | Ordered list of elements |
| **Function** | `function greet() {}` | Reusable block of code |

#### 💡 Example

```js
let user = { name: "Alice", age: 25 }; // Object
let numbers = [1, 2, 3];               // Array
function greet() {                     // Function
  return "Hello!";
}

console.log(typeof user);    // "object"
console.log(typeof numbers); // "object"
console.log(typeof greet);   // "function"
```

### 🔄 Type Casting (Type Conversion)

JavaScript **automatically** or **manually** converts values between data types.

#### 🧠 Conversion Types

| Conversion Type | Example | Result |
|------------------|----------|---------|
| **String → Number** | `Number("10")` | `10` |
| **Number → String** | `String(20)` | `"20"` |
| **Any → Boolean** | `Boolean(0)` | `false` |
| **Implicit (auto)** | `"5" * 2` | `10` |
| **Explicit (manual)** | `parseInt("100")` | `100` |

#### ⚙️ Example

```js
let a = "10";
let num = Number(a);   // Explicit conversion
let str = String(20);  // Explicit conversion
let bool = Boolean(0); // false

console.log(typeof num, typeof str, bool); // number string false
```



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

---

## Operator

### 🧩 Overview

Operators are symbols used to perform operations on variables and values.  
JavaScript supports several types of operators: **Arithmetic**, **Assignment**, **Comparison**, **Logical**, **Bitwise**, **Ternary**, and **Type** operators.

### ➕ 1. Arithmetic Operators

Used to perform mathematical calculations.

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| + | Addition | `5 + 2` | `7` |
| - | Subtraction | `5 - 2` | `3` |
| * | Multiplication | `5 * 2` | `10` |
| / | Division | `5 / 2` | `2.5` |
| % | Modulus (Remainder) | `5 % 2` | `1` |
| ** | Exponentiation | `2 ** 3` | `8` |
| ++ | Increment | `let a = 5; a++` | `6` |
| -- | Decrement | `let a = 5; a--` | `4` |

**Example:**
```js
let x = 10, y = 3;
console.log(x + y);  // 13
console.log(x ** y); // 1000
console.log(x % y);  // 1
```

### 📝 2. Assignment Operators

Used to assign or update values.

| Operator | Example | Same As |
|-----------|----------|----------|
| = | `x = 10` | Assign value |
| += | `x += 5` | `x = x + 5` |
| -= | `x -= 3` | `x = x - 3` |
| *= | `x *= 2` | `x = x * 2` |
| /= | `x /= 4` | `x = x / 4` |
| %= | `x %= 2` | `x = x % 2` |

**Example:**
```js
let a = 5;
a += 3; // a = 8
a *= 2; // a = 16
```

### ⚖️ 3. Comparison Operators

Used to compare two values and return a Boolean (`true` / `false`).

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| == | Equal to (value only) | `5 == "5"` | `true` |
| === | Strict equal (value + type) | `5 === "5"` | `false` |
| != | Not equal (value only) | `5 != "5"` | `false` |
| !== | Strict not equal | `5 !== "5"` | `true` |
| > | Greater than | `10 > 5` | `true` |
| < | Less than | `10 < 5` | `false` |
| >= | Greater than or equal | `5 >= 5` | `true` |
| <= | Less than or equal | `4 <= 3` | `false` |

**Example:**
```js
console.log(5 == "5");  // true
console.log(5 === "5"); // false
```

### 🔗 4. Logical Operators

Used to combine or invert Boolean expressions.

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| && | Logical AND | `true && false` | `false` |
| \|\| | Logical OR | `true || false` | `true` |
| ! | Logical NOT | `!true` | `false` |

**Example:**
```js
let a = true, b = false;
console.log(a && b); // false
console.log(a || b); // true
console.log(!a);     // false
```

### ⚙️ 5. Bitwise Operators

Operate on binary (bit-level) representations of numbers.

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| & | AND | `5 & 1` | `1` |
| \| | OR | `5 \| 1` | `5` |
| ^ | XOR | `5 ^ 1` | `4` |
| ~ | NOT | `~5` | `-6` |
| << | Left shift | `5 << 1` | `10` |
| >> | Right shift | `5 >> 1` | `2` |

**Example:**
```js
console.log(5 & 1); // 1
console.log(5 | 1); // 5
console.log(5 ^ 1); // 4
console.log(~5);    // -6
console.log(5 << 1); // 10
console.log(5 >> 1); // 2
```

### ❓ 6. Ternary Operator

A shorthand for `if-else` statements.

| Syntax | Example | Result |
|---------|----------|--------|
| `condition ? valueIfTrue : valueIfFalse` | `age >= 18 ? "Adult" : "Minor"` | `"Adult"` |

**Example:**
```js
let age = 20;
let type = age >= 18 ? "Adult" : "Minor";
console.log(type); // "Adult"
```

### 🧠 7. Type Operators

Used to check or manipulate data types in JavaScript.

| Operator | Description | Example | Result |
|-----------|--------------|----------|--------|
| typeof | Returns the variable type | `typeof "Hello"` | `"string"` |
| instanceof | Checks if an object is an instance of a class | `arr instanceof Array` | `true` |

**Example:**
```js
let arr = [1, 2, 3];
console.log(typeof arr);           // "object"
console.log(arr instanceof Array); // true
```

---

## Conditional

### 📚 Overview
Conditional statements in JavaScript are used to perform different actions based on different conditions.  
They help control the flow of execution in your program.

JavaScript supports the following conditional statements:
- `if` statement  
- `if...else` statement  
- `switch` statement  
- `ternary (?:)` operator  

### 🔹 if Statement

#### 🧩 Syntax
```javascript
if (condition) {
  // code to execute if condition is true
}
```
#### Example 
```
let age = 18;

if (age >= 18) {
  console.log("You are eligible to vote.");
}
```

### 🔹 if-else Statement

#### 🧩 Syntax
```javascript
if (condition) {
  // code executes if condition is true
} else {
  // code executes if condition is false
}
```
#### Example 
```
let isRaining = true;

if (isRaining) {
  console.log("Take an umbrella!");
} else {
  console.log("Enjoy the sunshine!");
}
```

### 🔹 if-else if Ladder

#### 🧩 Syntax
```javascript
if (condition1) {
  // code executes if condition1 is true
} else if (condition2) {
  // code executes if condition2 is true
} else {
  // executes if none of the above are true
}
```
#### Example 
```
let marks = 85;

if (marks >= 90) {
  console.log("Grade: A");
} else if (marks >= 75) {
  console.log("Grade: B");
} else {
  console.log("Grade: C");
}
```

### 🔹 switch Statement

#### 🧩 Syntax
```javascript
switch (expression) {
  case value1:
    // code block
    break;

  case value2:
    // code block
    break;

  default:
    // code block
}
```
#### Example 
```
let day = "Tuesday";

switch (day) {
  case "Monday":
    console.log("Start of the week");
    break;
  case "Tuesday":
    console.log("Second day of the week");
    break;
  case "Friday":
    console.log("Weekend is near!");
    break;
  default:
    console.log("Just another day");
}
```

### 🔹Ternary Operator (?:)

#### 🧩 Syntax
```javascript
condition ? expressionIfTrue : expressionIfFalse;
```
#### Example 
```
let age = 20;
let message = (age >= 18) ? "Adult" : "Minor";

console.log(message);
```

---

## Loops

### 📚 Overview
Loops in JavaScript are used to execute a block of code repeatedly as long as a specified condition is true.

JavaScript supports several types of loops:
- `for` loop  
- `while` loop  
- `do...while` loop  
- `for...in` loop  
- `for...of` loop  

### 🔹 for Loop

#### 🧩 Syntax
```bash
for (initialization; condition; increment/decrement) {
  // code block to be executed
}
```
#### Example 
```
for (let i = 1; i <= 5; i++) {
  console.log("Count:", i);
}
OUTPUT:1,2,3,4,5
```

### 🔹 while Loop

#### 🧩 Syntax
```bash
while (condition) {
  // code block to be executed
}
```
#### Example 
```
let i = 1;

while (i <= 5) {
  console.log("Number:", i);
  i++;
}
OUTPUT:1,2,3,4,5
```

### 🔹 do...while Loop

#### 🧩 Syntax
```bash
do {
  // code block
} while (condition);
```
#### Example 
```
let i = 1;

do {
  console.log("Iteration:", i);
  i++;
} while (i <= 5);
OUTPUT:1,2,3,4,5
```

### 🔹for...in Loop

#### 🧩 Syntax
```bash
for (key in object) {
  // code to execute
}
```
#### Example 
```
const user = { name: "John", age: 25, city: "Delhi" };

for (let key in user) {
  console.log(key + ":", user[key]);
OUTPUT:name: John
```

### 🔹for...of Loop

#### 🧩 Syntax
```bash
for (variable of iterable) {
  // code block
}
```
#### Example 
```
const fruits = ["Apple", "Banana", "Mango"];

for (let fruit of fruits) {
  console.log(fruit);
}
OUTPUT:name: Apple,Banana,Mango

```

### 🔹Nested Loops

#### Example 
```
for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 2; j++) {
    console.log(`i=${i}, j=${j}`);
  }
}

```

### 🔹break and continue

#### Example (break) 
```
for (let i = 1; i <= 5; i++) {
  if (i === 3) break;
  console.log(i);
}
output- 1,2

```

#### Example (continue) 
```
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue;
  console.log(i);
}
output- 1,2,4,5

```





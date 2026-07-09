# Tasks: JavaScript Basics

## Task 1: Variables and Data Types
**Purpose:** Understand variable declaration and data types in JavaScript.

**Skills:** let, const, var, data types.

**Theory:** `let` declares block-scoped variables, `const` declares constants that cannot be reassigned. JavaScript has dynamic typing with types including string, number, boolean, object, array, and null.

**Commands:** `let name = "Alice"`, `const pi = 3.14`

---

## Task 2: Functions
**Purpose:** Write functions using different syntax styles.

**Skills:** Function declarations, arrow functions.

**Theory:** Functions can be declared with `function` keyword or as arrow functions `() => {}`. Arrow functions do not have their own `this` binding. Functions are first-class objects and can be assigned to variables.

**Commands:** `function add(a, b) { return a + b; }`, `const add = (a, b) => a + b`

---

## Task 3: DOM Manipulation
**Purpose:** Interact with webpage elements using JavaScript.

**Skills:** getElementById, addEventListener, querySelector.

**Theory:** The DOM (Document Object Model) represents page structure as a tree. `getElementById` selects an element by ID, `querySelector` uses CSS selectors, `addEventListener` attaches event handlers.

**Commands:** `document.getElementById("btn").addEventListener("click", handler)`

---

## Task 4: Async JavaScript and Fetch
**Purpose:** Make asynchronous HTTP requests.

**Skills:** fetch, Promises, then/catch, async/await.

**Theory:** `fetch()` returns a Promise that resolves to the Response object. Promises use `.then()` for success and `.catch()` for errors. `async/await` provides cleaner syntax for working with Promises.

**Commands:** `fetch(url).then(r => r.json()).then(d => console.log(d))`

---

## Task 5: Security Considerations
**Purpose:** Identify common JavaScript security issues.

**Skills:** XSS, client-side trust.

**Theory:** Cross-Site Scripting (XSS) occurs when user input is rendered without sanitisation. Never trust client-side validation as it can be bypassed. Sensitive logic should be enforced server-side.

**Commands:** None

---

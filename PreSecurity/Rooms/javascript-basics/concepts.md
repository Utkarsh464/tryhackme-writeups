# Concepts: JavaScript Basics

## 1. Variables (let, const)
`let` declares block-scoped, mutable variables. `const` declares block-scoped, immutable bindings. `var` is function-scoped and should be avoided in modern code.

## 2. Arrow Functions
A concise function syntax using `=>`. Lexically binds `this`, making it useful for callbacks and closures. Single-expression arrows omit braces and return implicitly.

## 3. DOM (Document Object Model)
A programming interface for HTML documents. The DOM represents the page as nodes and objects that can be manipulated with JavaScript to change structure, style, and content.

## 4. Event Listeners
Functions that wait for specified events (click, submit, keydown) on DOM elements. `addEventListener` attaches multiple handlers to the same element without overwriting.

## 5. Promises
Objects representing the eventual completion or failure of an asynchronous operation. States include pending, fulfilled, and rejected. `.then()` and `.catch()` handle results and errors.

## 6. async/await
Syntactic sugar over Promises. `async` functions return a Promise. `await` pauses execution until the Promise settles, allowing asynchronous code to read like synchronous code.

## 7. Cross-Site Scripting (XSS)
A vulnerability where an attacker injects malicious scripts into web pages viewed by others. Prevented by input validation, output encoding, and Content Security Policy headers.

## 8. Client-Side Trust
Never rely solely on client-side controls for security. JavaScript can be modified, disabled, or bypassed. All security-critical checks must be replicated on the server.

# Concepts: How Websites Work

## 1. HTML (HyperText Markup Language)
HTML provides the structure of a web page using elements (tags). Elements can contain text, attributes, and nested elements. A basic HTML document includes `<!DOCTYPE html>`, `<html>`, `<head>` (metadata), and `<body>` (visible content).

## 2. HTML Attributes
Attributes provide additional information about HTML elements. Common attributes include `class` (CSS class), `id` (unique identifier), `href` (link destination), `src` (image/script source), `alt` (alternative text), and `style` (inline CSS). Attributes are written as `name="value"` pairs.

## 3. HTML Comments
Comments in HTML are written as `<!-- comment -->`. They are visible in page source and can unintentionally expose sensitive information like credentials, API keys, or internal notes if developers forget to remove them before deployment.

## 4. CSS Selectors
CSS selectors determine which elements a style rule applies to. Element selectors target all instances of a tag (e.g., `p`). Class selectors (`.className`) target elements with a specific class. ID selectors (`#idName`) target a unique element. Combinators like `>` and `+` target specific relationships.

## 5. The DOM (Document Object Model)
The DOM is a programming interface that represents the page structure as a tree of objects. JavaScript can access and modify the DOM to dynamically change content, style, and structure. The DOM is live — changes are immediately reflected in the browser.

## 6. JavaScript Events
JavaScript can respond to user interactions through events: `click`, `submit`, `keydown`, `load`, `mouseover`. Event listeners are attached to DOM elements using `addEventListener()`. Events bubble up through the DOM tree unless propagation is stopped.

## 7. Cross-Site Scripting (XSS)
XSS is a vulnerability where an attacker injects malicious JavaScript into a web page viewed by other users. Stored XSS persists on the server (e.g., in comments). Reflected XSS comes from the request (e.g., in search parameters). DOM-based XSS occurs entirely on the client side.

## 8. Browser Developer Tools
DevTools (F12) provide powerful features for web development and security analysis: Elements tab (inspect/modify HTML and CSS), Console (execute JavaScript, view errors), Sources (debug JavaScript), Network (monitor HTTP requests and responses), and Application (view cookies, storage, and cache).

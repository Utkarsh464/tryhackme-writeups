# Commands: JavaScript Basics

## Browser Console

| Command | Description |
|---------|-------------|
| `console.log("text")` | Print to browser developer console |
| `console.table(arr)` | Display array/object as table |
| `console.dir(obj)` | Display interactive object properties |
| `typeof x` | Return data type of a variable |

## DOM Manipulation

| Command | Description |
|---------|-------------|
| `document.getElementById("id")` | Select element by ID |
| `document.querySelector(".class")` | Select first matching element |
| `document.querySelectorAll("div")` | Select all matching elements |
| `element.textContent = "new"` | Set element text content |
| `element.innerHTML = "<b>bold</b>"` | Set element HTML content (dangerous with user input) |
| `element.addEventListener("click", fn)` | Attach event handler |

## Fetch API

| Command | Description |
|---------|-------------|
| `fetch("/api/data")` | Make GET request |
| `fetch("/api/data", {method: "POST", body: JSON.stringify(d)})` | Make POST request |
| `fetch(url).then(r => r.json()).then(d => console.log(d))` | Fetch and parse JSON |
| `async function getData() { let r = await fetch(url); return r.json(); }` | Async/await fetch wrapper |

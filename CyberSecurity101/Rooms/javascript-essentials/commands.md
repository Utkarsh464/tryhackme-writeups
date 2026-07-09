# JavaScript Essentials - Commands

## Browser Console Shortcuts

| Key Binding | Description |
|-------------|-------------|
| `F12` | Open developer tools |
| `Ctrl+Shift+I` | Open developer tools (Chrome/Edge) |
| `Ctrl+Shift+K` | Open developer tools Console (Firefox) |
| `Ctrl+Shift+J` | Open developer tools Console (Chrome) |
| `Ctrl+L` | Clear the console |
| `Shift+Enter` | Multi-line input in console |

## Console API Commands

| Command | Description |
|---------|-------------|
| `console.log("text")` | Print a message to the console |
| `console.error("error")` | Print an error message with red styling |
| `console.warn("warning")` | Print a warning message with yellow styling |
| `console.table([obj1, obj2])` | Display data as a table |
| `console.dir(element)` | Display an interactive tree of an object |
| `console.clear()` | Clear the console output |
| `console.group("label")` | Group related console messages |
| `console.time("label")` | Start a timer for performance measurement |
| `console.timeEnd("label")` | End a timer and log the elapsed time |

## Common JavaScript Snippets

| Code | Description |
|------|-------------|
| `typeof variable` | Check the data type of a variable |
| `document.cookie` | View cookies accessible to JavaScript |
| `document.getElementById("id")` | Select an element by ID |
| `document.querySelector("selector")` | Select first element matching CSS selector |
| `JSON.parse(jsonString)` | Parse JSON string to JavaScript object |
| `JSON.stringify(obj)` | Convert JavaScript object to JSON string |
| `fetch(url).then(r => r.json())` | Make a GET request and parse JSON response |
| `setTimeout(fn, ms)` | Execute a function after a delay |
| `setInterval(fn, ms)` | Execute a function repeatedly at intervals |

## Debugger Commands

| Command | Description |
|---------|-------------|
| `debugger;` | Set a breakpoint in code (pauses execution) |
| `F10` | Step over next function call |
| `F11` | Step into next function call |
| `Shift+F11` | Step out of current function |
| `F8` | Resume script execution |

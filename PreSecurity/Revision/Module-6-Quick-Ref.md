# Module 6: Software Basics — Quick Reference

## Key Concepts
- **Binary**: Base-2 number system (0,1) — how computers represent data
- **Hexadecimal**: Base-16 (0-9, A-F) — shorthand for binary, e.g., 0xFF = 255
- **Python**: High-level, interpreted, dynamically typed — great for scripting, automation, pentesting
- **JavaScript**: Client-side scripting for web, runs in browser, event-driven, async (Node.js for server-side)
- **SQL**: Structured Query Language — manage relational databases (MySQL, PostgreSQL, SQLite)
- **Data Types**: Integer, Float, String, Boolean, Array/List, Object/Dict, Null

## Python Basics
| Syntax | Purpose |
|--------|---------|
| `print("hello")` | Output |
| `input("prompt")` | User input |
| `if/elif/else` | Conditionals |
| `for x in list:` | Loops |
| `def func():` | Define function |
| `import module` | Import module |
| `open("file","r")` | File reading |
| `try/except` | Error handling |

## JavaScript Basics
| Syntax | Purpose |
|--------|---------|
| `console.log()` | Output to console |
| `let x = 5` | Variable declaration |
| `if/else if/else` | Conditionals |
| `for (let i=0; i<n; i++)` | Loop |
| `function f() {}` | Function |
| `() => {}` | Arrow function |
| `document.getElementById()` | DOM access |
| `fetch(url)` | HTTP requests |

## SQL Basics
| Command | Purpose |
|---------|---------|
| `SELECT * FROM table` | Read data |
| `INSERT INTO table VALUES (...)` | Create data |
| `UPDATE table SET col=val WHERE ...` | Update data |
| `DELETE FROM table WHERE ...` | Delete data |
| `WHERE col = 'value'` | Filter rows |
| `JOIN table2 ON table1.id = table2.fk` | Combine tables |
| `ORDER BY col ASC/DESC` | Sort results |
| `LIMIT n` | Limit rows |
| `GROUP BY col` | Aggregate groups |

## Key Terms
- **SQL Injection**: Injecting malicious SQL via user input
- **Prepared Statement**: Parameterized query that prevents SQLi
- **Variable**: Named storage for data in memory
- **Function**: Reusable block of code
- **Library**: Reusable code packaged for import
- **Framework**: Full set of tools/structure for building apps
- **API**: Defined way for software components to communicate

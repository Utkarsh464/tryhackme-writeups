# Tasks: Database SQL Basics

## Task 1: SELECT and WHERE
**Purpose:** Retrieve data from database tables.

**Skills:** SELECT, WHERE, filtering.

**Theory:** SELECT specifies columns to return; WHERE filters rows by conditions. Comparison operators (=, <>, <, >, LIKE) and logical operators (AND, OR) build complex filters.

**Commands:** `SELECT * FROM users WHERE username = 'admin'`

---

## Task 2: INSERT, UPDATE, DELETE
**Purpose:** Modify data in database tables.

**Skills:** INSERT, UPDATE, DELETE.

**Theory:** INSERT adds new rows, UPDATE modifies existing rows, DELETE removes rows. Always use WHERE with UPDATE and DELETE to avoid affecting all rows.

**Commands:** `INSERT INTO users (name, age) VALUES ('Alice', 25)`

---

## Task 3: JOINs
**Purpose:** Combine data from multiple tables.

**Skills:** INNER JOIN.

**Theory:** JOINs link tables using foreign key relationships. INNER JOIN returns only rows with matches in both tables. Other join types include LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN.

**Commands:** `SELECT * FROM orders INNER JOIN customers ON orders.cust_id = customers.id`

---

## Task 4: Aggregate Functions and GROUP BY
**Purpose:** Summarise and group data.

**Skills:** COUNT, SUM, AVG, MIN, MAX, GROUP BY, ORDER BY.

**Theory:** Aggregate functions compute a single value from a set of rows. GROUP BY groups rows sharing a value. ORDER BY sorts results ascending (ASC) or descending (DESC).

**Commands:** `SELECT department, AVG(salary) FROM employees GROUP BY department`

---

## Task 5: SQL Injection
**Purpose:** Understand how SQL injection works and how to prevent it.

**Skills:** SQL injection, parameterised queries.

**Theory:** SQL injection occurs when user input is concatenated directly into SQL statements. An attacker can break out of the query string and execute arbitrary SQL. Parameterised queries (prepared statements) separate SQL logic from data, preventing injection.

**Commands:** `SELECT * FROM users WHERE username = ? AND password = ?`

---

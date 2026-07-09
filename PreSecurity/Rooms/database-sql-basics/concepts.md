# Concepts: Database SQL Basics

## 1. SELECT
The SQL statement used to query data from a table. Can specify columns, filter with WHERE, sort with ORDER BY, and limit results with LIMIT.

## 2. WHERE
A clause that filters rows based on specified conditions. Supports operators: =, <>, <, >, <=, >=, LIKE, IN, BETWEEN, and logical AND/OR.

## 3. INSERT
Adds new rows to a table. Syntax: `INSERT INTO table (columns) VALUES (values)`. Each row is a complete record.

## 4. UPDATE
Modifies existing rows. Always include a WHERE clause to target specific rows; omitting it updates all rows.

## 5. DELETE
Removes rows from a table. Like UPDATE, WHERE is critical to avoid deleting all data.

## 6. INNER JOIN
Combines rows from two tables where a condition is met. Only rows with matching keys in both tables appear in results.

## 7. Aggregate Functions
Functions that perform calculations across multiple rows: COUNT (count rows), SUM (total), AVG (average), MIN (minimum value), MAX (maximum value).

## 8. SQL Injection
An attack where malicious SQL is inserted into query input. Caused by unsafe string concatenation. Prevented with parameterised queries, input validation, and least-privilege database accounts.

# SQL Fundamentals - Tasks

## Task 1: Introduction to Databases
- Understand what relational databases are
- Learn the difference between databases, tables, rows, and columns
- Recognize common database management systems (MySQL, PostgreSQL, SQLite, MSSQL)

## Task 2: Basic SELECT Queries
- Write SELECT statements to retrieve data from a table
- Use the asterisk (*) wildcard to select all columns
- Specify individual column names for targeted queries
- Use AS to alias column names in output

## Task 3: Filtering with WHERE
- Use the WHERE clause to filter rows based on conditions
- Combine conditions with AND and OR operators
- Use IN, BETWEEN, LIKE for flexible filtering
- Understand NULL and the IS NULL / IS NOT NULL operators

## Task 4: Sorting and Limiting
- Use ORDER BY to sort results ascending (ASC) or descending (DESC)
- Sort by multiple columns
- Use LIMIT to restrict the number of rows returned
- Combine LIMIT with OFFSET for pagination

## Task 5: Aggregate Functions
- Use COUNT to count matching rows
- Use SUM to calculate totals
- Use AVG to compute averages
- Use MIN and MAX to find extreme values
- Use DISTINCT to eliminate duplicate values

## Task 6: GROUP BY and HAVING
- Group rows using GROUP BY for aggregate analysis
- Filter groups using HAVING (similar to WHERE but for groups)
- Understand the order of execution: WHERE before GROUP BY before HAVING

## Task 7: JOIN Operations
- Understand INNER JOIN to match records in both tables
- Use LEFT JOIN to include all records from the left table
- Use RIGHT JOIN to include all records from the right table
- Understand how JOIN conditions work with ON clauses

## Task 8: Subqueries
- Write subqueries in WHERE clauses for dynamic filtering
- Use subqueries in SELECT for computed columns
- Write correlated subqueries that reference the outer query
- Understand performance implications of subqueries

## Task 9: Data Manipulation
- Insert new records with INSERT INTO
- Update existing records with UPDATE and WHERE
- Delete records with DELETE FROM
- Understand the importance of WHERE in UPDATE and DELETE

## Task 10: Database Relationships and Normalization
- Understand one-to-one, one-to-many, and many-to-many relationships
- Learn how junction tables implement many-to-many relationships
- Understand database normalization and why it matters for security
- Design simple database schemas with proper relationships

## Task 11: SQL Injection Awareness
- Understand how dynamic query construction works
- Identify places where user input enters SQL queries
- Recognize how unsanitized input can alter query logic
- Learn mitigation strategies: parameterized queries, stored procedures, input validation

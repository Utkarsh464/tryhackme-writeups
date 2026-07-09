# SQL Fundamentals - Concepts

## Relational Database Model
A relational database organizes data into tables (relations) consisting of rows (records/tuples) and columns (attributes/fields). Each table represents an entity (e.g., users, products, orders), and relationships between entities are established through keys. The relational model provides data integrity, consistency, and powerful querying capabilities through SQL. Database Management Systems (DBMS) like MySQL, PostgreSQL, SQLite, and Microsoft SQL Server implement the relational model with varying features and SQL dialects.

## Primary and Foreign Keys
A primary key is a column or combination of columns that uniquely identifies each row in a table. Primary keys must contain unique values and cannot be NULL. A foreign key is a column in one table that references the primary key of another table, establishing a link between the two tables. Foreign keys maintain referential integrity by ensuring that values in the referencing column correspond to valid values in the referenced table. Understanding key relationships is essential for writing correct JOIN queries and for identifying database structure during security assessments.

## SQL Query Execution Order
SQL queries are executed in a specific logical order that differs from their written order. The execution order is: FROM (determine source tables), JOIN (combine tables), WHERE (filter rows), GROUP BY (group rows), HAVING (filter groups), SELECT (choose columns), ORDER BY (sort results), LIMIT/OFFSET (paginate). Understanding this order is crucial for debugging queries and optimizing performance. For example, you cannot use a column alias defined in SELECT within the WHERE clause because WHERE executes before SELECT.

## JOIN Types
JOINs combine rows from two or more tables based on related columns. INNER JOIN returns rows where the join condition is true in both tables. LEFT JOIN returns all rows from the left table with matching rows from the right table (NULL in non-matching columns). RIGHT JOIN is the opposite. FULL OUTER JOIN returns all rows from both tables. CROSS JOIN produces a Cartesian product of all rows. Understanding JOIN types is critical for extracting data from normalized databases during penetration testing, especially when chaining multiple tables to retrieve sensitive information.

## SQL Injection Principles
SQL injection occurs when user input is incorporated into SQL queries without proper sanitization or parameterization. An attacker can manipulate the query structure by injecting SQL syntax through input fields. Basic techniques include breaking out of string literals with single quotes, using UNION SELECT to append results, commenting out the rest of the query with -- or #, and exploiting boolean-based or time-based blind injection when direct output is not available. SQL injection can lead to data exfiltration, authentication bypass, database modification, and in some cases, remote code execution through database features like xp_cmdshell in MSSQL.

## Database Normalization
Normalization is the process of organizing database schema to reduce redundancy and improve data integrity. First Normal Form (1NF) ensures atomic values and unique rows. Second Normal Form (2NF) removes partial dependencies. Third Normal Form (3NF) removes transitive dependencies. While normalization improves data integrity, it often results in more tables and more complex JOIN queries. Understanding the schema structure is important for security testing because highly normalized databases may require chaining multiple JOINs to access sensitive data.

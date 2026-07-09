# SQL Fundamentals - Commands

## SQL Query Commands

| Command | Description |
|---------|-------------|
| `SELECT * FROM users;` | Select all columns from the users table |
| `SELECT username, email FROM users;` | Select specific columns |
| `SELECT * FROM users WHERE id = 1;` | Filter rows with WHERE clause |
| `SELECT * FROM users WHERE username = 'admin' AND password = 'pass';` | Combine conditions with AND |
| `SELECT * FROM users WHERE username LIKE '%admin%';` | Use LIKE for pattern matching |
| `SELECT * FROM users ORDER BY id DESC;` | Sort results in descending order |
| `SELECT * FROM users LIMIT 5 OFFSET 10;` | Paginate results (skip 10, take 5) |
| `SELECT COUNT(*) FROM users;` | Count total rows |
| `SELECT AVG(salary) FROM employees;` | Calculate average of a column |
| `SELECT department, COUNT(*) FROM employees GROUP BY department;` | Group and aggregate |
| `SELECT department, COUNT(*) FROM employees GROUP BY department HAVING COUNT(*) > 5;` | Filter groups with HAVING |
| `SELECT * FROM users INNER JOIN orders ON users.id = orders.user_id;` | Inner join two tables |
| `SELECT * FROM users LEFT JOIN orders ON users.id = orders.user_id;` | Left join (all users, even without orders) |
| `SELECT * FROM users WHERE id IN (SELECT user_id FROM orders);` | Subquery in WHERE clause |
| `INSERT INTO users (username, email) VALUES ('john', 'john@example.com');` | Insert a new record |
| `UPDATE users SET email = 'new@example.com' WHERE id = 1;` | Update an existing record |
| `DELETE FROM users WHERE id = 1;` | Delete a record |
| `DROP TABLE users;` | Remove an entire table |
| `CREATE TABLE users (id INT PRIMARY KEY, username TEXT);` | Create a new table |
| `DESCRIBE users;` | Show table structure (MySQL) |
| `.tables` | List all tables (SQLite) |
| `.schema users` | Show CREATE statement for table (SQLite) |

## SQLite-specific Commands

| Command | Description |
|---------|-------------|
| `sqlite3 database.db` | Open a SQLite database file |
| `.mode column` | Display output in aligned columns |
| `.headers on` | Show column headers in output |
| `.exit` | Exit SQLite prompt |
| `.read script.sql` | Execute SQL commands from a file |

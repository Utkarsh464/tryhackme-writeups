# Commands: Database SQL Basics

## SQL Statements

| Command | Description |
|---------|-------------|
| `SELECT * FROM table` | Select all columns and rows |
| `SELECT col1, col2 FROM table WHERE condition` | Select with filtering |
| `INSERT INTO table (col1) VALUES (val1)` | Insert a new row |
| `UPDATE table SET col1 = val1 WHERE condition` | Update existing rows |
| `DELETE FROM table WHERE condition` | Delete rows |
| `SELECT * FROM t1 INNER JOIN t2 ON t1.id = t2.fk` | Inner join two tables |
| `SELECT COUNT(*) FROM table` | Count rows |
| `SELECT col, AVG(val) FROM table GROUP BY col` | Group and aggregate |
| `SELECT * FROM table ORDER BY col DESC` | Sort results descending |
| `SELECT * FROM table LIMIT 10` | Limit number of results |

## SQLite (Command Line)

| Command | Description |
|---------|-------------|
| `sqlite3 database.db` | Open SQLite database |
| `.tables` | List tables |
| `.schema table` | Show table schema |
| `.headers on` | Show column headers in output |
| `.mode column` | Format output as columns |
| `.quit` | Exit SQLite |

## MySQL (Command Line)

| Command | Description |
|---------|-------------|
| `mysql -u user -p database` | Connect to MySQL database |
| `SHOW DATABASES;` | List databases |
| `USE database;` | Select database |
| `SHOW TABLES;` | List tables |
| `DESCRIBE table;` | Show table structure |

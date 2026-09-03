---
{"dg-publish":true,"permalink":"/technologies/sql/sql-map/","dg-note-properties":{}}
---


for #BI, Big Data, data visualization, and project work**.

---

##  before #S7 

| Topic         | should know                                          |
| ------------- | ---------------------------------------------------- |
| Basic queries | `SELECT`, `WHERE`, `ORDER BY`, `LIMIT`               |
| Filtering     | `AND`, `OR`, `NOT`, `IN`, `BETWEEN`, `LIKE`          |
| Aggregation   | `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`                  |
| Grouping      | `GROUP BY`, `HAVING`                                 |
| Joins         | `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `FULL JOIN` |
| Keys          | Primary key, foreign key                             |
| Tables        | `CREATE TABLE`, `INSERT`, `UPDATE`, `DELETE`         |
| Constraints   | `NOT NULL`, `UNIQUE`, `CHECK`                        |
| Basic design  | Tables, relationships, normalization                 |

---

## before  8&9

| Topic | Why |
|---|---|
| Subqueries | Needed for analytics and cleaning |
| CTEs | Cleaner complex queries using `WITH` |
| Window functions | `ROW_NUMBER()`, `RANK()`, `SUM() OVER()` |
| Views | Reusable query logic |
| Indexes | Performance optimization |
| Transactions | `BEGIN`, `COMMIT`, `ROLLBACK` |
| Stored procedures | Automation in databases |
| Query plans | Understanding slow queries |
| Database engines | PostgreSQL, MySQL, SQLite, HiveQL, Spark SQL |

---

## Concepts learned through courses

| Course | SQL concepts learned |
|---|---|
| Business Intelligence | Data warehouses, star schema, fact tables, dimension tables, OLAP, analytical SQL, dashboards |
| Big Data | HiveQL, partitioning, large-scale querying, Spark SQL, HBase-style querying |
| Data Visualization | Preparing datasets, aggregation, time-series summaries, KPI tables |
| Information Retrieval | Structured indexing, metadata queries, search-related storage |
| Project work | Application database design, CRUD operations, reporting |

---

## Minimum #SQL

You should be able to write this:

```sql
SELECT
    category,
    COUNT(*) AS total_products,
    AVG(price) AS avg_price
FROM products
WHERE price > 100
GROUP BY category
HAVING COUNT(*) > 5
ORDER BY avg_price DESC;
```

Joins:

```sql
SELECT
    o.id,
    c.name,
    o.total
FROM orders o
JOIN customers c
    ON o.customer_id = c.id
WHERE o.created_at >= '2026-01-01';
```

Window function:

```sql
SELECT
    category,
    product,
    price,
    RANK() OVER (PARTITION BY category ORDER BY price DESC) AS rank_in_category
FROM products;
```

Before 7: master **SELECT, JOIN, GROUP BY, HAVING, subqueries, and basic database design
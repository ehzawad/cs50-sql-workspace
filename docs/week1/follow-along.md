# CS50 SQL Week 1 Follow-Along

This guide is built from the official Week 1 notes, transcript, and lecture source bundle already downloaded into this workspace.

Raw sources:

- `docs/week1/raw/lecture1-notes.html`
- `docs/week1/raw/lecture1-transcript.txt`
- `docs/week1/raw/lecture1-subtitles.srt`

## Start Here

Open the main lecture databases:

```bash
cd "$(git rev-parse --show-toplevel)"
./bin/cs50-sql cs50/week1/src1/longlist.db
./bin/cs50-sql cs50/week1/src1/sea_lions.db
```

Lecture files:

- `cs50/week1/src1/nested.sql`
- `cs50/week1/src1/joins.sql`
- `cs50/week1/src1/sets.sql`
- `cs50/week1/src1/groups.sql`

## What Week 1 Adds

Week 0 stayed inside one table. Week 1 is where SQL becomes relational.

Core ideas:

1. A real database usually spreads data across multiple tables.
2. Keys connect those tables.
3. Subqueries let one query feed another.
4. Joins merge related rows across tables.
5. Set operations compare result sets.
6. `GROUP BY` and `HAVING` summarize results by category.

## Concept Map

### Entity Relationship Diagrams

Use ER diagrams as the design-side view of SQL:

- entities become tables
- attributes become columns
- relationships become foreign keys or junction tables

In `longlist.db`, books, authors, publishers, translators, and ratings are separate things. That is why the course stops using a single flat table.

### Keys

- primary key: uniquely identifies a row
- foreign key: points at another table’s primary key

Examples:

- `books.id`
- `authors.id`
- `authored.book_id`
- `authored.author_id`

The `authored` table is a classic many-to-many bridge: one author can write many books, and one book can have many authors.

## Run In Lecture Order

### 1. Subqueries

File: `cs50/week1/src1/nested.sql`

What to learn:

- use a query inside another query when you need an ID first
- `IN (...)` handles multiple matches cleanly
- deeply nested queries work, but readability drops quickly

Good mental model:

- inner query finds the identifier
- outer query uses that identifier

### 2. Joins

File: `cs50/week1/src1/joins.sql`

What to learn:

- `JOIN ... ON ...` is the standard way to combine related tables
- `LEFT JOIN` keeps rows from the left table even when matches are missing
- `RIGHT JOIN` and `FULL JOIN` are useful conceptually, even if you do not use them often in SQLite work
- `NATURAL JOIN` is short, but explicit join columns are safer

Use joins when you want one result table containing columns from multiple tables.

### 3. Sets

File: `cs50/week1/src1/sets.sql`

What to learn:

- `UNION`: combine results
- `INTERSECT`: keep only shared rows
- `EXCEPT`: subtract one result set from another

These are useful when you are thinking in terms of row sets instead of table relationships.

### 4. Groups

File: `cs50/week1/src1/groups.sql`

What to learn:

- `GROUP BY` creates buckets
- aggregate functions run per bucket
- `HAVING` filters after aggregation

Typical pattern:

```sql
SELECT "book_id", ROUND(AVG("rating"), 2) AS "average rating"
FROM "ratings"
GROUP BY "book_id";
```

## PSet Readiness

Week 1 problem sets are mostly about reading schemas, joining correctly, and writing disciplined query logs. Before moving on, make sure you can:

- read `.schema` output without getting lost
- identify bridge tables for many-to-many relationships
- choose between subqueries and joins
- use `GROUP BY`, `HAVING`, and `ORDER BY` together

# CS50 SQL Week 0 Follow-Along

This is a local replacement for watching Week 0 video straight through.

It is built from:

- the official Week 0 notes
- the official Week 0 transcript
- the official Week 0 source code bundle already downloaded into this workspace

Official source files saved locally:

- `docs/week0/raw/lecture0-notes.html`
- `docs/week0/raw/lecture0-transcript.txt`
- `docs/week0/raw/lecture0-subtitles.srt`

## Start here

Open the lecture database:

```bash
cd /home/synesis/sql
./bin/cs50-sql week0
```

Useful shell shortcuts inside SQLite:

```sql
.tables
.quit
```

The main Week 0 database is:

```text
cs50/week0/src0/longlist.db
```

The lecture example files are here:

```text
cs50/week0/src0/0-SELECT.sql
cs50/week0/src0/1-LIMIT.sql
cs50/week0/src0/2-WHERE.sql
cs50/week0/src0/3-NULL.sql
cs50/week0/src0/4-LIKE.sql
cs50/week0/src0/5-compound.sql
cs50/week0/src0/6-range.sql
cs50/week0/src0/7-dates.sql
cs50/week0/src0/8-ORDER BY.sql
cs50/week0/src0/9-aggregate.sql
```

## What Week 0 is actually teaching

Week 0 is not really about memorizing syntax. It is teaching you a model:

1. Data lives in tables.
2. Each row is one thing.
3. Each column is one attribute of that thing.
4. SQL lets you ask better and better questions about those rows.

The first lecture stays inside one table, `longlist`, so you can focus on querying before learning joins or schema design.

## Core concepts

### 1. Table, row, column

Use this mental model for everything:

- table = collection of similar things
- row = one instance of that thing
- column = one property of that thing

For `longlist.db`:

- table: `longlist`
- one row: one longlisted book
- columns: `title`, `author`, `year`, `rating`, `votes`, `translator`, `publisher`, `pages`, `published`, etc.

### 2. Database vs spreadsheet

The lecture’s argument for databases over spreadsheets is straightforward:

- scale: databases handle much larger datasets
- update capacity: many reads/writes per second
- speed: better querying and lookup strategies than manual find operations

### 3. CRUD

A database supports four basic operations:

- create
- read
- update
- delete

Week 0 is mostly about the `read` part: querying data that already exists.

### 4. DBMS and SQLite

A DBMS is the software layer you use to interact with the database.

In this course:

- SQLite is the DBMS
- SQL is the language

SQLite is lightweight and good for learning because you can work directly on a single `.db` file.

### 5. SQL style rules used in the course

Follow these conventions:

- SQL keywords in uppercase: `SELECT`, `FROM`, `WHERE`
- identifiers in double quotes: `"title"`, `"longlist"`
- string literals in single quotes: `'hardcover'`, `'Fernanda Melchor'`

Examples:

```sql
SELECT "title"
FROM "longlist"
WHERE "format" = 'hardcover';
```

## Query flow, in lecture order

Run these in order. The numbered file beside each section matches the local example file.

### 1. `SELECT`

File:

```text
cs50/week0/src0/0-SELECT.sql
```

Use `SELECT` to choose columns and `FROM` to choose a table.

Start broad:

```sql
SELECT *
FROM "longlist";
```

Then narrow:

```sql
SELECT "title"
FROM "longlist";
```

Or choose multiple columns:

```sql
SELECT "title", "author"
FROM "longlist";
```

What to notice:

- `*` means all columns
- selecting fewer columns makes results easier to read
- SQL is declarative: you say what you want, not how to loop through rows

Practice:

```sql
SELECT "title", "author", "year"
FROM "longlist";
```

### 2. `LIMIT`

File:

```text
cs50/week0/src0/1-LIMIT.sql
```

Use `LIMIT` to cap result size.

```sql
SELECT "title", "author"
FROM "longlist"
LIMIT 10;
```

What to notice:

- this is only a slice of the result set
- without `ORDER BY`, “first 10” means first 10 in the database’s current order, not necessarily meaningful order

Practice:

```sql
SELECT "title"
FROM "longlist"
LIMIT 5;
```

### 3. `WHERE`

File:

```text
cs50/week0/src0/2-WHERE.sql
```

`WHERE` filters rows by condition.

```sql
SELECT "title", "author"
FROM "longlist"
WHERE "year" = 2023;
```

Other comparisons from the lecture:

```sql
WHERE "format" != 'hardcover'
WHERE "format" <> 'hardcover'
WHERE NOT "format" = 'hardcover'
```

What to notice:

- numeric values are not quoted
- strings are quoted
- `!=` and `<>` both mean “not equal”
- `NOT` can invert a condition

Practice:

```sql
SELECT "title", "format"
FROM "longlist"
WHERE "format" != 'hardcover';
```

### 4. Compound conditions with `AND`, `OR`, and parentheses

File:

```text
cs50/week0/src0/5-compound.sql
```

```sql
SELECT "title", "format"
FROM "longlist"
WHERE ("year" = 2022 OR "year" = 2023)
  AND "format" != 'hardcover';
```

What to notice:

- parentheses make intent explicit
- once conditions get more complex, readability matters

Practice:

```sql
SELECT "title", "author", "year"
FROM "longlist"
WHERE "year" = 2022 OR "year" = 2023;
```

### 5. `NULL`

File:

```text
cs50/week0/src0/3-NULL.sql
```

Missing data is not an empty string and not zero. It is `NULL`.

```sql
SELECT "title", "translator"
FROM "longlist"
WHERE "translator" IS NULL;
```

And the inverse:

```sql
SELECT "title", "translator"
FROM "longlist"
WHERE "translator" IS NOT NULL;
```

What to notice:

- use `IS NULL`, not `= NULL`
- use `IS NOT NULL`, not `!= NULL`

Practice:

```sql
SELECT "title", "publisher"
FROM "longlist"
WHERE "publisher" IS NULL;
```

### 6. Pattern matching with `LIKE`

File:

```text
cs50/week0/src0/4-LIKE.sql
```

Use `LIKE` for rough string matching.

Contains:

```sql
SELECT "title"
FROM "longlist"
WHERE "title" LIKE '%love%';
```

Starts with:

```sql
SELECT "title"
FROM "longlist"
WHERE "title" LIKE 'The %';
```

Single-character wildcard:

```sql
SELECT "title"
FROM "longlist"
WHERE "title" LIKE 'P_re';
```

Wildcards:

- `%` = any sequence of characters
- `_` = exactly one character

Important Week 0 behavior:

- in SQLite, `LIKE` is case-insensitive by default
- `=` is case-sensitive for strings in this lecture’s setup

That means:

```sql
SELECT "title"
FROM "longlist"
WHERE "title" LIKE 'pyre';
```

can match `Pyre`, but:

```sql
SELECT "title"
FROM "longlist"
WHERE "title" = 'pyre';
```

does not.

Practice:

```sql
SELECT "title"
FROM "longlist"
WHERE "title" LIKE 'The%love%';
```

### 7. Range conditions

File:

```text
cs50/week0/src0/6-range.sql
```

Use comparison operators:

```sql
SELECT "title", "year"
FROM "longlist"
WHERE "year" >= 2019 AND "year" <= 2022;
```

Or use `BETWEEN`:

```sql
SELECT "title", "year"
FROM "longlist"
WHERE "year" BETWEEN 2019 AND 2022;
```

Other examples:

```sql
SELECT "title", "rating"
FROM "longlist"
WHERE "rating" > 4.0;

SELECT "title", "pages"
FROM "longlist"
WHERE "pages" < 300;
```

What to notice:

- `BETWEEN` is inclusive
- range queries work for integers, dates, and real numbers

### 8. Dates are queryable too

File:

```text
cs50/week0/src0/7-dates.sql
```

The lecture also shows that dates can be filtered as ranges:

```sql
SELECT "title", "published"
FROM "longlist"
WHERE "published" BETWEEN date('2022-05-01') AND date('2022-08-01');
```

What to notice:

- dates are still values you can compare
- this becomes more important later when working with real datasets

### 9. `ORDER BY`

File:

```text
cs50/week0/src0/8-ORDER BY.sql
```

Use `ORDER BY` to sort results.

Default sort is ascending:

```sql
SELECT "title", "rating"
FROM "longlist"
ORDER BY "rating"
LIMIT 10;
```

For highest-rated books, use descending order:

```sql
SELECT "title", "rating"
FROM "longlist"
ORDER BY "rating" DESC
LIMIT 10;
```

Break ties with another column:

```sql
SELECT "title", "rating", "votes"
FROM "longlist"
ORDER BY "rating" DESC, "votes" DESC
LIMIT 10;
```

What to notice:

- `ORDER BY` happens before `LIMIT` in how you should think about the result
- the default is ascending
- sorting by multiple columns is normal and important

Text sorting example:

```sql
SELECT "title"
FROM "longlist"
ORDER BY "title";
```

### 10. Aggregate functions

File:

```text
cs50/week0/src0/9-aggregate.sql
```

Aggregate functions reduce many rows to one result.

Examples from Week 0:

```sql
SELECT AVG("rating")
FROM "longlist";

SELECT MAX("rating")
FROM "longlist";

SELECT MIN("rating")
FROM "longlist";

SELECT SUM("votes")
FROM "longlist";

SELECT COUNT(*)
FROM "longlist";
```

Rounded average:

```sql
SELECT ROUND(AVG("rating"), 2)
FROM "longlist";
```

Prettier column name:

```sql
SELECT ROUND(AVG("rating"), 2) AS "Average Rating"
FROM "longlist";
```

What to notice:

- `AVG`, `MAX`, `MIN`, `SUM`, `COUNT` are aggregate functions
- `ROUND(value, digits)` is useful after aggregates
- `AS` renames ugly output columns into readable ones

## The gotchas worth remembering

These are the details from the lecture that are easy to miss.

### `COUNT(*)` vs `COUNT(column)`

These are different:

```sql
SELECT COUNT(*)
FROM "longlist";

SELECT COUNT("translator")
FROM "longlist";
```

`COUNT(*)` counts rows.

`COUNT("translator")` counts non-`NULL` translator values.

That is why the lecture gets 78 books but only 76 translators.

### `DISTINCT`

If you want unique values, use `DISTINCT`.

```sql
SELECT COUNT(DISTINCT "publisher")
FROM "longlist";
```

Without `DISTINCT`, duplicates are counted repeatedly.

### `MAX` and `MIN` on text do not mean longest/shortest

On strings, `MAX` and `MIN` are alphabetical comparisons, not length comparisons.

So:

```sql
SELECT MAX("title"), MIN("title")
FROM "longlist";
```

is about lexicographic order, not string length.

### Quoting matters

- double quotes: identifiers
- single quotes: strings

One subtle SQLite oddity from the transcript: if you mistype a double-quoted column name badly enough, SQLite can behave in a surprising way instead of giving the clean error you expected. Keep identifiers accurate.

## A practical route through the lecture

If you want the shortest useful path, do this:

1. Open the DB:

```bash
./bin/cs50-sql week0
```

2. Run the numbered example files in order by copy/pasting the queries from:

```text
cs50/week0/src0/0-SELECT.sql
...
cs50/week0/src0/9-aggregate.sql
```

3. After each section, answer one question in plain English:

- What rows am I selecting?
- What columns am I returning?
- What condition is filtering rows?
- What order are results in?
- Am I asking for raw rows or one aggregate result?

If you can answer those five questions for a query, you understand it.

## Suggested self-checks

Try these without looking at the files first.

### Self-check 1

Find titles and authors for books in 2023.

### Self-check 2

Find books without translators.

### Self-check 3

Find titles containing the word `love`.

### Self-check 4

Find books from 2019 through 2022.

### Self-check 5

Find the top 5 books by rating, breaking ties by votes.

### Self-check 6

Find the average rating rounded to two decimal places and label the output column.

## When you are done with Week 0

If the following are easy, you are ready for Problem Set 0:

- you know when to use `SELECT`, `WHERE`, `ORDER BY`, `LIMIT`
- you understand `NULL`
- you can use `LIKE` with `%` and `_`
- you know `BETWEEN` is inclusive
- you know `COUNT(column)` skips `NULL`
- you know `DISTINCT` removes duplicates

## Quick commands

Open the lecture database:

```bash
./bin/cs50-sql week0
```

Preview result shape:

```sql
SELECT *
FROM "longlist"
LIMIT 3;
```

Leave SQLite:

```sql
.quit
```

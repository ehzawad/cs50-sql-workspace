# CS50 SQL Week 2 Follow-Along

This guide is built from the official Week 2 notes, transcript, and source files.

Raw sources:

- `docs/week2/raw/lecture2-notes.html`
- `docs/week2/raw/lecture2-transcript.txt`
- `docs/week2/raw/lecture2-subtitles.srt`

## Start Here

Week 2 is mostly schema work, not query work. The lecture source is a sequence of schema revisions.

Source directories:

- `cs50/week2/src2/schema/`
- `cs50/week2/src2/alter/`

Quick interactive loop:

```bash
cd "$(git rev-parse --show-toplevel)"
./bin/sqlite3 cs50/week2/src2/mbta.db
```

Inside SQLite, read a schema file, inspect it, then quit:

```sql
.read cs50/week2/src2/schema/schema0.sql
.schema
.quit
```

Then reopen and try another version, such as `schema4.sql` or `schema7.sql`.

## What Week 2 Adds

Week 2 is about designing tables before data exists.

Core ideas:

1. Start from entities and relationships.
2. Choose stable keys.
3. Pick column types intentionally.
4. Add constraints so bad data becomes impossible, not just discouraged.
5. Expect schemas to evolve over time.

## Concept Map

### Schema Design

The MBTA example evolves from a loose sketch into a stricter schema.

Watch the progression:

- `schema0.sql`: almost no type or constraint discipline
- `schema4.sql`: proper IDs, `NOT NULL`, `UNIQUE`, foreign keys
- `schema7.sql`: adds `CHECK` constraints and defaults

That progression is the point of the week.

### Types and Affinities

SQLite is permissive, but type choices still matter.

Use this as the practical rule:

- `INTEGER` for IDs and whole-number counters
- `TEXT` for names and labels
- `NUMERIC` for timestamps, amounts, or values that may need numeric behavior

The notes also distinguish:

- storage classes: how SQLite stores values
- type affinities: how SQLite tries to interpret values

You do not need to memorize every nuance yet. You do need to understand that SQLite is more flexible than server databases.

### Constraints

Week 2 is where data integrity starts.

Useful constraints:

- `PRIMARY KEY`
- `FOREIGN KEY`
- `NOT NULL`
- `UNIQUE`
- `CHECK`
- `DEFAULT`

These matter because they move correctness into the database itself.

## Run In Lecture Order

### 1. Schema revisions

Read these in order:

- `cs50/week2/src2/schema/schema0.sql`
- `cs50/week2/src2/schema/schema1.sql`
- `cs50/week2/src2/schema/schema2.sql`
- `cs50/week2/src2/schema/schema3.sql`
- `cs50/week2/src2/schema/schema4.sql`
- `cs50/week2/src2/schema/schema5.sql`
- `cs50/week2/src2/schema/schema6.sql`
- `cs50/week2/src2/schema/schema7.sql`

What to look for:

- where IDs become primary keys
- where names become unique
- where foreign keys appear
- where `CHECK` constraints encode business rules

### 2. Altering tables

Files:

- `cs50/week2/src2/alter/alter0.sql`
- `cs50/week2/src2/alter/alter1.sql`
- `cs50/week2/src2/alter/alter2.sql`
- `cs50/week2/src2/alter/alter3.sql`

These show how to change a live schema:

- drop a table
- rename a table
- add a column
- rename a column

## PSet Readiness

Problem Set 2 is pure schema design. Before you start it, make sure you can:

- identify many-to-many relationships and bridge tables
- choose sensible primary keys
- enforce required values with constraints
- separate entities cleanly instead of stuffing everything into one table
- explain why a design is normalized

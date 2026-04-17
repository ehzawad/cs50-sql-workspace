# CS50 SQL Week 4 Follow-Along

This guide is built from the official Week 4 notes, transcript, and source files.

Raw sources:

- `docs/week4/raw/lecture4-notes.html`
- `docs/week4/raw/lecture4-transcript.txt`
- `docs/week4/raw/lecture4-subtitles.srt`

## Start Here

Week 4 is about shaping access to data with views and related abstractions.

Useful databases:

```bash
cd "$(git rev-parse --show-toplevel)"
./bin/cs50-sql cs50/week4/src4/longlist.db
./bin/cs50-sql cs50/week4/src4/rideshare.db
./bin/cs50-sql cs50/week4/src4/network.db
./bin/cs50-sql cs50/week4/src4/mfa.db
```

Lecture files:

- `cs50/week4/src4/simplifying.sql`
- `cs50/week4/src4/aggregating.sql`
- `cs50/week4/src4/partitioning.sql`
- `cs50/week4/src4/securing.sql`
- `cs50/week4/src4/soft_delete.sql`
- `cs50/week4/src4/soft_deletion.sql`

## What Week 4 Adds

Core ideas:

1. A view stores a query, not duplicated data.
2. Views can hide complexity.
3. Views can expose only the part of the data that a consumer should see.
4. Temporary views and CTEs solve related problems at different scopes.

## Run In Lecture Order

### 1. Simplifying with views

File: `cs50/week4/src4/simplifying.sql`

This file shows the classic benefit of a view:

- first, write a complex join
- then wrap it in a named view
- then query that view as if it were a table

That is the move you should internalize.

### 2. Aggregating views and CTEs

File: `cs50/week4/src4/aggregating.sql`

What to learn:

- a view can represent already-aggregated data
- a temporary view is session-scoped
- a CTE is query-scoped

Practical rule:

- reuse across many queries: view
- reuse in one session: temporary view
- reuse inside one query: CTE

### 3. Partitioning

File: `cs50/week4/src4/partitioning.sql`

This is not physical sharding. It is logical partitioning through filtered views.

Example:

- view `2022`
- view `2021`

Same base table, narrower slices.

### 4. Securing and anonymizing

File: `cs50/week4/src4/securing.sql`

This is a design lesson:

- do not expose more columns than needed
- use views to anonymize sensitive fields

The `analysis` view is a simple but important pattern.

### 5. Soft deletion

Files:

- `cs50/week4/src4/soft_delete.sql`
- `cs50/week4/src4/soft_deletion.sql`

Week 3 introduced the idea. Week 4 shows how views make soft deletion practical for downstream consumers.

## PSet Readiness

Before moving on, make sure you can:

- create and drop views confidently
- decide between a base table query and a view
- use CTEs without confusing them with persistent schema
- expose an analysis-safe surface over sensitive data
- explain why a soft-delete view is often better than deleting rows

# CS50 SQL Week 5 Follow-Along

This guide is built from the official Week 5 notes, transcript, and source files.

Raw sources:

- `docs/week5/raw/lecture5-notes.html`
- `docs/week5/raw/lecture5-transcript.txt`
- `docs/week5/raw/lecture5-subtitles.srt`

## Start Here

Open the lecture databases:

```bash
cd "$(git rev-parse --show-toplevel)"
./bin/cs50-sql cs50/week5/src5/index/movies.db
./bin/cs50-sql cs50/week5/src5/concurrency/bank.db
```

Lecture files:

- `cs50/week5/src5/index/where.sql`
- `cs50/week5/src5/index/nested.sql`
- `cs50/week5/src5/index/partial.sql`
- `cs50/week5/src5/index/vacuum.sql`
- `cs50/week5/src5/concurrency/transactions.sql`

## What Week 5 Adds

Week 5 is about performance and correctness under load.

Core ideas:

1. Indexes trade space and write cost for faster reads.
2. Query plans tell you whether the database is using your index.
3. Partial indexes optimize specific access patterns.
4. Transactions protect multi-step changes.
5. Concurrency bugs happen when multiple sessions see inconsistent intermediate state.

## Run In Lecture Order

### 1. Single-column indexes

File: `cs50/week5/src5/index/where.sql`

What to learn:

- time a lookup before and after an index
- inspect `.schema`
- run `EXPLAIN QUERY PLAN`

The main skill here is not memorizing `CREATE INDEX`. It is learning to verify whether an index is actually helping.

### 2. Indexes across nested or related queries

File: `cs50/week5/src5/index/nested.sql`

This continues the same lesson: indexes matter most when they line up with your actual predicates and join paths.

### 3. Partial indexes

File: `cs50/week5/src5/index/partial.sql`

Use a partial index when:

- only one slice of the table is queried frequently
- indexing the full table would be wasteful

Example from the lecture: recent-year movies only.

### 4. Vacuum

File: `cs50/week5/src5/index/vacuum.sql`

This is about maintenance after lots of write churn. Know what it does conceptually:

- rebuild/compact storage
- reclaim space
- refresh the physical layout

### 5. Transactions and concurrency

File: `cs50/week5/src5/concurrency/transactions.sql`

What to learn:

- `BEGIN TRANSACTION`
- `COMMIT`
- `ROLLBACK`
- atomicity means all-or-nothing

The bank example is the one to remember:

- without a transaction, observers can see half-finished state
- with a transaction, the change is treated as one unit

## PSet Readiness

Before moving on, make sure you can:

- read `EXPLAIN QUERY PLAN` output at a basic level
- choose candidate columns for indexing
- explain the cost side of indexes
- use transactions for multi-statement updates
- spot where concurrency could produce invalid or misleading state

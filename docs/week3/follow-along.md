# CS50 SQL Week 3 Follow-Along

This guide is built from the official Week 3 notes, transcript, and lecture source files.

Raw sources:

- `docs/week3/raw/lecture3-notes.html`
- `docs/week3/raw/lecture3-transcript.txt`

## Start Here

Week 3 is about mutating data: `INSERT`, `UPDATE`, `DELETE`, and triggers.

Source tree:

- `cs50/week3/src3/insert/`
- `cs50/week3/src3/delete/`
- `cs50/week3/src3/update/`
- `cs50/week3/src3/triggers/`

The lecture uses multiple mini-scenarios instead of one permanent database. Open a scratch database and read one file at a time:

```bash
cd "$(git rev-parse --show-toplevel)"
./bin/sqlite3 cs50/week3/src3/week3.db
```

## What Week 3 Adds

Core ideas:

1. Data is not static.
2. Writes should respect schema constraints.
3. Bulk imports are still just inserts at scale.
4. Deletes can be hard to undo, so soft deletion is often safer.
5. Triggers let the database react automatically to writes.

## Run In Lecture Order

### 1. Insert basics

Files:

- `cs50/week3/src3/schemas/insert/schema.sql`
- `cs50/week3/src3/insert/insert0.sql`
- `cs50/week3/src3/insert/insert1.sql`

What to learn:

- explicit column lists are safer than relying on position
- constraints can reject inserts
- multi-row inserts are concise and often preferable

### 2. Importing CSV data

Files:

- `cs50/week3/src3/insert/import/import0/import0.sql`
- `cs50/week3/src3/insert/import/import1/import1.sql`

Associated data:

- `cs50/week3/src3/insert/import/import0/mfa.csv`
- `cs50/week3/src3/insert/import/import1/mfa.csv`

This is the first time the course pushes you toward real-world loading workflows instead of hand-written inserts.

### 3. Deletes

Files:

- `cs50/week3/src3/schemas/delete/schema0.sql`
- `cs50/week3/src3/delete/delete0.sql`
- `cs50/week3/src3/schemas/delete/schema1.sql`
- `cs50/week3/src3/delete/delete1.sql`
- `cs50/week3/src3/schemas/delete/schema2.sql`
- `cs50/week3/src3/delete/delete2.sql`

What to learn:

- deleting parent rows can break references
- foreign keys and delete rules matter
- destructive changes deserve caution

### 4. Updates

Files:

- `cs50/week3/src3/schemas/update/schema.sql`
- `cs50/week3/src3/update/update0.sql`
- `cs50/week3/src3/update/update1.sql`

Associated data:

- `cs50/week3/src3/update/votes.csv`

Focus here on targeted changes with `WHERE`. Unscoped updates are one of the easiest ways to destroy data.

### 5. Triggers and soft deletion

Files:

- `cs50/week3/src3/schemas/triggers/schema.sql`
- `cs50/week3/src3/triggers/triggers.sql`
- `cs50/week3/src3/delete/soft/delete.sql`
- `cs50/week3/src3/delete/soft/soft_delete.sql`

What to learn:

- triggers can maintain logs or derived state automatically
- soft deletion usually means adding a boolean or status field instead of removing rows

## PSet Readiness

Before moving on, make sure you can:

- insert rows without violating constraints
- import structured data into a clean schema
- update rows safely with precise filters
- explain when hard delete is appropriate versus soft delete
- read a trigger and say exactly when it fires

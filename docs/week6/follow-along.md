# CS50 SQL Week 6 Follow-Along

This guide is built from the official Week 6 notes, transcript, and source files.

Raw sources:

- `docs/week6/raw/lecture6-notes.html`
- `docs/week6/raw/lecture6-transcript.txt`

## Start Here

Week 6 shifts from SQLite to database servers.

Local wrappers:

```bash
cd "$(git rev-parse --show-toplevel)"
./bin/mysql
./bin/psql
```

Main source directories:

- `cs50/week6/src6/mbta/`
- `cs50/week6/src6/mfa/`
- `cs50/week6/src6/access/`
- `cs50/week6/src6/injection/`
- `cs50/week6/src6/mysql/`
- `cs50/week6/src6/postgres/`
- `cs50/week6/src6/postgresql/`

## What Week 6 Adds

Core ideas:

1. SQLite is embedded; MySQL and PostgreSQL are server databases.
2. Server databases give you stronger typing, richer administration, and easier scaling.
3. Stored procedures move logic into the database server.
4. Access control matters when multiple users share the same server.
5. SQL injection is an application bug, not just a query bug.

## Run In Lecture Order

### 1. MySQL basics and types

Files:

- `cs50/week6/src6/mbta/schema.sql`
- `cs50/week6/src6/mbta/alter.sql`
- `cs50/week6/src6/mbta/load.sql`

What to notice compared with SQLite:

- `AUTO_INCREMENT`
- `VARCHAR(n)`
- `ENUM`
- `DATETIME`
- `DECIMAL(p, s)`

Use MySQL to run MBTA examples:

```sql
CREATE DATABASE IF NOT EXISTS mbta;
USE mbta;
SOURCE /workspace/cs50/week6/src6/mbta/schema.sql;
SHOW TABLES;
```

### 2. Stored procedures

Files:

- `cs50/week6/src6/mfa/schema.sql`
- `cs50/week6/src6/mfa/procedures.sql`

What to learn:

- delimiter changes are needed because procedure bodies contain `;`
- procedures can encapsulate reusable server-side logic
- parameters and explicit error signaling make procedures more robust

### 3. PostgreSQL

Files:

- `cs50/week6/src6/postgres/schema.sql`
- `cs50/week6/src6/postgres/navigate.sql`
- `cs50/week6/src6/postgresql/schema.sql`
- `cs50/week6/src6/postgresql/login.sql`

The course uses PostgreSQL to show that server databases share concepts but differ in syntax and type systems.

Key contrasts to remember:

- PostgreSQL uses `SERIAL`-style patterns rather than MySQL `AUTO_INCREMENT`
- PostgreSQL uses `NUMERIC` where MySQL examples often use `DECIMAL`
- PostgreSQL shell commands are different from MySQL shell commands

### 4. Access controls

Files:

- `cs50/week6/src6/access/schema.sql`
- `cs50/week6/src6/access/users.sql`
- `cs50/week6/src6/access/privileges.sql`

Lesson:

- do not give every application the root user
- grant only the permissions a user actually needs
- views and privileges work well together

### 5. SQL injection

Files:

- `cs50/week6/src6/injection/schema.sql`
- `cs50/week6/src6/injection/injection.sql`
- `cs50/week6/src6/injection/prepared.sql`

What to learn:

- string concatenation with user input is dangerous
- prepared statements separate query structure from user data
- the database driver is part of your security story

## PSet Readiness

Problem Set 6 is where environment setup matters.

You are ready for the psets if you can:

- open MySQL with `./bin/mysql`
- create and switch databases with `CREATE DATABASE` and `USE`
- load a schema with `SOURCE /workspace/.../schema.sql`
- explain why prepared statements stop injection attacks
- switch between SQLite, MySQL, and PostgreSQL without mixing their syntax

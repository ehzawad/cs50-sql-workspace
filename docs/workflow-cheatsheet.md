# CS50 SQL Workflow Cheat Sheet

This is the short version of the workspace.

It is split into two modes:

1. learning the course material
2. solving problem sets on your own

No solution content is included here. This is only the environment and process layer.

`<repo-root>` in the snippets below is whichever directory you cloned this repo into. Inside the repo, `cd "$(git rev-parse --show-toplevel)"` takes you there.

## 0. One-Time Orientation

Start in the workspace root:

```bash
cd "$(git rev-parse --show-toplevel)"
```

Useful index files:

- `docs/course-index.md`
- `docs/psets/index.md`

Useful tools:

```bash
./bin/doctor
./bin/cs50-sql --list
./bin/python --version
./bin/mysql
./bin/psql
./bin/check50 --help
./bin/submit50 --help
```

## 1. Learning Mode

The rule for lecture study is simple:

1. open the local follow-along guide for the week
2. run the lecture files locally
3. inspect the real schema and data yourself

### Week-by-Week Entry Points

Week 0:

```bash
cd "$(git rev-parse --show-toplevel)"
./bin/cs50-sql week0
```

Week 1:

```bash
./bin/cs50-sql cs50/week1/src1/longlist.db
./bin/cs50-sql cs50/week1/src1/sea_lions.db
```

Week 2:

```bash
./bin/sqlite3 cs50/week2/src2/mbta.db
```

Week 3:

```bash
./bin/sqlite3 cs50/week3/src3/week3.db
```

Week 4:

```bash
./bin/cs50-sql cs50/week4/src4/longlist.db
./bin/cs50-sql cs50/week4/src4/rideshare.db
```

Week 5:

```bash
./bin/cs50-sql cs50/week5/src5/index/movies.db
./bin/cs50-sql cs50/week5/src5/concurrency/bank.db
```

Week 6:

```bash
./bin/python --version
./bin/mysql
./bin/psql
```

### Study Loop

For a normal SQLite lecture week:

```sql
.tables
.schema
SELECT * FROM "some_table" LIMIT 5;
```

For lecture query files:

```sql
.read <repo-root>/cs50/week0/src0/0-SELECT.sql
.read <repo-root>/cs50/week1/src1/joins.sql
```

For schema-building weeks, use a scratch database:

```bash
./bin/sqlite3 scratch.db
```

Then:

```sql
.read <repo-root>/cs50/week2/src2/schema/schema0.sql
.schema
```

### Good Lecture Habit

For each week:

1. read `docs/weekN/follow-along.md`
2. run every source file mentioned there
3. inspect the tables after each step
4. rewrite a few sample queries manually instead of only replaying them

## 2. Problem Set Mode

The rule for psets is also simple:

1. open the correct local folder
2. work only in the starter files or blank scaffold files
3. test locally
4. run `check50`
5. submit only when you are satisfied

### Find the Right Folder

Use:

```bash
cd "$(git rev-parse --show-toplevel)"
sed -n '1,220p' docs/psets/index.md
```

### SQLite Query Psets

Typical flow:

```bash
cd <repo-root>/cs50/pset1/dese
<repo-root>/bin/sqlite3 dese.db
```

Inside SQLite:

```sql
.tables
.schema
.read 1.sql
```

If you want output redirected to a file while testing:

```bash
<repo-root>/bin/sqlite3 dese.db < 1.sql > output.txt
```

### Schema Design Psets

Typical flow:

```bash
cd <repo-root>/cs50/pset2/atl
<repo-root>/bin/sqlite3 atl.db
```

Inside SQLite:

```sql
.read schema.sql
.schema
```

The same pattern works for:

- `cs50/pset2/connect/`
- `cs50/pset2/donuts/`

### CSV / import-style Psets

Typical flow:

```bash
cd <repo-root>/cs50/pset3/meteorites
<repo-root>/bin/sqlite3 meteorites.db
```

Then use the provided `import.sql` or your own test script as needed.

### MySQL Pset

For `sentimental-connect`:

```bash
cd "$(git rev-parse --show-toplevel)"
./bin/mysql
```

Inside MySQL:

```sql
CREATE DATABASE IF NOT EXISTS linkedin;
USE linkedin;
SOURCE /workspace/cs50/pset6/sentimental-connect/schema.sql;
SHOW TABLES;
```

### Python Pset

For `dont-panic/python`:

```bash
cd <repo-root>/cs50/pset6/dont-panic/python
<repo-root>/bin/python hack.py
```

Reset the database if needed:

```bash
<repo-root>/bin/sqlite3 dont-panic.db < reset.sql
```

### Java Pset

For `dont-panic/java`:

```bash
cd <repo-root>/cs50/pset6/dont-panic/java
<repo-root>/bin/javac Hack.java
<repo-root>/bin/java -cp .:sqlite-jdbc-3.43.0.0.jar Hack
```

Reset the database if needed:

```bash
<repo-root>/bin/sqlite3 dont-panic.db < reset.sql
```

## 3. Checking and Submission

Always run these from the correct pset folder.

Examples:

```bash
cd <repo-root>/cs50/pset1/packages
<repo-root>/bin/check50 cs50/problems/2024/sql/packages
```

```bash
cd <repo-root>/cs50/pset6/sentimental-connect
<repo-root>/bin/check50 cs50/problems/2024/sql/sentimental/connect
```

Submission:

```bash
<repo-root>/bin/submit50 TARGET
```

Use `docs/psets/index.md` to get the exact `TARGET`.

## 4. Reset / Recovery

List all local SQLite databases:

```bash
cd "$(git rev-parse --show-toplevel)"
./bin/cs50-sql --list
```

Stop MySQL:

```bash
./bin/mysql-stop
```

Stop PostgreSQL:

```bash
./bin/psql-stop
```

Reopen either later with:

```bash
./bin/mysql
./bin/psql
```

Docker must be installed and running for the week 6 database wrappers.

## 5. No-Cheat Guardrails

Use the workspace like this:

- read lecture guides
- inspect schemas
- run your own queries
- write your own pset answers
- use `check50` only to verify correctness

Do not use the local docs as a substitute for your own pset work. They are set up to support the process, not to provide answers.

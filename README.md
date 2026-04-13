# CS50 SQL Local Setup

This workspace is now prepared for the full CS50 SQL course: lecture materials, raw notes and transcripts, starter problem-set files, and local database tooling.

## Start Here

- Course index: `docs/course-index.md`
- Problem set index: `docs/psets/index.md`
- Workflow cheat sheet: `docs/workflow-cheatsheet.md`
- Lecture verification report: `docs/lecture-command-verification.md`
- Week 0 guide: `docs/week0/follow-along.md`

## Local Tools

From `/home/synesis/sql`:

```bash
./bin/cs50-sql --list
./bin/cs50-sql week0
./bin/mysql
./bin/psql
./bin/check50 --help
./bin/submit50 --help
```

What each tool does:

- `./bin/sqlite3`: local SQLite CLI from the official SQLite release
- `./bin/cs50-sql`: opens a local SQLite database with `.headers on` and `.mode box`
- `./bin/mysql`: starts a local MySQL 8 server in Docker and opens the MySQL client
- `./bin/psql`: starts a local PostgreSQL server in Docker and opens `psql`
- `./bin/java`, `./bin/javac`: local JDK wrappers for the Java-based pset
- `./bin/check50`, `./bin/submit50`: wrappers around a local Python virtualenv install
- `./bin/bootstrap-workspace`: redownloads ignored/generated assets and tools
- `./bin/verify-lecture-commands`: reruns the lecture command verification pass

## Workspace Layout

- `cs50/week0` through `cs50/week6`
  - lecture source bundles
- `docs/week0` through `docs/week6`
  - follow-along guides plus raw notes, transcript, and subtitles
- `cs50/pset0` through `cs50/pset6`
  - starter files, extracted distributions, and scaffold folders
- `docs/psets/raw`
  - local copies of the official problem pages
- `downloads/`
  - original ZIP archives

## Notes

- `sqlite3` was set up locally because installing the Debian package would require your system password.
- MySQL and PostgreSQL are provided via Docker so the week 6 material works without touching system packages.

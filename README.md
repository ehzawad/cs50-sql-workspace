# CS50 SQL Local Setup

This workspace is now prepared for the full CS50 SQL course: lecture materials, raw notes and transcripts, starter problem-set files, and local database tooling.

## Start Here

- Fresh clone or missing generated assets: `./bin/bootstrap-workspace`
- macOS quick start: `docs/macos-quickstart.md`
- Sanity-check the environment: `./bin/doctor`
- Course index: `docs/course-index.md`
- Problem set index: `docs/psets/index.md`
- Workflow cheat sheet: `docs/workflow-cheatsheet.md`
- Lecture verification report: `docs/lecture-command-verification.md`
- Week 0 guide: `docs/week0/follow-along.md`

## Local Tools

`<repo-root>` in the snippets below is whichever directory you cloned this repo into. On macOS and Linux you can jump there with `cd "$(git rev-parse --show-toplevel)"`.

From `<repo-root>`:

```bash
./bin/cs50-sql --list
./bin/cs50-sql week0
./bin/doctor
./bin/python --version
./bin/mysql
./bin/psql
./bin/check50 --help
./bin/submit50 --help
```

What each tool does:

- `./bin/sqlite3`: prefers the repo-local SQLite CLI and falls back to system `sqlite3` when needed
- `./bin/cs50-sql`: opens a local SQLite database with `.headers on` and `.mode box`
- `./bin/mysql`: starts a local MySQL 8 server in Docker (`mysql:8` by default) and opens the MySQL client
- `./bin/psql`: starts a local PostgreSQL server in Docker (`postgres:16` by default) and opens `psql`
- `./bin/mysql-stop`, `./bin/psql-stop`: stop the local database containers
- `./bin/java`, `./bin/javac`: local JDK wrappers for the Java-based pset
- `./bin/check50`, `./bin/submit50`: wrappers around a local Python virtualenv install
- `./bin/python`, `./bin/pip`: wrappers around the same local Python virtualenv
- `./bin/bootstrap-workspace`: redownloads ignored/generated assets and tools
- `./bin/doctor`: checks whether the local workspace is actually ready to use
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
- `./bin/mysql` and `./bin/psql` require Docker to be installed and running.
- The database containers are used through `docker exec`; they do not publish host ports by default.
- Default Docker images are `mysql:8` and `postgres:16`, and can be overridden with `CS50_SQL_MYSQL_IMAGE` and `CS50_SQL_POSTGRES_IMAGE`.
- MySQL and PostgreSQL passwords default to `crimson` but can be overridden with `CS50_SQL_MYSQL_ROOT_PASSWORD` and `CS50_SQL_POSTGRES_PASSWORD`.
- On a fresh machine, the recovery path is `./bin/bootstrap-workspace` and then `./bin/doctor`.
- On macOS, bootstrap uses the system `sqlite3` if available and downloads a platform-matching JDK.

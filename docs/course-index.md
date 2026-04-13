# CS50 SQL Local Course Index

This workspace is set up around the official CS50 SQL materials:

- Notes: `https://cs50.harvard.edu/sql/notes/`
- Weeks: `https://cs50.harvard.edu/sql/weeks/`
- Problem sets: `https://cs50.harvard.edu/sql/psets/`

## Quick Start

From `/home/synesis/sql`:

```bash
./bin/bootstrap-workspace
./bin/doctor
./bin/cs50-sql --list
./bin/cs50-sql week0
./bin/mysql
./bin/psql
```

Workflow sheet:

- `docs/workflow-cheatsheet.md`
- `docs/lecture-command-verification.md`

Local helper tools:

- `./bin/sqlite3`: local SQLite CLI from the official SQLite prebuilt tools
- `./bin/cs50-sql`: opens a local SQLite database with readable defaults
- `./bin/mysql`: starts a local MySQL 8 Docker container and drops you into it
- `./bin/psql`: starts a local PostgreSQL Docker container and drops you into it
- `./bin/check50`: wrapper for the course checker
- `./bin/submit50`: wrapper for submission
- `./bin/python`, `./bin/pip`: wrappers for the local Python environment
- `./bin/doctor`: local readiness check

## Lecture Guides

- Week 0: `docs/week0/follow-along.md`
- Week 1: `docs/week1/follow-along.md`
- Week 2: `docs/week2/follow-along.md`
- Week 3: `docs/week3/follow-along.md`
- Week 4: `docs/week4/follow-along.md`
- Week 5: `docs/week5/follow-along.md`
- Week 6: `docs/week6/follow-along.md`

Each week folder also contains the raw official notes, transcript, and subtitles used to build the guide.

## Problem Sets

See `docs/psets/index.md` for the workspace map, starter files, local commands, and check50/submit50 targets.

## Verification

The current workspace verification report is in:

- `docs/lecture-command-verification.md`

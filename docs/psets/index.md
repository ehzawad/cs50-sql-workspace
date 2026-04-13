# CS50 SQL Problem Set Index

This file maps every problem set to its local workspace path and the official checker target.

Fast workflow reference:

- `docs/workflow-cheatsheet.md`

## Shared Commands

SQLite problems:

```bash
cd /home/synesis/sql
./bin/cs50-sql packages
./bin/cs50-sql snap
```

MySQL problem:

```bash
cd /home/synesis/sql
./bin/mysql
```

Java helper toolchain:

```bash
./bin/python --version
./bin/javac
./bin/java
```

Course tools:

```bash
./bin/doctor
./bin/check50 --help
./bin/submit50 --help
```

## PSet 0

- `cyberchase`: `cs50/pset0/cyberchase/`
- `views`: `cs50/pset0/views/`
- `normals`: `cs50/pset0/normals/`
- `players`: `cs50/pset0/players/`

PSet 0 does not use the same check50/submit50 flow as the later SQL psets, so only the local folders are listed here.

## PSet 1

- `packages`: `cs50/pset1/packages/`
  - check: `check50 cs50/problems/2024/sql/packages`
  - submit: `submit50 cs50/problems/2024/sql/packages`
- `dese`: `cs50/pset1/dese/`
  - check: `check50 cs50/problems/2024/sql/dese`
  - submit: `submit50 cs50/problems/2024/sql/dese`
- `moneyball`: `cs50/pset1/moneyball/`
  - check: `check50 cs50/problems/2024/sql/moneyball`
  - submit: `submit50 cs50/problems/2024/sql/moneyball`

## PSet 2

- `atl`: `cs50/pset2/atl/schema.sql`
  - check: `check50 cs50/problems/2024/sql/atl`
  - submit: `submit50 cs50/problems/2024/sql/atl`
- `connect`: `cs50/pset2/connect/schema.sql`
  - check: `check50 cs50/problems/2024/sql/connect`
  - submit: `submit50 cs50/problems/2024/sql/connect`
- `donuts`: `cs50/pset2/donuts/schema.sql`
  - check: `check50 cs50/problems/2024/sql/donuts`
  - submit: `submit50 cs50/problems/2024/sql/donuts`

These are scaffold-only problems. CS50 expects you to create the folders yourself; this workspace already created them.

## PSet 3

- `dont-panic`: `cs50/pset3/dont-panic/`
  - check: `check50 cs50/problems/2024/sql/dont-panic`
  - submit: `submit50 cs50/problems/2024/sql/dont-panic`
- `meteorites`: `cs50/pset3/meteorites/`
  - check: `check50 cs50/problems/2024/sql/meteorites`
  - submit: `submit50 cs50/problems/2024/sql/meteorites`

## PSet 4

- `census`: `cs50/pset4/census/`
  - check: `check50 cs50/problems/2024/sql/census`
  - submit: `submit50 cs50/problems/2024/sql/census`
- `private`: `cs50/pset4/private/`
  - check: `check50 cs50/problems/2024/sql/private`
  - submit: `submit50 cs50/problems/2024/sql/private`
- `bnb`: `cs50/pset4/bnb/`
  - check: `check50 cs50/problems/2024/sql/bnb`
  - submit: `submit50 cs50/problems/2024/sql/bnb`

## PSet 5

- `snap`: `cs50/pset5/snap/`
  - check: `check50 cs50/problems/2024/sql/snap`
  - submit: `submit50 cs50/problems/2024/sql/snap`
- `your.harvard`: `cs50/pset5/your.harvard/`
  - check: `check50 cs50/problems/2024/sql/harvard`
  - submit: `submit50 cs50/problems/2024/sql/harvard`
  - note: the local folder keeps the `your.` prefix, but the checker slug does not

## PSet 6

- `sentimental-connect`: `cs50/pset6/sentimental-connect/schema.sql`
  - check: `check50 cs50/problems/2024/sql/sentimental/connect`
  - submit: `submit50 cs50/problems/2024/sql/sentimental/connect`
- `deep`: `cs50/pset6/deep/answers.md`
  - submit: `submit50 cs50/problems/2024/sql/deep`
- `dont-panic-python`: `cs50/pset6/dont-panic/python/`
  - check: `check50 cs50/problems/2024/sql/sentimental/dont-panic/python`
  - submit: `submit50 cs50/problems/2024/sql/sentimental/dont-panic/python`
- `dont-panic-java`: `cs50/pset6/dont-panic/java/`
  - check: `check50 cs50/problems/2024/sql/sentimental/dont-panic/java`
  - submit: `submit50 cs50/problems/2024/sql/sentimental/dont-panic/java`

If you want to stay inside the local course toolchain, use the wrappers:

```bash
cd /home/synesis/sql/cs50/pset6/dont-panic/python
/home/synesis/sql/bin/python hack.py

cd /home/synesis/sql/cs50/pset6/dont-panic/java
/home/synesis/sql/bin/javac Hack.java
/home/synesis/sql/bin/java -cp .:sqlite-jdbc-3.43.0.0.jar Hack
```

## Local Raw Sources

The official problem pages are mirrored under `docs/psets/raw/` so you can inspect them offline.

# Lecture Command Verification

This report reruns the official lecture command files against the local workspace setup. It separates clean runs, expected instructional errors, and unexpected failures.

## SQLite Weeks 0-5

| Case | Result | Note |
|---|---|---|
| week0 0-SELECT.sql | passed | |
| week0 1-LIMIT.sql | passed | |
| week0 2-WHERE.sql | passed | |
| week0 3-NULL.sql | passed | |
| week0 4-LIKE.sql | passed | |
| week0 5-compound.sql | passed | |
| week0 6-range.sql | passed | |
| week0 7-dates.sql | passed | |
| week0 8-ORDER BY.sql | passed | |
| week0 9-aggregate.sql | passed | |
| week1 nested.sql | passed | |
| week1 joins.sql | passed | |
| week1 sets.sql | expected error | Parse error near line 13: near "UNION": syntax error UNION SELECT 'translator' AS "profession", "name" FROM "translators |
| week1 groups.sql | passed | |
| week2 schema0.sql | passed | |
| week2 schema1.sql | passed | |
| week2 schema2.sql | passed | |
| week2 schema3.sql | passed | |
| week2 schema4.sql | passed | |
| week2 schema5.sql | passed | |
| week2 schema6.sql | passed | |
| week2 schema7.sql | passed | |
| week2 alter0.sql | passed | |
| week2 alter1-3 chain | passed | |
| week3 insert chain | expected error | Runtime error near line 17: UNIQUE constraint failed: collections.accession_number (19) Runtime error near line 21: NOT  |
| week3 import0.sql | passed | |
| week3 import1.sql | expected error | Parse error near line 13: near "IF": syntax error CREATE TABLE "collections" IF NOT EXISTS ( "id" INTEGER, "title" TEXT  |
| week3 delete0 chain | passed | |
| week3 delete1 chain | passed | |
| week3 delete2 chain | passed | |
| week3 triggers chain | passed | |
| week3 soft_delete.sql | passed | |
| week4 simplifying.sql | passed | |
| week4 aggregating.sql | expected error | Parse error near line 39: near "SELECT": syntax error ."book_id" = "books"."id" GROUP BY "book_id" ), SELECT "year" ROUN |
| week4 partitioning.sql | passed | |
| week4 securing.sql | passed | |
| week4 soft_delete.sql | expected error | Parse error near line 33: cannot modify current_collections because it is a view  |
| week4 soft_deletion.sql | expected error | Parse error near line 33: cannot modify current_collections because it is a view  |
| week5 where.sql | passed | |
| week5 nested.sql | expected error | Parse error near line 37: index person_index already exists  |
| week5 partial.sql | passed | |
| week5 vacuum.sql | passed | |
| week5 race_conditions.sql | expected error | Runtime error near line 24: CHECK constraint failed: balance (19)  |
| week5 transactions.sql | expected error | Runtime error near line 29: CHECK constraint failed: balance (19) Runtime error near line 37: CHECK constraint failed: b |

## Week 6 Server-Side Commands

| Case | Result | Note |
|---|---|---|
| week6 mysql login equivalent SHOW DATABASES | passed | |
| week6 mysql types schema | passed | |
| week6 mysql types alter | passed | |
| week6 mysql access schema | passed | |
| week6 mysql create user | passed | |
| week6 mysql Carter SHOW DATABASES before grants | passed | |
| week6 mysql grant select on analysis | passed | |
| week6 mysql Carter SELECT analysis | passed | |
| week6 mysql Carter SELECT rides | expected error | mysql: [Warning] Using a password on the command line interface can be insecure. ERROR 1142 (42000) at line 1: SELECT co |
| week6 mysql Carter CREATE VIEW before grant | expected error | mysql: [Warning] Using a password on the command line interface can be insecure. ERROR 1142 (42000) at line 1: CREATE VI |
| week6 mysql grant create view | passed | |
| week6 mysql Carter CREATE VIEW after grant | passed | |
| week6 mysql injection schema | passed | |
| week6 mysql injection example | passed | |
| week6 mysql prepared statement example | passed | |
| week6 postgres list databases (\l equivalent) | passed | |
| week6 postgres create database | passed | |
| week6 postgres schema in dedicated database | passed | |
| week6 postgres schema.sql | passed | |
| week6 postgres \dt after schema | passed | |

## Summary

- Passed: 53
- Expected instructional errors observed: 11
- Unexpected failures: 0

## Notes

- Week 1 `sets.sql`, Week 4 `aggregating.sql`, Week 3 `import1.sql`, and Week 5 `nested.sql` contain source-level issues or replay problems in the official bundle, so they were classified as expected source issues rather than local environment problems.
- Some Week 6 login files show raw Docker and interactive client commands intended for CS50 Codespaces. Here they were verified through the local wrappers `./bin/mysql` and `./bin/psql`, which exercise the same server behavior without conflicting container names.
- The `SHOW DATABASES` behavior for the restricted MySQL user differs slightly from the lecture narration on this image version: the user can still list the database it can access.
- Files that intentionally demonstrate permission errors, view-delete errors, or constraint failures were marked as expected instructional errors rather than setup failures.

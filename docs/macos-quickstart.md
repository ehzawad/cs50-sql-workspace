# macOS Quick Start

This repo can be made usable on macOS quickly, but the important distinction is that MySQL and PostgreSQL run through Docker, not through Homebrew services.

## Fastest path

1. Install Docker Desktop and start it.
2. Make sure `python3` is available.
   - If not: `brew install python`
3. Clone the repo and enter it:

```bash
git clone git@github.com:ehzawad/cs50-sql-workspace.git
cd cs50-sql-workspace
```

4. Bootstrap the workspace:

```bash
./bin/bootstrap-workspace
```

5. Verify everything:

```bash
./bin/doctor
```

## What bootstrap does on macOS

- uses system `sqlite3` if it already exists
- downloads a macOS-compatible Temurin JDK 21 into `vendor/jdk`
- creates the Python virtualenv for `cs50`, `check50`, and `submit50`
- downloads lecture notes, transcripts, subtitles, source bundles, and pset archives
- leaves MySQL and PostgreSQL to the Docker wrappers

## What you need installed yourself

- Docker Desktop
- Python 3
- Git
- either `wget` or `curl` (macOS already has `curl`)

## First commands to try

```bash
./bin/doctor
./bin/cs50-sql week0
./bin/mysql
./bin/psql
```

## If SQLite is missing on macOS

Most macOS setups already have `/usr/bin/sqlite3`. If yours does not, install one with Homebrew:

```bash
brew install sqlite
```

## Shell note

macOS defaults to `zsh` as the interactive login shell; the wrappers under `bin/` run Bash via their shebang, so you can invoke them directly from zsh:

```bash
./bin/cs50-sql week0
./bin/mysql
```

Do **not** invoke them with an explicit `zsh ./bin/...` — that bypasses the shebang and runs Bash-specific syntax through zsh, which breaks. Just run `./bin/<thing>` and zsh will hand off to Bash automatically.

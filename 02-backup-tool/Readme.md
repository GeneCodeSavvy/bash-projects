## Project 2: Automated Backup & Cleanup Tool

**Level:** 2 - Beginner

**Objective:** Back up a specified directory into a timestamped archive and clean up old backups.

**Description:**
Write a script that handles command-line arguments, file operations, looping constructs, and age-based file cleanup using `find`.

**Key Concepts:**

* `for` loops and optional `while` loops
* Command-line arguments (`$1`, `$2`)
* File/directory operations (`mkdir`, `cp`, `tar`)
* Date formatting (`date +%Y-%m-%d_%H-%M-%S`)
* Using `find` to delete old files

**Core Requirements:**

1. Accept two args: source directory and backup destination.
2. Show usage and exit if args missing.
3. Validate source directory existence.
4. Create a timestamped backup subdirectory.
5. Archive and compress the source into `.tar.gz` in that directory.
6. After success, delete backups older than 7 days.
7. Print informative messages at each stage.

**Bonus Challenges:**

* Make retention period a third arg.
* Read backup sources from `backup_sources.txt`.
* Check free disk space before backing up.

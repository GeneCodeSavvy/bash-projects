## System Administration Script Projects

This repository contains a series of progressively challenging shell scripting projects designed to build your Linux administration and automation skills. Each project introduces new concepts and practical exercises, from beginner "read-only" scripts to advanced remote deployment tools.

---

### Table of Contents

1. [Project 1: System Welcome & Status Dashboard](#project-1-system-welcome--status-dashboard)
2. [Project 2: Automated Backup & Cleanup Tool](#project-2-automated-backup--cleanup-tool)
3. [Project 3: Log File Analyzer](#project-3-log-file-analyzer)
4. [Project 4: Service & Process Monitor](#project-4-service--process-monitor)
5. [Project 5: Remote Server Health & Deployment Assistant](#project-5-remote-server-health--deployment-assistant)

---

## Project 1: System Welcome & Status Dashboard

**Level:** 1 - Beginner

**Objective:** Create a script that greets the user and displays essential system information upon login.

**Description:**
A safe "read-only" script that captures output of common Linux commands into variables and displays them in a formatted MOTD-style dashboard.

**Key Concepts:**

* Variables (declaring and using)
* Command substitution (`$(...)` or backticks)
* Reading user input (`read`)
* Basic conditionals (`if`/`elif`/`else`)
* String formatting and `echo` with ANSI colors (optional)

**Core Requirements:**

1. Clear the terminal screen upon execution.
2. Display a welcome message with the current username.
3. Show the current date and time.
4. Display the system's hostname and kernel version.
5. Show free memory.
6. Check disk usage of `/`; if over 80%, display a red warning.
7. Prompt to list currently logged-in users; on `y`/`yes`, run `who`.

**Bonus Challenges:**

* Use ANSI escape codes for colored output.
* Display the system's current IP address.
* Fetch a "quote of the day" from a local text file.

---

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

---

## Project 3: Log File Analyzer

**Level:** 3 - Intermediate

**Objective:** Parse a web server log file to extract and summarize key metrics.

**Description:**
Shift to modular scripting with functions and `getopts` for flags, processing logs line by line and using associative arrays.

**Key Concepts:**

* Functions for reuse
* `getopts` for option parsing
* File I/O with `while read`
* Text processing with `grep`/`awk`
* Associative arrays (Bash 4+)
* `case` statements

**Core Requirements:**

1. Structure script with functions: `show_usage()`, `parse_log()`, `generate_report()`.
2. Use `getopts` to accept:

   * `-f [file]` (required): path to log file.
   * `-n [number]` (optional): top N IPs.
   * `-e` (optional): only HTTP error codes (4xx/5xx).
3. Validate log file readability.
4. Report:

   * Total requests
   * Unique IP count
   * HTTP status codes and counts
5. Implement `-n` and `-e` behaviors.

**Bonus Challenges:**

* `-r [IP]` for a single-IP report.
* Output summary to `log_summary_YYYY-MM-DD.txt`.
* Use `awk` for bytes transferred.

---

## Project 4: Service & Process Monitor

**Level:** 4 - Advanced

**Objective:** Monitor a system service, restart on failure, and check resource usage of its process.

**Description:**
Build robust scripts with error handling, traps for cleanup, and process/service management.

**Key Concepts:**

* Exit-code checks (`$?`, `set -eo pipefail`)
* Signal handling with `trap`
* `ps`, `pgrep`, `kill` for process management
* `systemctl` or `service` for service control
* Advanced `awk`/`sed` extraction
* Conditional execution (`&&`, `||`)

**Core Requirements:**

1. Accept service name arg.
2. `check_service()` uses `systemctl is-active`.
3. On inactive, log failure and `systemctl restart`.
4. Re-check status and report success/failure.
5. `monitor_process()` to get PID, CPU, and memory usage; warn if thresholds exceeded.
6. Use `trap` to handle interrupts and cleanup.
7. Check exit codes of all critical commands.

**Bonus Challenges:**

* Run as a background daemon checking every 60 seconds.
* Send email alerts on warnings.
* Add option to monitor by process name.

---

## Project 5: Remote Server Health & Deployment Assistant

**Level:** 5 - Expert / Capstone

**Objective:** Create a multi-functional tool to check health, run commands, and deploy files across remote servers defined in a config file.

**Description:**
Combine all learned skills into a professional-grade utility with config parsing, logging, SSH automation, and robust error handling.

**Key Concepts:**

* Reading `.conf`/`.ini` config files
* Advanced functions and logging
* Remote execution (`ssh`) and file transfer (`scp`/`rsync`)
* Complex argument parsing and `case` modes
* Looping, conditionals, and error handling in large scripts

**Core Requirements:**

1. **Configuration File** (`servers.conf` example):

   ```ini
   SERVERS=("server1.example.com" "server2.example.com")
   SSH_USER="admin"
   REMOTE_PATH="/var/www/html"
   ```
2. **Logging Function:** Append timestamped INFO/WARN/ERROR messages to `/var/log/mytool.log` and print to console.
3. **Modes (via `case`):**

   * `health-check`: SSH into each server to report uptime, disk/memory, logging results.
   * `run-command "cmd"`: Execute arbitrary command on all servers, prefix output by server name.
   * `deploy /local/path`: Copy files/dirs to `REMOTE_PATH` on all servers, verify success, log.
4. **Robustness:** Handle SSH/connectivity errors, remote command failures, file permissions; log without crashing.

**Bonus Challenges:**

* `--parallel` flag for concurrent operations.
* `--dry-run` to preview commands.
* Interactive `select` menu when no args provided.

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

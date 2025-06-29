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

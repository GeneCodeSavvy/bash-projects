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


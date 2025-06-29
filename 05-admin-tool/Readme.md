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

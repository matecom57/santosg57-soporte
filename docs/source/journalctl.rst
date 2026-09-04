journalctl
==========

The journalctl command is a tool used on Ubuntu to query and view system logs managed by the systemd-journald service. [1] (https://www.geeksforgeeks.org/linux-unix/journalctl-command-in-linux-with-examples/), [2] (https://oneuptime.com/blog/post/2026-03-02-how-to-read-and-filter-journalctl-logs-on-ubuntu/view), [3] (https://www.ionos.com/digitalguide/server/tools/journalctl/)

**Basic Usage**

* View all logs: Type journalctl to open the full log history, paginated for scrolling.

* Live follow mode: Use journalctl -f to watch new log entries appear in real time

**Common Filtering Commands**

* Filter by service: Run sudo journalctl -u nginx to see logs for a specific service like Nginx or SSH.

* View current boot: Run journalctl -b to see logs from the latest system startup only.

* Filter by priority: Run journalctl -p err to display only error-level messages and higher priority issues.

* Filter by time: Run journalctl --since "1 hour ago" or journalctl --since today to limit output to a specific timeframe.

**Log Maintenance**

* Check disk space: Run journalctl --disk-usage to see how much storage the logs consume.

* Clean old logs: Run journalctl --vacuum-time=2weeks

Would you like help troubleshooting a specific service error (such as SSH, Nginx, or Docker) or filtering logs by a custom time range?



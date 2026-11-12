| Facility | Use |
|---|---|
| Auth/Security | Log information relating to user authentication. |
| Authpriv | A more detailed version of auth. |
| Cron | Logs activity of the cron daemon, which is used to schedule events. |
| Daemon | Collects information about *all* system daemons. |
| Mail | Tracks mail server activity. This is a must have if you're running a mail server. |
| Syslog | Information about the syslog server itself. |

Along with this selection of facilities, you need to understand the priorities that are available. How much detail you need is up to you. Keep in mind that if a problem occurs and you don't have enough information to identify the source, the logs are essentially useless. However, if you collect every transaction and message in the log, it may be nearly impossible to locate meaningful information. Table 1-2 describes the available priorities.

| Priority | Use |
|---|---|
| Info | Logs general informational messages |
| Notice | Logs occurrences that require special interaction (that is, user prompts) |
| Warning | System warning, “might be a problem” |
| Err | System error, “a problem occurred” |
| Crit | Critical condition, “a big problem has occurred” |
| Alert | Intervention required, “problem happening, need help” |
| Emerg | Serious system failure, “something is hosed” |
| Panic | System panic, “HUGE problem” |
| Debug | Logs nearly everything |
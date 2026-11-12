Some formats for log entries are defined in the main configuration file by default. Check your file to see what formats are defined. One format is usually defined and called common. This format is used for the default format for your log file. The following two sections show how to use the LogFormat directive and the CustomLog directive to change your log files if needed.

# CustomLog

**Description:** Logs requests to the server. You specify the format for the log entries.

**Format:** `CustomLog file|pipe format|nickname`

CustomLog takes two arguments. Each argument can take one of two formats. The arguments are as follows:

+   • **First argument:** Specifies where log entries are sent. The argument can be either a filename or a command that sends (pipes) the log entries to a script.

+   • **Filename:** Filename where log entries will be stored.

+   • **Pipe:** A pipe character (|) followed by the name of a script/program that you want to process the log entries. For example, the argument might be `| /usr/bin/apachelog.pl`, where apachelog.pl is a script that processes and stores the log entries.

+   • **Second argument:** Specifies the format for the log entry. The argument can be either a string log format or a nickname for a log format.

+   • **Log format:** A text string that defines a format for the log entry. The symbols that are available for use in the text string are shown in Table 3-1 in the description for LogFormat.

+   • **Nickname:** The nickname under which a log format was stored using the LogFormat directive.

# Example:

```
CustomLog logs/mylog_file "%h %u %t %r %>s"
```

This directive sends the log entry to a file called `logs/mylog_file`. Each entry contains the remote host name (h), the remote username (u), the time of the request (t), the first line of the request (r), and the response to the request (s). The `%` tells Apache that a format character comes next.

**Context in Which It Is Valid:** Server, virtual host
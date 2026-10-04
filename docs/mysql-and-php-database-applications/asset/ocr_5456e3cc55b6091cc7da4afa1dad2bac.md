# Part V: Appendixes

# Table C-7 MYSQLQLADMIN COMMAND-LINE OPTIONS

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -? | --help | Display help and exit. |
| -# | --debug= | Output debug log. Often this is d:t:o:filename |
| -f | --force | Don't ask for confirmation on drop database; with multiple commands, continue even if an error occurs. |
| -h | --host=# | Connect to host. |
| -p[...] | --password=[...] | Password to use when connecting to server. If password is not given on the command line, you will be prompted for it. Note that if you use the short -p you can't have a space between the option and the password. |
| -P | --port= | Port number to use for connection. |
| -I | --sleep=sec | Execute commands again and again with a sleep between. |
| -r | --relative | Show difference between current and previous values used with -i. Currently works only with extended-status. |
| -s | --silent | Silently exit if one can't connect to server. |
| -t | --timeout= | Timeout for connection to the mysql server. |
| -w | --wait[-retries] | Wait and retry if connection is down. |
| -W (Windows only) | --pipe | Use named pipes to connect to server. |
| -E | --vertical | Print output. Similar to -relative, but prints output vertically. |

# mysqldump

This is the command-line utility for dumping out schema and data from your databases. This is what you would use to back up your database, or move it from one machine to another.
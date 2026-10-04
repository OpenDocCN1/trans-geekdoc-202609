# Part V: Appendices

# TABLE C-2 COMMON MYSQL COMMAND-LINE CLIENT OPTIONS, PART II

| Flag | Alternate Flag | Description |
|---|---|---|n| -f | --force | Continue even if we get a SQL error. |
| -h | --host= | Connect to the given host. |
| -H | --html | Produce HTML output. |
| -L | --skip-line-numbers | Don't write line for errors. Useful when one wants to compare result files that include error messages. |
| -n | --unbuffered | Flush buffer after each query. |
| -p[password] | --password[...] | Password to use when connecting to server. If password is not given on the command line, you will be prompted for it. Note that if you use the short form (-p) you can't have a space between the option and the password. |

Examples:

```
mysql -u root -pfoobar
```

or

```
mysql --username=root --password=foobar
```

# TABLE C-3 COMMON MYSQL COMMAND-LINE CLIENT OPTIONS, PART III

| Flag | Alternate Flag | Description |
|---|---|---|n| -P | --port=... | TCP/IP port number to use for connection. |
| -q | --quick | Don't cache result, print it by row. This may slow down the server if the output is suspended. Doesn't use history file. If you have problems due to insufficient memory in the client, use this option. It forces mysql use_result() rather than mysql_store_result() to retrieve the result set. |
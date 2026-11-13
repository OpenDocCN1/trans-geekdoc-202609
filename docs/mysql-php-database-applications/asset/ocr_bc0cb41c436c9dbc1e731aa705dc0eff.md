mysql.max_links =
mysql.default_port =
mysql.default_host =
mysql.default_user =
mysql.default_password =

If you want to forbid persistent connections, change that setting to 0ff; if you want to limit the number of persistent links to MySQL, change the setting on max_persistent and max_links from -1 to an appropriate number.

You can use the default_user, default_host, and default_password entries if you want to save yourself the trouble of entering these strings in your mysql_connect() command. Note that putting your MySQL password in the MySQL configuration file is a tremendous security risk.

You can make lots of other settings in your MySQL configuration file. The following sections explain some of the more useful ones.

# MAGIC QUOTES

magic_quotes_gpc
magic_quotes_runtime

If magic_quotes_gpc is set to 0n, all single quotes ('), double quotes ("), backslashes (\\), and NULLs are prepended with a backslash immediately upon being uploaded from a form element. This makes doing your inserts into MySQL a lot easier.

If magic_quotes_runtime is set to 0n, data retrieved from the file system or a database are automatically escaped with backslashes.

# EXECUTION TIME

max_execution_time = 30
memory_limit = 8388608

These settings are intended to protect you in the event of an infinite loop or an endlessly recursive function. All scripts are automatically terminated if they reach either of these limits. If you want to use a script that you expect to take more than 30 seconds, you can set the maximum execution time within a script with the set_time_limit() function. This function can contain a number of seconds; if you want to specify no limit, specify set_time_limit(0).

# AUTO PREPEND AND APPEND

auto_prepend_file   -
auto_append_file    -
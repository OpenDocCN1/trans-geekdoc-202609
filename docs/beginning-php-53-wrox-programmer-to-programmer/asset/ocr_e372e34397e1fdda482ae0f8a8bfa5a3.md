# Appendix D: Using PHP from the Command Line

Make your script executable by the owner of the crontab, and that it contains the path to the command-line PHP engine in the shebang, otherwise the script won't run!

By default, the system emits any output from the script to the crontab owner's email address (for example, joe@localhost). Because you might not check this address, you can specify another address in the line of the crontab:

```
MAILTO=joe@example.com
15 23 * * 1,3,5 /home/joe/backup_databases.php
```

If you'd not receive any email from the script, redirect its output to /dev/null:

```
15 23 * * 1,3,5 /home/joe/backup_databases.php > /dev/null
```

# Useful Command-Line Options

The command-line PHP engine lets you set various options that affect the way it runs. You can get a full list by typing:

```
-h
```

Here are some of the most commonly used options:

| Option | Description |
| --- | --- |
| -a | Runs in interactive mode. This lets you run single lines of PHP one at a time. Type a line of PHP code, press Enter/Return, and see the results. (Don't forget to wrap your code in `<php ... ?>` tags.) |
| -c path_to_ini_file | Uses a custom .ini configuration file instead of the normal php.ini. |
| -d name=value | Sets a custom configuration directive. |
| -i | The equivalent of calling phpinfo() within a script. Displays configuration information in the terminal window. |
| -l script_filename | Checks the supplied file for syntax errors, without actually running the script. |
| -m | Displays a list of all built-in and loaded PHP and Zend modules. |
| -r php_code | Runs a line of PHP code. You don't need to include `<php ... ?>` tags. (Make sure you wrap the code in single quotes rather than double quotes to prevent the shell itself from performing variable substitution on any PHP variables in the code.) |
The script then creates the text for the e-mail, and finally sends it to the administrator:

```
```php
$email = "Summary of codes for todays logs\n\nCode\tCount\n";
foreach ($status_code as $code => $count) {
    $email .= "$code:\t$count\n";
}

mail($admin_email, "Summary of weblogs", $email);
?>
```
```

For ease of use, we want to automate the running of this script so that it runs every night at midnight.
To do this under Linux we use cron, and under Windows NT/2000 we use the AT command. I will deal
with cron first.

# cron

cron is a way of automating tasks under Linux/UNIX. The cron daemon looks at each user's crontab
file every minute and checks to see if it needs to perform any actions. The systems administrator (or any
user for that matter) can use it to automate tasks such as running the script above.

A crontab entry has six fields. The first five are used to specify the time that an action should take
place; the last specifies the command that should be run by the cron daemon. Each of the time fields
specifies a value that must be matched to the current system time for the command to run. They can
also contain the wild card * to run the command at any time where all the other fields match.

The first field specifies the number of minutes past the hour (0-59) that the command should be run.
The second field specifies the hour of the day the command should be run (0-23), the third field
specifies the day of the month (1-31), the fourth the month of the year (1-12), and the fifth the day of the
week (0-6, where 0 is Sunday). You may find more detailed information about the crontab command
at http://hoth.stsci.edu/man/man1/crontab.html.

We need our script to run every day at midnight. If the script is called mail_stats.php and lives in
the directory /home/jmoore/, the following crontab entry would accomplish this. If you need to edit
your crontab file you may do so by typing in crontab at your terminal:

```
```
0 0 * * * /usr/local/bin/php -q /home/jmoore/mail_stats.php
```
```

This tells the cron daemon that when the hour, minute both equal 0 on any day of any month it
should run the command /usr/local/bin/php -q mail_stats.php.

> Under the Linux/UNIX shell you can make the script itself executable by setting the
> correct permissions on the script (normally this is achieved by running the command
> chmod a+x mail_stats.php, but check your system's documentation if you are
> unsure how to do this). You can then add the command the shell should use to execute
> the script, as the first line of the script. For example #!/usr/local/bin/php -q.
> This tells the shell to execute the script with the executable found at
> /usr/local/bin/php with the flag -q.
![](bbox=[0.07, 0.11, 0.75, 0.43])

FIGURE 10-2 Drilling Down in the /sys Directory.

# Crond

Crond is a daemon (thus the d on the end of the name) that is responsible for seeing that scheduled tasks run as scheduled. This is a critical system service for a network administrator. It is inefficient for you to manually run every task every time it is needed. And on any but the smallest networks it is simply impossible. Therefore, you must have some mechanism whereby you can schedule tasks to run. Crond is that mechanism.

The crond daemon uses crontab files for scheduling tasks. Crond searches /var/spool/cron for crontab files. Essentially crond periodically examines all the crontab files to see if there are commands to be run, and if so it executes them. Each user has their own crontab, and commands in any given crontab will be executed as the user who owns the crontab. It is important to keep this in mind. Unless absolutely necessary, you should not run tasks as the root. For the penetration tester, you may wish to see what cron jobs are running and you may need to turn some off, or at least verify if an intruder can turn them off.

A crontab file contains instructions to the crond daemon of the general form: “run this command at this time on this date.” Inside crontabs, blank lines and leading spaces and tabs are ignored. Lines which begin with a pound sign (#) are comments, and are ignored. Note that comments are not allowed on the same line as cron commands. It is common practice to put the comment just before the command. Similarly, comments are not allowed on the same line as environment variable settings.

An active line in a crontab will be either an environment setting or a cron command. An environment setting is of the form:

```
name = value
```
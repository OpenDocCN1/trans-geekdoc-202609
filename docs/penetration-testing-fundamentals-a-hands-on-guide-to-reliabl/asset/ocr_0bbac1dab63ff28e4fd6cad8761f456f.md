# Syslogd

This shell utility is part of the daemon that provides system logging, more specifically kernel logging. This service is what provides the ability to log data to syslog. As you might expect, syslogd has some options you can set:

+   - **-a:** This allows you to add additional sockets for the syslog daemon to listen to. This is useful if you have other servers forwarding their syslog messages to a central server.
+   - **-d:** This runs the daemon in debugging mode, allowing you to view issues live in the shell.
+   - **-h:** This option allows you to forward syslogd messages from the server/machine you are on to a centralized server.
+   - **-r:** You would use this option on the central server receiving syslogd messages from other servers. It puts the daemon into a mode that allows it to receive messages from the network.
+   - **-s:** This option is used to cause the daemon to log in verbose mode. This will increase the amount of detail in log entries.

There are other options, but these are some of the most widely used, particularly -h and -s.

Obviously, logging is an issue for penetration testers. From the attack perspective, you would like to know if your attacks are being logged. From a security testing perspective, you wish to ensure they are.

# Scripting

Eventually most penetration testers want to write their own scripts, in order to automate their favorite tests. Script writing is very similar to traditional programming that one might do in languages such as C, C++, or Java. However, it has some significant differences. First and foremost, you do not compile a script. You simply write your script code in your preferred text editor, then execute it when you need to. Secondly, script writing requires no special software tools or utilities. You can, as previously stated, use any text editor you prefer. But script writing does share one thing in common with traditional programming: the need for proper syntax and structure. Any errors in your script, even trivial ones, will either render your script nonfunctional or drastically change the output from your script.

Scripts can be written in any basic text editor. You can use Kate, Kwrite, or any other text editor that you wish. The first issue to keep in mind when writing a script is that scripts are generally written for a particular shell ( i.e. BASH, C shell, Korn, etc.). For this reason, all the shells have an agreed upon standard, that the first line of a script declares what type of shell it runs in. Then that shell will be used to run the script. For example, if you want a script run by the C shell, your first line would be:

```
#!/bin/csh
```
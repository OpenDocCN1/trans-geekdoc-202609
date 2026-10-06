That's all very nice, you may be thinking, but how do I apply it to dozens of computers? Do I have to visit each one? Well, if you want to use this tool! If you want to use other options, one would be to use a command-line tool. A command-program called sedit.exe will both convert templates into databases and apply databases. To read a template, apply, and then create a database in the process, use the following syntax:

```
/secedit /cfg templatefilename /db filename/overwrite / log filename
```

To apply an existing database without first reading the template, leave off the /cfg switch and argument. To apply the template to your workstations, you could use the sedit command in a login script (be sure to use full paths for the template, database, and log files) that will reapply it with every login. You could also use the Task Scheduler to run a batch file at specific intervals. Or you could enable the Telnet server on your Windows servers and apply the template whenever you like.

Automation and scripting are nice, but what if you want to take advantage of the "automatic" background refreshes through Group Policy, as well as the 16-hour forced security settings update? That's right, use Group Policy! You'll learn about this in the next section.

# Using Domain-based Group Policy to Apply Templates

sedit is nice, but it has to be invoked manually from a batch file, which means a lot of messy editing of login batch files or fiddling with the scheduled tasks on all your systems. If you use a login script, the security template gets applied at login time only. How do you enforce security settings more often? With a GPO.
Domain GPOs have a few benefits:

+   - It's easy to control whom they apply to, which is much easier than having to figure out which batch files go where.
- They reapply not only at login time but throughout the day—the workstations seek them every 60 to 120 minutes.
- Security settings are "reapplied" every 16 hours, just in case a security setting was modified by the user, an application, and so on.

# Import Security Templates

You already have your security template, simple.inf, which you created in the previous section. Now, you want to leverage the deployment of the security settings in the template by using a GPO.

The steps to import the template are very simple. Follow these steps to import the simple.inf template into a GPMC.

+   1. Launch the GPMC.
2. Go to an OU that contains the computers that you want to apply the security settings to.
For example, the simple.inf template could apply to all the desktops in your organization.
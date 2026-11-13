# # Removing comments and debug helpers

Comments are often removed due to file size, which can be a valid concern on a large program. However, most of the time, comments are automatically removed when an application is compiled or built.

Depending on the application you use, debug statements should also be removed. For example, the native Flash IDE that ships with CS3 has a configuration option in the Publish Settings dialog box. If you select Omit Trace Actions, which is located on the Flash tab of the Publish Settings, trace calls are removed from the application.

> NOTE If Omit Trace Actions is enabled during debugging you will not see any trace calls displayed in the Output window.

If you decide to use a custom Class or package for debugging, then you could use Find and Replace to remove those instances. However, be careful to not accidentally remove application-specific code.

As you can see, comments can be beneficial from the standpoint of code readability. You also now know that properly commenting your code has additional advantages when using some of the more robust code editors available today.

# # Managing a ChangeLog

A ChangeLog is a formatted block of records or log entries placed in a custom file. These files generally have the name CHANGES or UPDATES. This section is used to take notes on the features of an application or to communicate progress with the rest of a development team.

An advantage to using a ChangeLog is that some applications can read this formatted log and automatically display it, as shown in Figure 15.2. This, of course, depends on the application you are using but can be very beneficial as an application begins to grow.

# # Bug tracking

Many developers use this dynamic ChangeLog format to track bugs. This is a process that many commercial and freeware applications, such as Jira and Bugzilla, use to create a more graphical alternative to the basic text file.

# # Using bug tracking with teams

Bug tracking becomes especially important when teams are involved. For instance, many open source technologies consist of developers around the world. Imagine how tedious it would be to track bugs in e-mails or phone calls across all these developers. This is where bug tracking becomes especially important. That doesn't mean a single developer can't benefit from the same system.
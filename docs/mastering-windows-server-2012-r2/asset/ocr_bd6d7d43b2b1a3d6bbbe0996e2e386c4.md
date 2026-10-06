# FIGURE 13.22
Viewing a quota template

![](bbox=[0.166, 0.175, 0.833, 0.368])

The page on the right of the figure was reached by selecting the Warning (100%) notification threshold and clicking Add. It is the quota.exe command-line tool to modify the quota from a limit of 200 MB to 250 MB. The commands you put here are limited only by your imagination. If necessary, you also set the security context of the command depending on what permissions the command needs to execute.
In addition executing a command, the other threshold responses are sending an email, logging an event, and creating a report.

# E-Mail Message Tab

The E-Mail Message tab allows you to configure an email response if the threshold is reached. If you want to send an email to an administrator, simply add the administrator's email address (or an administrator's distribution group) on this page in the format of account@domain, such as ITAdmins@bigfirm.com. You can also configure it to send an email to the user who exceeded the threshold by selecting a box. FSR uses Active Directory to look up the user's email address
The templates include a preconfigured subject line and message body, and both include variables. In Figure 13.23 the message body includes several variables: Source I/O Owner, Quota Path, Server, and more. If you click either the subject line or the message body, the variable drop-down box will be enabled. You can select any of these variables to see a short explanation of what it is. We know when we first saw [Source Io Owner], we couldn't figure out what “lo” was, but after selecting it from the drop-down box, we saw meant I/O, or input/output.
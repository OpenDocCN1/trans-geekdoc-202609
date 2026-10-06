Local Group Membership Perhaps you have a policy that workstations are set up so that the only accounts in the local administrators account and the Domain Admins group from the domain. But now and then, some support person "temporarily" elevates a user account to the Administrators group, with the unintended intention of undoing the action "as soon as the need is over." And, because support person is busy as all support folks are, and undoing never gets done. By applying a security template that says "only Administrator and Domain Admins can be in the local Administrators,” reapplying the template kicks everybody out who's not supposed to be there.

# ENFORCING SECURITY SETTINGS

Templates automate the process of setting some security information, just as if you had sat down and done it from the GUI. There is no magic guardian that constantly monitors a system to ensure that your desired template settings are always enforced. The only way to ensure that your settings remain in force is to either reapply the template on some regular basis or create a GPO to apply the template, because security settings in a GPO are updated, regardless of any changes, every 16 hours.

Local Security Policy Settings Every machine has dozens of local security settings, things like, "Should I show the name of the person who logged in?" and "How often should passwords on locally stored accounts be changed?" and "Who should be allowed to change the time on this system?" to a name few.

# Working with Templates

It's easy to show you how to work with templates with an example, let's build a template to do three things:

+   - We'll ensure that no one is in the local Power Users group.

+   - We'll set NTFS permissions so that the directory C \SECRET will be accessible only to the local Administrators group.

+   - Finally, we'll shut down Internet Information Services, that pesky web server that seems to install itself on every operating system that Microsoft makes.

First, you'll need some tools. Let's build an all-in-one tool using the MMC. Also, you'll need two snap-ins: Security: Security Templates and Security Configuration and Analysis. Set it up like so:

+   1. Click Start, type mmc /a in the Search field, and then press Enter to bring up the empty MMC.

+   2. In the empty MMC, choose Add/Remove Snap-in from the File menu.

+   3. In the Add or Remove Snap-in dialog box, click Security Configuration and Analysis and then the Add button. Then click Security Templates and Add again.

+   4. Click OK.

+   5. Save your new custom tool for future use.
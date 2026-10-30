There are three permissions. First is the user, the second is the group that user is in, and the third is everyone. So, in Figure 9-12, I am giving full permissions to the user, the group, and read only to everyone else to file atestfile.txt.

![](bbox=[0.12, 0.2, 0.78, 0.53])

FIGURE 9-12 Assigning File Permissions with chmod Command.

# bg Command

The bg command sends a job to the background. Then it is running without interaction with the user.

# fg Command

The fg command sends a job to the foreground, so you can interact with it. The process will use your current terminal. If you omit the job you wish to use the fg command with, it will simply bring to the foreground the last job that was backgrounded.

# useradd Command

The useradd command is pretty straightforward: it adds a specific user to the system. There are a number of options for this command:

+   - -c: Comment. This adds a comment to the user file. Often administrators use this to put in a full name for the user or an account name.
# FIGURE 26.19

Configuring a single user with a roaming profile

![](bbox=[0.318, 0.103, 0.658, 0.452])

When you do this, no folder is created. Remember that the folder will be created on behalf of the user when they log in. So, don't be surprised to find no new folders in the Profiles folder yet. You'll have to test it first.

You can also use PowerShell to configure a user's roaming profile attribute of the user object. You will use the -aduser cmdlet:

```
set-aduser jbloggs -profilepath \\\bigfirm.com\\bigfirmshares\\Profiles\\Jbloggs
```

You're now ready to test this, which is a necessary step before allowing your users to log in.
A profile is created on the workstation (Remote Desktop server) when the user logs in for the first time. You can see this in Figure 26.20.
A new, empty folder is created on the profile for the user. Note that the name has a .V2 extension. This signifies that the profile is a version 2 profile and was created by a Windows 7 or newer operating system. Do not make the mistake of specifying .V2 in the profile path. It's an easy trap to fall into. For example, specifying a profile as \\\bigfirm.com\\bigfirmshares\\Profiles\\Jbloggs.V2 will cause the profile to not load. Windows will automatically add that extension to the folder name as required.

Log out, and the user's profile is uploaded from the workstation to the file share. It is now possible for this user to roam from workstation to workstation and maintain the same working environment.
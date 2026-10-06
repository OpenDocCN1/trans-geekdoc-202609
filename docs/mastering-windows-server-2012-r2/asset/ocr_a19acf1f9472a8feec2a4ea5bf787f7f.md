After you log in, you will be asked for the domain name:

```
cmdlet Add-Computer at pipeline position 1
Supply values for the following parameters:
Credential
DomainName:BigFirm.com
```

By default, the Windows Setup program assigns a really imaginative computer name. You can find that using the hostname:

```
PS: c:\Users\Administrator>hostname
```

Since that name isn't very friendly, we'll change it to Bfsc1. (It's not a huge improvement, but at least you can without your fingers getting in a knot). The following command tells PowerShell what you want to rename the computer:

```
PS: c:\Users\Administrator>Rename-Computer
```

PowerShell will prompt you for the new computer name:

```
cmdlet Rename-Computer at pipeline position 1
Supply values for the following parameters:
NewName:bfsc1
```

# Updating the Server

Next, you'll perform the typical housekeeping chores to update the server with the latest revisions and security patches. This consists of two steps:

+   1. Enable automatic updating and feedback.
2. Download and install updates.

# ENABLING AUTOMATIC UPDATING

You can modify automatic updates with just a few commands using SCONFIG. At the command prompt type SCONFIG. You will see a menu appear in your command window. Select option 5, Windows Updates Settings. It will first tell you the current setting, which is Manual by default. To change it to Automatic, simply type the letter A. Figure 3.9 shows the Server Configuration menu and the alert telling us that automatic updates have been.

You can also see in Figure 3.9 all the tasks you can use SCONFIG for. We have covered some of these tasks using tools like PowerShell, but this is another option to accomplish the stage.

# DOWNLOADING AND INSTALLING UPDATES

For this step a full installation, we prefer to open the system properties of the computer and navigate to the hyperlink Windows Update Web Site Then we kick off the download and installation of patches. However, this uses Internet Explorer, which isn't installed on Server Core. If you look back at Figure 3.9, you will see that option 6, Download and Install Updates, can take care of this for you.

After you enter the command prompt, SCONFIG will ask you if you want to search for all updates or just recommended updates. When you make your selection, it will return your results. You can then choose to install all, none, or just individual updates.
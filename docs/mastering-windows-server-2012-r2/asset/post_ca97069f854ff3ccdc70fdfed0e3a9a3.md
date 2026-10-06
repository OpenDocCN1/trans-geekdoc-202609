
# FIGURE 26.48
BigFirm's populated DFS namespace

![](img/41a83208e6906a3732620203b836cea7_1364_0.png)

We've already covered the basics of creating and linking Group Policy objects in Chapter 9, we will skip ahead to the meat of what the drive-mapping preferences are all about. In a newly created group policy called Drive Mappings, select the Drive Maps preference item and create a new mapping.

Your first option will be to select what action you want your drive mapping to perform. As shown in Table 26.13, you have four choices. It is also worth noting that these four choices will appear again and again throughout most of the Group Policy Preferences.

# TABLE 26.13 Drive-mapping actions

| ITEM | DESCRIPTION |
| :--- | :--- |
| Create | This will create a new drive mapping if one does not exist. If there is a drive mapping already in place with drive letter, it will do nothing. |
| Replace | Deletes the existing mapped drive and creates a new one. |
| Update | Modifies the settings of an existing mapped drive. If no mapped drive exists, then it will create a new one. |
| Delete | Deletes the mapped drive. |

We are going to select Replace, because we want to ensure that the drive will be mapped to our DFS file by Y. Next, you will want to enter the location of the DFS file shares and your drive letter to Y, as shown in Figure 26.49.

The next step will be to make sure that the members of the Senior Management group get this drive mapping. To do this use item-level targeting. With the Common tab, check the "Item-level targeting" box, and click the Targeting button. As Figure 26.50 shows, you can select a multiple of options for applying the preference, everything from the type of network connection you have to the time of day. In our scenario we will select Security Group, apply the BigFirm\Senior Management group, and link the group policy to the root of BigFirm.

# CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

# FIGURE 26.49

New Drive Properties

![](img/41a83208e6906a3732620203b836cea7_1365_0.png)

# FIGURE 26.50

New Drive Properties options

![](img/41a83208e6906a3732620203b836cea7_1365_1.png)

# MANAGING USERS WITH GROUP POLICY PREFERENCES AND LOGON SCRIPTS

Item-level targeting not only allows you to select a condition, such as if a user is a member of a group (Inclusive), but also allows you to choose to apply the policy if the user is not a member of a security group (Exclusive). You have the ability to mix and match conditions, such as if the user is a member of a security group and has a particular application installed as well.

As you can see in Figure 26.51, when you log in as one of the users in the Senior Managers group, the user inherits the Group Policy object, and the D drive mapping preference has been applied.

FIGURE 26.51
Drive mapping via Group Policy Preferences

![](img/41a83208e6906a3732620203b836cea7_1366_0.png)

# Executing Commands at Logon

Login scripts still have a place in the Windows 2012 world. They are still very useful, such when needing to execute a series of commands at logon.

Say you've deployed an antivirus application that will run for every user you logs in. The command is MyVApp --configure. The script that will run everyone when they run in their logon is:

MyVApp --configure

Launch Notepad, type the following in the previous commands, and this time as Logon.bat on your workstation. That script will cause the commands to run every time the user logs in. You can also use Visual Basic Scripting (VBS) or PowerShell instead. To make this login script available to all users in the domain in all locations where they can log in. Frankly, there is a share on every domain controller that is part of Active Directory and is replicated for you. This share is called NETLOGON and can be found in \\bigfig.com\SYSVOL\bigfig.com\scripts as well as \\bigfig.com\Netlogon. You can also find it on every domain controller in \<servername>\NETLOGON. Copy all your login scripts in here.

You'll want to think about the name of your logo script if you have a large domain and will have many logo scripts. A naming standard describes the role of the script and who it will be associated with will simplify keeping track of the script. There are several ways you decide how this logon script will be linked to your users.

The simplest solution is to define the logon script on a per-user basis, which you can see in Figure 26.52. The "Logo script" field in the user object allows you to specify a script that is contained within the NETLOGON share on your domain controllers. The logon script must be contained in NETLOGON.

# FIGURE 26.52

Configuring the user object
"Logo script" attribute

![](img/41a83208e6906a3732620203b836cea7_1367_0.png)

This method is fine if there are only a few users or if the user has a unique script. However, you will want a different mechanism if there are many users to configure.
A better way to configure users with a logon script is to use a GPO. Think about this for a moment:

- A single GPO can apply to many users.
- A GPO can be linked to an OU; that is, a logon script can be linked to a unit of the structure of the organization.
- A GPO can be linked to an Active Directory site; that, a logon script can be linked to a unit of the physical structure of the organization. For example, may certain things should be done when logs into specific local networks in a site.
- You can use loopback policy processing to associate a different logon script with a user when they log onto certain computers.

Create and link a GPO, and open it for editing. Navigate to \User Configuration\Windows Settings\Scripts (Logon/Logoff).
You cannot argue that this isn't a powerful approach. Some organizations have chosen to use-per-user. That's why we don't recommend it as a place to keep your logon script! Its entirety is available to everyone as a share; we will now use to deploy your script via a GPO. Double-click Logon in the GPO to edit the logon script. This opens the dialog box where you can add a logon script:

- 1. Click Add.
This opens the dialog box in Figure 26.53.

FIGURE 26.53
Specifying the logon script

![](img/41a83208e6906a3732620203b836cea7_1368_0.png)

- 2. Select a specific logon script.
3. Feed parameters to the logon script that will change its behavior.
4. Browse to open a wizard to select an existing logon script.
The default location that it chooses is a folder \User\Scripts\Logon within which the GPO you are editing is contained. This is a nasty location to hide when you aren't editing the GPO.5. Navigate to the DNS folder that represents NETLOGON in your domain.
Our domain is bigfig.com. This is in \\bigfig.com\SYSVOL\bigfig.com.scripts. The NETLOGON share is in \\bigfig.com.scripts. In this folder you will find the logon script you previously copied to NETLOGON.

- 6. Click OK in the Logon Properties dialog box shown in Figure 26.54, and you will have finished deploying your logon script via a GPO.
You should test this now, by logging in and verifying that your command is executed before configuring users.

# CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

FIGURE 26.54

The configured logon script using Group Policy

![](img/41a83208e6906a3732620203b836cea7_1369_0)

# Multiple Logon Scripts

You can associate multiple logon scripts with a user if you use Group Policy assignment. Each of these scripts will run for the user.

Figure 26.55 shows where we have added multiple logon scripts using a GPO. You can change the ordering of the logon scripts using the Up and Down buttons. The script that is listed on top is the first to be executed.

FIGURE 26.55

Configuring many logon scripts using Group Policy

![](img/41a83208e6906a3732620203b836cea7_1369_1.png)

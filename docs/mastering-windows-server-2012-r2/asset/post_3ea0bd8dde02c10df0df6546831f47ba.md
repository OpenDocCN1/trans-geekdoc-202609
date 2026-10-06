
to impose control over IE settings (unfortunately, many companies use Firefox instead of Internet Explorer). Here are a few settings that we find useful:

- If you want to prevent users from messing with the security zones you set up or if you want Explorer to use the same security zones and proxy settings for all on the computer, enable the Security Zones and Proxy settings under Computer Configuration/Policies/Administrative Templates/Windows Components/Internet Explorer.

- To prevent users from downloading offline content to their workstations, enable the policy named Adding Schedules for Offline Pages under User Configuration/Policies/Administrative Templates/Windows Components/Internet Pages.

- To prevent users from making any changes to IE's Security, Connections, or Advanced properties, disable access to these and other Control Panel pages in the User node under Internet Explorer/Internet Control Panel.

- If you want to prevent users from downloading any software from the Web, that's a little more difficult. There is a policy under the User Configuration/.../Internet Explorer/Browser Menu that disables the Save This Program to disk. However, this will prevent users from installing the software without saving it, and there are probably a couple of other ways around the restriction for a determined user.

## Prevent Users from Installing or Running Unauthorized Software

While we're on the subject of preventing users from installing software, enable the policy named Prevent Removable Media Source for Install found under User Configuration/.../Windows Components/Installer to keep users from running installations from CD-ROM or floppy (remove them?). And if you are going to do that, you should enable the policy to hide the "Add a program from CD-ROM or floppy disk" option in User Configuration/.../Control Panel Add or Remove Programs. The Control Panel node includes several options to disable or remove part or all of the Add/Remove Programs applet.

Disabling/Add-Remove Programs will prevent users from running setup routines in others; however, anyone can use a command line that can circumvent these restrictions, so you'd need to open the system node of the User Configuration Policies and enable the policy called "Prevent access to own programs." If you are looking for that policy called "Run only specified Windows applications," it's found in the System node of the User Configuration templates (shown in Figure 9.26). Be careful with this one, though; you have to make a list of all applications that can be loaded from Windows Explorer. There is also a setting in the same location called "Don't run specified Windows applications." For this one, you'd need to make a list of disallowed programs.

## PREVENTING REGISTRY EDITING

You can create a policy to prevent access to the registry editing tools. This policy prevents users from running regedt32.exe and regedt, although regular users only have access to the vast majority of the registry anyway.

## FIGURE 9.26

To run only specified applications

![](img/41a83208e6906a3732620203b836cea7_537_0.png)

The same principle applies to the Start menu and taskbar option called "Run from the Start menu." Experienced users will not be prevented from running unapproved programs just because Run is removed from the Start menu, so you have to seek out all the other ways of launching programs from Task Manager unless you disable it in the Ctrl+Alt+Del options.

### CREATING A CONSISTENT DESKTOP AND START MENU

If you want to achieve a simplified and consistent desktop and Start menu for your organization or department, you'll probably need to combine folder redirection with the restrictions that are available in the administrative templates.

## Using Group Policy to Set Password and Account Lockout Policy

One of the most misunderstood and complex aspects of Windows AD is how and where password policies are configured and managed. In this section we will get the skinny on how it works to remove doubt moving forward. Here is a list of truths and myths Account Policy settings that should answer all of your FAQs.

### Truths

- The only way to modify the Account Policy settings for domain user accounts is in a GPO linked to the domain.
- Fine-grained password policies can be set up to have users in the same domain have different- Account Policy settings. In other words, IT users can have a 20-character password, and executives can have a three-character password.

A GPO linked to an OU will modify the local SAM Account Policy settings for the local users in the SAM of all computer accounts in that OU.

### Myths

- A GPO can be linked to the Domain Controllers OU to modify the Account Policy settings for domain user accounts.

- A GPO can be linked to an OU to modify the Account Policy settings for the user accounts contained within the OU.

- The ACL for the Default Domain Policy can be modified to include only certain groups, allowing different password policies in the same domain.

By default in a Windows Server 2012 R domain, the Default Domain Policy is used to establish the Account Policy for all user accounts in the domain. (This includes domain user accounts and all local SAM user accounts for computers joined to the domain). Password and account lockout policy settings are located under Computer Configuration/Policies/Windows Settings/Security Settings. The password policy includes the following:

Enforce Password History: Enable this option to specify the required number of consecutive unique passwords after a given password can be used.

Maximum Password Age: This option sets the amount of time for which a password can be used before the system requires the user to pick a new one. Organizations usually set this interval between 30 and 90 days.

Minimum Password Age: The value here is the amount of time for which a password must be used before the user is allowed to change it.

Minimum Password Length: This option defines the smallest number of characters that a user's password can contain. Seven or eight characters are a good minimum for passwords. This policy also disallows blank passwords.

Password Complexity Requirements: Enable this option to specify the complexity of passwords. Passwords must contain at least three of the following types: uppercase letters (A–Z), lowercase letters (a–z), numbers (0–9), and special characters (for example, @, %, #). If you enable this option but leave it blank, the requirement is not enforced.

Account Lockout Duration: This determines the interval for which the account will be locked out. After this time expires, the account will no longer be locked out and the user can try to log in.

Account Lockout Threshold: This value defines how many times the user can unsuccessfully attempt to in before the account will be locked out. If you define this setting, be sure to specify the number of attempts, or the account will never lock out.

Reset Lockout After: This defines the time interval after the count of bad login attempts will start. For example, suppose you have a count of two minutes and three attempts. If you mistype, you can wait two minutes after the second attempt, and have three tries again.

## Group Policy Preferences

One of the most impressive aspects of Windows Server 2012 R2 (not just Group Policy, but of the new OS) is Group Policy preferences (GPP). Group Policy preferences are extensions to Group Policy, which in normal speak is “settings in GPO”. These new settings add more than 3,000 policy settings to a GPO, and some of them are just amazing! For example, now you can modify the local Administrator password on every desktop in your environment, within about 90 minutes. You can also control the membership of the local Administrators group on all desktops and servers, without removing the key service accounts and other domain groups that are unique to each computer.

### GPP Settings

The GPP settings are a bit different from the other Group Policy settings, because they exist in duplication under both the computer and user areas of a GPO. This gives you great flexibility and power over setting you wish to unleash on the desktops and users in the environment.
For the GPP settings, you will see the list of options displayed in Table 9.1.

TABLE 9.1: Group Policy Preferences Settings

| GROUP POLICY PREFERENCES SETTING | AVAILABLE UNDER CONFIGURATION? | AVAILABLE UNDER CONFIGURATION? |
|--- |--- |--- |
| Applications | No | Yes |
| Drive Maps | No | Yes |
| Environment | Yes | Yes |
| Files | Yes | Yes |

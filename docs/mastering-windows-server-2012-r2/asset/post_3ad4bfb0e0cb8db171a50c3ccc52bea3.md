
## CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

- 3. Browse to where the NTUSER.DAT file is contained on the file server.

In our case, that is: D:\Shares\Profiles\Mandatory\V2\NTUSER.DAT. Open that file.

- 4. You'll need to give the loaded hive

You can't have a second HKEY_CURRENT_USER. Don't worry; this is only a temporary label that will be used when you're editing the opened NTUSER.DAT file. For the sake of simplicity, we've named the hive after the profile, that is, Mandatory.V2.

- 5. Browse to your loaded hive, for Mandatory, .V2 as shown in Figure 26.29, and right-click it.

## FIGURE 26.29
Browsing to the loaded registry hive

![](img/41a83208e6906a3732620203b836cea7_1331_0.png)

- 6. Select Permissions from the pop-up menu.

What you see in Figure 26.30 is the permissions for HKEY_CURRENT_USER as contained within the NTUSER.DAT file in the new roaming profile.

## FIGURE 26.30
Permissions for the loaded registry hive

![](img/41a83208e6906a3732620203b836cea7_1331_1.png)

- 7. Do two things to the permissions:

- Remove the entry for the user that was used to create the profile, it is, Jelway

- Add an entry for a security group that will require access to the roaming mandatory profile. In this case, it is, Authenticated Users from the domain. Grant this group Full Control over the hive.

8. Close the Permissions dialog box, and then select File > Unload Hive in regedit.exe.

You will be alerted if you want to unload the key and its subkeys.

9. Say Yes to that, and your modified NTUSER.DAT is saved.

You cannot use this roaming profile until you unload the hive.

## COMPLETING THE MANDATORY PROFILES

At this point, all you have done is create a roaming profile that could be used by anyone. Have made it a mandatory roaming profile. The conversion is quite: Navigate to the roaming profile you created, and rename NTUSER.DAT to NTUSER.MAN, as shown in Figure 26-31. The extension is what Windows detects that no changes saved to this profile; that is, it is a mandatory roaming profile.

## FIGURE 26-31
Rename NTUSER
DAT to NTUSER
MAN

![](img/41a83208e6906a3732620203b836cea7_1332_0.png)

You need to secure the mandatory roaming profile folder on the file server. Follow these steps:

1. Disable the inheritance of permissions from the parent folder, and set the mandatory profile's permissions as follows:

| Group | Permission |
| :--- | :--- |
| BF2\Administrators | Full Control |
| System | Full Control |
| BigFirm\Authenticated Users | Read & Execute |

You've granted access to the Authenticated Users security group.

- 2. Choose a group that matches the group to which you granted access to the NTUSER.DAT registry hive.

Setting the folder permissions does two things for you. It provides Authenticated Users (or whatever security group you choose to use) with access to the mandatory roaming profile but prevents members from changing it.

Now you to test the mandatory roaming profile.

- 3. Simply navigate to a test user, and change the profile entry to \bigfirm.com\BigFirmShares\Mandatory.

## WHERE'S “V2”?

> Notice that you did not add the .V2 extension. Consider it to be silent; the newer versions of Windows will add it as required, as discussed earlier.

- 4. Log in as the test user and verify that the customizations to the mandatory roaming profile are loaded.

- 5. Make some changes, then undo the customizations, and make a few of your own.

- 6. Log out and log in.

You should find that the loaded profile is reset to what was set up in the original mandatory roaming profile; no changes were saved. If that's what is happening, then you have a correctly functioning mandatory roaming profile.
You've configured JBlogs with \bigfirm.com\BigFirmShares\Profiles\Mandatory.V2 as the path to it.
JBlogs will now attempt to download the mandatory profile every time he logs in. If you log in now as a workstation, you will find that the entire profile is identical to that of Jelway. You can still make changes. However, when you log out, those changes are not saved. You can log in again and get the same mandatory profile that you had before, without any of the previously made and unsaved changes.

## Configuring Super Mandatory Profiles

There are some scenarios where you are using mandatory profiles but you cannot afford to allow anyone to be logged in if the mandatory profile cannot be downloaded for some reason, such as because of a network issue or a file server problem. When this be a realistic option? You're probably talking about something like a kiosk or a publicly accessible computer where it's better to have no service than a service that isn't tightly controlled.

So, it appears you need to find a solution for this scenario. Luckily, you have one in the form of super mandatory profiles. Implementing this solution isn't all different from implementing mandatory profiles.

Setting up super mandatory profile is just an extension of setting up a mandatory profile. Follow the previously described steps for configuring a mandatory profile, and then do the:

- 1. Rename the profile on the file server it has a .MAN.V2 extension; for example, rename Mandatory.V2 to Mandatory.MAN.V2.

- 2. Configure the .V2 component; for example, set the profile to \Bigfirm.com\BigFirmShares\Profiles\Mandatory.MAN.

- 3. Ignore the .V component to include the .MAN extension.

That's it! You've set a super mandatory profile for the user. The profile will act like a normal profile, not allowing any changes to be saved to the file server. However, unlike a normal profile, this user will not be to log in if the super mandatory profile cannot be downloaded.

There's an easy mistake that you can re-create to test this "no logon" functionality. Rename the NTUSER.MAN file in the mandatory profile to NTUSER.DAT. Now try to log on. You'll be informed that the profile could not be downloaded.

# CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

FIGURE 26.34
Redirecting folders to the user's home directory

![](bbox=[0.333, 0.105, 0.666, 0.401])

Redirect To The User's Home Directory This very simple solution will redirect the folder to the user's home directory. It does not create a subfolder for the redirected folder. Instead, it just dumps contents to the root of their home directory. Things will get impossible for users you redirect many folders.

Create A Folder For Each User Under The Root Path This will create a folder named after the redirected folder within the path you specify; for example, Documents will be created in \|Bigfirm.com\BigFirmShares\Home\Jblogs if you specify \|Bigfirm.com\BigFirmShares\Home. How do you intelligently adds the username? This will solve the previous confusion mentioned we.

Redirect To The Following Location This is a simple redirection where all users share a common folder. This might be suitable if redirecting a Start menu for Remote Desktop server farm.

Redirect The Local User Profile Location This forces the folder back to the local profile.

+   6. As shown in Figure 26.34, select redirect Documents to a subfolder in a DFS namespace. You can move the physical storage location of the folders, and you won't have to change this policy. You just need to update the link in the DFS namespace. You can do this with additional folders knowing that the user will see a distinct folder within their home directory for each redirected folder—nice and simple and fewer help-desk tickets!

+   7. Click the Settings tab to see how Windows will handle the redirection.
We'll go through the settings in Figure 26.35 in a moment.
# CHAPTER 14 CREATING AND MANAGING SHARED FOLDERS

conflict with these. But when you try to get the effective permissions for the Domain Users using this tool, it comes up with no access because this tool cannot calculate the effective permissions for domain groups that are nested in local groups.

This clearly limits the effectiveness of the tool, but you can still use it to calculate multiple ACEs for a user or group, as you saw in the previous example.

# OWNERSHIP

Through the course of assigning and revoking permissions, you are bound to run into the problem where no one, including the administrators, can access a file. And you cannot change the file's permissions because you need permissions in order to assign permissions. This could be a really tricky situation. Fortunately, ownership can help you.

There is an attribute of every object called owner. The owner is completely separate from permissions. There will be some owner for every object. But does that help you? Well, the owner of an object has a special privilege—the ability to assign permissions. Taking ownership of a file or folder is as easy task as the account being used has ownership over the desired resource. If you refer back to Figure 14.16, you will notice the Owner field identifies the Name. You will also notice there a Change option available (if this option is grayed out, you are not logged in with an account that has privileges) if you Select, a User Dialog box will appear, allowing you to assign ownership to another user or group.

On a corporate share in a production environment it would be a good idea to make sure that an IT-managed elevated or storage service account is the owner of all the files and folders. This configuration is used for most backup and restore purposes. Certain file systems cannot restore files for which they do not have permissions to do so. Imagine trying to restore a share on users who have made themselves owners of folders and files and removed all other access. Those folders or files would be un-restorable by anyone except the owner. This reinforces the good policy of keeping tight and manageable permissions throughout the environment from one controlled, centralized location.

# Working with Hidden Shares

Once you share a folder to the network, it becomes visible to the user community. But what if you don't necessarily want everyone to see the share? For example, we have created an installation share on a server that whenever we go to a user's workstation, we can install applications without having to bring CDs. It's really a convenience, but at the same time, we don't want the users clicking through shares, installing every program they can get their hands on. Sure, we could limit the share to access only to us, but that is a kind of pain, too. We don't want to log the off and log in every time we do an install, especially if user profiles are being used. This is why creating hidden shares can help. We want the share to be available but just not easily available. Although not a completely solution, it is a deterrent to browse-happy users.

To create a hidden share underneath a folder, but place a dollar sign at the end of the name. That's it. Now, whenever the server registers its information to the browse list with its available resources, it will not register that hidden share.

We'll now show how to create a share called INSTALL$, which will be shared from I:\Install
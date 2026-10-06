# MANAGING PERMISSIONS 67

or launched. If a user has only Read permission, and not Read & Execute, the files can't be executed.

List Folder Contents The List Folder Contents permission allows a user to view the contents of a folder. It will allow a user to see files in a folder but not apply Read permissions to those files.

Write If a user is assigned Write permission to a file or folder, the user can modify the file or folder. This includes adding new files or folders to a folder or making changes to existing files or folders. However, it does not include deleting files from a folder.

Modify includes all of the permissions from Read, Read & Execute, and Change and adds the ability to delete files and folders.

Full Control Full Control is a combination of all the available permissions. It adds the ability to change permissions and take ownership of files or folders.

# Share Permissions

Share permissions to share shares only when they are accessed over the network. There are only three share permissions:

Read Users granted Read permission can read files and folders within the share.

Change Users granted Change permission can read, execute, modify, and delete files and folders within the share.

Full Control Users Full Control permission have all the permissions from Change and can also modify permissions on the share.

# Share and NTFS Permission Similarities

Now that you have a basic understanding of the overall NTFS and share permissions, it's easier to explore the similarities, and there are many. These include:

+   - Both can be assigned Either Allow or Deny.
- Both are cumulative.
- Deny takes precedence with both.
- Both support implicit deny.

# ASSIGNING ALLOW OR DENY

As you start working with permissions, you'll notice that they have both Allow and Deny boxes for the listed permissions. Here's an overview of how they work:

+   - If the permission is set to Allow for a user or group, the user or group has this permission.
- If the permission is set to Deny for a user or group, the user or group does not have the permission.
- Permissions are cumulative. If a user has multiple Allow permissions assigned (such as Allow Read and Allow Change), the user has a combination of the assigned permissions.
- If both Allow and Deny permissions are assigned for a user, Deny takes precedence.
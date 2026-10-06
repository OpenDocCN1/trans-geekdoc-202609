2. Disable inheritance of permissions on the folder, and configure the permissions as shown here (and Figure 26.13):

| Group | Permission | Where |
| --- | --- | --- |
| Creator Owner | Full Control | Subfolders and files |
| BF2\Administrators | Full Control | This folder, subfolders, and files |
| System | Full Control | This folder, subfolders, and files |
| Authenticated Users | List Folder/Read Data; Create Folder/Append Data; Read Attributes | This folder, subfolders, and files |

FIGURE 26.13
The advanced permissions of the Profiles folder

![](bbox=[0.25, 0.386, 0.863, 0.712])

Why Read Attributes?
Notice that we've added last permission for Read Attributes. It isn't documented in Microsoft documentation that we have read. However, a user's profile will fail to completely save to the file server if this permission is not added to the profile folder.
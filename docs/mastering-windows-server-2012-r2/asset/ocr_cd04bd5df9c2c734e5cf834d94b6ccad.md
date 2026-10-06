# Removing a Group or User

To remove a group or user entry, just click the Remove button from either of the two properties sheets you just saw. If a user or group is there because of inheritance, the Remove option will be unavailable, and you will have to disable inheritance by selecting the "Disable inheritance" option.

# Using the Detailed Interface to Get the Whole Story

Look at Figure 14.19. We'll remind you of something we said before the interfaces used for managing NTFS permissions: this window doesn't give enough information, and it's clunky. If you decided to disable inheritance to get rid of the Users' group permissions and clicked the Remove button in this dialog box to accomplish that, you would remove both of the entries that you saw in Figure 14.16. Also, if you used this window to add a user or group account, you'd only be able to select the permissions boxes you see here—you wouldn't be able to specify exactly where you wanted those permissions applied using inheritance. You'd have to drill down to the dialog box in Figure 14.16 to do that. It's best to bypass this unnecessary dialog box and go straight to the detailed view. View that you have the full story to start with.

# CONFLICTING PERMISSIONS

You can assign permissions to files, and you can assign permissions to directories. Just as permissions can conflict with file and directory permissions, file permissions can conflict with directory permissions. In share-level conflicts, the share wins: The share-level permissions set the maximum allowable access, so if the share-level permission is Read and the NTFS permission is Write, then the result is Read only. If you assign read-only rights to a directory but assign change rights to a file within directory, you will still be able to change the file.

# MULTIPLE PERMISSIONS

Now for another problem. You have given Administrators group control over the APPS folder, and everyone else has Read & Execute permissions only. Here is where permissions can come into conflict. Everyone is a user, right? Even administrators are users. Hmm. How does this work? Well, in the case of multiple permissions, the least restrictive permissions prevail, as long as share permissions aren't involved. Let's say we have an administrator named Bob. Bob is part of the Users group, which has read-only rights on a file. Bob is also part of the Administrators group, which has full control. In this case, Bob will get full control because he is restrictive.

# DENY PERMISSIONS

We talked about Deny permissions with respect to shares earlier and then briefly about the effects of inheriting permissions as it relates to Allow and Deny. The same thing applies in file and directory permissions, but in a way that's just a bit more complex than the increased number of security options. Think of a corporate bonus-award spreadsheet file that you are trying to protect. You want everyone to see the file, but you only want the managers to be able to actually change the file. It makes sense: grant the Employees group the right to
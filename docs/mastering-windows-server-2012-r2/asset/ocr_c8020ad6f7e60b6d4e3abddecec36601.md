8. Select the Allow Write permission for the group you've added to ensure they can also make changes to the files, and then click OK.

9. Remember to remove the Everyone group from this set of permissions as well: Select the Everyone group and click Remove.

Share permissions and NTFS permissions are managed separately but work together to provide proper permissions. Your display will look similar to Table 13.18.

FIGURE 13.18
Viewing the NTFS permissions

![](bbox=[0.328, 0.256, 0.903, 0.563])

10. Click Apply and OK on the Advanced Security page to finalize permissions.

11. Click Apply and OK on the Apps Properties page to finish the exercise.

# Combining Share and NTFS Permissions

People sometimes find it challenging to identify the permissions a user will have when they access a file or folder via a share. We like to keep it simple with these three steps:

+   1. Determine the cumulative NTFS permissions.
2. Determine the cumulative share permissions.
3. which of the two provides the least access (commonly called the most restrictive permission).
Imagine that Sally is a member of the G_Sales and G_ITAdmins groups. The assigned permissions for the SalesData folder (shared as the SalesData share) are shown in Table 13.2.
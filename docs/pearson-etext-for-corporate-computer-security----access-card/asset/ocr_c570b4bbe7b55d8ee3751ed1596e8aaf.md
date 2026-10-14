Some versions of UNIX assign permissions more granularly than the standard, but the standard is the normal behavior of UNIX. Figure 7-23 compares the assignment of permissions in Windows and UNIX.

# NUMBER OF PERMISSIONS

As just noted, Windows has six different permissions that can be assigned to users and groups. If finer granularity is needed, Windows has 13 specialized permissions to assign.

By contrast, UNIX only has three permissions to assign. **Read** is read-only access (denoted by an **r**). **Write** allows the account or group to make changes (denoted by a **w**). **Execute** permits the execution of programs (denoted by an **x**). These permissions are usually written as **rwx**.

# NUMBER OF ACCOUNTS OR GROUPS

As just noted, Windows can assign different permissions to many accounts and groups. In a directory (folder) for a project team, for instance, different members and subgroups within the team probably should be given different access permissions.

UNIX, however, historically can only assign different permissions to three entities. One entity is the account that *owns* the file or directory. The second is a single *group* associated with the directory. The third is *everyone else*. There is no way to assign different permissions to multiple accounts or groups. This is limiting.

Although UNIX generally has good security, its inflexibility in handling permissions is a serious issue. Even UNIX evangelists touting the security strengths of UNIX will say, “Oh yeah, that,” when asked about permissions in UNIX.

# Test Your Understanding

+   13. a. What are the three UNIX permissions?
+       b. Briefly characterize each.
+       c. Compare the number of UNIX directory and file permissions with that of Windows.
+       d. To which three individual accounts or groups can permissions be assigned for a particular directory in UNIX?
+       e. How does the number of accounts or groups to which permissions can be assigned in UNIX compare with that of Windows?

# 7.6 Creating Strong Passwords

# 7.6 Explain how to create strong passwords.

At this stage in computing history, one of the most effective ways of hardening a host is to have a strong password-protecting access to the underlying system. In Chapter 5, we looked at how to develop effective password policies to control access to the system. We have also listed a few basic guidelines to govern password creation.

+   - Be at least 12 characters long.
+   - Have at least one change of case, not at the start of the password.
+   - Have at least one digit (0 through 9), not at the end of the password.
+   - Have at least one non-alphanumeric character, not at the end of the password.

However, in this chapter, we will look more closely at how passwords are created, stored, and cracked. Despite knowing what they *should* do, systems administrators often ignore established password policies. They may get negative responses from
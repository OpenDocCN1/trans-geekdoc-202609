+   - **--help:** This will displays help for **chown** and exits.
+   - **--version:** This will display the version information and exits.

Figure 9-11 shows a very simple example of **chown**. In this figure, we change the owner of the file *atestfile.txt* to the user *bob*.

![](bbox=[0.07, 0.24, 0.73, 0.59])

FIGURE 9-11 Changing File Ownership with **chown** Command.

# chmod Command

The **chmod** command is used to change the permissions on a file. The options are simple:

+   - **4** stands for “read.”
+   - **2** stands for “write.”
+   - **1** stands for “execute.”
+   - **0** stands for “no permission.”
+   - **7** combines **4**, **2**, and **1**, giving all permissions.

The syntax is

```
chmod options permissions filename
```
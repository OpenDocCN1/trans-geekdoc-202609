# Part II: Solutions

![](bbox=[0.175, 0.109, 0.953, 0.335])

Fig. II.13.4. Setting access permissions for the index.php file

Frequently, an Apache Web server is executed with the apache user privileges, and PHP cannot change access permissions. To allow a PHP script to change access permissions, its owner has to be changed to apache (Listing II.13.5).

# Listing II.13.5. File access permissions

```
shell> ls -l
-rw-r--r-- 1 igor igor 690 Sep 27 17:35 2.php
-rw-r--r-- 1 igor igor 527 Sep 27 20:22 3.php
-rw-r--r-- 1 igor igor 568 Sep 27 20:51 4.php
-rw-r--r-- 1 igor igor 628 Sep 23 21:19 5.php
-rw-r--r-- 1 apache igor 2164 Jan 7 21:09 index.php
drwxr-xr-x 1 root root 11 Oct 5 2004 -> /mnt/e/main
```

In Listing II.13.5, produced by the Linux ls -l utility, access permissions are indicated by the first-character group. The first character, defines the file type (in this case, a regular file) or a symbolic link (i). The remaining nine characters define the file or directory access permissions for owners, group members, and others. The permissions for each group are the following:

+   - r — Read the file
- w Write or modify the file
- x Execute the file if it is a script or program; view the file if it is a directory

Thus, the string -rw-r--r-- in Listing II.13.5 describes a regular file whose owner has read and write rights, with the group members and other users having only read rights.
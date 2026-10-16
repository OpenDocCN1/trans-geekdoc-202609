# From source files

Before you decide to install MySQL from source files, check for binary files for your operating system. MySQL binary files are precompiled, ready-to-install packages for installing MySQL. MySQL binary files are very convenient and reliable.

You install MySQL by downloading source files, compiling the source files, and installing the compiled programs. This process sounds terribly technical and daunting, but it’s not. Read all the way through the following steps before you begin the installation procedure.

To install MySQL from source code, follow these steps:

+   1. **Point your Web browser to www.mysql.com, the MySQL home page.**
+   2. **Click the Production version number link.**
+      Look in the list on the right side of the screen, labeled MySQL Products. Look for the section under the Database Server heading. As of this writing, the production release is 4.0.17.
+   3. **Scroll to the bottom of the screen to the Source Downloads heading.**
+      This section lists several downloads.
+   4. **Locate the tarball version and click the download link next to it.**
+      A dialog box opens.
+   5. **Select the option to save the file.**
+      A box opens that lets you select where the file will be saved.
+   6. **Navigate to where you want to install MySQL and then click Save.**
+      The standard location is `/usr/local`. It is best to use the standard location if possible.
+   7. **After the download is complete, change to the download directory — for instance, cd /usr/local.**
+      You see a file named `mysql-`, followed by the version number and `.tar.gz.` — for instance, `mysql-4.0.17.tar.gz`. This file is a *tarball*.
+   8. **Create a user and group ID for MySQL to run under by using the following commands:**

```
groupadd mysql
useradd -g mysql mysql
```

The syntax for the commands might differ slightly on different versions of Unix, or they might be called `adduser` and `addgroup`.

*Note:* You must be using an account that is authorized to add users and groups.
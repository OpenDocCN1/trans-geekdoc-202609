# Chapter 11

In this section, you protect a folder so when a user visits a page in that directory, a dialog box pops up requiring that a username and password be entered.

# Try Out Creating htaccess and htpasswd Files

First of all, let's take a look at your Apache configuration file, http.conf. The Linux example is located somewhere similar to /usr/local/apache/conf, and the Windows example will be similar to: c:\FoxServer\Apache\conf.

Follow these steps:

+   1. Open the http.conf file and look for the following lines around line 270 or so. By default the lines are likely to look like this and will reside in the <Directory /> section that contains your Web root:

```
# AllowOverride controls what directives may be placed in .htaccess
# files.
# It can be "All", "None", or any combination of the keywords:
# Options FileInfo AuthConfig Limit
AllowOverride None

```

+   2. For htaccess capabilities, change the lines to look like this:

```
# AllowOverride controls what directives may be placed in .htaccess files
# It can be "All", "None", or any combination of the keywords:
# Options FileInfo AuthConfig Limit
AllowOverride AuthConfig

```

+   3. Create a file named .htaccess in the directory that you wish to restrict access to. This file will require only the following lines to function correctly:

```
AuthType Basic
AuthUserFile /usr/local/apache/htdocs/protected #or your windows path
AuthName "Restricted"
<LIMIT GET POST>
require valid-user
</LIMIT>
```

+   4. Now, when creating the password file and adding your first user, you need to separate the installation based on your operating system selection. Create your password file in your main login directory by completing these steps:

For Linux htaccess installation:
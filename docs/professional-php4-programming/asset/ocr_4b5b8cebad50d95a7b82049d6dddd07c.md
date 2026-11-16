# allow_url_fopen

This disables the opening of remote files on other web or FTP servers. If there is no need to access files from other HTTP or FTP sites then turn this off.

# Safe Mode

PHP, in an attempt to solve the shared server security problem, has a feature called safe mode. This feature limits the actions that can be performed by scripts, thus limiting the damage possibly malicious scripts can do to the server and other people's work on the server.

When safe mode is on, PHP checks if the owner of the current script is the same as the owner of any file trying to be opened. If the user ids do not match, PHP will issue a warning telling the user that this feature has been restricted.

There are several other settings that can be set in the php.ini file directly related to the behavior of safe mode. These are explained below.

# safe_mode

This directive controls whether safe mode is on or off . By default it is set to off.

# safe_mode_gid

Normally when safe_mode opens a file, the user id of the owner of the file has to be the same as the user id of the script. If you turn this on, it relaxes this slightly so only the group ids have to be the same. By default this is off.

# safe_mode_exec_dir

This directive is a list of directories where people in safe mode can execute programs. If the program is not in one of the directories in this list, the execution of the program will fail. Symlinks are resolved, so it is not possible to bypass this directive by using symlinks.

# safe_mode_allowed_env_vars

A list of prefixes for the names of environmental variables users may be set under safe mode. By default this is set to PHP_, so only environmental variables starting with PHP_ may be set.

# safe_mode_protected_env_vars

This is a list of variables that are explicitly protected under safe mode. Even if safe_mode_allowed_env_vars allows the altering of all environmental variables, this setting will stop any listed here from being changed. By default this is set to LD_LIBRARY_PATH.

# Securing MySQL

MySQL is one of the most popular open source database servers. It is worth spending a bit of time making sure it's secure. The default installation of MySQL isn't particularly secure; the steps below will help to secure it a bit more.
Failure to remove the -c flag after the first user setup will result in a new password file and remove any existing users.

While not required, it is a good practice to periodically back up this and any other important files in case your system encounters an unexpected crash or data corruption.

The command to create a password is simply a call to the password application with the username appended to the end.

```
$ cd /usr/local/apache/bin/
$ htpasswd -c /usr/local/apache/passwd/passwords USERNAME
```

Be sure to replace USERNAME with the actual username you want to add.

The htpasswd application will ask you for the password you want to assign, and then ask you to type the same password again to confirm it.

The generated password file is encrypted. However, you should still store it in a secure location.
Under no circumstances should this file be stored in the public directory because it could compromise
the integrity of your system.

This isn't as important in a development system, but it is a good practice to follow all proper security
steps, even in a development setup, to become familiar with them. As you continue to work on
servers, security will become second nature. You should never put it off to save time.

After you create the password file, add the security check in a .htaccess in whatever location
you want to password protect. For example, let's add the authentication to the entire server
because this a development server and you wouldn't want anyone viewing it.

Add the following to a new .htaccess file in the root of the Web directory.

```
AuthType Basic
AuthName "Authorization Required"
AuthUserFile /usr/local/apache/passwd/passwords
Require valid-user
```

This informs Apache that any request to this directory and below requires authorization. The last
line allows any user in the password file to be able to log in.

**Require valid-user**

You can also add a specific username, but this is more difficult to maintain.

This is basic authentication so it does have various limitations. For example, you cannot modify
the dialog box that displays in the user's browser. You can't modify the label values next to the
input boxes and, most importantly, you cannot allow the user to log out.

If your application requires a more customized and integrated login system, it may be better to
build a custom PHP/MySQL setup, depending on your requirements.
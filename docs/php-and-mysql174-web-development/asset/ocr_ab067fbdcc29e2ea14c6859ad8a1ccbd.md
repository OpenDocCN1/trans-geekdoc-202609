The line

```
ErrorDocument 401 /var/www/pmdwe/chapter16/rejection.html
```

tells Apache what document to display for visitors who fail to authenticate (HTTP error
number 401). You can use ErrorDocument directives to provide your own pages for
HTTP errors such as 404. The syntax is

```
ErrorDocument  error_number URL
```

Listing 16.6 htpassword File Stores Usernames and Each
User's Encrypted Password

```
user1:$apS12dTFUq0ok6JPLkwoYqwTwd.
user2:$apS12aAOuccSphrrV4Vgaah0wIG5qTer1
user3:$apS12c2xbFrFs5dDLbI4NGTcn0bRBW/1
user4:$apS1svjxonbPzfyInu2vDcpio1.PZO
```

Each line in the .htpassfile file contains a username, a colon, and that hashed password.

The contents of your .htpassfile file will vary. To create it, you use a small program called
htpassword that comes in the Apache distribution.

The htpassword program supports a large number of options. Commonly, it's used as follows:

```
htpassword -b[c] passwordfile username password
```

Using the -c switch tells htpassword to create the file. You must use this if exists for the first user you
add. Be careful not to use it for other users, because if the file exists, htpassword will delete it
and create a new one.

The -b switch tells the program to expect the password as a parameter rather than prompt
for it. This feature is useful if you are calling htpassword nonactively as part of a
process, but you should not use it if you are calling htpassword from the command line because
passwords will be retained in history.

The following commands create the file shown in Listing 16.6:

```
htpassword -b /var/www/.htpassfile user1 pass
htpassword -b /var/www/.htpassfile user2 pass
htpassword -b /var/www/.htpassfile user3 pass
htpassword -b /var/www/.htpassfile user4 pass
```

Note that htpassword may not be in your path: if it is, you may find it in the /usr/local/apache/bin directory.

This sort of authentication is easy to set up, but there are a few problems with using an
.htaccess file this.

Users and passwords are stored in a text file. Each time a browser requests a file that is protected
by the .htaccess file, the server must parse the .htaccess file and then parse the password
file, attempting to match the username and password. Instead of using an .htaccess file,
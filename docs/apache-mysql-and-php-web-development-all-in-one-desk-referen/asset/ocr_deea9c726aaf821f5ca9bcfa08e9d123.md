# # Creating a root password

If you don't have a root password, you will want to add one so that your system isn't left wide open for just anybody to climb into and muck things up. Here's how you set a root password:

First, if you're on Linux or Unix, make sure you're logged in as root.

Next, regardless of your operating system, start mysql without a password by using either

```
`mysql`
```

```
`mysql -u root`
```

Then type the following, substituting your own secret password for *somepassword*:

```
set password for root@localhost=
password('somepassword');
```

The word password after the equal sign is vital: This function takes the following string and encrypts it. Thus, you're not storing your password in the database; you're storing an encrypted form of your password. Then, when you log in, mysql automatically encrypts the password you type and compares it to the encrypted password stored in the database. If the two match, mysql lets you in. Otherwise, you get an error message.

After you type this preceding `set` command, you can exit out of mysql and then start it back up, using the password:

```
`mysql -u root -p`
```

You are then prompted for the password, which you may now enter. Then you'll get into the newly password-protected mysql command-line utility. Yay!

Here's how you add the user. Make sure you're inside the mysql utility and then enter the following:

```
grant all privileges on *.* to phpuser@localhost
identified by 'phpass';
```

Then press Enter. You see a message stating the query worked. (Although, really, the message isn't particularly clear. It is as follows.)

```
Query OK, 0 rows affected (0.00 sec)
```

(Yes, it worked, even though the message says that zero rows were affected.) You now have a user called phppass with full privileges. You can exit out of the mysql program by typing quit. Then you can sign back in by using this new username:

```
`mysql -u phpuser -p`
```
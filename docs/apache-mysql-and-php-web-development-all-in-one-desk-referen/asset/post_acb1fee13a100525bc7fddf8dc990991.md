
## Removing the anonymous user on Windows

If you discover that you can connect to MySQL simply by typing mysql with nothing after it, your system is set up to allow anonymous users. Bad news! This anonymous user has full root privileges! Very bad indeed. This is the default with many Windows installations, but fortunately you can fix the problem. (In fact, please fix the problem. You don't want hackers getting into your site.) First, enter mysql from the command prompt. Then select a database by typing this line:

```
use mysql
```

You see the message Database changed. Now type this line (note that those things before the semicolon are two consecutive single quotes with no space between them):

```
delete from user where user='';
```

You probably also have a default root user that allows anyone to log in from anywhere using the username root with no password. (Big time yikes!) To remove that major security hole, type this:

```
delete from user where host = '%' and user = 'root';
```

Then type this command:

```
quit
```

After you're outside the mysql command-line utility, type this line:

```
mysqladmin -u root -p reload
```

You are prompted for the root password, which you may enter. Now you won't be able to get into mysql by simply typing mysql. Whew!

If you don't get in right away, you're presented with a password prompt:

```
Enter password:
```

Type in your root password and press Enter.

![](img/3f967ab8a8fddc723173059f56621648_525_0.png)

If you've forgotten your root password (or never knew it), please check out the following Web page for information on how to reset your root password:

```
www.mysql.com/doc/en/Resetting_permissions.html
```

After you have created your user password and are inside the mysql command-line utility, you can add your first user. In this section, I show you how to create a user with username phpuser and password phppass. I encourage you to find a different password other than the one I've written here in this big thick book that over 100 million people will purchase and read. You may also consider picking a different username. However, in the samples throughout this book, I use the username phpuser and password phppass. You need to substitute your own username and password for the examples.

### Creating a root password

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
set password for root@localhost=password('somepassword');
```

The word password after the equal sign is vital: This function takes the following string and encrypts it. Thus, you're not storing your password in the database; you're storing an encrypted form of your password. Then, when you log in, mysql automatically encrypts the password you type and compares it to the encrypted password stored in the database. If the two match, mysql lets you in. Otherwise, you get an error message.

After you type this preceding `set` command, you can exit out of mysql and then start it back up, using the password:

```
`mysql -u root -p`
```

You are then prompted for the password, which you may now enter. Then you'll get into the newly password-protected mysql command-line utility. Yay!

Here's how you add the user. Make sure you're inside the mysql utility and then enter the following:

```
grant all privileges on *.* to phpuser@localhost identified by 'phpass';
```

Then press Enter. You see a message stating the query worked. (Although, really, the message isn't particularly clear. It is as follows.)

```
Query OK, 0 rows affected (0.00 sec)
```

(Yes, it worked, even though the message says that zero rows were affected.) You now have a user called phppass with full privileges. You can exit out of the mysql program by typing quit. Then you can sign back in by using this new username:

```
`mysql -u phpuser -p`
```

You are then prompted for the password:

Enter password:

After you enter the password, you will be logged in under the new username.

## Managing domain access

If you peruse the MySQL online documentation, you will see references to both username and username@localhost. The @localhost thing seems to crop up a lot. The idea behind username and username@localhost is you are specifying where the user can be when logging into MySQL. By simply specifying username, you're saying the user can log in from any computer. By specifying username@localhost, you're saying the user must be logged into the same computer running MySQL, and from there, log into MySQL. In other words, these two choices allow people to log in remotely to your MySQL system.

Like most things in this great big world of ours, tradeoffs exist. Here are some points to consider when deciding whether to allow outside access:

- Disadvantage: It can create a security risk. You don't want people from across the globe trying to log in to your database through their own remote connections. (You'd probably prefer they log in through your .php files, which run on your server.)
- Advantage: Allowing for such remote connections lets you create some rather powerful, distributed software.

![](img/3f967ab8a8fddc723173059f56621648_527_0.png)

Here's my rule of thumb: I don't allow outside access on my server because all my access takes place from within the server. If I want to use the mysql program, I first telnet into my server and then run mysql. If I want to access the MySQL databases from my Web pages, I use PHP, which runs on the server side and does not require outside access. Thus, I have no need for outside access. Unless you're planning to run client-side database software that will make remote connections to your server, thereby creating a distributed system, you should also turn off any access from the outside. (If you're not sure what all this mumbo jumbo means, most likely you won't need the outside access, and you can just do away with it once and for all!)

## Preventing outside access

By default, your system should be set up to prevent outside access. Here's how you can check whether your system allows outside access. Log into the mysql program as the root and then carefully type these commands:

```
use mysql
select host, user from user;
```

In case you're curious, this is an SQL select statement that retrieves all the rows from the user table, showing only the user and host columns. I talk all about SQL in Book VI, Chapter 5.

Here's some sample output (yours will be similar but not necessarily the same):

| host | user |
| :--- | :--- |
| % | guest |
| 192.168.1.103 | jeff |
| localhost | phpuser |
| localhost | root |

This is a list of users allowed to access your system. The user column is the username, and the host column is the name of the host from which the user is connecting. And look: This output is saying that the user named jeff (that's me!) can log in from the computer on IP address 192.168.1.103, which is a separate computer. In other words, jeff can log in remotely. (However, 192.168.1.103 is an IP address on the local network and not a computer from outside the network.)

Now look at the first line: The host is simply % , which in SQL is a wildcard. That means if you see a line like this, somebody can log into the system with username guest from any computer on the Internet. If you don't want guest logging in from anywhere on the Internet, change the entry's host to localhost, like so:

```
update user set host = 'localhost' where user = 'guest' and host = '%';
```

Or, if you prefer to remove the guest user altogether, you can type this:

```
delete from user where user = 'guest';
```

## Logging in remotely

If you want to allow outside access, you can specify an IP address (or computer name on a local network) when you create a user; you'll then be able to log in from the computer with that IP address. I have installed MySQL on both my desktop and laptop computers. On the MySQL system running on the desktop, I created a user called jeff@192.168.1.100. (The IP address

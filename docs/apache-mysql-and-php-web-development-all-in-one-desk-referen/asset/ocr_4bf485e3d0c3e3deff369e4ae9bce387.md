In case you’re curious, this is an SQL select statement that retrieves all the rows from the user table, showing only the user and host columns. I talk all about SQL in Book VI, Chapter 5.

Here’s some sample output (yours will be similar but not necessarily the same):

| host | user |
| :--- | :--- |
| % | guest |
| 192.168.1.103 | jeff |
| localhost | phuser |
| localhost | root |

This is a list of users allowed to access your system. The user column is the username, and the host column is the name of the host from which the user is connecting. And look: This output is saying that the user named jeff (that’s me!) can log in from the computer on IP address 192.168.1.103, which is a separate computer. In other words, jeff can log in remotely. (However, 192.168.1.103 is an IP address on the local network and not a computer from outside the network.)

Now look at the first line: The host is simply % , which in SQL is a wildcard. That means if you see a line like this, somebody can log into the system with username guest from any computer on the Internet. If you don’t want guest logging in from anywhere on the Internet, change the entry’s host to localhost, like so:

```
update user set host = 'localhost' where user = 'guest' and
host = '%';
```

Or, if you prefer to remove the guest user altogether, you can type this:

```
delete from user where user = 'guest';
```

# Logging in remotely

If you want to allow outside access, you can specify an IP address (or computer name on a local network) when you create a user; you’ll then be able to log in from the computer with that IP address. I have installed MySQL on both my desktop and laptop computers. On the MySQL system running on the desktop, I created a user called jeff@192.168.1.100. (The IP address
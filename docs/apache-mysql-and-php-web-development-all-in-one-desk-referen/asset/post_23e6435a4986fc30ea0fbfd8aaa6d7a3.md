
## For users of third-party hosting services

If you're using a third-party hosting service, most likely MySQL is already installed and ready for you to use. Usually, a hosting service provides you with a single database you can access, and a single username and password for accessing that database. You can change the password, but you probably can't change the username or the database name and can't create new databases. In general, you do have a significant amount of power because you can store many tables of information within the single database. If you're using a third-party hosting service, I encourage you to read this chapter because doing so greatly enhances your general understanding of MySQL, and also I specifically address your situation throughout the chapter.

These features make MySQL a great choice for a Web server database. In this chapter, I provide you with information on configuring MySQL.

![](img/3f967ab8a8fddc723173059f56621648_519_0.png)

You can find information about MySQL at the main MySQL site at www.mysql.com. You can find the online manual at www.mysql.com/doc/en/index.html.

## Connecting MySQL and PHP on the Web

When you create a Web site that requires database access, you typically use PHP code to access the data. Remember, PHP is a server-side scripting language, and the PHP processor takes a .php file, grinds through it, and generates a resulting .html file. The Web server then sends the resulting .html file to the client browser on the Web user's computer. (You can find out more about PHP in Book V.)

For example, suppose your company wants to create a Web page that lists the company directory on its internal corporate Web site. To tackle this problem, you create a .php file that connects to a MySQL database, retrieves the data for the phone list, and then writes out an HTML table showing the names, e-mail addresses, and phone extensions.

You also include a Web form that allows certain users to modify the data in the company directory. This Web form is guarded with an HTTP authentication (using PHP), requiring users to log in before gaining access to the form. Users make updates using the HTML form and then click a submit button. The submit button connects to a .php file that again requires HTTP authentication. (But because users already entered their information, they don't have to reenter it.) This .php file connects to the database and updates the directory information accordingly.

MySQL stores its data in a database. You can have multiple databases on your system, but often people have only a single database containing many tables of information. MySQL also maintains a list of passwords and usernames, including a root username, which is the administrator. You can set up your MySQL system so that each user has certain rights. For example, you may authorize one user to read certain databases and another user to modify certain databases. When you write a PHP program to connect to a MySQL database, you supply this username and password. However, these usernames and passwords are separate from the username and password you would require in HTTP authentication (although you can make them the same if you want).

Often when using a third-party hosting service, you are given only a single database and a single username (often the same as the database). This single username can modify and read the data in your database. You can set up HTTP authentication on the Web pages that modify the data. Further, you can store your data within the single database in separate tables of information, so you're not limited to storing only a tiny bit of data.

Figure 1-1 shows a typical process for reading data from a MySQL database using PHP; in this diagram, an “SQL query” simply refers to a program requesting data from a MySQL database.

Figure 1-1:
This is the
typical process for
reading data
from a
MySQL
database.

![](img/3f967ab8a8fddc723173059f56621648_520_0.png)

Figure 1-2 shows a typical process for writing data to a MySQL database using PHP.

![](img/3f967ab8a8fddc723173059f56621648_521_0.png)

## Starting MySQL

The MySQL web site includes easy, clear instructions for installing MySQL; you can find the instructions at www.mysql.com/doc/en/Installing.html.

If you follow these instructions, you should be ready to go. The Linux version starts up the daemon automatically. (A daemon is a program that runs all the time on your computer, often supplying some sort of service, such as MySQL database handling. As for who in the computer world came up with this term — which is really just a variant of demon — and why they use it, frankly, I don't have a clue. It must have been somebody having a really bad day.)

> If you're using Red Hat Linux 8.0 and higher, you can configure the MySQL daemon (called mysqld) to start up automatically upon reboot by selecting Server Settings from the Gnome menu, and then selecting Services. In the window that opens, click mysqld, and then choose Start. Then check the box beside mysqld on the menu.

If you're working on a Windows system, you may need to start MySQL as a service. (Services can run only on the NT, 2000, and XP versions of Windows. If you're using Windows 95, 98, or Me, you need to upgrade anyway because they're not very secure as Web servers.) You can easily find out if the service is running by making sure the mysql\bin directory is in your path. Then from the command prompt, type the following:

```
mysqlshow
```

If the server is running, you will see a list of tables similar to this:

| Databases |
|-----------|
| mysql     |
| test      |

If the server is not running, you'll see this error message:

```
mysqlshow: Can't connect to MySQL server on 'localhost'
(10061)
```

If you see this error message, you need to start up the MySQL service. To do so, follow these steps. (If you have the Apache server running on your Windows computer, instead of following Steps 1, 2, and 3, you can right-click the Apache icon in the tray on the lower-right corner of your screen and, in the pop-up menu that appears, choose Open Services.)

- 1. On the Windows desktop, right-click My Computer and, in the pop-up menu, choose Manage.
  The Computer Management window opens, as shown in Figure 1-3.
- 2. Expand the Services and Applications tree, which you can see in the left pane of the window in Figure 1-3.
- 3. Under Services and Applications, click Services.
  The Services list appears in the right pane, as shown in Figure 1-4.
- 4. In the Services pane, scroll down to MySQL, right-click the name MySQL, and in the pop-up menu, choose Start.
  The MySQL service starts, and the word Started appears under the Status column beside the word MySQL.

![](img/3f967ab8a8fddc723173059f56621648_523_0.png)

Figure 1-3: Expand the Services and Applications tree.

![](img/3f967ab8a8fddc723173059f56621648_523_1.png)

Figure 1-4: The list of services is in the right pane.

Now close the Computer Management window, return to the command prompt, and try the mysqlshow command again.

The MySQL system also includes a handy command-line utility called mysql (in all lowercase). This command-line utility lets you make changes to your database and tables. Typically when you create Web pages that access the MySQL databases, those pages use a programming language such as PHP to access the databases. But when you’re logged into your own system and want to make changes to the databases, you will likely use the mysql command-line utility.

Don't confuse the mysql command-line utility with the MySQL service or daemon. The MySQL service or daemon is the heart of MySQL. The service or daemon listens to data requests and then manipulates the data on the hard drive. The mysql command-line utility is just that: a command-line utility that lets you manipulate your data. People often like to think of the mysql command-line utility as MySQL itself, while in fact, the command-line utility is nothing more than a user interface to MySQL.

## Adding MySQL Users

In this section I show you how to add users to your MySQL system. You can have these users log into MySQL and perform database processes.

If you’re using a third-party hosting service, usually you will have received a username and password and won’t have access to the root, in which case you can skip this section and use that username and password in the sample PHP programs throughout this text.

To add users to your MySQL system, you must be logged in either as the administrator under username root, or as a user who has administrator rights.

The easiest way to add a user to the MySQL system is by logging into the command-line utility. To start the command-line utility, make sure the mysql/bin directory is in your path and, from the command line, type the following:

```
mysql -u root -p
```

If you enter mysql immediately, then you’re logged in, in which case you need to add a root password (because presently your system is wide open). To find out how to set a root password, check out the nearby sidebar “Creating a root password.”

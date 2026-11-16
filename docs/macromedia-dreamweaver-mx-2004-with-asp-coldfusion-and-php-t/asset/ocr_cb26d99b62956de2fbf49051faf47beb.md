The source command is used to run one or more SQL commands stored in an external document. If you open newland_tours.sql in a text editor, you'll see all the code needed to create the newland database, tell MySQL to start using that database, provide instructions to generate each of the six tables in the database, and finally populate each of those tables with data.

Once you press Enter. MySQL goes to work, outputting dozens of success messages that fly by your screen too fast to read, until it reaches the end.

![](bbox=[0.26, 0.24, 0.78, 0.53])

The newland_tours database is properly installed and running in MySQL. You can skip ahead to the section, “Touring the Newland Database.”

# INSTALLING THE NEWLAND TOURS DATABASE ON A REMOTE SERVER

Unfortunately, I can't tell you how to install the newland_tours database into a remote MySQL server. Only your ISP can tell you how to do it.

In my experience, many Linux-based ISPs offer a utility for maintaining MySQL databases remotely, called phpMyAdmin. phpMyAdmin is a Web-based interface, which lists all of the databases to which your account has access. It lets you view the data in your databases, see the SQL code used to generate each table, and it has a host of database maintenance features that make it easy to add new tables, modify existing ones, and even drop tables and even whole databases. The following screenshot provides a glimpse of phpMyAdmin.
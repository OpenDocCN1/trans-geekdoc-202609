
The following instructions show you how to import the list of USPS abbreviations and states from the example at the beginning of the lesson. You’ll use the table you create here in lessons later in this book:

# 1. In the Dreamweaver Files panel, double-click lesson05/states.sql. It should open automatically in the Document window.

If Dreamweaver fails to recognize the `.sql` file type, right-click the file name, and select Open With > Dreamweaver.

You should see on the first line that the file is described as a SQL Dump. A `dump` is a text file that contains all the SQL commands to build and populate one or more database tables.

Lines that begin with a double-dash are treated as comments, as are sections of text enclosed between `/*` and `*/`.

# 2 Scroll down to line 25, where you’ll see a comment about the table structure for the `states` table. This is followed on line 28 by a SQL command that deletes the table if it already exists (`DROP` is the SQL command for deleting an entire column, table, or database). Lines 29–33 build the table and define its structure. Even without any knowledge of SQL, you should be able to follow what the commands are for. SQL is closely based on human language.

![Image](graphics/fig05_27.jpg)

The SQL commands on lines 39–90 insert the values into the `states` table.

### ![Image](graphics/tip.jpg)
**TIP:**

Don’t worry that you’ll need to code this type of file by hand. MySQL has a utility program called `mysqldump` that’s invoked by phpMyAdmin and does everything for you. Even with thousands of records, it takes only a few seconds to generate a `.sql` file.

# 3. Now that you have seen what a `.sql` file contains, you need to switch to phpMyAdmin and import the data.

In phpMyAdmin, make sure that you have selected the `phpcs5` database from the list on the left. Then click the Import tab at the top of the page.

![Image](graphics/fig05_28.jpg)

# 4. In the page that opens, click the Browse button in the “File to import” section, and use your operating system’s dialog box to locate and select lesson05/states.sql. It doesn’t matter if the file is still open in Dreamweaver.

# 5 Click Go. After a few seconds, you should see confirmation that the import was successful. The `states` table should also be listed together with the `users` table on the left of the page.

![Image](graphics/fig05_29.jpg)

# 6. Click the `states` link on the left of the page to reveal the first 30 records in the newly imported table.

That’s all there is to importing data from a `.sql` file. If the file contains more than one table, they will be imported in a single operation.

### ![Image](graphics/tip.jpg)
**TIP:**

If the import fails, it’s likely to be caused by your server failing to understand some of the commented lines in the `.sql` file. Try removing all lines that begin with a double-dash, as well as all commands wrapped between `/*` and `*/`.

## What You Have Learned

***In this lesson, you have:***

• Taken a quick look at the most popular UIs for MySQL ([pages 142–143](#ch05.html#page_142))

• Seen how a relational database stores information ([pages 143–144](#ch05.html#page_143))

• Examined how primary and foreign keys build one-to-many, many-to-many, and one-to-one relationships between tables ([pages 145–149](#ch05.html#page_145))

• Studied best practices for naming databases, tables, and columns ([pages 149–150](#ch05.html#page_149))

• Explored the most important data types used in MySQL ([pages 150–155](#ch05.html#page_150))

• Created a database ([pages 155–156](#ch05.html#page_155))

• Seen the effect of collation on how records are sorted ([pages 156–157](#ch05.html#page_156))

• Defined a table for a user registration system ([pages 157–161](#ch05.html#page_157))

• Learned the difference between the MyISAM and InnoDB storage engines ([page 160](#ch05.html#page_160))

• Created MySQL user accounts and assigned privileges ([pages 161–165](#ch05.html#page_161))

• Imported existing data with a `.sql` file ([pages 165–167](#ch05.html#page_165))

## Lesson 6. Generating PHP Automatically with Server Behaviors

### What You Will Learn

***In this lesson, you will:***

• Create connection files for your MySQL user accounts

• Use an online form to insert records in a database table

• Build a login system and password-protect pages

• Encrypt passwords

• Display the results of a database query

• Use a repeat region to display multiple results

• Update and delete database records

• Hide part of the page and display a message when there are no results

### Approximate Time

This lesson takes approximately 2 hours and 30 minutes to complete.

### Lesson Files

***Media Files:***

styles/users.css

***Starting Files:***

lesson06/start/add_user.php

lesson06/start/delete_user.php

lesson06/start/login.php

lesson06/start/members_only.php

lesson06/start/restricted.php

lesson06/start/update_user.php

lesson06/start/user_list.php

lesson06/start/users.sql

***Completed Files:***

lesson06/completed/add_user.php

lesson06/completed/add_user_encrypt.php

lesson06/completed/delete_user.php

lesson06/completed/login.php

lesson06/completed/login_encrypt.php

lesson06/completed/members_only.php

lesson06/completed/members_only_encrypt.php

lesson06/completed/restricted.php

lesson06/completed/update_user.php

lesson06/completed/update_user01.php

lesson06/completed/user_list.php

lesson06/completed/user_list01.php

lesson06/completed/user_list02.php

lesson06/completed/user_list03.php

lesson06/completed/user_list_showif.php

lesson06/completed/Connections/cs5write.php

lesson06/completed/Connections/cs5read.php

A database without data is like a pub with no beer. Even with no PHP experience, Dreamweaver’s built-in server behaviors can help you rectify the situation in next to no time. The server behaviors generate all the necessary code for basic database operations—processes that geeks with their love of acronyms sometimes refer to as CRUD (create, read, update, and delete).

By the end of this lesson, you will have used all the main server behaviors to create a simple user registration and login system. You’ll also learn how to display, update, and delete existing records. Almost all the work will be done through dialog boxes, with only a minimal need to write code.

*Dreamweaver server behaviors make it easy to insert records from a custom form.*

![Image](graphics/fig06_01.jpg)

### What Server Behaviors Do

When Dreamweaver was first released in the late 1990s, the browser war between Netscape and Internet Explorer was at its height. A minefield of incompatibilities stood in the way of the average web designer trying to add dynamic features to a web page with JavaScript. So, Dreamweaver cut through the complexity by creating off-the-shelf scripts to solve common problems. A separate program called Dreamweaver UltraDev offered similar ready-made solutions for server-side functionality, which were merged into the core program in 2002 with the release of Dreamweaver MX. Everything is done through dialog boxes. Dreamweaver takes care of the rest.

This is a great boon for anyone who wants to create a database-driven site in a hurry, but you should be aware of the limitations of server behaviors. They provide only basic functionality. Apart from security improvements, they have remained essentially unchanged since they were first introduced. Adobe regards them more as a learning tool than as a production-level feature.

If you have no experience working with a database-driven site, this lesson will give you some useful insights to prepare you for later lessons. However, the rest of this book takes advantage of the enhanced PHP support in Dreamweaver CS5 to work with the Zend Framework, which offers a much wider range of features than server behaviors.

### Connecting to the Database

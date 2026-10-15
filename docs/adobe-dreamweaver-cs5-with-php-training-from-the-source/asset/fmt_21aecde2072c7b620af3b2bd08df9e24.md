
The two lines beginning with `RewriteCond` exclude file and directory names from the rewriting rules, which are defined in the lines beginning with `RewriteRule`.

The rewriting rules are constructed like this:

```
RewriteRule Pattern Substitution
```

The pattern is a regex. The first matches places/ followed by anything. The second one matches states/ followed by anything. The parentheses capture the value after the slash and use it in place of `$1`. So, places/Hollywood actually looks for /lesson12/completed/details_clean.php?place=Hollywood.

If you’re using a virtual host in Apache as your testing environment, copy .htaccess from lesson12/completed/scripts to the phpcs5 site root, type `[http://phpcs5/states/](http://phpcs5/states/)` into your browser address bar, and press Enter/Return. This loads a modified version of gallery.php into the browser, which works in exactly the same way. Instead of query strings, the links use places/ followed by a `link_name` value or states/ followed by a `state_name` value. (You might need to amend the path to the Zend Framework library.php.)

You can study the code in the files that contain `_clean` at the end of the filename in lesson12/completed and lesson12/completed/scripts. All links have been made relative to the site root, so it won’t work if you’re using a subfolder of localhost for testing. This has been only a brief introduction to rewriting URLs. Hopefully, it will encourage you to search online for more detailed tutorials.

### What You Have Learned

***In this lesson, you have:***

• Installed the Adobe Widget Browser (pages [420–422](#ch12.html#page_420))

• Downloaded and configured the LightBox Gallery Widget (pages [422–430](#ch12.html#page_422))

• Populated the gallery widget dynamically from the database (pages [430–437](#ch12.html#page_430))

• Created a master/detail set (pages [437–448](#ch12.html#page_437))

• Formatted a MySQL date (pages [441–442](#ch12.html#page_441))

• Used jQuery to send a request to the web server and refresh content without reloading the page (pages [448–457](#ch12.html#page_448))

• Learned how to rewrite URLs to eliminate a query string (pages [457–458](#ch12.html#page_457))

## Lesson 13. Deploying Your Site Online

### **What You Will Learn**

***In this lesson, you will:***

• Learn how to create a `.sql` file to transfer data to your remote database

• Consider alternative methods of transferring data to your remote server

• Remove error messages from scripts and write them to a log file

• Adjust file paths, user accounts, and passwords

• Check whether the Zend Framework needs to be uploaded

• Create and set the permissions on a folder for file uploads

• Define the FTP connection settings for a remote server

• Explore the Files panel in expanded mode

• Devise a strategy for transferring files outside the site root

### **Approximate Time**

This lesson takes approximately 1 hour to complete.

### **Lesson Files**

***Media Files:***

None

***Starting Files:***

None

***Completed Files:***

None

In most respects, deploying a PHP website online is no different from a static site built entirely in HTML. However, there are some differences. In this lesson, you’ll learn how to transfer a database from your local environment to a remote server. There’s also a rundown of changes you might need to make to ensure a smooth transition to the Internet.

***Exporting data as a `.sql` file in phpMyAdmin is a common way of transferring a database.***

![image](graphics/fig13_01.jpg)

### Transferring a Database

MySQL doesn’t store data in a single file that you can upload to your website. How the data is stored on disk depends on the engine you selected when creating each table, but the method of storage is irrelevant. You don’t transfer the database files to your remote server. Instead, you transfer only the data stored in them. There are several ways of doing so.

#### Using phpMyAdmin

If phpMyAdmin is installed on your remote server, you can create a `.sql` file to upload the data from your local computer.

**1.** Open your local version of phpMyAdmin, select the database that you want to transfer, and click the Export tab. This opens a screen with a large number of options, as shown in the screen shot on the preceding page. Most of the default settings are fine.

**2.** In the Export section at the top left, check that the tables you want to export are selected. Ctrl-click/Cmd-click to deselect any tables you want to exclude.

**3.** The radio button in the Export section determines the format. The default is SQL, which is what you want.

**4.** In the Options section, the “SQL compatibility mode” menu adjusts the syntax for compatibility with different servers:

• **MySQL 4.1, 5.0, and 5.1.** Select NONE (default).

• **MySQL 4.0.** Select MYSQL40.

• **MySQL 3.23.** Select MYSQL323.

• **Microsoft SQL Server.** Select MSSQL.

**5.** The Structure checkbox is selected by default. Deselect this only if you have already created the table structure on the remote server.

The only option that you might need to change in the Structure section is Add DROP TABLE / VIEW / PROCEDURE / FUNCTION / EVENT, which is deselected by default. Select this checkbox to replace any tables on your remote server that have the same name as those you are exporting. This option is useful if you have redesigned the database structure but want to use the same table names.

### ![image](graphics/caution.jpg)**CAUTION!**

The DROP TABLE option irretrievably deletes all data on the remote server in elements with identical names to those you’re exporting.

**6** The Data checkbox must remain selected to transfer the data.

The Export Type menu in the Data section should normally be set to INSERT. This is intended for populating new tables with data. There are two other options:

• **UPDATE.** Existing data is updated with values from the `.sql` file. Only existing records are affected. New records are *not* inserted.

• **REPLACE.** New records are inserted, and existing data is updated with values from the `.sql` file.

**7.** The “Save as file” section sets various options for the `.sql` file.

![image](graphics/fig13_02.jpg)

If you deselect the checkbox at the top left of the section, phpMyAdmin lets you preview the contents of the file that it will generate. Click the browser’s back button to return to the main screen.

“File name template” automatically names the `.sql` file. The default value depends on whether you clicked the Export tab from the page showing the structure of the database or an individual table. __DB__ gives the `.sql` file the same name as the database. __TBL__ uses the table’s name. The template recognizes `strftime()` formatting characters (see [www.php.net/strftime](http://www.php.net/strftime)) and plain text, so you can add the date to the file name like this:

\_\_DB\_\_**\-%Y-%m-%d**

This produces a file name like phpcs5-2010-06-09.sql. By default, phpMyAdmin remembers your custom template for future use.

“Character set of the file” should normally be left at the default utf-8.

The `.sql` file is output as plain text, but the Compression radio button offers the option to compress it as a `.zip, .gzip, or .bzip2` file. This is useful if you have a large amount of data. When importing, phpMyAdmin automatically recognizes the file type and decompresses it.

**8.** When you have made your selections, check that “Save as file” is selected, click Go, and save the `.sql` file to your local computer.

**9** Log into phpMyAdmin on your remote server. If you have more than one database, select the one you want to use, and click the Import tab to upload the data from the `.sql` file you just created. There is no need to create the table structure on your remote server. The `.sql` file does it for you. The process is exactly the same as described in “Importing Existing Data” in [Lesson 5](#ch05.html#ch05).

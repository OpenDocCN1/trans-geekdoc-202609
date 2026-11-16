
When you close the dialog, Dreamweaver creates a new folder in your site, called Connections, with a new file inside called conn_newland.asp. You should also notice that the Databases panel now has an expandable listing of the database and its assets.

![](img/43fd0127a958864ab2d93e28efe683e7_259_0.png)

- 9) Select the Connections folder in the Files panel, and click the Put button to upload it to the server.

You are ready to create a recordset and start binding database data. Skip ahead to the task. “Retrieving Recordsets and Displaying Database Information.”

## COLDFUSION USERS (RUNNING COLDFUSION LOCALLY OR CONNECTING TO A REMOTE SERVER)

This section is for all ColdFusion users, regardless of how they connect to their server.

ColdFusion users who connect to a remote server must have the administrator for that server grant them RDS login information—which consists of a password. Without RDS login, you will not be able to complete this book.

- 1) Open index.cfm.

It doesn’t matter which page of your site is open when initially creating the connection. Dreamweaver creates the connection for the whole site. You’ve opened index.cfm because you will add dynamic content to that page in the next task.

- 2) Open the Databases panel, in the Application panel group. Click the Specify the RDS login for your ColdFusion server link, enter your password, and click OK.

RDS login grants developers permission to access the ColdFusion server, which is necessary for defining and using data sources.

![](img/43fd0127a958864ab2d93e28efe683e7_259_1.png)

At the end of this step, if there are already many data sources existing on the ColdFusion server, they are all visible in the Databases panel.

The only problem is, the Newland database is not among them.

- 3) Click the Create a ColdFusion data source link (if it is available), or click the Modify Data Sources button on the right side of the Databases panel.

Regardless of whether you click the button or the link, after a moment, the ColdFusion administrator opens in a browser, to the Data Sources page. You will first need to enter the password to access the administrator.

![](img/43fd0127a958864ab2d93e28efe683e7_260_0.png)

- 4) In the Add New Data Source box, enter newland as the Data Source Name. In the Driver drop-down menu, select Microsoft Access. Click Add.

A DSN consists of a name, a driver that enables the application to communicate with the database, and the path to the database. In this step, you have entered the first two of these three pieces of information.

![](img/43fd0127a958864ab2d93e28efe683e7_260_1.png)

- 5) In the Microsoft Access Data Source box that appears, click the first Browse Server button and browse to the newland_tours.mdb file on the site. Click Submit.
For Windows XP users, browse to the following directory: C:\Documents and Settings\All Users\Documents\database\'. This is the directory to which the shortcut Shared Documents points.
For Windows 2000 users running ColdFusion in standalone mode, browse to the following directory: C:\CFusionMX\wwwroot\newland\database\.
For Windows 2000 users running ColdFusion alongside IIS, browse to the following directory: C:\Inetpub\wwwroot\newland\database\.
This step provides ColdFusion with the remaining information it needs to connect to your database.

![](img/43fd0127a958864ab2d93e28efe683e7_261_0.png)

- 6) Close the ColdFusion Data Sources Web page to return to Dreamweaver. In the Databases panel, click the Refresh button beside the Modify Data Sources you clicked earlier. The newland DSN should show up. Click the + button beside it to expand it and explore the data source.

![](img/43fd0127a958864ab2d93e28efe683e7_261_1.png)

Now that you can see the contents of the newland_tours.mdb database, you know that Dreamweaver has successfully made the connection. You are ready to create a recordset and start binding database data.

Skip ahead to the section entitled “Retrieving Recordsets and Displaying Database Information.”

## PHP USERS (RUNNING PHP/MYSQL LOCALLY OR ON A REMOTE SERVER)

Because PHP doesn’t make use of ODBC or DSNs, you can specify all the information you need to access your MySQL database right in Dreamweaver.

- 1) Open index.php.
  It doesn’t really matter which file is open, since Dreamweaver makes the connection available site-wide. However, at least one file must be open in the site, before you can create a connection to MySQL.

- 2) In the Databases tab, click the + button and choose MySQL Connection to create a new connection to MySQL.
  The MySQL Connection dialog opens.

- 3) Specify the following information, so that Dreamweaver can make the MySQL data source available to your site.
  Connection name: conn_newland
  MySQL server: localhost (if developing locally) or whatever your server administrator tells you (if developing remotely)
  User name and Password: the user name and password of the MySQL account that you use to access MySQL.
  Database: newland_tours.

![](img/43fd0127a958864ab2d93e28efe683e7_262_0.png)

If you are developing on a remote server, only your server administrator will be able to tell you how you access MySQL from Dreamweaver/PHP. If you are developing locally, then just use the information you specified when you first installed MySQL. If you installed MySQL yourself and are unsure of your username and password, try root as the username and leave the password blank.

**TIP** Optionally, click the Test button to make sure that Dreamweaver can actually access MySQL.

- **4) Click OK.** Dreamweaver creates a Connections directory on your site, with a file in it called conn_newland.php. This file contains the information your pages will need to access MySQL. Whenever you call a database from PHP, Dreamweaver references this file.

- **5) Expand conn_newland in the Databases panel to explore the structure of the newland_tours database from within Dreamweaver.** Dreamweaver is actually accessing the database within MySQL and providing you with information about it. Albeit in a limited way, you can interface with MySQL via Dreamweaver.

![](img/43fd0127a958864ab2d93e28efe683e7_263_0.png)

- **6) In the Files panel, click the Connections folder, and then click the Put button to upload it to the server.** The PHP/MySQL connection won't work unless this folder is uploaded.

## RETRIEVING RECORDSETS AND DISPLAYING DATABASE INFORMATION

It seems like a long time since you made any improvements to the actual site. You've done some theory, some exploration, and some configuration. But you haven't done anything to any pages yet. In this final task of the lesson, you'll cause the Traveler's Journal to load dynamically from the database. In the browser, the homepage will look the same as it did before, but in Dreamweaver, the difference will be unmistakable.

- 1) With index.asp open in Design view, select the text from "Teens Discover..." down to "...putting together" at the bottom. Do not select the yellow image icon beside the T in Teens (if it appears). Press Delete.

  You're going to replace this text with dynamic text, so you are just making room in this step.

![](img/43fd0127a958864ab2d93e28efe683e7_264_0.png)

- 2) Click the Traveler's Journal image to select it. In the tag selector (in the bottom-left corner of the document window), right-click the <h3> tag just to the left of the  tag, and choose Remove Tag from the menu.

  The journal entry in the database is already marked up in HTML. You need to remove the <h3> tag here, or the tags in the journal entry will be illegally nested inside the <h3> tag.

- 3) In the Bindings panel, click the New Binding (+) button, and choose Recordset (Query) from the menu.

At this point, you have connected your site to a data source, which means you have made it possible for Dreamweaver to write code for you that retrieves data from your database. However, you have not actually retrieved any data yet. In this and the next two steps, you'll create a recordset, which as you'll recall from the beginning of this lesson, is a collection of data that meets certain criteria and that is retrieved from a database using SQL.

![](img/43fd0127a958864ab2d93e28efe683e7_265_0.png)

Your goal is to display the journal entry, but you don't want to display all the journal entries, only the most recent. In order to facilitate this, each journal entry has been given an unique ID (a primary key). These IDs are numbered incrementally, as the records are added. Therefore the record with the highest journalID is the most recent. You'll need to sort the data, and then retrieve the contents of the latest journal entry in order to display it. You'll take the first steps toward doing this in the next step.

- 4) In the Recordset dialog, enter rs_journal as the Name. Choose conn_newland (or newland for ColdFusion users) from the Connection drop-down. Select tbl_journal from the Table drop-down. In the Columns section, choose the Selected radio button, and Ctrl-select (Windows) or Command-select (Macintosh) journalID and journal_entry.

In this dialog, you are creating a recordset, named rs_journal. The data in this recordset is retrieved using criteria specified in SQL. You may not realize it, but you have already begun the SQL statement.

Specifically, you have specified data in the data source stored in conn_newland (that connection specifies the newland DSN). Within that data source, you are specifying that the data is in a table named tbl_journal. Going a step further, you are specifying that you only want to retrieve the journalID and journal_entry fields from that table.

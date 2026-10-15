
Collation is important if you work with languages other than English. If you work exclusively in English, you can ignore it entirely—well, almost. When phpMyAdmin displays the structure of a database or table, you’ll notice that the Collation column is set to `latin1_swedish_ci`. Why the Swedish setting? MySQL was originally developed in Sweden, so its default collation is Swedish, which also happens to use exactly the same sort order as English.

However, in some languages, the traditional sort order is different from alphabetical order. For example, in Spanish, *LL* is treated as a separate character that comes after the letter *L*. The following screen shots show the difference.

![Image](graphics/fig05_12.jpg)

In the Traditional Spanish sort order, *llamar* comes after *loco*. But when sorted in alphabetical order, *llamar* comes first. The screen shot on the left was taken with collation set to `utf8_spanish2_ci`. The one on the right was taken with collation set to the default `latin1_swedish_ci`.

Collation can be set for the whole database, at table level, or for individual columns. If set at the database level or table level, that setting becomes the default for the whole database or table, but you can override the default for individual tables or columns.

The available options for collation depend on how MySQL has been set up, but the naming convention is easy to understand. Each name is composed of the following three elements separated by underscores:

• Encoding

• Language

• Case sensitivity: `bin` for binary, `ci` for case insensitive, and `cs` for case sensitive

### ![Image](graphics/note.jpg)**NOTE:**

Collation does not affect the encoding of data stored in MySQL. It is concerned solely with sort order.

#### **Defining the users table**

The `users` table for a user registration system needs to have at least five columns as follows:

• `user_id`

• `first_name`

• `family_name`

• `username`

• `password`

You might want to add other columns later, for example, to store the user’s email address, but this will do for now.

**1.** If you left phpMyAdmin open on the page that confirmed the creation of the `phpcs5` database, skip to the next step.

If you need to relaunch phpMyAdmin, select `phpcs5` from the list of databases in the left column of the welcome page. This will open the Structure tab for the database and display the text fields for creating a new table.

**2.** In the section labeled “Create new table on database phpcs5,” type **users** in the Name text field, and **5** in “Number of fields.” Then click Go.

![Image](graphics/fig05_13.jpg)

**3.** A huge matrix opens where you define the database table. There’s a line for defining each table column.

This is perhaps the least user-friendly part of phpMyAdmin. The matrix is so large you will have difficulty seeing all of it onscreen without scrolling horizontally. In spite of this problem, it’s quite easy to fill in.

![Image](graphics/fig05_14.jpg)

### ![Image](graphics/tip.jpg)**TIP:**

When you create a table with only three columns, phpMyAdmin presents this matrix in a vertical layout, which makes it easier to see all options.

**4.** In the first row, type **user_id** in the Field text field.

**5.** Set the Type menu to `INT`. The first two fields should look like this:

![Image](graphics/fig05_15.jpg)

**6.** A primary key cannot be a negative number, so set the value of Attributes to `UNSIGNED`.

**7.** The `user_id` will be the primary key, so select `PRIMARY` from the Index menu.

**8.** You want the primary key to be automatically incremented, so select the A_I checkbox.

The values set in steps 6–8 should look like this:

![Image](graphics/fig05_16.jpg)

**9.** The remaining columns are less complicated. Use the values shown in the following screen shot:

![Image](graphics/fig05_17.jpg)

You don’t know how long the values of `first_name`, `family_name`, or `username` will be. So, the data type needs to be `VARCHAR`. With this data type, you need to specify the width of the column in the Length/Values text field. It’s a good idea to be generous in the size allocated. Otherwise, you run the risk that values will be truncated in the database.

Why use the `CHAR` fixed-width string data type for `password` and set its width at 40? Surely no one will have a password that long!

Passwords should not be stored in plain text, so the value will be encrypted as a 40-digit hexadecimal number.

**10** Beneath the matrix in the center of the screen is a menu labeled Storage Engine. Make sure it’s set to MyISAM (this is the default in XAMPP and MAMP).

![Image](graphics/fig05_18.jpg)

For more details, see the sidebar “Choosing the Right Storage Engine.”

**11** Leave the remaining fields blank or at their default values, and click the Save button at the bottom right of the screen.

![Image](graphics/fig05_19.jpg)

### ![Image](graphics/caution.jpg)**CAUTION!**

Make sure that you click the Save button. The Go button adds an extra column to the matrix. If you click the Go button by mistake, type a dummy name in the Field text field, and set the Type menu to `INT`. Then click Save. This adds a column with the dummy name, which you can delete after saving the table definition.

**12** After you have saved the table definition, phpMyAdmin presents you with a screen showing the settings for your new table. Check the values against the following screen shot.

![Image](graphics/fig05_20.jpg)

### **Choosing the Right Storage Engine**

Choosing a storage engine in MySQL determines how your data is stored and retrieved. MySQL supports several storage engines, but the most widely used are MyISAM and InnoDB. MyISAM has been the default since MySQL 3.23, but it was announced in April 2010 that a new version of InnoDB would become the default from MySQL 5.5.

MySQL 5.5 was still in beta at the time this book was being prepared for publication. Moreover, many hosting companies don’t offer support for InnoDB. Consequently, all the exercises in this book use MyISAM tables. Fortunately, choosing a storage engine isn’t an irreversible decision. You can change a table’s storage engine by selecting the Operations tab in phpMyAdmin and then selecting the new engine in the “Table options” section.

The main difference between the storage engines lies in InnoDB’s added support for transactions and foreign key constraints.

A *transaction* is a series of database commands that must be executed as a group. If any part of the series fails, the transaction automatically undoes any changes. This is important in financial databases where money might be deducted from one account for transfer into another. If, for any reason, the money cannot be added to the second account, the whole transaction fails, and the money is restored to the original account.

A *foreign key constraint* keeps track of relationships between tables and prevents a record from being deleted if its primary key is still in use as a foreign key elsewhere.

If you installed the Windows Essentials version of MySQL and chose the Multi-functional Database option, your setup will default to InnoDB. You can change the default to MyISAM by editing C:\\Program Files\\MySQL\\MySQL Server 5.x\\my.ini in Notepad (launch Notepad by right-clicking it in the Start menu and selecting “Run as administrator”). Locate the following line:

default-storage-engine=INNODB

Change it to this:

default-storage-engine=**MyISAM**

Either restart your computer or restart the MySQL service by choosing Start > Control Panel > Administrative Tools > Services. Select MySQL in the Services panel, and click Restart.

Note that `user_id` is underlined, which indicates that it has been set as the table’s primary key. This is confirmed by the Indexes section at the bottom.

You should also check that the Attributes field for `user_id` is set to `UNSIGNED`, and that Extra is set to `auto_increment`.

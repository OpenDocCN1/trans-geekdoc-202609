# Other skills for creating a database

This topic describes two more skills that you may need to create a database. To start, you may want to load data that’s stored in text files into a database. In addition, you may want to dump a database and its data to a SQL script file. Then, you can create the same database on another computer by running that script.

# How to load data from text files

After you’ve created a table, you can fill the table with data. There are two ways to do that. First, you can use the INSERT statement to insert one or more rows into a table as described in the next chapter. Second, you can load data from text files into a table as described in figure 17-13.

If you have a tab-delimited text file like the one shown in this figure, you can load the data in that file into a table. However, for this to work, the file must provide for all of the columns that are defined for the table. For example, a table for this text file would need to have four columns like this: userID, firstName, lastName, emailAddress.

The easiest way to load data from text files into MySQL is to use phpMyAdmin. To do that, you start phpMyAdmin, select the database, select the table, and click the Import tab. In this figure, for example, I have selected the database named my_guitar_shop2 and the table named products. Then, you select the file to import. Although you can’t see it in this figure, I have selected the file named products.txt that’s in the ch17_db_scripts directory. Next, you select the option that you want to use for importing. For this import, I have selected the “CSV using LOAD DATA” option, and I have set the field terminator to a tab character (\t), but I have left the rest of the options at their default settings. (Here, CSV stands for comma-separated values, even though this import uses tab-separated values.)

If you don’t have access to phpMyAdmin, you can use the command prompt to load data. To do that on a Windows system, you can use commands like the ones in this figure. To start, you use the mysql command to connect to the MySQL server. Then, you use the USE command to select the database. Finally, you use the LOAD command to load the data from the text file into the specified table. In this example, the LOAD command loads data from a local file named products.txt into the products table.

If you aren’t using a Windows system, the commands in this procedure will vary somewhat. Similarly, if you’re loading data into a table on a remote web server, this procedure will vary depending on how your web server is configured. As a result, you may need to check with your Internet service provider for details about connecting to the server and for the correct path to your files.
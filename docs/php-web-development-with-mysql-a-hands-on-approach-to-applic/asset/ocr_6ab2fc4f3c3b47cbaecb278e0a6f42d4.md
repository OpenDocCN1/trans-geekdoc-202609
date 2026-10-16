# 12. INSERTING DATA INTO A MYSQL DATABASE

# Loading Up the Northwind Database

The Northwind database is contained in two SQL files; one containing the schema, the second containing the data. It is available to download from:

+   - https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind.sql
+   - https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind-data.sql

You can download them using wget in the Bash shell. I like to download files into a Downloads folder under my home folder. Once you have navigated to the folder where you want to download the Northwind SQL file, type the following commands:

```
wget https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind.sql
wget https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind-data.sql
```

You will see the output shown in Figure 12.6 after downloading the files and doing a directory listing (ls).

![](bbox=[0.6, 0.1, 0.85, 0.2])

![](bbox=[0.11, 0.43, 0.86, 0.88])
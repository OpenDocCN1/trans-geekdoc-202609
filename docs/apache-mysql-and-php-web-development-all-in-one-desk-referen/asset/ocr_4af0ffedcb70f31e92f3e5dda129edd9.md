```
    print "Succeeded!\n";
}
else {
    print "Something went awry with the awful SQL!";
}
mysql_close();
?>
</body></html>
```

This code first connects to the MySQL system using the mysql_connect function. Next, the code calls mysql_query, simply passing an SQL statement. Here's the SQL statement by itself:

```
insert into phpbase.customer
(name, email, signup, last_access) values
('Jeff', 'me@domain.com', '2003-06-21', '2003-06-21')
```

This is a basic SQL insert statement, which adds data to the customer table. Notice that I specified the database name followed by a dot, before the table name, as in phpbase.customer.

The MySQL functions in PHP include an older function, mysql_db_query, in which you specify the database as a parameter rather than in the SQL statement. However, this function has been deprecated, meaning the PHP folks are phasing it out. Therefore, be sure to use mysql_query instead of mysql_db_query.

Notice that in the SQL statement I passed to mysql_query, I did not include a semicolon (not inside the double quotes, that is). I did end the mysql_query function call itself with a semicolon — just not inside the double quotes.

If you open this page in a Web browser, you simply see the word Succeeded!, meaning the mysql_query statement succeeded. But this script is only the beginning. As is, it's not very useful because the new data is hardcoded right into the script. In the next two sections, I show you how to create a Web form that allows users to enter data and how you use JavaScript to validate the data before sending it out.

# Entering data with PHP and a form

If you want to allow users of your site to add data to your tables, the easiest way is to set up a form in an .html file and have the form submit its data to a .php file, at which point the .php file submits the data to the database, and the world submits to your Web site and becomes yours. Whooohahaha.

But seriously, folks, start with a form like the one shown in Listing 4-1. This is the newcustomer.html file.
# Core PHP Programming

Just to check that everything went well, Figure 17-1 shows the output you would get if you selected everything from the catalog table from within the MySQL client. I got this output by typing

```
SELECT * FROM catalog;
```

in the MySQL client.

# Figure 17-1. SELECT * FROM catalog

| ID | Name | Price |
| 1 | Toothbrush | 1.79 |
| 2 | Comb | 0.95 |
| 3 | Toothpaste | 5.39 |
| 4 | Dental Floss | 3.50 |
| 5 | Shampoo | 2.50 |
| 6 | Conditioner | 3.15 |
| 7 | Deodorant | 1.50 |
| 8 | Hair Gel | 6.25 |
| 9 | Razor Blades | 2.99 |
| 10 | Brush | 1.15 |
| 10 rows in set | (0.01 sec) |

The last step is to write a PHP script that gets the contents of the table and dresses it up in an HTML table. Listing 17.3 lists PHP code for extracting the name and price values, displaying them in an HTML table. The first step in communicating with a database server is to connect to. This is done with the mysql_connect function. It takes a hostname, a username and a password. I usually create a user named http in my MySQL databases with no password. I also restrict this user to connections from the local server. I name it after the UNIX user who will be executing scripts—in other words, the Web server. If you are renting space for a hosting service, you may have a MySQL user and database assigned to you, in which case you'll need to modify the function arguments, of course.

# Listing 17.3 Creating HTML Table from a Query
# Looking at Advanced Algorithms

Here is sample output from a browser:

![](bbox=[0.24, 0.17, 0.76, 0.38])

# Displaying a multi-dimensional array and accumulating totals

How to properly display data from a multi-dimensional array has been a classic problem for any web developer. For illustration, assume you wish to display a list of customers and their purchases. For each customer, you wish to show their name, phone number, account balance, and so on. This already represents a two dimensional array where the x axis represents customers and the y axis represents data for that customer. Now add in purchases and you have a third axis! How can you represent a 3D model on a 2D screen? One possible solution would be to incorporate "hidden" division tags with a simple JavaScript visibility toggle.

# How to do it...

+   1. First we need to generate a 3D array from a SQL statement that uses a number of **JOIN** clauses. We will use the *Application/Database/Connection* class introduced in **Chapter 1, Building a Foundation**, to formulate an appropriate SQL query. We leave two parameters *open*, *min* and *max*, in order to support pagination. Unfortunately, we cannot use a simple **LIMIT** and **OFFSET** in this case, as the number of rows will vary depending on the number of purchases for any given customer. Accordingly, we can restrict the number of rows by placing restrictions on the customer ID that presumably (hopefully) is incremental. To make this work properly, we also need to set the primary **ORDER** to customer ID:

```
define('ITEMS_PER_PAGE', 6);
define('SUBROWS_PER_PAGE', 6);
define('DB_CONFIG_FILE', '../config/db.config.php');
include __DIR__ . '../Application/Database/Connection.php';
```
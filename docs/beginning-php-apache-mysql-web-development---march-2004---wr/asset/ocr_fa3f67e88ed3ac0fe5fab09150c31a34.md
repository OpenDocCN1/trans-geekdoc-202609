# Online Selling: A Quick Way to E-Commerce

# How It Works

First, we start a session for the customer. Then we again connect to the database. From there we have the following:

```
$prodid = \$_REQUEST['prodid'];
$query = "SELECT * FROM products WHERE prodnum='$prodid'";
$results = mysql_query($query);
or die(mysql_error());
$row = mysql_fetch_array($results);
extract($row);
```

In this block of code, we first take prodid, which came from the URL, and rename it so we can easily use it in our MySQL queries. In the next line, we use the products table for the appropriate product. We then run the query and extract the results so we can use them.

In the next details, we will build a table and display the information straight from the database. Here we have the following:

```
<td><form method="POST" action="add.php">
Quantity:
<input type="text" name="qty" size="2">
<input type="hidden" name="prodnum" value="<?php echo $prodnum ?>">
<input type="submit" name="Submit" value="Add to cart />
</form></td>
```

Here we have created a form that calls the action to add.php file (which we'll create in a moment) and passes only the variables we can carry: the product number (prodnum) and the quantity (qty).

The following gives the customer the option of viewing the current contents of the shopping cart. You can also supply this in form of a link, but we choose to offer it as a button in this case.

```
<form method="POST" action="cart.php">
<input type="submit" name="Submit" value="View cart">
</form>
</td>
```

We also give our customers the option to return to the main page.

# Try Out Creating a Table for the Shopping Cart

Create a temporary table to store the items in the customer's cart before he she checks out.

This file will be createtemp.php:

```
<?php
//connect to the database - either include a connection variable file or
//to typing the following lines:
$connect = mysql_connect("localhost","root","mysqlpass") or
```
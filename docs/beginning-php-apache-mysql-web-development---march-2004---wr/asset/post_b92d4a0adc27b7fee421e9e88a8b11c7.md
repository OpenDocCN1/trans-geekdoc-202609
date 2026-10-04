
# Online Selling: A Quick Way to E-Commerce

```html
<table>
  <tr>
    <td>
      value="<?php echo $_POST['shipstate']?>"
    </td>
  </tr>
  <tr>
    <td width="50%">
      <div align="right">Zip</div>
    </td>
    <td width="50%">
      <input type="text" name="shipzip" maxlength="5" size="5"
      value="<?php echo $_POST['shipzip']?>"
    </td>
  </tr>
  <tr>
    <td width="50%">
      <div align="right">Phone Number</div>
    </td>
    <td width="50%">
      <input type="text" name="shipphone" size="12" maxlength="12"
      value="<?php echo $_POST['shipphone']?>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <div align="right">E-Mail Address</div>
    </td>
    <td width="50%">
      <input type="text" name="shipmail" maxlength="50"
      value="<?php echo $_POST['shipmail']?>"
    </td>
  </tr>
</table>
```

<table border="1" align="left" cellpadding="5">
  <tr>
    <td>Quantity</td>
    <td>Item Image</td>
    <td>Item Name</td>
    <td>Price Each</td>
    <td>Extended Price</td>
    <td></td>
  </tr>
</table>

```php
<?php
$sessid = session_id();
$query = "SELECT * FROM carttemp WHERE sess = '$sessid";
$results = mysql_query($query);
or or die(mysql_query($query));
while ($row = mysql_fetch_array($results)) {
  extract($row);
  $prod = "SELECT * FROM products WHERE
  prodnum = '$prodnum'";
  $prod2 = mysql_query($prod);
```

# Chapter 14

```php
$prod2 = mysql_fetch_array($prod2);
extract($prod3);
echo "<td>";
echo "$quan";
echo "</td>";
echo "<td>";
echo "<a href='getprod.php?prodid=" . $prodnum . ".'>";
echo "THUMNAIL<br>IMAGE</img></a>";
echo "<td>";
echo "<a href='getprod.php?prodid=" . $prodnum . ".'>";
echo "$prodName";
echo "</td></a>";
echo "<td align='right'>";
echo "$Price";
echo "</td>";
echo "<td align='right'>";
//get extended price
$extprice = number_format($Price * $quan, 2);
echo "$extprice";
echo "</td>";
echo "<td>";
echo "<a href='cart.php?Make Changes to Cart'></a>";
echo "</td>";
echo "</tr>";
//add extended price to total
$total = $extprice + $total;
}
?>
<tr>
<td colspan='4' align='right'>Your total before shipping is:</td>
<td align='right'><?php echo number_format($total, 2) ?></td>
<td></td>
<td></td>
</tr>
</table>
<input type="hidden" name="total" value="<?php echo $total?>?>
<p>
<input type="submit" name="Submit" value="Send Order ->"/>
</form>

</BODY>
</html>
```

If you entered the information in checkout.php, your screen should look like that in Figure 14-6.

488

# Online Selling: A Quick Way to E-Commerce

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_511_0.png)

Figure 14-6

# How It Works

In the code, we use the standard connection lines and our session lines. Then we check to see if the billing info is the same as the shipping info, and, if so, we populate the table with the billing information:

```php
if ($_POST['name'] == 'on') {
    $_POST['shipfirst'] = $_POST['firstname'];
    $_POST['shiplast'] = $_POST['lastname'];
    $_POST['shipadd1'] = $_POST['add1'];
    $_POST['shipadd2'] = $_POST['add2'];
    $_POST['shipcity'] = $_POST['city'];
    $_POST['shipstate'] = $_POST['state'];
    $_POST['shipzip'] = $_POST['zip'];
    $_POST['shipphone'] = $_POST['phone'];
    $_POST['shipmail'] = $_POST['email'];
}
```

489

# Chapter 14

The rest of the script is pretty similar to previous pages. We show the billing and shipping information as we did in checkout1.php and show our cart contents as we did in cart.php. We decided in this case to keep our shopping cart changes in the cart .php file itself, we provide a link to cart.php.

Just another point worth mentioning: We passed the $total variable in a hidden field instead of retating in the next page; we needed to access it early on the code. This just makes a bit easier.

We also set our form action to checkout.php, where it all happens.

# Try It Out: Step Three

For our final file, we went to complete checkout.php. Numerous things will be going on this file, and we'll talk about them in a minute.

```php
<?php
session_id();
session_start();
// connect to the database - either include a connection variable or
type the following lines:
$connect = mysqli_connect('localhost', 'root', 'mysql') or
die('error, check your server connection.');
mysqli_select_db('ecommerce');
//Let's make the variables easy to access in our queries
$firstname = $_POST['firstname'];
$lastname = $_POST['lastname'];
$add1 = $_POST['add1'];
$add2 = $_POST['add2'];
$city = $_POST['city'];
$state = $_POST['state'];
$zip = $_POST['zip'];
$phone = $_POST['phone'];
$fax = $_POST['fax'];
$email = $_POST['email'];
$today = date('Y-m-d');
//1) Assign Number to new Customer, or find existing number
$query = 'SELECT * FROM customers WHERE
firstname = '$firstname' AND
lastname = '$lastname' AND
add1 = '$add1' AND
add2 = '$add2' AND
city = '$city';
$results = mysql_query($query)
or (mysql_error($query));
$rows = mysql_num_rows($results);

if ($rows < 1) {
//assign new customer
$query2 = 'INSERT INTO customers (
firstname, lastname, add1, add2, city, state, zip, phone, fax, email)
VALUES ('$firstname',
$lastname',
$add1',
$add2',
$city',
$state',
$zip',
$phone',
$email)';
$insert = mysql_query($query2)
or (mysql_error($query));
$custid = mysql_insert_id();
}
//If custid exists, we want to make it equal to total
if($custid) $custid = $custid;
//2) Insert Info into order
//determine shipping costs based on order (25% of total)
$shipping = $total * 0.25;

$query3 = 'INSERT INTO order (ordate, subtotal,
shipping, shipfirst, shiplast, shipadd1, shipadd2,
city, state, zip, shippone, email)
VALUES (
$today,
$total,
$shipping,
$shipfirst,
$shiplast,
$shipadd1,
$shipadd2,
$city,
$state,
$zip,
$shippone,
$email)';
$insert2 = mysql_query($query3)
or (mysql_error($query3));
$orderid = mysql_insert_id();

//3) Insert Info into order
//find the correct cart information temporarily stored
$query = 'SELECT * from carttemp WHERE sess=$sessid';
$results = mysql_query($query)
or (mysql_error($query));
//put the data into the database one row at a time
while ($row = mysql_fetch_array($results)) {
    extract($row);
    $query4 = "INSERT INTO orderdet (ordernum, qty, prodnum)
VALUES ('$orderid',
'$quan',
'$prodnum')";
    $insert4 = mysql_query($query4)
    or (mysql_error($query4));
}

//(4)delete from temporary table
$query="DELETE FROM carttemp WHERE sess='$sessid";
$delete = mysql_query($query);

//(5)email confirmations to us and the customer
/* recipients */
$to = "" . $email . "*";

/* subject */
$subject = "Order Confirmation";

// message */
/* top of message */
$message = "<html>
<head>
<title>Order Confirmation</title>
</head>
<body>
Here is a recap of your order:<br><br>
Order date: $today;
$message .= "<br>
Order Number: $orderid;
$message .= "<table width='50%' border='0'>
<tr>
<td>
<p><font size='2'>Bill to:</font><br>";
$message = "$firstname";
$message .= " * ";
$message .= "$lastname";
$message .= "<br>";
$message = "$add1";
$message .= "<br>";
if ($add2) $message .= $add2 . "<br>";
$message = $city . ", . $state . ", . $zip;
$message = "</font></p>
</td>
<td>
<p size='2'>Ship to:</font><br>";
$message = $shipfirst . ", . $shiplast;
$message .= "<br>";
$message = $shipadd1 . "<br>";
if ($shipadd2=='3') $shipadd2 . "<br>";
$message = $shipcity . ", . $shipstate . ", . $shipzip;
$message = "</font></p>
</td>
</tr>
</table>
<table noshade width='250px' align='left'>
<table padding='5'>
<tr>
// grab the contents of the order and insert them
// into the message field

$query = 'SELECT * from order WHERE ordernum = '$orderid';
$results = mysql_query($query);
while ($row = mysql_fetch_array($results)) {
  extract($row);
  $prod = 'SELECT * FROM products
WHERE prodnum='$prodnum';
  $prod2 = mysql_query($prod);
  $prod3 = mysql_fetch_array($prod2);
  extract($prod3);
  $message = "<td><font size='2'>*";
$message = $quan;
  $message .= "</font><td size='2'>*";
$message = $name;
  $message .= "</font></td>*";
  $message .= "<td align='right'><font size='2'>*";
$message = $price;
  $message .= "</font></</td>";
} // extended price
$extprice = number_format($price * $quan, 2);
$message = $extprice;
$message .= "</font></</td>";
}

$message = "<tr>
<td colspan='3' align='right'><font size='2'>
Your total before shipping is:</font>
</td>
<td align='right'><font size='2'>*";
$message = number_format($total, 2);
$message .= "</font>";
</tr>";
```

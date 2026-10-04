
# Answers to Exercises

die ("Hey loser, check your server connection.");

# Chapter 8

In Chapter 8 you were shown three short snippets of code and asked to spot the errors and figure out how to fix them. Then you were asked to create a little error-catching script to catch the errors.

- 1.

```php
<?
$query = "select * from table_name where name = '' . \$_POST['name'] . "'";
$result = mysql_query($result) or die(mysql_error());
?>
```

- 2.

```php
<?
if ($_POST['first_name'] = "Jethro")
{
echo "Your name is *" . $_POST['first_name'];
}
?>
```

# Appendix A

3.

```php
<?php $full_name = $_POST['mrmiss'] * $_POST['first_name'] * $_POST['last_name'];}?>
```

A1. Parse error from lack of semicolon at the end of the statement; the semicolon is here for the SQL

A2. You always need to check equality with double equals (==), not single equals (=). Simple equals are for setting a variable equal to a value.

A3. This is missing concatenation operators between the variables and the strings.

# Chapter 14

- Allow for options. You may have noticed that we didn't let our customers pick the size of their T-shirt or size of the Superhero Body Suit. Alter the code to allow for these options.

A: First, you need to alter your database to add size and color fields to enable the users to give you input. You should add these fields to your product and shopping cart-related tables. Your shopping cart show these two options as extra columns.

- Allow for payment. Because of copyright issues, we weren't able to actually hook up with Paypal or one of the other payment processors available. Decide how you want to accept payment, and then alter the code accordingly.

A: Again you need to alter your tables to add payment information. If customer is paying with a credit card, you need to make sure the form is submitted to you via SSL. You need a field for type of credit card, such as Visa, MasterCard, or Discover; you also need a field for expiration date. These fields must be added in the main order information, as this information will be unique to each order.

If you are hooking directly for instant payment processing through Verisign or online merchant, you need to check with them for specific instructions on coding your shopping cart to match with theirs.

- Allow for tax. Many states require you to charge sales on orders shipped to the state where you have a physical presence, and some states require sales tax on all online orders. Set your code to check for taxes in your own state and add the appropriate sales tax to those orders only.

A: Because we allowed for a sales tax already in the main order table, this requires a simple if in the final step of the order, everything is processed. If the customer is having or her order shipped within your state, take whatever your tax rate is, multiply by the customer's subtotal, and insert that tax value when you are inserting all the other information.

- Check for mistakes. We have not any mechanism to check for required fields, or for mismatched types (such as an e-mail address). Add these checks in your code.

A: To check weird characters and improperly formatted text, you should include statements that fix these potential problems. You can find such statements in Chapter 7 under validating user data.

- Allow for registering, login, and order tracking. Some customers like to check the status of their orders.

A: We discussed login and user authentication in Chapter 11. You apply these principles here, and it is a matter of issuing a SELECT statement based on customer number and displaying the results in a simple table. The only change you could make is to add the ordermain table that shows order status such as “Shipped,” “Received,” and so for customers can tell where in the order fulfillment process their order lies.

# Chapter 15

- Add code to admin.php to prevent unauthorized users from loading the page. Redirect back to index.php.

A: This block of code should be at the top of admin.php:

```php
<?php
include "http.php";
session_start();
if ($_SESSION['access_lvl'] < 3) redirect('index.php');
?>
```

- Create a regular expression that recognizes an e-mail address in a post and turns it into a link.

A: This is not the only answer but it gets the job done:
/[\w-]+\.[\w-]+\@[\w-]+\.[\w-]+/

- Add a bit of code to the pagination function to go to the first or last page. For example, if there are 14 pages, and the user is on page 8, and the range is 7, it should look like this:

```
<PREV] 1 [5] [6] [7] 8 [9] [10] [11] ... [14] NEXT >
```

A: Replace the appropriate lines of code with the following snippets:

```php
if ($range > 1) {
  $pagelinks .= "<a class='pagenumlink' href='<?php echo $currpage-1; ?>'>$1</a>...";
} else {
  $pagelinks .= "&nbsp;&nbsp;";
}

if ($range < $numpages) {
  $pagelinks .= "..<a class='pagenumlink' href='<?php echo $currpage+1; ?>'>" . $page . "." . $numpages . "</a>...";
} else {
  $pagelinks .= "&nbsp;&nbsp;";
}
```

# Quick Reference

In this appendix, we have listed some notes for your use.

# Displaying to Browser

To display text, use the following syntax:

```php
<?php
echo "text";
?>
```

# Setting a Value

To set a variable, use the following syntax:

```php
<?php
$variable = "value";
?>
```

# Passing Variables

There are three ways to pass variables:

```php
<?php
$name = array("firstname"=>"Albert", "lastname"=>"Einstein", "age"=>124);
echo $name["firstname"];
?>
```

or

```php
<?php
$name["firstname"] = "Albert";
$name["lastname"] = "Einstein";
$name["age"] = 124;
?>
```

# Arrays

If no keys are required, you can set the values for an array like this:

```php
<?php
$flavor[] = "blue raspberry";
$flavor[] = "root beer";
$flavor[] = "pineapple";
?>
```

# if Statements

In order to use if, use the following syntax:

```php
<?php
if ($condition) {
  // code
}
?>
```

or

```php
<?php
if ($condition) {
  // code;
}
?>
```

# else Statements

In order to use else, use the following syntax:

```php
<?php
if ($condition) {
  // code;
} else {
  // code;
}
?>
```

# Nested if Statements

You can use nested if by using the following syntax:

```php
<?php
if ($condition1) {
  if ($condition2) {
    // code;
  }
} else {
  // code
} //remember to use == for equals
?>
```

# Including a File

To include a file, use the following syntax:

```php
<?php
include "header.php";
?>
```

# Using Functions

Functions can be created and called using the following syntax:

```php
<?php
function functionname() {
  // code
}
functionname(); //calls the function to execute
?>
```

# for

You can execute a block of code a specified number of times with the following statement:

```php
<?php
for ($n = 0; $n <= 10; $n=$n+1){
  //these lines will execute while the value 'n' is
  less than or greater than 10
  echo $n;
  echo "<br>";
}
?>
```

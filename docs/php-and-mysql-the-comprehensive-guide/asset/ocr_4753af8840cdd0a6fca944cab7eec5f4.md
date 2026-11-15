```
<body>
<?php
$token = "";

if (isset($_POST["quantity"]) &&
(int)$_POST["quantity"] > 0 &&
isset($_POST["articleId"]) &&
isset($_SESSION["token"]) &&
isset($_POST["token"]) &&
$_SESSION["token"] == $_POST["token"]) {
file_put_contents(
"orders.txt",
sprintf("%d x article %s - %s\\n",
(int)$_POST["quantity"],
$_POST["articleId"],
date("Y-m-d H:i:s")),
FILE_APPEND);
echo "Order submitted!";
unset($_SESSION["token"]);
} else {
$token = random_bytes(32);
$_SESSION["token"] = $token;
}
?>

<form method="post" action="">
Quantity: <input type="text" name="quantity" /><br />
<input type="hidden" name="articleId" value="123" />
<input type="hidden" name="token" value="<?php echo $token; ?>" />
<input type="submit" value="Order" />
</form>
</body>
</html>
```

# Listing 32.9 The Improved Order Form ("order-token.php")

Try it out: You can still place orders by calling up the form directly. However, if you use the HTML file (for which you must adjust the form dispatch destination), you will land on the "normal" order page, but an order will not be sent automatically or entered in the text file.

**Note**

Another additional protective measure against CSRF is the use of SameSite cookies, which have already been discussed in Chapter 14. The following php.ini setting activ-ates a specific SameSite mode for all PHP sessions:
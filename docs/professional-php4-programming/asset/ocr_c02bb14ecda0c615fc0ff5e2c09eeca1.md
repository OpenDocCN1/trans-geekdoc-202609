```
printf("%s <br/>\n", $item->getItemType());
```

Print the price of the item:

```
printf("$$%s <br/>\n", $item->getPrice());
?>
</p>
</card>
</wml>
```

# Displaying the User's Cart

The PHP script DisplayCart.php displays the user's shopping cart:

```
<?php
include_once("Common.php");
include_once("User.php");
include_once("BookItem.php");
include_once("MusicItem.php");

setSessionHandlers();

if (!headers_sent()) {
   header("Content-Type: text/vnd.wap.wml" );
}
```

If the session is not authenticated, then send an error page:

```
checkSessionAuthenticated();
?>
```

The WML Document Type Declaration:

```
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
  "http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<card id="main">
```

Define a <do> element of type options. The action of the <do> element points to the main page of the application (AppMain.php):

```
<do type="options" label="HOME">
   <go href="AppMain.php?<?php echo(getSessionIdString()) ?>"/>
</do>
<p>
<b> Shopping Cart Items </b>
<?php
```

Get shopping cart items:
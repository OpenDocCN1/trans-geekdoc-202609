# # Changing Quantities in the Shopping Cart

The script GenChangeQuantityForm.php generates a form for changing the quantity of a shopping cart item. The URL parameter $selectedItem contains the index of the selected item in the $shoppingCartArray:

```
```php
<?php
include_once("Common.php");
include_once("MusicItem.php");
include_once("BookItem.php");
include_once("ShoppingCart.php");

setSessionHandlers();
header("Content-Type: text/vnd.wap.wml");
```
```

If the session is not authenticated then send an error message:

```
```php
checkSessionAuthenticated();
```
```

The WML Document Type Declaration:

```
```html
<!DOCTYPE wml PUBLIC "-//WAPFORUM//DTD WML 1.1//EN"
 "http://www.wapforum.org/DTD/wml_1.1.xml">
<wml>
<card>
```
```

Define a <do> element of type options. The action of the <do> element points to the main page of the application (AppMain.php):

```
```html
<do type="options" label="HOME">
 <go href="AppMain.php<?php echo(getSessionIdString()) ?>"/>
</do>
<p>
```
```

Define an <input> element for entering the new quantity. The value entered by the user is stored in $quantity variable:

```
```php
<?php
$shopCartItem = $shoppingCart->getShoppingCartItem($selectedItem);
$item = $shoppingCart->getItem($selectedItem);
?>
Enter Quantity for <?php echo($item->title()) ?>
<input name="quantity" type="text" format="N"
 value="<?php echo($item->getQuantity()) ?>" />
```
```

Define a <do> element of type accept, with Submit as its label. The action of the <do> element points to ChangeQuantity.php. The variables $selectedItem, $quantity, and the session id string are sent as URL parameters:
```
```php
$shoppingCartItems = $shoppingCart->getItems();
$first = true;
$insertedSelect = false;
for($i=0; $i < sizeof($shoppingCartItems) ; $i++) {
  if ($first) {
    printf("<select>");
    $insertedSelect = true;
  }
  $item = $shoppingCartItems[$i]->getItem();
```
```

Display the title of the item as a link. The action of the link points to a card containing the details of the item on the same page:

```
```php
generateOptionElement("#". $item->getItemNo(),
                      $item->getTitle());
              $first=false;
}
if ($insertedSelect) {
  printf("</select>");
}
?>
</p>
</card>
```
```

For each entity (book/music album), which is displayed in the main card, generate a card containing a description of the entity:

```
```php
<?php
// Display the details of each card
for($i=0; $i<sizeof($shoppingCart); $i++) {
  $item = $shoppingCartItems[$i]->getItem();
  $itemNo = $item->getItemNo();
?>
```
```

The id attribute of the card element is set to the itemNo of the entity:

```
```html
<card id="<?php echo($itemNo) ?>">
```
```

Generate a <do> element of type accept with CHG as its label. The action of the <do> element points to GenChangeQuantityForm.php. This script generates a form for changing the quantity of the item. The itemNo of the item and the session id string are passed as URL parameters to GenChangeQuantityForm.php:

```
```html
<do type="accept" label="CHG">
  <go href="GenChangeQuantityForm.php?selectedItem=<?php echo($itemNo)
       ?>&amp;
<?php
```
```
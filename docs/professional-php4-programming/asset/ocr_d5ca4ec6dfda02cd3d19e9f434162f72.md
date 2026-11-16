The function removeItem(), removes $item from the shopping cart:

```
```php
function removeItem($item){
    $shoppingCartItem = $this->getShoppingCartItem($item->getItemNo());

    if ($shoppingCartItem != null) {
```
```

Removing the item from the shopping cart is the same as setting its quantity to zero:

```
```php
        $shoppingCartItem->setQuantity(0);
        }
    }
```
```

The function changeQuantity(), changes the quantity of $item to $newQuantity:

```
```php
function changeQuantity($item, $newQuantity)
{
    $shoppingCartItem = &$this->getShoppingCartItem(
            $item->getItemNo());

    if ($shoppingCartItem != null) {
        $shoppingCartItem->setQuantity($newQuantity);
    }

    $shoppingCartItem = &$this->getShoppingCartItem(
            $item->getItemNo());
}
```
```

The function getItems(), returns an array of shopping cart items:

```
```php
function getItems()
{
    $retItems = array();
    for($i=0; $i<sizeof($this->shoppingCartItems); $i++) {
        $shoppingCartItem = $this->shoppingCartItems[$i];

        if ($shoppingCartItem->getQuantity() != 0) {
            $retItems[] = $shoppingCartItem;
        }
    }
    return $retItems;
}
```
```

Resets the shopping cart:

```
```php
function clear()
{
    $this->shoppingCartItems = array();
}
}
```
```
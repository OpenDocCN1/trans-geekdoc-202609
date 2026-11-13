```
public function addProduct(product:Object):void
{
    // Look for product in list
    for(var i in cartContents)
    {
        if(cartContents[i].id == product.id)
        {
            var q:Number = cartContents[i].cartItem.quantityTxt.text;
            cartContents[i].cartItem.quantityTxt.text = q + 1;
            updateTotal();
            return;
        }
    }
    ...
}
```

The loop is set up to first check for a valid cart item ID. If a valid ID is found, the quantity is assigned to the q variable. This is then appended to the value of the quantity text box and a call to the price updater is made to ensure that it is always correct. A return is used to halt any further execution of code located within this function.

This method was probably the largest, as it is responsible for a lot of the functionality in this application. The completed code is provided in one final display at the end of this section, and of course, is also available on the book’s Web site.

The next method is used to remove an item from the shopping cart. The getID method that was created in the ShoppingCartItem class is used in this function to retrieve the id. The parent reference is used to take the target (Delete button) and inform the code what the parent or upper object is. This provides a solid link to the ShoppingCartItem class instance and ultimately the method to retrieve the id.

```
public function removeProduct(e:MouseEvent):void
{
    var id:uint = e.target.parent.getID();
    ...
}
```

After the id is known it can be used to remove the item from the array of cart items and from the display list. The splice method is used to delete the cart item using the id, which is actually the position the item can be found in the array. The second argument in the splice method is to ensure only one element is deleted.

```
cartContents.splice(id, 1);
removeChild(e.target.parent);
cartItemCount--;
```

NOTE If the second argument is not provided, the splice method will remove all of the items from that point.
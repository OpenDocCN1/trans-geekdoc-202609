| Array | new Array() [] |
| Object | new Object() {} |
| String | new String() "" |

Both application methods that were created are public because they are called from external classes. You could also build an intermediate function that offers a higher level of security, which would be responsible for calling the private methods.

With the StoreItem class built, you can move to the ShoppingCartItem, which is attached to the shopping cart item MovieClip.

# Developing the ShoppingCartItem class

This class is basically responsible for holding the item id, which will be used in the ShoppingCart class. Just like the previous class, this one also needs to import the MovieClip and TextField classes to accommodate the components located in this MovieClip.

```
package
{
import flash.display.MovieClip;
import flash.text.TextField;

public class ShoppingCartItem extends MovieClip
{
private var cartItemID:uint;
function ShoppingCartItem() ( )
public function getID():uint
{
return cartItemID;
}

public function setID(id:uint):void
{
cartItemID = id;
}
}
}
```

The last portion of this class is responsible for getting and setting the cartItemID. This value is used to link the products with the cart items.
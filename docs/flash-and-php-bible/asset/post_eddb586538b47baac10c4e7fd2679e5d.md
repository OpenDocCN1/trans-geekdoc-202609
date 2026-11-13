
The contents of that dbconn.php file are seen here.

```php
<?php
$host = "localhost";
$user = "username";
$pass = "password";
$database = "database name";

$link = mysql_connect($host, $user, $pass);
mysql_select_db($database, $link);

unset($host);
unset($user);
unset($pass);
unset($Database);

?>
```

Now you can determine which action is being requested. There are two possible options: getproducts, which returns an xml document of store items, or checkout, which loads the xml from Flash and displays it.

```php
if($_GET['action'] == 'getproducts')
{
    print getProducts();
}
else if($_GET['action'] == 'checkout')
{
    $xml = new SimpleXMLElement($_GET['xml']);

    $nodeCount = count($xml->product);

    print "<table border=\"1\" width=\"500\">";
    print "<tr><td><strong>Quantity</strong></td>";
    print "<td><strong>Product</strong></td>";
    print "<td><strong>Price</strong></td></tr>";

    for($x=0; $x < $nodeCount; $x++)
    {
        print "<tr style=\"background-color:#eeeee\">";
        print "<td style=\"width:60px; text-align:center;\">"
        . $xml->product[$x]->quantity . "</td>";
        print "<td>" . $xml->product[$x]->name . "</td>";
        print "<td>" . $xml->product[$x]->price . "</td></tr>";
    }

    print "<tr>";
    print "<td colspan=\"3\">Total: <strong>"
    . getAttribute($xml, 'total') . "</strong></td></tr>";
    print "</table>";
    print "<br />Checkout code goes here<br />";
}
```

The getproducts action simply makes a call to another function that returns the xml generated from the database entries. The checkout action, as shown in Figure 12.3, is a little more involved. It starts off by grabbing the XML data passed from Flash. This XML is loaded into the SimpleXML library where it is parsed and each of the store items is retrieved.

## FIGURE 12.3

Here is a sample of the checkout page, loaded from Flash. This page is visible when the Checkout button is clicked.

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_329_0.png)

This function is called from the first action and is responsible for building an XML document from the data in the database. The store items are broken down by id, name, desc, and thumbnail, which are all visible in the Flash file.

The result set from MySQL returns any item that is currently active. This result is then passed into a while loop, which is where the XML data is built. Finally, the XML is returned to the caller and, in this example, is printed to the screen for Flash to load.

```php
function getProducts()
{
    global $link;

    $result = mysql_query("SELECT * FROM flashStore_products 
    WHERE active=1", $link);

    $xml = "<products>\n";
    while($row = mysql_fetch_array($result))
    {
        $xml .= "<product id=\"" . $row['id'] . "\"
        name=\"" . $row['name'] . "\"
        desc=\"" . $row['description'] . "\"
        thumbnail=\"" . $row['thumbnail'] . "\"
        price=\"" . $row['price'] . "\" />\n";
    }
    $xml .= "</products>";

    return $xml;
}
```

The last function is actually a forgotten feature of SimpleXML. This function takes two arguments, the xml and the attribute name you are looking for. It first loops through all of the arguments and matches those arguments against the passed-in variable. It returns either the value of the attribute or false, depending on what the result is.

```php
function getAttribute($xml, $name)
{
    foreach($xml->attributes() as $key=>$val)
    {
        if($key == $name)
        {
            return (string)$val;
        }
    }
    return false;
}
```

Now that all of the code is complete, here are the three classes and Timeline code provided in one place for easier viewing and comparison with your code.

## ShoppingCart

```actionscript
package
{
    import flash.display.MovieClip;
    import flash.text.TextField;
    import flash.events.MouseEvent;
    import flash.net.*;

    public class ShoppingCart extends MovieClip
    {
        private var cartItemCount:uint = 0;
        private var cartContents:Array;

        private var cartItemHeight:uint = 20;
        private var lineSpacing:uint = 30;
        private var gateway:String;

        function ShoppingCart()
        {
            cartContents = new Array();

            checkoutBtn.addEventListener(MouseEvent.CLICK,
            function():void
            {
                var xml:String = "<?xml version='1.0' ?>\n\r";
                xml += "<products total=\"" + totalTxt.text + "\">";

                for(var i in cartContents)
                {
                    xml += "<product>";
                    xml += "<quantity>" +
                    cartContents[i].cartItem.quantityTxt.text
                    + "</quantity>";
                    xml += "<name>" + cartContents[i].name
                    + "</name>";
                    xml += "<price>" + cartContents[i].price
                    + "</price>";
                    xml += "</product>";
                }
                xml += "</products>";

                var variables:URLVariables = new URLVariables();
                variables.action = "checkout";
                variables.xml = xml;

                var urlRequest:URLRequest = new URLRequest(gateway);
                urlRequest.data = variables;
                urlRequest.method = "GET";

                navigateToURL(urlRequest);
            })
        }

        public function addProduct(product:Object):void
        {
            // Look for product in list

            for(var i in cartContents)
            {
                if(cartContents[i].id == product.id)
                {
                    var quantity:Number =
                    cartContents[i].cartItem.quantityTxt.text;
                    cartContents[i].cartItem.quantityTxt.text =
                    quantity + 1;

                    updateTotal();
                    return;
                }
            }

            if(cartItemCount == 0)
            {
                noItemsTxt.visible = false;
            }

            var cartItem:ShoppingCartItem =
            new ShoppingCartItem();

            cartItem.removeItemBtn.addEventListener(
            MouseEvent.CLICK, removeProduct);

            cartItem.quantityTxt.text = String(1);
            cartItem.nameTxt.text = product.name;
            cartItem.setID(cartItemCount);

            cartItem.y =
            (cartItemCount * cartItemHeight) + lineSpacing;

            product.cartItem = cartItem;

            cartContents.push(product);

            addChild(cartItem);

            cartItemCount++;

            updateTotal();
        }

        public function removeProduct(e:MouseEvent):void
        {
            var id:uint = e.target.parent.getID();

            cartContents.splice(id, 1);
            removeChild(e.target.parent);

            cartItemCount--;

            if(cartItemCount == 0)
            {
                noItemsTxt.visible = true;
            }

            updateList();
            updateTotal();
        }

        public function updateList():void
        {
            for(var i:uint=0; i < cartItemCount; i++)
            {
                cartContents[i].cartItem.setID(i);
                cartContents[i].cartItem.y =
                    (i * cartItemHeight) + lineSpacing;
            }
        }

        public function updateTotal():void
        {
            var total:Number = 0;
            for(var i:uint=0; i < cartItemCount; i++)
            {
                total += Number(cartContents[i].price) *
                    Number(cartContents[i].cartItem.quantityTxt.text);
            }

            totalTxt.text = "$" + String(round2D(total));

            // tack on extra 0 if needed or two 0's
            if(totalTxt.text.indexOf('.') == -1)
            {
                totalTxt.appendText(".00");
            }
            else if(totalTxt.text.indexOf('.') + 2 ==
                totalTxt.text.length)
            {
                totalTxt.appendText("0");
            }
        }

        public function setGatewayURL(url:String):void
        {
            gateway = url;
        }

        private function round2D(n:Number):Number
        {
            return Math.round(n * Math.pow(10, 2)) / Math.pow(10, 2);
        }
    }
}
```

## ShoppingCartItem

```actionscript
package
{
import flash.display.MovieClip;
import flash.text.TextField;

public class ShoppingCartItem extends MovieClip
{
private var cartItemID:uint;

function ShoppingCartItem() {

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
}
```

## StoreItem

```actionscript
package
{
import flash.display.MovieClip;
import flash.text.TextField;

public class StoreItem extends MovieClip
{
private var albumName:String;
private var albumDesc:String;
private var albumThumb:String;
private var albumPrice:String;
private var storeItemID:uint;

function StoreItem() {

public function setStoreData(
id:uint, n:String,
```

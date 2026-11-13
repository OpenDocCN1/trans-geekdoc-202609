
## Timeline code

```actionscript
d:String, t:String, p:String):void
{
    storeItemID = id;
    albumName = n;
    albumDesc = d;
    albumThumb = t;
    albumPrice = p;

    nameTxt.text = albumName;
    descTxt.text = albumDesc;
}

public function getItem():Object
{
    return {
        target:this,
        id:storeItemID,
        name:albumName,
        price:albumPrice
    };
}
}
```

## Timeline code

```actionscript
var phpFile:String = "http://localhost/ch11/store/flashCart.php";
var cart:MovieClip = shoppingCart;
cart.setGatewayURL(phpFile);

var storeItems:MovieClip = new MovieClip();
storeItems.x = 25;
storeItems.y = 80;

var urlRequest:URLRequest = new URLRequest(phpFile +
    "?action=getproducts");
var urlLoader:URLLoader = new URLLoader();
urlLoader.addEventListener(Event.COMPLETE, productsLoaded);
urlLoader.load(urlRequest);

function productsLoaded(e:Event):void
{
    var urlLoader:URLLoader = URLLoader(e.target);
    var xml:XML = new XML(urlLoader.data);

    trace("XML: " + xml);

    var id:uint = 0;
    for each(var xmlItem in xml..product)
    {
        var item:StoreItem = new StoreItem();
        item.y = 85 * id;
        item.setStoreData(id,
            xmlItem.attribute('name'),
            xmlItem.attribute('desc'),
            xmlItem.attribute('thumbnail'),
            xmlItem.attribute('price'));
        item.addToCartBtn.addEventListener(
            MouseEvent.CLICK, addItemHandler);
        storeItems.addChild(item);
        id++;
    }
    addChild(storeItems);
}

function addItemHandler(e:MouseEvent):void
{
    var prod:Object = e.target.parent.getItem();

    trace("Add Item: " + e.target.parent);
    trace("Item ID: " + prod.id);

    cart.addProduct(prod);
}
```

## PHP code

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
unset($database);

?>

<?php

include 'dbconn.php';

function getProducts()
{
    global $link;

    $result = mysql_query("SELECT * FROM flashStore_products
    WHERE active=1", $link);

    $xml = "<products>\n";

    while($row = mysql_fetch_array($result))
    {
        $xml .= "<product id=\"" . $row['id'] .
            "\" name=\"" . $row['name'] .
            "\" desc=\"" . $row['description'] .
            "\" thumbnail=\"" . $row['thumbnail'] .
            "\" price=\"" . $row['price'] . "\" />\n";
    }

    $xml .= "</products>";

    return $xml;
}

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
        print "<tr style=\"background-color:#eeeeee;\">";
        print "<td style=\"width:60px;text-align:center;\">"
            . $xml->product[$x]->quantity . "</td>";
        print "<td>" . $xml->product[$x]->name . "</td>";
        print "<td>" . $xml->product[$x]->price . "</td></tr>";
    }

    print "<tr><td style=\"text-align:right;\" colspan=\"3\">Total: "
        . $xml->getAttribute($xml, 'total') .
        "</strong></td></tr>";
}

print "<br />Checkout code goes here<br />";
}
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
?>
```

The example is now complete; it is just a matter of placing the PHP on an active Web server. From this point you can extend the example to have multiple categories, products, and images. Realistically, building the application in a class format offers greater expandability, but don't just take my word for it. Experiment and extend the example.

## Using PHP and Flash to Build an Amazon Search Application

Amazon offers a very powerful set of tools designed to work with its site data. This section covers the building of a search application using Amazon.com as the data source. This example uses the ECS (Amazon E-Commerce Service), which provides direct access to Amazon's amazing searching and inventory system.

In order to use the ECS you need to have a valid Amazon access ID, which is provided when you create a developer's account. This registration process is quick and free; all you need is a valid e-mail address and an active account.

## Using the Amazon Web Service

To get started with creating a developers account, visit the Amazon Web Service (AWS) page at www.amazon.com/gp/aws/landing.html.

> Be sure to activate the account via e-mail before you begin to use it.

The AWS is set up to be accessed from different mediums. The format used for this example is Representational State Transfer (REST), which is basically a formatted URL with all of the necessary information provided in GET format.

Here is a sample request sent to Amazon, as shown in Figure 12.4, to return information about possible book matches for a keyword or series of keywords.

```
http://ecs.amazonaws.com/onca/xml?Service=AWSECommerceService&AWSAccessKeyId={AWS_ACCESS_KEY}&Operation=ItemSearch&SearchIndex=Books&ResponseGroup=Medium&Keywords={SEARCH_TERMS}
```

The AWS_ACCESS_KEY is the access id that is provided by Amazon, and the SEARCH_TERMS would be the keyword(s) that are passed along for searching.

As you may have noticed, the XML response from Amazon is fairly complex. However, for this example the focus will be on the book title, author, and thumbnail path. Amazon is actually very nice to provide the amount of detail it does. You can build some pretty interesting applications with the AWS system.

### FIGURE 12.4

Here is the XML response from Amazon, after a search for “PHP”.

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_339_0.png)

In fact, the URL sent to Amazon can be modified to search for different items or subjects all together. The AWS is set up to even return valid error messages similar to this one if you don't provide an operation parameter.

> AWS.InvalidOperationParameter The Operation parameter is invalid.
> Please modify the Operation parameter and retry. Valid values
> for the Operation parameter include TagLookup, ListLookup,
> CartGet, SellerListingLookup, CustomerContentLookup,
> ItemLookup, SimilarityLookup, SellerLookup, ItemSearch,
> VehiclePartLookup, BrowseNodeLookup, CartModify, ListSearch,
> CartClear...

The search system offers a lot of types and modifiers, and you don't have to rely on this “create an error” concept to see what is available. Amazon happens to provide very robust documentation in the developer's center. Log in for access.

## Simplifying the XML response

When the XML response was loaded in the previous section, the result was overwhelming. There are many XML nodes and data that just aren't applicable to this application. You could pass this raw data into Flash, but what if you want to cache the results? You would have a bunch of unused information clogging up your database.

The idea is to build a custom XML response that only contains the data necessary for this application.

```php
<?php
$terms = "";

define("AWS_ACCESS_KEY", "(AWS_KEY_GOES_HERE)");
```

It is important to check for valid tags before a response is sent to Amazon. It really doesn't harm anything, but it could be considered a fraudulent request.

```php
if(!empty($_GET['terms']))
{
    ...
}
```

Assuming valid tags were found, build the request that will be sent to the AWS.

```php
if(!empty($_GET['terms']))
{
    $terms = $_GET['terms'];
    $request = 'http://ecs.amazonaws.com/onca/xml' .
        '?Service=AWSECommerceService' .
        'AWSAccessKeyId=' . AWS_ACCESS_KEY .
        '&Operation=ItemSearch' .
        '&SearchIndex=Books' .
        '&ResponseGroup=Medium' .
        '&Keywords=' . $terms;
}
```

Now call the AWS, passing along the search parameters.

```php
$rawXml = file_get_contents($request);
```

The response from the AWS is loaded using file_get_contents, which reads in the entire file requested into a string. In this example, the string is saved to the $rawXML variable. A call to the simplexml library is made to build a properly formatted XML object.

```php
$xmlResponse = simplexml_load_string($rawXml);
```

The next step is to build the custom XML document that will be sent back to Flash when it is requested. The nodeCount variable is hard-coded to 4 so that only four book results are saved. Even if Amazon returns thousands, Flash only sees four.

```php
$nodeCount = 4;

$xml = "<?xml version=\"1.0\" ?>\n<books>";

for ($i=0; $i < $nodeCount; $i++)
{
    ...
}

$xml .= "</books>";
```

The contents of the for.. loop is where the majority of the XML building process occurs. For example, to load the current book title, you first access the Items node. Once inside that node, the selected Item node is accessed using the $i variable to determine which child should be referenced. Inside the current child node, there is another child with the node name ItemAttributes, which contains a title node and ultimately becomes the name of the book for this selected child.

$xmlResponse->Items->Item[$i]->ItemAttributes->Title

As you can see, Amazon packs this XML file full of information, which in this instance makes it sort of difficult to load the desired information. The process of loading the author and thumbnail data is pretty much the same—just access each child and reference the desired node.

```php
$xml .= "\t<book>";
$xml .= "\t\t<title><![CDATA[" . $xmlResponse->Items->Item[$i]->ItemAttributes->Title . "]]></title>";
$xml .= "\t<author><![CDATA[" . $xmlResponse->Items->Item[$i]->ItemAttributes->Author . "]]></author>";
$xml .= "\t<price><![CDATA[" . $xmlResponse->Items->Item[$i]->ItemAttributes->Price . "]]></price>";
```

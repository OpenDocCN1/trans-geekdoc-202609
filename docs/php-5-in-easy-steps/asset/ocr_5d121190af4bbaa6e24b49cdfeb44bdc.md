# Querying with XPath

XPath allows you to query an XML document for specific nodes matching particular criteria. This is far more powerful than the getElementsByTagName() method, which simply returns a DomNodeList of all elements having the specified name. For instance, the XML document food.xml (listed below), a call to getElementsByTagName("item") would return all the "item" child elements of "fruit" and "veg" elements.

![](bbox=[0.199, 0.252, 0.273, 0.348])

```
<?xml version = "1.0" encoding = "iso-8859-1" ?>
<fruit>
  <item id="1">Apple</item>
  <item id="2">Banana</item>
  <item id="3">Cherry</item>
</fruit>
<veg>
  <item>Lettuce</item>
  <item>Onion</item>
</veg>
<food>
```

XPath, however, can return specific elements.

To start using XPath in PHP 5, a DomXPath object must first be created using the "new" keyword and stating the name of the loaded DomDocument as its parameter. The DomXPath object is assigned to a variable in the same manner as with a new DomDocument object.

![](bbox=[0.03, 0.743, 0.135, 0.831])

Significantly, the DomXPath object has a query() method that returns a DomNodeList of those nodes matching the criteria specified as its parameter. The simplest query specifies the path to a particular element, such as "food/fruit/item".

The PHP script listed opposite assigns a DomXPath object to a variable called "$xp". Its query() method is used to return a DomNodeList of all "item" nodes within the "fruit" element. Their textContent is then written out in a HTML list.
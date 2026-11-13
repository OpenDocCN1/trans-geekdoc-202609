request per second). Start by creating a SoapClient instance with the location of the WSDL document:

```
<?php
$client = new SoapClient("http://webservices.amazon.com/AWSECommerceService/
AWSECommerceService.wsdl");
?>
```

Now you need to set up an object for the request you want to send. Set up an object called $search containing nodes for your access key ID, the category, and keywords for a search:

```
$search->AWSAccessKeyId = "your_key_id";
$search->Request->SearchIndex = "Music";
$search->Request->Keywords = "Merle Haggard";
```

To perform the search, run the client's itemSearch() method:

```
$r = $client->itemSearch($search);
```

If everything goes well, the XML results appear in $r. You can access this object in much the same way you would a SimpleXML instance:

```
foreach ($r->Items->Item as $item) {
    $attributes = $item->ItemAttributes;
    if (is_array($attributes->Artist)) {
        $artist = implode($attributes->Artist, ", ");
    } else {
        $artist = $attributes->Artist;
    }
    print "artist: $artist; title: $attributes->Title<br />";
}
?>
```

This is remarkably easy to use if you happen to know how everything works. Unfortunately, most of the time, you won't know how everything works. WSDL files often have no accompanying documentation. So assuming that you know how to read WSDL or you have a browser, you can find all of the methods available to the client, and you will know which parameters the methods expect, but you won't know what the parameters do. Furthermore, even though you will know what the responses from the methods will look like, you won't even know exactly what it is the methods are supposed to do. Part of the reason is that it's hard to be concrete about documentation when you don't know which programming language or SOAP implementation you're dealing with. Moreover, no one wants to document it.

Performance is another serious issue. In the preceding example, PHP needs to fetch the WSDL file, parse its XML, and then set up an entirely new class and instance based on the WSDL content. This is exceptionally inefficient, especially considering that you normally just need to send a few short parameters to a service. PHP does cache the WSDL files that it sees (other languages may require you to generate and compile code based on the WSDL, which isn't any better).
Finally, add a user control panel (for zooming and panning), and wrap up with the HTML to display the map:

```
map.addControl(new GLargeMapControl());
}
}

</script>
</head>
<body onload="initialize()" onunload="GUnload()">
<div id="map_canvas" style="width: 500px; height: 300px"></div>
</body>
</html>
```

Now you have a simple application that draws a line on a Google map
between the White House and the address you choose. By itself, this script is
a bit of a toy (especially because you can get the geolocation code from
Google instead of Yahoo!), but you can probably imagine many different
ways it can serve as a starting point for real applications.

We could go on and on with web services, showing you how to authorize
credit cards and get shipping quotes, but all of that is busy work at this
point—you gather the data from the client, package it for the server, send
the request, and check the results. For much of this, you can even find
PHP client code to do the work for you. However, one topic we have not yet dis-
cussed is SOAP, and this protocol is very important in many web services.

# #72: Using PHP and SOAP to Request Data from Amazon.com

Simple Object Access Protocol (SOAP) is a full-blown web service standard
that, like anything with *simple* in the name, is far from simple. The idea is to
place all of the details concerning the input and output of a web service into
a Web Services Description Language (WSDL) document, so that you can
automatically generate a programming interface and call a web service just as
you would a method or function. You don’t have to mess around with cURL,
building queries, or any of that stuff—just create an object with your request,
tell PHP to create the interface, call the method, and you get an object
containing your goodies. In fact, when everything works the way it should, it
*is* as easy as that, and the script in this section shows you how to get started.

PHP 5 includes a collection of built-in SOAP classes, including the
SoapClient class that we’ll see soon. However, the classes typically aren’t built
in by default. To use it, you need to include the –enable-soap parameter when
configuring and building PHP (refer back to Chapter 2 for more details on
this process).

Our example is based on the Associates Web Service that Amazon.com
offers to help you sell its goods from your website. All you need to do is apply
for an access key ID, and then you can access it for free (at a rate of one
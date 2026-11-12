Note that if you’re trying this code yourself, you’ll need to modify the $baseUrl variable to fit your environment. With $baseUrl defined, we can fetch the full URL, relative to the Web root, using $_SERVER[ 'PHP_SELF' ], then strip out the $baseUrl. This leaves us with a string we can match against the location field in the menu table. I took this approach for the sake of example, as it allowed me to demonstrate the menu with a single script, while taking advantage of Apache’s “look back” functionality (which we’ll discuss in more detail later in this chapter). Using this, we can fetch the path fragment that appears to the right of the script name in the URL, and insert it into our PHP script. For example, consider this URL:

http://localhost/sitepoint/WebPageElements/12.php/products/

The actual script name is 12.php; I can examine the additional /products/ fragment to decide on the correct menu to display. You’re not required to do things this way, though. You might, for example, have multiple PHP scripts that use the same code—perhaps an include file—to display the correct menu:

http://www.example.com/products/index.php
http://www.example.com/news/index.php

Adopting that approach, you would likely use the PHP variable $_SERVER[ 'PATH_INFO' ] to obtain the script location, and choose a menu based on that.

But let’s move on with our single-script example that uses a URL suffix for the menu location. Next comes the line in which all the action happens:

```
$crumbs = &new BreadCrumb($mysql, $location);
```

This instantiates the BreadCrumb class and passes it the MySQL object, which it uses to fetch from the menu table, using the $location variable to find the user’s current location within the menu. The BreadCrumb class is primed to do all the work and build the menu automatically.

So where’s the menu? Well, I couldn’t make it too easy, could I? The generation of the menu in HTML, JavaScript, or whatever, is up to you. All the BreadCrumb class does is return a list of menu items which you then need to format. Here’s one way you could do it:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```
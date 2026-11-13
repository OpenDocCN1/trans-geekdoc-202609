setting the testing parameter to indicate that it's a second access. You'll see how the location header works in the following section.

```
} else {
    setcookie("test", "1", 0, "/");
    header("Location: $_SERVER[PHP_SELF]?testing=1");
}
?>
```

It's extremely important that you do not forget to include the testing parameter. If you omit it, the page will reload infinitely if the browser does not support cookies.

This script isn't terribly intuitive to read, because the first pieces that the user encounters do not correspond to the first lines of code. However, it is so small that you can easily understand it entirely, and once you do that, you should have no problems with it.

# #59: Redirecting Users to Different Pages

Redirecting users to new pages is a fact of life when programming dynamic websites. The primary reason is that you often need to redirect a user after making session state changes. For example, when you add an item to a shopping cart, you want the user to go to a page such as the current shopping cart, and you don't want to add another one of the same item to the cart again if you reload that shopping cart page. Most sites achieve this with a script that processes the state change and then redirects to the page that they want the user to see.

There are essentially two ways to do it. The first and preferred way is to use the HTTP Location header, like this:

```
<\?
header("Location: new_page.php");
\?>
```

The header() function sends raw HTTP headers to the user's browser. Therefore, you need to do this before sending any other output to the browser, just as you would when setting a cookie.

There are two advantages to this method. First, it is instant, and the intermediate script does not appear in a web browser's history. Second, because it is HTTP based, it does not require a web browser to process; automatic web crawlers and programs such as wget understand it.

However, if you would like to show an intermediate page to the user with a delay, you need to use a different method that uses the HTML <meta> tag. It's pretty simple; to send a user to a different page after displaying the current page for five seconds, put the following in your HTML header:

```
<meta http-equiv="Refresh" content="5;URL= new_page.php" />
```
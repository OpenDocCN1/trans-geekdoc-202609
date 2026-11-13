
## Chapter 6

## Working with Cookies

- Using cookies in PHP
- Using cookies in Flash
- Understanding shared objects

Cookies are very common in Web browsing. In fact, you would find it very hard to navigate the Internet in the way we are accustomed to if cookies stopped working. This chapter is how to work with cookies in both Flash and PHP. It covers loading and sending of cookies and investigates how a cookie is deleted.

The second half of the chapter is about shared objects, which are cookies in Flash. They act almost the same as standard browser cookies with some differences, which you will investigate.

Once you have completed this chapter you will fully understand how to work with cookies and why they are important for a successful application and user experience.

### Loading Cookies

A cookie is a small file placed on the user’s computer by a Web server. This file is then sent back to the server unchanged each time the user accesses the server. Most often a cookie will contain the username for a Web site. A cookie can also be used to save user settings and any other small pieces of information.

The process of loading cookies is explained in multiple pieces to better understand how they work. You will notice that the process of loading cookies is very similar to loading other forms of data.

### Using cookies with PHP

Using cookies with PHP is necessary in order to develop a usable Web application. You will find many opportunities to implement cookie support from user login to styles and many other uses.

As you begin to work with dynamic data more often you will want to save portions to the user's machine. Doing this allows the program to log a user in automatically or modify a style based on the user's settings.

Cookies are saved per domain and directory: This means that any page within the same domain or path can read that cookie. This is very useful when building multiple examples and also means another Web site cannot read cookies from a different site.

> NOTE
> The common workaround for sharing cookies across a domain is to create a subdomain. A cookie is only specific to the overall domain and simply ignores paths, parameters, and subdomains.

### Loading a cookie

Now that you have an understanding of what a cookie is, take a look at how to load and work with one in PHP: The following code attempts to load a cookie and display the response as shown in Figure 6.1.

```php
<?php
$username = "Jimmy";

if ( !isset( $_COOKIE['user'] )) {
    setcookie( "user", $username );
    print "Welcome " . $username;
}
else
{
    print "Welcome back, " . $_COOKIE['user'];
}

?>
```

The previous code checks for the existence of the cookie "user" in the global array of cookies. If the cookie is found, the user is welcomed back. If the cookie is not found, the cookie is set and the user is welcomed for the first time.

The $_COOKIE variable is a multidimensional array that can contain many different cookies. This variable is automatically filled by PHP and doesn't require you to add to it.

### FIGURE 6.1 The print statement as displayed in the browser window

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_136_0.png)

### Saving a cookie

Setting or saving a cookie in PHP is very simple: you make a call to the setcookie function. The first argument is the cookie name; the second argument is the cookie value. For example, say you want to set a time_logged_in cookie.

```php
setcookie("time_logged_in", time());
```

Anytime you want to save a cookie you can call the setcookie function. If the cookie exists, it is updated, and if it doesn't exist it is created.

> NOTE
> A cookie's ability to be saved depends on whether or not a user allows cookies.

The setcookie function accepts more than two arguments, but actually only requires the first argument, which is the name.

### Cookie expiration

By default, a cookie expires when the session ends or the user closes the browser. The way a session ends is by a predefined amount of time on the server. By default, this amount is 0 seconds because the session ends when the browser closes. Normally, you as the developer do not need to know how long a session lasts. You would, of course, be more interested in whether or not the cookie exists.

Occasionally, you will want to ensure a cookie is deleted after a certain amount of time. This is the case when working with secure data or a content management system. Assume you want the cookie to expire soon after the cookie is created.

```php
setcookie("username", "adminDave", (time() + 7200));
```

This tells the user's browser to delete the cookie 2 hours after the cookie is created. The expiration time of a cookie is in seconds, so for this example 7200 is 2 hours. Another way to look at it is (60 * 60 * 2).

Have you ever opened your browser, visited a site, and were introduced to custom content that you had applied in a previous session? This data was determined by a cookie saved on your machine that was not deleted when the session ended.

Look at an example of a cookie that doesn't expire for three months.

```php
<?php
$secondsInDay = 86400;
$daysBeforeExpiration = 90;
setcookie("userStylePref", "blueTheme", (time() + ($secondsInDay * $daysBeforeExpiration)));
?>
```

You start by setting the number of seconds in a day—86400. Then you set our $daysBeforeExpiration variable that is holding how many days you want the cookie to live. The last step is to set the cookie. Multiply the seconds by the days, add to the time() function, and this becomes your expiration date.

Three months is only an example; you can set a cookie to expire years later. However, users have a tendency to clean up their browser storage. So, you should never allow an application to rely on the existence of a cookie.

### Deleting a cookie

At some point in your application you will probably want to delete a cookie. However, the local Web browser that your user is on does not allow a Web server to directly delete a cookie. Instead, set the expiration date behind the current date and basically make the cookie expire. This tells the Web browser to delete the cookie because it is no longer in use.

```php
setcookie("time_logged_in", "", (time() - 300));
```

### Assigning multiple cookies

The process of assigning multiple cookies is fairly straightforward. You basically make multiple calls to the setcookie function ensuring that each cookie has a unique name.

```php
<?php

$username = "jimmy";
$userID = 5;
$loggedInTime = time();

setcookie("username", $username);
setcookie("userid", $userID);
setcookie("logged_in_since", $loggedInTime);

?>
```

The previous code sets three cookies by making three unique calls to the setcookie function.
You could also place the setcookie call into a custom function if the passed-in code requires
more security. For example, you can create a saveCookie function that ensures the data is clean.

```php
<?php

function saveCookie($name, $value, $expires=0)
{
    if($name == "")
    {
        print "Name not provided, cookie not saved";
    }
    if($value == "")
    {
        print "Value not provided, cookie not saved";
    }

    setcookie($name, $value, $expires);
}

$username = "jimmy";
$userID = 5;
$loggedInTime = time();

saveCookie("username", $username);
saveCookie("userid", $userID);
saveCookie("logged_in_since", $loggedInTime);

?>
```

Your saveCookie function is used as a proxy to the prebuilt setcookie function. This allows
you to check the passed in data and ensure that it is filled in properly. In the previous example,
you print an error if either the name or value is empty. You could take this simple security check a
step further by ensuring the data is, in fact, a string and doesn't contain any potentially malicious code. As you begin to develop Web applications you will learn to follow rigid guidelines as far as security is concerned.

Now that you have looked at how to use cookies in PHP, you can look at using cookies in Flash. The
process of using cookies in Flash is very similar, but offers some advantages that you will look at.

### Using cookies in Flash

Cookies in Flash are actually called shared objects and share similar attributes to cookies in PHP.
Some of these attributes include the ability to store small amounts of data locally and retrieve them
by any file in the same basic domain. Just like cookies in PHP, the user is able to disable them per
site or globally. However, they have some distinct differences. One major advantage to shared
objects is the ability to bind to them. This means multiple movies have the ability to watch the file
and be alerted when it is updated. For example, say you have a multiplayer game and want each
client to track the score in sync. With shared objects you can allow each of the clients to have
read/write access and the others will update the score as it changes.

### Loading shared objects

The following code attempts to load a shared object and creates one if it doesn't exist. As you can
see, loading a shared object is fairly simple and only requires one line of code. Cookies in PHP
don't offer the ability to natively create one if it doesn't exist; you have to check for the cookie and
manually create it.

```actionscript
var so:SharedObject = SharedObject.getLocal("sample");
trace("Object is " + so.size + " bytes in size");
```

### Saving shared objects

The process of saving a shared object is also straightforward. Start by creating a new instance of the
SharedObject class.

```actionscript
var so:SharedObject = SharedObject.getLocal("sample");
```

After the object is created, you can attach data to the shared object by adding elements to the data
object, such as:

```actionscript
var so:SharedObject = SharedObject.getLocal("sample");
so.data.user = "guest";
```

You can call and recall that above block of code and the value won't be saved just yet. The reason is
because you need to alert the object to write it to the local filesystem by calling the flush method.

```actionscript
var so:SharedObject = SharedObject.getLocal("sample");
so.data.user = "guest";
so.flush();
```

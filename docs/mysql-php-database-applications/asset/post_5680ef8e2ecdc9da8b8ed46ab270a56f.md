

In PHP versions 4.2 or later, you should be getting your form data via the super-global (so called because they are globally available without ever having to be declared as global) array variables $_POST and $_GET, depending on the method used in your form. You can also use the $_REQUEST variable, which is a combination of GET, POST, and cookie values.

To add a bit more security to the previous listing, you could rewrite Listing 4-1 to look like Listing 4-2:

## Listing 4-2: Simple Script That Does Not Use Globals

```
if (isset($_POST['submit']) && $_POST['submit']=="yes")
{
    echo "thank you for submitting your form.";
}
else
{
?>
<form action="test1.php" method="POST">
<input type="text" name="email">
<input type="text" name="first_name">
<input type="submit" name="submit" value="yes">
</form>
<?php
}
```

You can access any individual element as you would an element in any associative array ($_POST ['email']). Or you can loop through all the contents of an array as follows:

```
foreach ($_POST as $key => $value)
{
    echo "variable = $key value = $value <br>";
}
```

## Passing arrays

Sometimes passing scalar variables won't be enough, and you'll need to pass arrays from your HTML page to your PHP script. This will come up when the user can choose one or more form elements on a page. Take, for example, multiple select boxes, which enable users to pass one or more items from a number of items. The form element is made with the HTML in the following code example. The multiple attribute indicates that the user can choose more than one element, as shown in Figure 4-1. To choose more than one element on the PC, hold down the Ctrl key while selecting additional values. On the Mac, use the Apple key. Gnome users can select and unselect individual elements with a click.

```
<form action="mypage.php" method="POST">
<select name="j_names[]" size="4" multiple>
    <option value="2">John
    <option value="3">Jay
    <option value="4">Jackie
    <option value="5">Jordan
    <option value="6">Julia
</select> '
<input type="submit" value="submit">
</form>
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_148_0.png)

Figure 4-1: Multiple select boxes

Notice that in the select name attribute we've added opening and closing brackets ([ ]). This tells PHP to expect an array. If we didn't include the brackets, two values might end up fighting for the same variable name, and that's no good at all.

Once it has been submitted you can address this array like any other two-dimensional array:

```
if (is_array($_POST['j_names']))
{
    echo "<b>the select values are:<br> <br>";
    foreach ($_POST['j_names'] as $value) {
        echo $value . "<br>\n";
    }
}
```

Passing arrays can also be useful when you want to present a series of check-boxes that the user may or may not check before pressing the Submit button. Chapter 8 contains a code example for a page that enables the program's administrator to use checkboxes to select which entries should be deleted. Figure 4-2 shows a sample of this type of page. If you were to assign a different name to each check-box, you would have to check each one individually. With arrays, you can write a three-line loop to check them all.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_149_0.png)

Figure 4-2: Series of checkboxes

Arrays passed from forms can also have associative keys, which can be multidimensional. The name of the form element should take the form name="array_name[element_name]". Or, for a multidimensional array, name="array_name[element_name][subelement_name]".

## Cookies

Cookies are small pieces of information that are stored by a user's Web browser. Some are kept in memory and discarded after a short time, and others are written to the user's hard drive for long-term use. Once a Web browser has accepted a cookie from a server, it resends the same cookie to its owner(s) on each HTTP request until the cookie expires or is deleted. Cookies provide the only way to keep track of users over the course of several visits. Remember that the Web is a stateless environment. Your Web server really has no idea who is requesting a page. Cookies help you keep track of users as they move around your site.

When they exist, cookies become part of the HTTP request sent to the Web server. But first you’ll need to set a cookie. The PHP developers have made this, like everything else in PHP, exceedingly simple. Use the `setcookie()` function. This function takes the following arguments:

```
setcookie(name [, value [, time_to_expire [, path [, domain [, security setting]]]]]);
```

We will discuss this function in more detail in Chapter 6, but for now, suffice it to say that the following statement—

```
setcookie("mycookie", "my_id",time()+(60*60*24*30), "/", ".mydomain.com", 0)
```

– would set a cookie with the following parameters:

- Stores a variable named my_cookie
- The value of mycookie is "my_id".
- The cookie will expire 30 days from the time it is set (current time plus the number of seconds in 30 days).
- The cookie will be available to every page in the domain. (You could restrict it to a specific path within a domain by including a path.)
- The cookie will be available to every site with a mydomain.com address.
- There are no special security settings.

Once the cookie is set, you can retrieve cookie values through the `$_COOKIE` superglobal array variable. The value of the cookie set with the previous `setcookie()` function is available as `$_COOKIE['mycookie']`.

You can also set cookies that are accessible as arrays:

```
setcookie("mycookie[first]", "dddd",time()+2592000,"/","192.168.1.1", 0);
```

```
setcookie("mycookie[second]", "my_second_id",time()+2592000,"/","192.168.1.1", 0);
```

These two variables would be accessible as associative arrays within the `$_COOKIE` array.

> The preceding code works fine on Internet Explorer 5 on the PC. However, it might not work on other browsers. In any case, you are probably better off avoiding situations that require arrays within cookies.

## Sessions

PHP, like ASP and ColdFusion, natively supports sessions, only it does a much better job. What's a session? Basically, it's another means of maintaining state between pages. Your script declares that a session should start by accessing the $_SESSION superglobal variable (you can also use the older-style session_start() function). At that point PHP registers a unique session ID, and usually that ID is sent to the user via a cookie. PHP then creates a corresponding file on the server that can then keep track of any number of variables. The file has the same name as the session ID.

Once the session is created, you can register any number of variables. The values of these variables are kept in the file on the server. As long as the session cookie lives, these variables will be available to any page within the same domain that wishes to access them. This setup is much more convenient than sending variables from page to page through hidden form elements or bloated cookies.

Of course, it is possible that some users will not allow cookies. For this reason, PHP enables you to track the session ID through the querystring. You can do this manually by appending the session ID to the querystring, or by changing the session.use_cookies value in your php.ini file to equal 1.

The constant SID is predefined as "session-name=session-ID". To add it to the querystring manually, use <?php echo SID; ?>. This automatically prints out a string like this:

```
PHPSESSID=07d696c4fd787cd6c78b734fb4855520
```

Adding this value to a link will cause PHPSESSID to be passed via the querystring. Use something like this:

```
<a href="mypage.php?<?php echo SID; ?>">click to page</a>
```

The following script will register a session variable named my_var, and will assign it a value of "hello world".

```
<?php
$_SESSION['my_var'] = "hello world";
?>
```

On subsequent pages, you are able to access this by simply referring to $_SESSION['my_var'].


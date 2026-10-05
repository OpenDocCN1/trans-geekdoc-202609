# I.5.4. Determining Cookie Status on a Client Machine

Users often disable cookies in their browser's settings. For a Web application that uses cookies to work correctly, it must contain the code that checks whether the visitor has enabled cookies on the client computer. Implement such a check.

# I.5.5. Forging Cookies

Assume there is a script that checks cookies installed on the client machine for authenticity. The cookie name sets the user name, and cookies such as admin, editor, and user allow authorization for the administrator, the editor, and the user, respectively.

Listing I.5.3. Providing access to information using cookies

```
<?php
if(isset($_COOKIE['name']))
{
    if(isset($_COOKIE['admin']))
    {
        echo "Hello administrator $_COOKIE[name]<br>";
    }
    if(isset($_COOKIE['editor']))
    {
        echo "Hello editor $_COOKIE[name]<br>";
    }
    if(isset($_COOKIE['user']))
    {
        echo "Hello user $_COOKIE[name]<br>";
    }
}
?>
```

The script shown in Listing I.5.3 can be found in the /scripts/5/5/5.1.php file on the accompanying CD-ROM.

![](bbox=[0.09, 0.831, 0.188, 0.928])
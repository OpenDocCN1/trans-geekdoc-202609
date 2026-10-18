# FIGURE 13.9 Fruit machine

![](bbox=[0.088, 0.085, 0.789, 0.35])

A simple form is used to allow the user to ‘spin’ the fruits again:

```
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p><input type='submit' value='spin'/></p>
</form>
```

The output from the above script is illustrated in Figure 13.9.

# 13.6 Page redirection and referral

Quite often you may wish to build a secure web page. You may create a login form and require that a user enters their username and password. You may check that these are correct by comparing them to a file or database (we shall show you how to do this later). If the username and password are valid then you may wish to direct the user to a new page for them to access. Otherwise the user will remain on the username and password form page.

User redirection can be performed using the ‘Location:’ string in the header() function:

```
header ("Location: webpage");
```

This basic form of web security is illustrated in Figure 13.10.

| NOTE | Header functions, like those of cookies, must be called before any output is sent to the browser. |
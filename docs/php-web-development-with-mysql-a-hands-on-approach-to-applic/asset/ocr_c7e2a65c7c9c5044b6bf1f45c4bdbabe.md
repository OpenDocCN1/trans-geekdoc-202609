# 21. PERSISTENCE

```
9.     <input type="test" class="form-control" id="entered_cookie"
10.         name="entered_cookie" placeholder="Enter a cookie you like to eat"
11.         required>
12. </div>
13. <button type="submit" class="btn btn-primary"
14.     name="cookie_submission">Submit</button>
15. </form>
16. <?php
17. }
```

Again, notice we are POSTing to $_SERVER['PHP_SELF'], so we use different name attributes for the submit button for this form. Doing so lets us track which form the user is submitting.

Once the user has submitted this form, execution starts up in the first elseif clause where we set a cookie named favorite_cookie for the entered favorite cookie:

```
elseif (isset($_POST['cookie_submission']) && isset($_POST['entered_cookie']))
{
    setcookie('favorite_cookie', $_POST['entered_cookie']);
    header("Location: {$_SERVER['PHP_SELF']}");
    exit;
}
```

This code saves the favorite cookie and redirects the browser to $_SERVER['PHP_SELF']. Remember, until we send our response to the user's browser, the cookie is not set, and the value does not exist in the $_COOKIE superglobal. We can differentiate from direct navigation to this script which displays the first form by checking for the existence of the two cookies.

Next, execution starts in the second elseif clause where we want to output the phrase that uses the saved cookies:

```
elseif (isset($_COOKIE['name']) && isset($_COOKIE['favorite_cookie']))
{
    // ...
    setcookie('name', '', time() - 3600);
    setcookie('favorite_cookie', '', time() - 3600);
}
```

Notice the two calls to setcookie(). These calls set the time back one hour (in seconds), which tells the browser to delete the cookies.
# Understanding Basic Session Functionality 477

The parameters correspond exactly to the ones in the Set-Cookie header mentioned previously.

If you set a cookie in PHP using

```
setcookie('mycookie', 'value');
```

then when the users visit the next page in your site (or reloads the current page), you will have access to the data stored in the cookie via $COOKIE['mycookie'].

You can delete a cookie by calling setcookie() again with the same cookie name and an expiry time in the past. You can also set a cookie manually via the PHP header function and the syntax given previously. One tip is that cookie headers must be sent before any other headers; otherwise, they will not work; this is a requirement for standard use of cookies rather than a PHP limitation.

# Using Cookies with Sessions

Cookies have some associated problems: Some browsers do not accept cookies, and some users might have disabled cookies in their browsers. (This is one of the reasons PHP sessions use a dual cookie/URL method, which we will discuss.)

When you are using sessions, you do not have to manually set any cookies. The session functions take care of this task for you by creating the necessary cookies to match the session being created when the sessions are used.

You can use the function session_get_cookie_params() to see the contents of the cookie set by session control. It returns an array containing the elements lifetime, path, domain, and secure.

You can also use

```
session_set_cookie_params(lifetime, path, domain, [secure], httponly);
```

to set the session cookies manually.

If you want to read about cookies, you can consult the cookie specification (“HTTP State Management Mechanism”) at http://tools.ietf.org/html/rfc6265.

# Storing the Session ID

By default PHP uses cookies to store the session ID on the client side. The other built-in method PHP can use is adding the session ID to the URL. You can set this to happen automatically if you use the session.use_trans_sid directive in the php.ini file to On; it is off by default.

Use caution when turning this directive on, as it increases your site's security risks. If value is set to on, a user can email the URL that contains the session ID to another person, the URL could be stored in a publicly accessible computer, or it may be available in the history or bookmarks of a browser on a publicly accessible computer.
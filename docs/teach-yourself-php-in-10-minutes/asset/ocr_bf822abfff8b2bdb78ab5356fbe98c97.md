# # Deleting Cookies

There is no unsetcookie function to tell the web browser to delete a cookie. To stop a cookie value from being sent back to the web server, you use setcookie with an empty value and an expiration date that has already passed.

The following example unsets the email cookie by using an expiration value that is one hour ago:

```
setcookie("email", "", time()   3600);
```

![](bbox=[0.113, 0.33, 0.173, 0.375])

**Overwriting Cookies** When unsetting a cookie or when overwriting an existing cookie with a new value, you must make sure the domain , path , and ssl-only arguments are exactly the same as when the cookie was originally created.
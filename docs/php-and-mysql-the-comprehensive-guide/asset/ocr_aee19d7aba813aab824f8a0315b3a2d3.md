```
```php
<?php
setcookie("ProgrammingLanguage", "PHP",
      time() + 60*60*12, "/", ".php.net");
?>
```
```

This cookie can be read from all subdomains of php.net.

# Safe

Finally, the sixth parameter for setcookie() deserves a mention. If this is set to true, the cookie is only sent via secure connections (i.e., via HTTPS). So if you store sensitive data in cookies, you should set this parameter—but then you also need an HTTPS-capable web server.

If you omit this parameter (or set it to false), the cookie is only sent via HTTP, not via HTTPS.

> > **Note**
> > However, it is not necessarily advantageous to hide sensitive data in cookies, whether encrypted or not; in fact, it is not advisable. It is better to store this data exclusively on the server. In the next chapter, you will learn how this is possible.

The following is another secure cookie:

```
```php
<?php
setcookie("password", "top secret",
      time() + 60*60*12, "/", ".php.net",
      true);
?>
```
```

# httpOnly

One of the possible manifestations of cross-site scripting (an attack against web applications that we discuss in detail in Chapter 32) is that JavaScript code that has been smuggled in can access cookies. Microsoft has suggested how this could at least be made more difficult: If httpOnly is specified as an additional cookie argument, then the cookie is sent along with the complete HTTP communication as before, but JavaScript no longer sees the cookie.1 In the meantime, other browser developers have followed suit and also retrofitted this feature.

The following cookie cannot be read by JavaScript:

1 In certain configurations, it is still possible for JavaScript to access the cookie, but only with some effort.
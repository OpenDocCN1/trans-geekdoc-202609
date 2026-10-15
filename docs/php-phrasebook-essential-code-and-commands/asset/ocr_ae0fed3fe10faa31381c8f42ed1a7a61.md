> **NOTE**
> The (unofficial) cookie specification goes back to Netscape and is still available at http://wp.netscape.com/newsref/std/cookie_spec.html. There have been attempts to create a special Request for Comment (RFC) for next-generation cookies, but this hasn't found any reasonable browser support yet.

Cookies are sent as part of the HTTP header. If a cookie is set, the HTTP header entry Set-Cookie is created. The name and value of the cookie (both strings) follow and, optionally, further information such as expiration date, domain, and path of the cookie. For instance, when visiting http://www.php.net/, the PHP website sends this header entry (your mileage may vary, especially in terms of the language and IP address used):

```
Set-Cookie: COUNTRY=DEU%2C84.154.17.84; expires=Thu, 19-May-05 15:23:29 GMT; path=/; domain=.php.net
```

When the browser (or the user) accepts the cookie, it is then sent back to the server in the HTTP header Cookie:

```
Cookie: COUNTRY=DEU%2C84.154.17.84
```

A cookie can have an expiration date. If that is set, the cookie lives up to this date (at most) and is a so-called persistent cookie. After that, the browser automatically deletes the cookie—but this could also happen earlier, for instance when the maximum number of cookies in the browser is reached and the oldest cookies are purged. If, however, no cookie expiration date is set, a so-called session cookie or temporary cookie has been
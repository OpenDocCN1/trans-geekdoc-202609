![](bbox=[0.14, 0.1, 0.78, 0.28])

Figure 32.4 Where Does the Warning Window Come From?

And think about what could be stored in cookies: the current session ID, for example. This makes it very easy to take over a victim's session (this is called session hijacking).

So you can see that the data must be filtered, either when writing to the database or when reading it out. This can be done using the htmlspecialchars() function, which reliably converts all angle brackets (and other "bad" characters: the apostrophe, the double quotation mark, and the ampersand) into the corresponding HTML entities:

```
$coded = htmlspecialchars($input);
```

Everything that comes from the client (and could therefore be malicious) must be saved before output. In addition to $_GET, $_POST, and $_COOKIE, this also includes some entries in $_SERVER, including $_SERVER["PHP_SELF"].

> Note
> To prevent session hijacking and cookie theft, it also helps to protect the session cookie from being accessed by JavaScript by using the HttpOnly flag:
> session.cookie_httponly = "On"

XSS is therefore incredibly easy to exploit, but even websites of specialist magazines have proved vulnerable here in the past. Above all, this happens to people who have little HTML experience and don't see much difference between developing web and desktop applications.

Finally, a cautionary example on the subject of unchecked user data. Imagine you have developed (another) content management system and URLs of the following types:

+   - http://server/index.php?section=index
+   - http://server/index.php?section=products
+   - http://server/index.php?section=support
+   - http://server/index.php?section=imprint
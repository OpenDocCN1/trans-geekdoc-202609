+   1. Call up the script in the web browser.
+   2. Save the HTML code locally on the hard disk.
+   3. Set the `action` attribute of the `<form>` tag in the code to the URL of the original script.
+   4. Change the value of the hidden field to a different ID.
+   5. Call up the (local) form in the web browser and submit it. The script on the web server is called and the fake ID is transferred via POST.

Figure 32.7 shows the new code; the changed or added areas are highlighted.

> **Note**
> 
> Most browsers have built-in tools that make it particularly easy to change form data (they are often accessible via `[F12]`). As a consequence, hidden form fields are not invisible!

Don't think that this attack is too trivial and not (or no longer) up to date. Just a few years ago, a security vulnerability was discovered in a relatively well-known online store that was based on precisely this attack method.

```
<html>
<head>
<title>Delete</title>
</head>
<body>
<form method="post" action="http://server.xy/delete.php">
<input type="hidden" name="id"
value="99" />
<input type="submit" value="Confirm deletion" />
</form>
</body>
</html>
```

Figure 32.7 The HTML Code Can Be Changed Locally in the Editor

# 32.5 Input Filter

PHP has an integrated extension that takes care of filtering input. The initial developers of the package are Derick Rethans and PHP inventor Rasmus Lerdorf.

This extension is available without any further installation steps. It does not operate at the SAPI level, so it does not intercept any input before PHP even sees it. Instead, the filter implements several functions that filter data in such a way that in the end (according to the plan), nothing harmful is included.

One of the main functions of the extension is `filter_input()`, with which you can determine GET, POST, and cookie data. You specify the type of data (`INPUT_GET`, `INPUT_POST`, `INPUT_COOKIE`), then the name, and finally the desired data type. If this is not ful-
```
$name = "user";
$theme_value = "Alice Dupont";

// Set cookie lifetime (1 hour)
$expiration = time() + 3600; // current timestamp + 3600 seconds (1 hour)

// Set the path for which the cookie is valid (the whole site)
$path = "/";

// Set the domain for which the cookie is valid (current domain)
$domain = "";

// Create cookie with setcookie()
setcookie($name, $theme_value, $expiration, $path, $domain);

// Display a confirmation message
echo "The cookie has been created successfully";
?>
```

In this example :

+   - The cookie name is set to "user" and its value to "Alice Dupont".
+   - The cookie expires after 1 hour (3600 seconds) from the time it is created.
+   - The path is defined as "/" to indicate that the cookie is valid throughout the site.
# Chapter II.6: User Agents and Referrers 251

However, the script presented in Listing II.6.3 will register redirections among pages within the same site in addition to the redirections from third-party sites. Such redirections might be numerous, especially if the site contains many pages. At any rate, it would exceed the number of redirections from third-party sites. To exclude registration among internal site pages, it is necessary to add a check that would test whether the domain name is part of the refer to the current site (Listing II.6.4).

# Listing II.6.4. Excluding redirections among pages of the current site

```
<?php
// If the referrer is not empty, placing it into the database
if(!empty($_SERVER['HTTP_REFERRER']) &&
    strpos($_SERVER['HTTP_REFERRER'], $_SERVER['SERVER_NAME'])
{
    // Establishing the database connection
    require_once("config.php");
    if (!get_magic_quotes_gpc())
{
        $_SERVER['HTTP_REFERRER'] = =
            mysql_escape_string($_SERVER['HTTP_REFERRER']);
    }
    // Adding a new record
    $query = "INSERT INTO referer VALUE (NULL, $_SERVER['HTTP_REFERRER'])"";
    if(!mysql_query($query)) exit(mysql_error());
}
?>
```

The domain name of the site can be obtained by accessing the $_SERVER['SERVER_NAME'] superglobal array element.

# II.6.2. Protecting an HTML Form Using a Referrer

To protect HTML forms against being filled in at third-party sites, it is possible to add a check by a refer into the HTML form handler in the handler.php file (Listing II.6.5).
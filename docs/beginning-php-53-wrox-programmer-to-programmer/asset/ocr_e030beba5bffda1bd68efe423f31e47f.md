# Chapter 20: Writing High-Quality Code

Generally speaking, it's better to whitelist, if possible, because it's safer than blacklisting. Blacklisting, it's easy to forget to include a particular character in the blacklist, creating a potential security hole. Sometimes it's not possible or practical to use a whitelist, in which case a blacklist is the best approach.

Although regular expressions give you a lot of flexibility with checking input, you can use other techniques to make life easier. HTML::::Form (covered in Chapter 15) lets you use the PEAR Validate package (see `http://pear.php.net/package/Validate`) to validate input such as dates, email addresses, URLs, and so on.

An alternative to whitelisting is filtering. However, rather than checking that input doesn't contain malicious data (rejecting if it does), you remove any malicious data from the input, and proceed as normal:

```
```php
$searchQuery = $_GET['search'];
$searchQuery = preg_replace('/[^a-zA-Z0-9]/", "", $searchQuery);
echo "You searched for: " . $searchQuery;
// (display search results here)
?>
```
```

In this example, any characters that aren't letters or digits are removed from the query string before it is used. When the previous malicious query string is supplied, the script produces the following output:

You searched for:
scriptdocumentlocationhref://examplecomcookiesdocumentcookiescript

A variation on filtering is casting to ensure that the input is of the required type:

```
```php
$pageStart = (int) $_GET["pageStart"];
```
```

Filtering is often nicer from a user's perspective, because they don't have to deal with error messages or reentering data. However, because data is silently removed by the application, it can also lead to confusion for the user.

# Encoding Output

As well as validating or filtering all input to your script, it's a good idea to encode the script's output. This can help to prevent cross-script scripting attacks, such as the one shown previously.

With this approach, you can encode, or escape, potentially unsafe characters using whatever escaping mechanism is available to output the format you're working with. Because you're outputting HTML, you can use PHP's `htmlspecialchars()` function to replace unsafe characters with their encoded equivalents:

```
```php
$searchQuery = $_GET['search'];
echo "You searched for: " . htmlspecialchars($searchQuery);
// (display search results here)
?>
```
```
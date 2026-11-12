# **Outlet exhaust :**

Properly escape all dynamic data before inserting it into an HTML page. This means converting all special characters into HTML entities, so that they are treated as plain text by the browser rather than as HTML or JavaScript code.

In our comment form example, before displaying the comments on the web page, we need to escape special characters such as <, >, &, ", etc., to prevent the execution of malicious scripts.

If you run the following code, a JavaScript window is displayed with the text "XSS!" :

```
$comment = "<script>alert('XSS!');</script>";
echo "<div>$comment</div>";
```

In PHP, to escape the contents of the $comment variable, simply use the htmlspecialchars() function as follows:

```
$comment = "<script>alert('XSS!');</script>";
// Escape special characters
$comment_echappe = htmlspecialchars($comment);
// Display the escaped comment on the web page
echo "<div>$comment_echappe</div>";
```

In this code, the htmlspecialchars() function is used to escape special characters in the comment, meaning that special characters such as <, >, &, ", etc., will be converted into HTML entities to render them harmless
# A PHP file that includes HTML and embedded PHP

```
```php
<?php
    // get the data from the request
    $first_name = $_GET['first_name'];
    $last_name = $_GET['last_name'];
?>
<!DOCTYPE html>
<html>
    <head>
        <title>Name Test</title>
        <link rel="stylesheet" type="text/css" href="main.css">
    </head>
    <body>
        <h2>Welcome</h2>
        <p>First name: <?php echo $first_name; ?></p>
        <p>Last name: <?php echo $last_name; ?></p>
    </body>
</html>
```
```

# The PHP file displayed in a browser

![](bbox=[0.095, 0.391, 0.831, 0.566])

# Description

+   - To embed PHP within HTML, code a PHP tag by beginning with `<?php` and ending with `?>`. Then, you can enter PHP code between these tags.
+   - Although there are several ways to embed PHP in HTML, the technique above is the one that’s commonly used and recommended.
+   - If you want to do some processing before displaying the HTML, you embed PHP before the start of the HTML document.
+   - If you want to use PHP to display dynamic data within an HTML document, you embed PHP within the HTML.
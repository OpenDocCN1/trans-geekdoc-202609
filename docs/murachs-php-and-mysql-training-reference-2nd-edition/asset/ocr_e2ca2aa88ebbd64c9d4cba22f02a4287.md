# The util/main.php file

```
```php
<?php
// Get the document root
$doc_root = filter_input(INPUT_SERVER, 'DOCUMENT_ROOT');

// Get the application path
$uri = filter_input(INPUT_SERVER, 'REQUEST_URI');
$dirs = explode('/', $uri);
$app_path = '/' . $dirs[1] . '/' . $dirs[2] . '/';

// Set the include path
set_include_path($doc_root . $app_path);
?>
```
```

# The view/header.php file

```
```html
<!DOCTYPE html>
<html>
<!-- the head section -->
<head>
    <title>My Guitar Shop</title>
    <link rel="stylesheet" type="text/css"
          href="<?php echo $app_path ?>main.css" />
</head>

<!-- the body section -->
<body>
<header>
    <h1>My Guitar Shop</h1>
</header>
<main>
```
```

# Description

+   - General-purpose files like the tags.php file in figure 20-2 are often called *utility files* because they can be used by many applications.
+   - View files like the header.php and sidebar.php files in this figure are included by more than one of the other view files.

Figure 20-3    Include files for the Guitar Shop website (part 2 of 4)
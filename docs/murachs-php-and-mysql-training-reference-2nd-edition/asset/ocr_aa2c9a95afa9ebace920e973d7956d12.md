# How to set and get scalar variables

# Set a variable in a session

```
```php
$_SESSION['product_code'] = 'MBT-1753';
```
```

# Get a variable from a session

```
```php
$product_code = $_SESSION['product_code'];
```
```

# How to set and get arrays

# Set an array in a session

```
```php
if (!isset($_SESSION['cart'])) {
    $_SESSION['cart'] = array();
}
```
```

# Add an element to an array that's stored in a session

```
```php
$_SESSION['cart']['key1'] = 'value1';
$_SESSION['cart']['key2'] = 'value2';
```
```

# Get and use an array that's stored in a session

```
```php
$cart = $_SESSION['cart'];
foreach ($cart as $item) {
    echo '<li>' . $item . '</li>';
}
```
```

# How to remove variables from a session

# Remove a session variable

```
```php
unset($_SESSION['cart']);
```
```

# Remove all session variables

```
```php
$_SESSION = array();
```
```

# Description

+   - Once you start a session, you can use the autoglobal $_SESSION variable to set and get the user's data for a session. This variable is an associative array.
+   - If necessary, you can use the isset function to test if an element already exists in the $_SESSION array.
+   - You can use the unset function to remove an element from the $_SESSION array. However, don't use the unset function on the $_SESSION array itself as it can cause unpredictable results.
+   - You can set the $_SESSION array to an empty array to remove its contents.
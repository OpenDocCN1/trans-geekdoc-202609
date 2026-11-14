# **2. Include the configuration file:**

```
```php
<?php
require ('./includes/config.inc.php');
```
```

# **3. Validate the product type:**

```
```php
if (isset($_GET['type']) && ($_GET['type'] == 'goodies')) {
   $page_title = 'Our Goodies, by Category';
   $sp_type = 'other';
   $type = 'goodies';
} else { // Default is coffee!
   $page_title = 'Our Coffee Products';
   $type = $sp_type = 'coffee';
}
```
```

The product type can be one of only two values: *goodies* or *coffee*. The default product type to display will always be coffee, so the first part of the conditional just checks if `$_GET['type']` is set and if it equals *goodies*. For each condition, the page's title is determined, and the `$type` and `$sp_type` variables are assigned appropriate values. Two variables are required here because the Web site uses the term *goodies*, but the database uses the term *other*. If the same term were used in both cases, you could use just one variable. The `$sp_type` variable represents what the stored procedure expects.

The assignment of *coffee* to both `$sp_type` and `$type` in one line is possible as the assignment will occur from right to left. First, `$sp_type` is assigned the value *coffee*, then `$type` is assigned the value of `$sp_type`.

> > **note**
> >
> > I use “goodies” in the viewable site instead of “other” because it’s more meaningful to users and search engines (in theory).

# **4. Include the header file and the database connection:**

```
```php
include ('./includes/header.html');
require (MYSQL);
```
```

# **5. Call the stored procedure:**

```
```php
$r = mysqli_query($dbc, "CALL select_categories('$sp_type')");
```
```

This one line is all you need to invoke the stored procedure for either type. Because the `$sp_type` value will be a string, it must be quoted when you pass it to the stored procedure. The root SQL command is the same that would be run in the *mysql* client or phpMyAdmin:

```
CALL select_categories('coffee')
```

or

```
CALL select_categories('other')
```
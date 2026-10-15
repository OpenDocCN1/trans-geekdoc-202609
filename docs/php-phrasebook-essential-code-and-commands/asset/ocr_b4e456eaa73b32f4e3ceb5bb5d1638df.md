# Creating a Sortable Time Stamp

```
function timestamp($t = null) {
    if ($t == null) {
        $t = time();
    }
    return date('YmdHis', $t);
}
```

Sometimes, using date values with a database is not a clever thing. Different language versions of the database, its drivers, or the underlying operating system could cause some trouble when the regional date formats do not fit together.

```
<?php
function timestamp($t = null) {
    if ($t == null) {
        $t = time();
    }
    return date('YmdHis', $t);
}

echo 'Time stamp: ' . timestamp(time());
?>
```

*Converting a Date into a (Sortable) Time Stamp (timestamp.php)*

A potential alternative is the use of time stamps. Several different formats are available, but most of them have the following structure: year-month-day-hours-minutes-seconds. Using this value order, the string representation of the date can be easily sorted, which allows using it in databases.

To create such a time stamp, just a special call to date() is required. In the preceding code, this is encapsulated in a function for easy reuse.
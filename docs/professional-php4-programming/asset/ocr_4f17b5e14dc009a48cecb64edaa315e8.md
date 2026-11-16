```
```php
$sql .= " AND series.series_ID = $series";
}
if (!empty($query) && !empty($type)) {
    if ($type == 'isbn') {
        $sql .= " AND details.ISBN = '$query'";
    } elseif ($type == 'author') {
        $sql .= " AND author.auth_name LIKE '%$query%'";
    } elseif ($type == 'title') {
        $sql .= "AND title.book_title LIKE '%$query%'\\";
    }
}

$result = pg_exec($conn, $sql);

// Print the <option> rows for the <select> widget
if ($result && (pg_numrows($result) > 0)) {
    $row_counter = 0;
    while ($row = pg_fetch_array($result, $row_counter, PG_ASSOC)) {
        ?><tr>
            <td><u><?php echo(htmlspecialchars($row['book_title'])); ?></u></td>
            <td><?php echo(htmlspecialchars($row['auth_name'])); ?></td>
            <td><?php echo(htmlspecialchars($row['price'])); ?></td>
        </tr>
        <?php
        $row_counter++;
    }
} else {
    echo("<tr><td colspan=\"3\">No matches were found.</td></tr>\n");
}

pg_close($conn);
```
```

That's all there is to it.

# # Database Abstraction

In the last chapter, we also built a simple database abstraction layer. Now that we know about two different databases (MySQL and PostgreSQL), you probably understand the need for such an abstraction layer. We have already discussed the database abstraction layer in the previous chapter, so if you haven't already read the corresponding section in the previous chapter, you may want to do so now. In this section, we will revisit the database abstraction layer and implement the PostgreSQL version.

We already learned how to port a PHP database application from one database to the next in the last section, so we won't go into those details again. Instead, we'll start with a DB.php file that has already been ported to PostgreSQL. The changes from the MySQL version are highlighted:

```
```php
class DB
{
    /* Connection parameters */
```
```
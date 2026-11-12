```
```php
from phpbase.ad, phpbase.status,
phpbase.category
where phpbase.ad.customerID = $CustID and
phpbase.status.statusID =
phpbase.ad.status and
phpbase.ad.categoryID =
phpbase.ad.categoryID;");

if ($result) {
    if (mysql_num_rows($result) > 0) {
        while ($row = mysql_fetch_assoc($result)){
            print "<h2>{$row['headline']}</h2>\n";
            print "<b>Category:</b> " ;
            print "{$row['category_name']}]<br>\n";
            print "<b>item:</b> " ;
            print "{$row['item_name']}]<br>\n";
            print "<b>description:</b> " ;
            print "{$row['description']}<br>\n";
            print "<b>expires on:</b> " ;
            print "{$row['expiration_date']}]<br>\n";
            print "<b>price:</b> " ;
            $price = $row['price'] / 100;
            print "\$${price}<br>\n";
            print "<b>Status:</b> " ;
            print "{$row['status_desc']}]<p>\n";
            print "<hr>";
        }
    }
    mysql_free_result($result);
}
mysql_close();
?>
</body>
</html>
```
```
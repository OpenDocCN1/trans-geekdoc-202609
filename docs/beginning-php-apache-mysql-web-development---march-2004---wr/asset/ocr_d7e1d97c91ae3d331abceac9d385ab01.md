# Using Tables to Display Data

![](bbox=[0.15, 0.093, 0.915, 0.558])

Figure 4-3

# Try It Out

# Improving Our Table

The table may look pretty, but as in Chapter 3, it doesn't do us much good if we don't have our secret decoder ring to decipher what actors and directors were associated with our movies. You need to link your tables to pull this information.

+   1. Modify table2.php file as shown in bold text:

```
<php
$link = mysql_connect("localhost","root","$mysqlpass") or die(mysql_error());
mysql_select_db("wiley") or die(mysql_error());

$query = "SELECT
movie_name,
movie_director,
movie_leadactor
FROM
";
```

117
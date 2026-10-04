# Letting the User Edit the Database

![](bbox=[0.166, 0.087, 0.931, 0.54])

First, let concentrate on the people combos. Each combo lists all persons present in a `people` table.

```
<?php
$link = mysql_connect("localhost", "root", "*");
or die("Could not connect: " . mysql_error());
mysql_select_db('chapter6', $link) or die (mysql_error());
$peoplesql = "SELECT
FROM
`people`
*";
$result = mysql_query($peoplesql . " * " . mysql_error());
nor die("Invalid query: " . mysql_error());});
while($row = mysql_fetch_array($result , MYSQL_ASSOC)){
  $people[] = array($row['`people_id`'] => $row['`people_fullname`']);
}
?>
```

175
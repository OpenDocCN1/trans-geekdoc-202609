over using foreach. If these documents then have a uniform schema, the output is also simplified (see Figure 24.7).

```
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $result = $db->find();
    echo "<table><tr><th>name1</th><th>name2</th></tr>";
    foreach ($result as $id => $row) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
            htmlspecialchars($row["name1"]),
            htmlspecialchars($row["name2"])
        );
    }
} catch (Exception $x) {
    echo "Error: " . $x->getMessage();
}
?>
```

# Listing 24.4 Output All Data of the Collection ("mongo-read-all.php")

![](bbox=[0.14, 0.515, 0.785, 0.675])

# Figure 24.7 II Data Is Output

If you only want to access certain data, you must pass the corresponding search criteria to the find() method. MongoDB supports a very powerful query language here. However, the simplest way to search is to pass an associative array with properties and the desired values. The following query therefore searches for all data records that contain the "Value1" value in the Name1 property and correspondingly "Value2" in Name2:

```
$db = $conn->PHP->my_table;
$result = $db->find(
    ["name1" => "value1", "name2" => "value2"]
);
```
```
// Access now via $conn->PHP->my_table
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
}?>
```

# Listing 24.2 Creating a Collection ("mongo-create.php")

# 24.2.2 Insert

As already explained, MongoDB "thinks" in documents. Such documents are essentially objects with primitive properties—such as JSON in the JavaScript environment or an enriched StdClass in PHP (but in the latter case, remember that since PHP 8.2, dynamically adding class properties to StdClass is deprecated). Essentially, you create an associative, possibly nested array and insert that. With regard to a schema, you are therefore not bound or must ensure yourself that the data is structured consistently enough to enable a search.

Entering data is very simple; the collection offers the insertOne() method for this purpose. The data is transferred by reference.

```
<?php
require_once __DIR__ . "/vendor/autoload.php";
try {
$conn = new MongoDB\Client();
$db = $conn->PHP->my_table;
$data = [
"name1" => "value1",
"name2" => "value2"
];
$result = $db->insertOne($data);
echo "Data entered.<br />";
echo "<pre>". print_r($result, true). "</pre>";
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
?>
```

# Listing 24.3 Writing Data to the Database ("mongo-insert.php")

It becomes interesting if you look at the return value of insertOne(). As Figure 24.6 shows, you will receive a unique object ID oid of the type MongoDB\\BSON\\ObjectId.

This is similar to an autovalue in MySQL and other databases, but in this case it is a longer GUID and not a simple number. Later in this chapter, we will be able to access individual data records directly via this.
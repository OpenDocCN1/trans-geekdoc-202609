
Consider the following complete listing.

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $result = $db->find([
        "name1" => "value1", "name2" => "value2"
    ]);
    echo "<table><tr><th>name1</th><th>name2</th></tr>";
    foreach ($result as $id => $row) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
            htmlspecialchars($row["name1"]),
            htmlspecialchars($row["name2"]));
    }
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

Listing 24.5 Search and Output Collection Data ("mongo-read.php")

> **Note**
> 
> If you only expect one data record to be returned by the query (or you only need the first of all the documents returned), use `findOne()` instead of `find()`. The syntax remains the same.

An important note at the end: If you want to use the ID of a document as a search criterion, you must be careful. As you can see in Figure 24.6, there is an ID—not as a simple string value, but as an object of type `ObjectID`. You must therefore also specify an `ObjectID` instance when comparing criteria, including the complete namespace. The associated property is called `_id`:

```php
$result = $db->find([ "_id" => new MongoDB\BSON\ObjectID("abc123") ]);
```

## 24.2.4 Refresh

To update an existing entry, MongoDB uses the `updateOne()` and `updateMany()` methods, depending on whether you only want to change one or several data records. As an alternative to `updateOne()`, you can also use `replaceOne()`. This method replaces a complete data record; `updateOne()` in turn could add additional fields without destroying existing data. The functions first expect search criteria such as find() and findOne() and then the new documents that are to be used in place of those found. The syntax is somewhat special: the $set array key is used to specify the writing of values. MongoDB also offers a number of additional options here, such as special operators for the update. We will limit ourselves in the following listing to simply inserting another data record.

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $db->updateOne(
        ["name1" => "value1"], //Search criterion
        ["\$set" => ["name1" => "value3", "name2" => "value4"]] //New document
    );
    $result = $db->find();
    echo "<table><tr><th>name1</th><th>name2</th></tr>";
    foreach ($result as $id => $row) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
            htmlspecialchars($row["name1"]),
            htmlspecialchars($row["name2"])
        );
    }
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

Listing 24.6 Update Collection Data ("mongo-update.php")

Figure 24.8 shows the result.

![](img/ae7820c36e8f24c1623d26668b28e80e_694_0.png)

Figure 24.8 The Data Has Been Updated

## 24.2.5 Delete

Last but not least, data can also be deleted from the MongoDB database. After the previous explanations, the procedure is probably no longer a big surprise. The deleteOne() method is responsible for removing one data record, while deleteMany() removes several data records at once. A search criterion is again expected as a parameter. Listing 24.7 contains the complete code.

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $db->deleteOne(
        ["name1" => "value3"] //search criterion
    );
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

Listing 24.7 Delete Collection Data ("mongo-delete.php")

So that's the first insight into the PHP control of MongoDB. The online manual at http://php.net/mongodb contains a complete and detailed API description.

## 24.3 Application Example

To conclude this chapter—and the entire database section—we implement the well-known guestbook example based on MongoDB. The basic structure of the application remains the same, but the communication of the database is carried out according to the information on the previous pages. Only a few details have been changed.

### 24.3.1 Create Data Memory

We assume the default values for the application: the running MongoDB instance is on the current server, uses the default port, and needs no additional authentication. We create a new guestbook collection once in the PHP database (which may already exist from the previous examples). As discussed, we do not need a database schema.

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP;
    $db->createCollection("guestbook");
    echo "Database created.<br />";
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

Listing 24.8 The Collection Is Created ("gb-create.php")

### 24.3.2 Enter Data

Once the data store has been created, our usual HTML interface is used for data input. There is one special feature: MongoDB works on the basis of UTF-8, so we encode the input accordingly with utf8_encode().² From this we create a simple associative array, which we then send directly to MongoDB:

```php
$data = [
    "heading" => utf8_encode($_POST["Heading"]),
    "entry" => utf8_encode($_POST["Comment"]),
    "author" => utf8_encode($_POST["Name"]),
    "email" => utf8_encode($_POST["Email"]),
    "date" => time()
];
$result = $db->insertOne($data);
```

After insertion, we can use the getInsertedId() method to determine the generated autovalue. As previously explained, this is of the ObjectID type. However, the string representation is the ID value itself, so we can append it to a URL as follows:

```php
$id = $result->getInsertedId();
echo "Entry added. <a href=\"gb-edit.php?id=$id\">Edit</a>";
```

Consider the following complete listing.

```php
<html>
<head>
    <title>Guestbook</title>
</head>
<body>
    <h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
    isset($_POST["Email"]) &&
    isset($_POST["Heading"]) &&
    isset($_POST["Comment"])) {
    require_once __DIR__ . "/vendor/autoload.php";

    try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->guestbook;
    $data = [
        "heading" => utf8_encode($_POST["Heading"]),
        "entry" => utf8_encode($_POST["Comment"]),
        "author" => utf8_encode($_POST["Name"]),
        "email" => utf8_encode($_POST["Email"]),
        "date" => time()
    ];
    $result = $db->insertOne($data);
    $id = $result->getInsertedId();
    echo "Entry added.
    <a href=\"gb-edit.php?id=$id\">Edit</a>";
    } catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
    }
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /><br />
Email address <input type="text" name="Email" /><br />
Heading <input type="text" name="Heading" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

2 On systems that rely completely on UTF-8, this step may not be necessary. In this case, you can remove the call to utf8_encode()—as well as utf8_decode() in the following listing.

Listing 24.9 Data Can Be Entered ("gb-enter.php")

### 24.3.3 Output Data

The output of all data is child's play—even in comparison with the other database systems: find() returns all documents, and we iterate over them via foreach. The only thing we still need to consider is UTF-8 decoding of the data using utf8_decode().

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
require_once __DIR__ . "/vendor/autoload.php";
try {
$conn = new MongoDB\Client();
$db = $conn->PHP->guestbook;
$result = $db->find();
foreach ($result as $id => $row) {
printf("<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
<h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
urlencode(utf8_decode($row["email"])),
htmlspecialchars(utf8_decode($row["author"])),
htmlspecialchars(date("Y-m-d, H:i", $row["date"])),
htmlspecialchars(utf8_decode($row["heading"])),
nl2br(htmlspecialchars(utf8_decode($row["entry"])))
);
}
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
?>
</body>
</html>
```

Listing 24.10 The Guestbook Data Is Output ("gb-show.php")

### 24.3.4 Delete Data

To delete data, we need the `deleteOne()` method and a corresponding query. At this point, however, we would like to show an additional method of the MongoDB PHP Library API in action: `findOneAndDelete()`. The name is obviously self-explanatory. As the ID is transferred via a GET parameter when deleting, we can formulate this as follows:

```php
$db->findOneAndDelete(["_id" => new MongoDB\BSON\ObjectID($_GET["id"])]);
```

One important change compared to the other database systems presented in the book is the validation of the ID. This is not purely numerical but consists of both letters and digits. With `ctype_alnum()`, we can check whether only these characters are used.

The following listing shows the complete code for the deletion mask.

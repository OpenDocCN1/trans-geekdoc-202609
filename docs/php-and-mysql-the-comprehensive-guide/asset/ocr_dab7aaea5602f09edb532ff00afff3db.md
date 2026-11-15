```
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
}
?>
</body>
</html>
```

# Listing 24.11 Display of All Data with Deletion Option ("gb-admin.php")

# 24.3.5 Edit Data

Finally, the administration mask for the guestbook needs to be created. In particular, it is possible to edit an existing entry there. To display it for the first time, it must first be read out. To do this, we create a corresponding query using the previous example. The method used this time is findOne(), as the ID should be unique:

```
$row = $db->findOne(
    ["_id" => new MongoDB\\BSON\\ObjectID($_GET["id"])]
)
```

We also extend the input form so that the creation time is also supplied as part of the form. This simplifies updating later because we can then compile the complete new data record from form data:

```
// PHP
$Date = $row["date"];
<!-- HTML -->
<input type="hidden" name="Date" value="<?php
echo htmlspecialchars($Date);
?>" />
```

After sending the form, we create a new array, which then—using replaceOne()— replaces the old data record:

```
$data = [
    "heading" => utf8_encode($_POST["Heading"]),
    "entry" => utf8_encode($_POST["Comment"]),
    "author" => utf8_encode($_POST["Name"]),
    "email" => utf8_encode($_POST["Email"]),
    "date" => $_POST["Date"]
];
$db->replaceOne(["_id" => new MongoDB\\BSON\\ObjectID($_GET["id"])], $data);
```

And that's it! Listing 24.12 contains the complete coherent code.

```
<html>
<head>
<title>Guestbook</title>
```
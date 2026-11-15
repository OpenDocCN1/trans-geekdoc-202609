```
heading VARCHAR(1000),
entry VARCHAR(5000),
author VARCHAR(50),
email VARCHAR(100),
date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)");
$db->exec($sql);
echo "Table created.";
} catch (PDOException $e) {
echo 'Error: ' . htmlspecialchars($e->getMessage()));
}
?>
```

# Listing 18.6 The Table Is Created ("gb-create.php")

# 18.3.2 Enter Data

To enter the data, we use a simple HTML form in which the user can enter their data. We could determine the time of the entry with time(), but because the timestamp is automatically updated in the database during the update, we leave it alone. As there is only one INSERT command, we take the trouble to write the SQL command by hand, but of course we use placeholders. You can see the form in Figure 18.2.

```
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
try {
$db = new PDO("mysql:dbname=PHP;host=localhost",
"user",
"password");
$sql = "INSERT INTO guestbook
(heading,
entry,
author,
email)
VALUES (?, ?, ?, ?)";
```
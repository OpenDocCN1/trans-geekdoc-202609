The results of this form are passed along to insert_book.php, a script that takes the details,
performs some minor validations, and attempts to write the data into the database. The code
for this script is shown in Listing 11.4.

# Listing 11.4 insert_book.php—This Writes New Books into the Database

```
<!DOCTYPE html>
<html>
<head>
<title>Book-O-Rama Book Entry Results</title>
</head>
<body>
<h1>Book-O-Rama Book Entry Results</h1>
<?php

if (!isset($_POST['ISBN']) || !isset($_POST['Author']) 
    || !isset($_POST['Title']) || !isset($_POST['Price'])) {
    echo "<p>You have not entered all the required details.<br />\n    Please go back and try again.</p>";
    exit;
}

// create short variable names
$isbn=$_POST['ISBN'];
$author=$_POST['Author'];
$title=$_POST['Title'];
$price=$_POST['Price'];
$price = doubleval($price);

$db = new mysqli('localhost', 'bookorama', 'bookoramal23', 'books');

if (mysqli_connect_errno($db)) {
    echo "<p>Error: Could not connect to database.<br/>\n    Please try again later.</p>";
    exit;
}

$query = "INSERT INTO BOOKS VALUES (?, ?, ?, ?, ?)";
$stmt = $db->prepare($query);
$stmt->bind_param("sssdss", $isbn, $author, $title, $price);
$stmt->execute();

if ($stmt->affected_rows > 0) {
    echo "<p>Book inserted into the database.</p>";
} else {
    echo "<p>An error has occurred.<br/>\n    The item was not added.</p>";
}
n?>
```
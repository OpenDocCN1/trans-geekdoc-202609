```
$searchtype = \$_POST['searchtype'];
$searchterm = trim(\$_POST['searchterm']);
```

```
if (!$searchtype || !$searchterm) {
    echo <p>You have not entered search details.<br>
    Please go back and try again.</p>
    exit;
}
```

```
// whitelist the searchtype
switch ($searchtype) {
    case 'Title':
    case 'Author':
    case 'ISBN':
        break;
    default:
        echo <p>That is not a valid search type.<br>
        Please go back and try again.</p>
}
```

```
$db = new mysqli('localhost', 'bookoram', 
'bookoram23', 'books');
if ($mysqli_connect_errno()) {
    echo <p>Error: Could not connect to database.<br>
    Please try again later.</p>
}
```

```
$query = "SELECT ISBN, Author, Title, Price\nFROM BOOKS WHERE $searchtype = ?";
$stmt = $db->prepare($query);
$stmt->bind_param('s', $searchterm);
$stmt->execute();
$stmt->store_result();
```

```
$stmt->bind_result($isbn
```

```
while ($stmt->fetch()) {
    echo <p><strong>" . $title . ".</strong></p>
    echo "<br /> /Author: " . $author . ";
    echo "<br /> /ISBN: " . $isbn . ";
    echo "<br /> /Price: \" . number_format($price, 2) . ".</p>\n}
```
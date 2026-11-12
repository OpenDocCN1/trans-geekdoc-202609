```
</head>

<body>
<h2>List of Authors</h2>
<?php

// Part1 - select and retrieve all authors

$connection = new PDO("mysql:host=localhost;dbname=library", "root", "");
$connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);


$query = $connection->prepare("SELECT * FROM authors");
$query->execute();
$authors = $query->fetchAll(PDO::FETCH_ASSOC);


// Part 2 - Displaying results in an HTML table

if (count($authors) > 0) {
    echo "<table>";
    echo "<tr>
        <th>Edit</th>
        <th>ID</th>
        <th>Last Name</th>
        <th>First Name</th>
        <th>Email</th>
        <th>Biography</th>
```
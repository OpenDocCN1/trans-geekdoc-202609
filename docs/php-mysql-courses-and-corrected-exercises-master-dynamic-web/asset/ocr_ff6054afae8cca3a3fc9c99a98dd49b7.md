Each cell in this column will contain a link allowing the corresponding author ID to be transmitted to a new "delete_author.php" file. This file will be responsible for processing the deletion of the selected author. Here is the code of the display_authors.php script after it has been updated:

```
```html
<!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8"> <meta name="viewport" content="width=device-width,
initial-scale=1.0"> <title>List of Authors</title> <link rel="stylesheet" href="style_tab.css"> </head> <body>
<h2>List of Authors</h2>
<?php
// Database connection
$connexion = new PDO("mysql:host=localhost;dbname=bibliotheque", "root", "");
$connexion->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
// Prepare selection query
$query = $connexion->prepare("SELECT * FROM authors");
// Execute query
$requete->execute();
// Retrieve results
$authors = $requete->fetchAll(PDO::FETCH_ASSOC);
// Display results in HTML table
if (count($authors) > 0) {
```
```
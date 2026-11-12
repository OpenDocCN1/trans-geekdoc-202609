
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
</tr>";
foreach ($authors as $author) {
 echo "<tr>";
 echo "<td>{$author['author_id']}</td>";
 echo "<td>{$author['last_name']}</td>";
 echo "<td>{$author['first_name']}</td>";
 echo "<td>{$author['email']}</td>";
 echo "<td>{$author['biography']}</td>";
 echo "<td><a href='form_edit_author.php?author_id={$author['author_id']}'>
Edit</a></td>";
 echo "</tr>";
}
echo "</table>";
} else {
 echo "No author found.";
}
?>
</body>
</html>

These modifications add an "Edit" column to the author display table, where each line contains an "Edit" link pointing to a script named "form_edit_author.php" with the corresponding author ID passed as a parameter. Executing this code produces a result similar to the following:

![](img/caba2aa22f5409ba73dea47176330677_395_0.png)

Then create a new empty script named form_edit_author.php. When you click on the "Edit" link, you are redirected to this file "form_edit_author.php", and the corresponding author ID is transmitted via the URL.

![](img/caba2aa22f5409ba73dea47176330677_395_1.png)

## Retrieving and displaying data in a form

In the "form_edit_author.php" file that we previously created, we retrieve the author's ID to be updated from the URL using the $_GET superglobal. Then, we query the database to retrieve all the data of the author in question into an associative array.

- Retrieving data from the database

```php
<?php

// Retrieve the author ID to be updated
$author_id = $_GET['author_id'];

// Connect to database
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");
$connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

// Prepare selection query
$query = $connection->prepare("SELECT * FROM authors WHERE author_id =:author_id");

$query->bindParam(':author_id', $author_id);

// Execute request
$query->execute();

// Retrieve results
$author = $query->fetch(PDO::FETCH_ASSOC);
```

This PHP code is used to retrieve a specific author's information from the database and display it in a modification form. Here's a detailed explanation of the code:

$_GET['author_id']: This line retrieves the author identifier transmitted in the URL and is accessible via the $_GET superglobal variable.

The fetch(PDO::FETCH_ASSOC) method is used to retrieve the first row of query results in the form of an associative array. This array contains the author data retrieved from the database.

- Save recovered data in variables

Then, if there is an author with the identifier passed in URL, the data stored in the associative array $author in variables to facilitate their use.

```
// Check if author exists
if($author) {
// Retrieve author information
$lastname = $author['last_name'];
$firstname = $author['first_name'];
$email = $author['email'];
$password = $author['password'];
$biography = $author['biography'];
}
```

This code segment is used to extract author information retrieved from the database and store it in individual variables for later use in a modification form. For example: the line $lastname= $author['lastname']; extracts the value of the author's "last_name" column from the associative array $author and stores it in the variable $lastname. This means that the variable $lastname now contains the author's last name retrieved from the database.

- Displaying data in a form

Once this has been done, we display this data in a form similar to the one used to register a new author in the previous chapter.

```html
<form action="modify_author.php" method="POST">
<h2>Edit an Author</h2>
<label>Last Name:</label>
<input type="text" name="lastname" value="<?= $lastname ?>"><br>
<label>Firstname:</label>
<input type="text" name="firstname" value="<?= $firstname ?>"><br>
<label>Email:</label>
<input type="email" name="email" value="<?= $email ?>"><br>
<label>Password:</label>
<input type="password" name="password" value="<?= $password ?>"><br>
<label>Biography:</label>
<textarea name="biography"><?= $biography ?></textarea><br>
<input type="hidden" name="author_id" value="<?= $author_id ?>">
<input type="submit" value="Edit">
</form>
```

This HTML code represents a form for modifying author information in the database. Here's a detailed explanation:

The action attribute of the <form> tag specifies the URL of the PHP script that will process the form data once submitted. In this case, it's "modify_author.php" and the HTTP method used is POST.

Inside the <form> tag, a <h2> heading is used to indicate that the form is intended for author modification.

Next, a series of <input> fields and a <textarea> field are used to enter the author's new information. Each field has a name attribute that corresponds to the field name in the $_POST array when the form is submitted.

Current field values are defined with PHP, using <?= tags to display PHP variables containing the author's current data. For example: value="<?= $lastname ?>" sets the value of the variable $lastname in the form's lastname field.

The password field uses type="password", which hides the characters entered for security reasons.

A <input> field of type "hidden" is used to store the author ID, but is not visible to the user. This allows the author ID to be passed to the processing PHP script without the user having to enter it.

Finally, a "submit" button is used to submit the form and send the data to the PHP script for processing.

This form allows the user to modify an author's information and submit it for updating in the database.

Here is the complete code of the script form_edit_author.php :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Edit Author</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
<?php
// Retrieve the author ID to be updated
$author_id = $_GET['author_id'];
// Connect to database
$connection = new PDO("mysql:host=localhost;dbname=library", "root", "");

$connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

// Prepare selection query
$query = $connection->prepare("SELECT * FROM authors WHERE author_id = :author_id");

$query->bindParam(':author_id', $author_id);

// Execute request
$query->execute();

// Retrieve results
$author = $query->fetch(PDO::FETCH_ASSOC);

// Check if author exists
if($author) {
// Retrieve author information
$lastname = $author['last_name'];
$firstname = $author['first_name'];
$email = $author['email'];
$password = $author['password'];
$biography = $author['biography'];
}
?>
```

<form action="modify_author.php" method="POST">
<h2>Edit an Author</h2>
<label>Last Name:</label>
<input type="text" name="lastname" value="<?=$lastname ?>"><br>
<label>Firstname:</label>
<input type="text" name="firstname" value="<?=$firstname ?>"><br>
<label>Email:</label>
<input type="email" name="email" value="<?= $email ?>"><br>
<label>Password:</label>
<input type="password" name="password" value="<?=$password?>"><br>
<label>Biography:</label>
<textarea name="biography"><?=$biography ?></textarea><br>
<input type="hidden" name="author_id" value="<?= $author_id ?>">
<input type="submit" value="Edit">
</form>
</body>
</html>

At this point, if you select one of the links in the "Edit" column of the table displaying all authors, you will be redirected to a page similar to the one shown below:

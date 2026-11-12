
## Edit an Author

Last Name:
Lambert

First Name:
Maximilien

Email:
maximilien@gmail.com

Password:
******************

Biography:
Maximilien Lambert is an expert in computer technology

Edit

In addition to presenting the retrieved data, this form offers the possibility of making modifications before being submitted. When the form is validated, it is directed to the modify_author.php script, which is responsible for updating the data in the database using the information entered in the form. This is the code of the "modify_author.php" script after it has been updated:

```php
<?php
$author_id = $_POST['author_id']; // Author ID to be updated

// New author information
$new_lastname = $_POST['lastname'];
$new_firstname = $_POST['firstname'];
$new_email = $_POST['email'];
$new_password = $_POST['password'];
$new_biography = $_POST['biography'];

// Hash password
$password_hashed = password_hash($new_password, PASSWORD_DEFAULT);

// Database connection
$connection = new PDO("mysql:host=localhost;dbname=library","root","");

// Update request
$request = $connection->prepare("UPDATE authors SET last_name = :new_lastname, first_name = :new_firstname, email = :new_email, password = :new_password, biography = :new_biography WHERE author_id = :author_id");

// Bind parameters
$request->bindParam(':author_id', $author_id);
$request->bindParam(':new_lastname', $new_lastname);
$request->bindParam(':new_firstname', $new_lastname);
$request->bindParam(':new_email', $new_email);
$request->bindParam(':new_password', $password_hashed);
$request->bindParam(':new_biography', $new_biography);

// Execute query
$result = $request->execute();

// Check update success
if ($result) {
    echo "Information updated successfully";
} else {
    echo "An error occurred during the update.";
}
?>
```

This PHP code retrieves the data submitted by the author's modification form via the POST method. Using the $_POST superglobal, it first retrieves the author ID to be updated, along with new information such as first and last name, email, password and biography.

The password is then hashed using the password_hash() function for security reasons. A connection to the database is then established using PDO.

An update query is prepared to update the author's information in the "authors" table. The query parameters are linked to the values retrieved from the form.

The request is then executed and the result checked. If the update is successful, a success message is displayed. Otherwise, an error message is returned.

## Deleting data from a database

In this new section, we'll look at the process of deleting data from a database using PHP and MySQL. Deleting data is a critical operation that requires special care to avoid any unintentional loss or damage to existing data. We'll explore different methods for deleting records in a database table, with an emphasis on good security and efficiency practices. You'll learn how to build and execute deletion queries securely, as well as how to deal with any errors that may arise during the process.

We'll start by exploring the simplest method, which involves using a SQL DELETE query to delete individual records or sets of records based on certain criteria. We'll also discuss the precautions to be taken when using this method to avoid unintentional or unauthorized deletion of data.

To illustrate the process of deleting data, we will be further developing our "library" project. We'll be providing detailed explanations of how to carry out this operation safely and efficiently in your own projects.

In the "display_authors.php" page, which displays all authors, we'll introduce a new column called "Delete".

Each cell in this column will contain a link allowing the corresponding author ID to be transmitted to a new "delete_author.php" file. This file will be responsible for processing the deletion of the selected author. Here is the code of the display_authors.php script after it has been updated:

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
echo "<table>";
echo "<tr>
	<th>ID</th>
	<th>Name</th>
	<th>First name</th>
	<th>Email</th>
	<th>Biography</th>
	<th>Edit</th>
	<th>Delete</th>
</tr>";
foreach ($authors as $author) {
	echo "<tr>";
	echo "<td>{$author['author_id']}</td>";
	echo "<td>{$author['name']}</td>";
	echo "<td>{$author['firstname']}</td>";
	echo "<td>{$author['email']}</td>";
	echo "<td>{$author['biography']}</td>";
	echo "<td>
		<a href='form_modifier_auteur.php?id_auteur={$auteur['id_auteur']}'>
		Edit
		</a></td>";
echo "<td>
<a href='supprimer_auteur.php?id_auteur={$auteur['id_auteur']}'>
Delete
</a></td>";
echo "</tr>";
}
echo "</table>";
} else {
echo "No author found.";
}
?> </body> </html>
```

In the "display_authors.php" script, a new "Delete" column has been added to the author table. This column is identified by the "Delete" header, defined by the following code:

<th>Delete</th>

Each line in this column contains a link to the file "delete_author.php" with a delete action.

```php
<?php
echo "<td>
<a href='delete_author.php?author_id={$author['author_id']}'>
Delete
</a>
</td>";
```

This modification provides users with an additional feature to directly delete a specific author from the list displayed in the table. When accessing the "display_authors.php" script, you will get a result similar to the one shown below:

![](img/caba2aa22f5409ba73dea47176330677_410_0.png)

We then created a new empty file named "delete_author.php" at the root of the "library" project. If you currently click on the first link in the "Delete" column, you'll be taken to a blank page, as the "delete_author.php" file is still empty. However, note the URL that transmits the author ID in the "author_id" parameter.

![](img/caba2aa22f5409ba73dea47176330677_410_1.png)

Here is the code allowing the deletion of the author whose identifier is passed in the URL:

```php
<?php
// Check if the ID of the author to be deleted is present in the URL
if(isset($_GET['author_id'])) {
    // Retrieve author ID from URL
    $author_id = $_GET['author_id'];

    // Connect to database
    $connection = new PDO("mysql:host=localhost;dbname=library", "root", "");
    $connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    // Prepare deletion request
    $request = $connection->prepare("DELETE FROM authors WHERE author_id= :author_id");

    // Bind parameters
    $request->bindParam(':author_id', $author_id);

    // Execute query
    $result = $request->execute();

    // Verify successful deletion
    if ($result) {
        echo "The author has been successfully deleted.";
} else {
    echo "An error occurred during deletion";
}
} else {
    echo "No author ID specified for deletion";
}
?>
```

This PHP code performs the following operations:

- Check for the presence of the author ID to be deleted in the URL using the isset($_GET['author_id'])) condition. This ensures that an author ID has been correctly transmitted before proceeding with deletion.
- If the author ID is present in the URL, it is retrieved from the superglobal $_GET['author_id'].
- A database connection is established using PDO, with the appropriate credentials.
- A delete request is prepared to delete the author from the "authors" table, where the author ID corresponds to the one passed in the URL.
- The query parameters are bound to the author ID using the bindParam() method.
- The query is executed using the execute() method.

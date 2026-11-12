```
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
```
function validateMovieImageFile()
{
    $error_message = "";
    // ...
    return $error_message;
}
```

There are two top-level conditions we need to check before we can do anything with the uploaded file. We need to check that the $_FILES super global variable exists—it does not exist if the user chose not to select a file for upload. Also, we need to check there were no errors uploading the file. We can combine these checks in a single if statement, joining them with a logical AND (&&). Add the following code after $error_message = "":

```
$error_message = "";

// Check for $_FILES being set and no errors.
if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
{
    // ...
}
```

There is one other elseif condition that we need to check if the above if condition is false. We need to check if there was an error uploading the file. Since we do not know whether the condition failed because the $_FILES super global was not set or because the error was not equal to UPLOAD_ERR_OK, we need to check if the $_FILES is set before we can check to see if there was an error uploading the file. We also need to check that the user did upload a file. Again, we can combine all these into one elseif condition check combining these clauses using &&. PHP provides several constants to describe file errors. For our purposes, we can catch all the error conditions by testing that 'error' in our $_FILES array is NOT UPLOAD_ERR_OK. If we get into this elseif condition, it was because there was an error uploading the image file. if so, we need to set error_message to an appropriate error message stating there was an error uploading the file:

```
elseif (isset($_FILES) && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_NO_FILE
    && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_OK)
{
    $error_message = "Error uploading movie image file.";
}
```

So, our function looks like Listing 19.2 so far.
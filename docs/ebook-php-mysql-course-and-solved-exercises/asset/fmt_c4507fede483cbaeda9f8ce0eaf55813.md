
The `<select>` and `<option>` elements are used for drop-down lists. The `<select>` tag creates a drop-down list, while the `<option>` tag defines each option in the list. The `value` attribute of each option is the value sent to the server upon selection.

The `<input type="submit">` button allows the user to submit the form. The `value` attribute defines the text displayed on the button, in this case "Submit".

The `<form>` tag frames all the elements of the form. The `action` attribute specifies the URL of the data processing script (in this example, "processingform.php"), while the `method` attribute defines the HTTP method used to send the data (here, POST).

To retrieve data sent from an HTML form, PHP provides two methods: `GET` and `POST`, accessible via the superglobal variables `$_GET` and `$_POST`. These superglobals are used to retrieve the values of form fields, as we'll see later.

![Image](images/image-116.png)

### Data retrieval using the POST method in PHP

Once the form has been created in the `form.php` file, the process of retrieving the transmitted data is as follows:

When the user submits the form by clicking on the "Send" button, the data is sent to the server.

The server receives the data and transmits it to the processing file specified in the form's `action` attribute (in this case, "processingform.php").

In the `processingform.php` file, we retrieve the data transmitted via the `$_GET` or `$_POST` superglobal variables, depending on the method used in the form (in this example, POST).

We then process this data according to the needs of the application, such as validation, manipulation, storage in a database, and so on.

Here's an example of code for the file `processingform.php`, which assumes that the form uses the POST method to send data:

```php
<?php

 // Retrieve form data

 $lastname = $_POST["lastname"];

 $firstname = $_POST["firstname"];

 $email = $_POST["email"];

 $country = $_POST["country"];

 // Example of data processing (display)

 echo "Last Name : " . $lastname . "<br>";

 echo "First Name : " . $firstname . "<br>";

 echo "Email : " . $email . "<br>";

 echo "Country : " . $country . "<br>";

?>
```

In this code, variables such as `$lastname`, `$firstname`, `$email` and `$country` are used to store the values entered in the form fields. Each variable is associated with a specific key in the `$_POST` superglobal, which corresponds to the `name` attribute of the form fields.

Data is retrieved from the `$_POST` superglobal using the keys associated with the form fields. For example, `$_POST["lastname"]` retrieves the value of the field with the `name` attribute equal to "lastname".

Once the data has been retrieved, it is processed or displayed according to the needs of the application. In this example, the data is simply displayed on the screen using the `echo` function.

Each form field is displayed with its corresponding label to make it easier to read and understand the data entered by the user.

In short, this PHP code retrieves data submitted via an HTML form, stores it in appropriate variables and displays it on screen for demonstration or further processing.

To test this code, simply fill in the form in the `form.php` file and validate it by clicking on the "Send" button. You will obtain a result similar to the following:

![Image](images/image-117.png)

> **Warning**
>
> If you try to access the `processingform.php` file directly, you'll get errors similar to the following:
>
> ![Image](images/image-118.png)

In fact, when you try to access the file `processingform.php` directly, without passing through the form that sends data via the POST method, you'll get this type of error. This is because the PHP code in `processingform.php` attempts to access form field values from the `$_POST` superglobal, but since these values are not sent via POST when accessing the file directly, PHP cannot find them in `$_POST`.

In other words, when you access `processingform.php` directly, there's no data sent via POST, so indexes such as "last name", "first name", "email" and "country" don't exist in the `$_POST` superglobal. As a result, when PHP tries to access these non-existent indexes, it generates errors.

To avoid these errors, it's important to add tests to check whether the data is available in `$_POST` before attempting to retrieve it. Let's modify the code in the file `processingform.php` as follows:

```php
<?php

 // Check whether data has been sent via POST

 if ($_SERVER["REQUEST_METHOD"] == "POST") {

 // Retrieve form data

 $name = $_POST["lastname"];

 $firstname = $_POST["firstname"];

 $email = $_POST["email"];

 $country = $_POST["country"];

 // Example of data processing (display)

 echo "Name : " . $name . "<br>";

 echo "First name : " . $firstname . "<br>";

 echo "Email : " . $email . "<br>";

 echo "Country : " . $country . "<br>";

 }else{

 // Display an error message if the request method is not POST

 echo "Error: Access not authorized.";

 }

?>
```

With this approach, you first check whether data has been sent via POST using `$_SERVER["REQUEST_METHOD"] == "POST"`. If the request method is not POST, you can display an appropriate error message to inform the user.

In other words, if you try to access the `processingform.php` file directly, you'll get the message displayed in the `else` block; otherwise, if you go through the form in the `form.php` file, you'll get the data entered displayed.

For example:

![Image](images/image-119.png)

We can further optimize our code by performing a pre-check to ensure that all expected data is available in the `$_POST` variable. For example, we can check that all the required fields are filled in, and that the email field contains a valid email address, in line with email address standards (in particular, by checking for the presence of the "@" symbol). This will improve the robustness and reliability of our processing of the data entered in the form. Here is the updated code:

```php
<?php

 // Check whether data has been sent via POST

 if ($_SERVER["REQUEST_METHOD"] == "POST") {

 // Check if expected data is available in $_POST

 if (empty($_POST["lastname"])) {

 echo "Please enter your last name!";

 } elseif (empty($_POST["firstname"])) {

 echo "Please enter your first name!";

 } elseif (empty($_POST["email"]) || !filter_var($_POST["email"], FILTER_VALIDATE_EMAIL)) {

 echo "Please enter a valid email!";

 } elseif (empty($_POST["country"])) {

 echo "Please select your country!";

 } else {

 // Retrieve form data

 $lastname = $_POST["lastname"];

 $firstname = $_POST["firstname"];

 $email = $_POST["email"];

 $country = $_POST["country"];

 // Example of data processing (display)

 echo "Last Name : " . $lastname . "<br>";

 echo "First Name : " . $firstname . "<br>";

 echo "Email : " . $email . "<br>";

 echo "Country : " . $country . "<br>";

 }

 } else {

// Display an error message if the request method is not POST

 echo "Error: Access not authorized";

 }

?>
```

This PHP code first checks whether data has been sent via the POST method by checking the value of `$_SERVER["REQUEST_METHOD"]`. It then checks whether the expected data is available in `$_POST`. If any of the following conditions are not met, an appropriate error message is displayed:

*   If the "last name" field is empty, the message "Please enter your last name!" is displayed.
*   If the "first name" field is empty, the message "Please enter your first name!" is displayed.
*   If the "email" field is empty or does not contain a valid email address (checked using `FILTER_VALIDATE_EMAIL`), the message "Please enter a valid email!" is displayed.
*   If the "country" field is empty, the message "Please choose your country!" is displayed.

Quite a number of new things have been introduced to the script to allow us to perform validation of data. We shall go through each of these in turn. The first thing to note is that there is some PHP script before the XHTML form as we need to determine if the form has any missing fields before it is redisplayed. The following three variables are initialized to zero:

```
$booTitle = 0;
$booFirstname = 0;
$booSurname = 0;
```

Next, an ‘if’ construct determines if the form has been submitted:

```
if (isset($_POST["submit"]) ) {
```

The variables are used to record whether the form data items contain a value or not. As we have three form fields, we have three variables. Next, three ‘if’ constructs determine if the values of the form elements contain a value or not and if not set the value of the corresponding variable to 1:

```
if($_POST["strTitle"] == "Select . . .")
    $booTitle = 1;
if($_POST["strFirstname"] == NULL)
    $booFirstname = 1;
if($_POST["strSurname"] == NULL)
    $booSurname = 1;
```

The next part of the script outputs the (X)HTML form. Embedded within the form is the PHP script which will display the ‘error messages’ if the form field is null. The PHP scripts are:

```
<?php if ($booTitle) echo "Please select a title!" ?>
<?php if ($booFirstname) echo "Please enter a firstname!" ?>
<?php if ($booSurname) echo "Please enter a surname!" ?>
```

Finally, after the (X)HTML form we have some further PHP script which determines if the form has any missing data and if not displays a message that all is well:

```
if (!( $booTitle + $booFirstname + $booSurname) &&
    isset($_POST["submit"]) )
    echo "<p>All is well, you are " . $_POST["strTitle"] . " " .
    $_POST["strFirstname"] . " " . $_POST["strSurname"] . "</p>";
```

The output from the above script is shown in Figure 10.15.

# Retaining form data

The previous script works well, however it is far from perfect. You will note that, when you fail to complete one of the form fields and an error message is generated, all the data
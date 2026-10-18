These variables are used to hold the values of their corresponding form fields.

When the form is submitted, a number of ‘if’ constructs set variables either to indicate that no field data has been received or to hold the value of the data received:

```
if (isset($_POST["submit"]) ) {
    if($_POST["strTitle"] == "Select . . .")
        $booTitle = 1;
    else
        $strTitle = $_POST["strTitle"];
    if($_POST["strFirstname"] == NULL)
        $booFirstname = 1;
    else
        $strFirstname = $_POST["strFirstname"];
    if($_POST["strSurname"] == NULL)
        $booSurname = 1;
    else
        $strSurname = $_POST["strSurname"];
}
```

To indicate that a particular option has been selected, the keyword ‘selected’ needs to be included in the opening option tag:

```
<option selected>
```

This means that we need to check each option element to determine if the option was previously selected and if so output the text “selected”:

```
<option <?php if($_POST["strTitle"] == "Mr") echo "Selected" ?>>Mr</option>
<option <?php if($_POST["strTitle"] == "Miss") echo "Selected" ?>>Miss</option>
<option <?php if($_POST["strTitle"] == "Ms") echo "Selected" ?>>Ms</option>
<option <?php if($_POST["strTitle"] == "Mrs") echo "Selected" ?>>Mrs</option>
<option <?php if($_POST["strTitle"] == "Dr") echo "Selected" ?>>Dr</option>
```

This can be quite a problem if you have a lot of select options! Luckily things are much easier with input text fields. They simply require a new attribute called value which is set to the value you wish to be displayed:

```
<input type='text' name='name' value='value'>
```

| NOTE | Data retention with ‘password’ form elements is exactly the same as input text elements. |
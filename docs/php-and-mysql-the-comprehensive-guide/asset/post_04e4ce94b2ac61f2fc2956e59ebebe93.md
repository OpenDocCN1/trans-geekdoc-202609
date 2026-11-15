
Let's explain what happens here: Initially, it is assumed that the form must be displayed, which is why $ok is set to false. If, on the other hand, the form has just been sent, then the PHP script initially assumes that everything is OK ($ok = true). If no error occurs (if ($ok)), then the form data is output. However, if an error occurs (if (!$ok)), then the form itself is output. Of course, this also occurs if the page is called up directly without sending the form. This is why there is the if (!$ok) stand-alone query at the end of the script.

> **Tip**
> 
> In the event of an error, the form is displayed directly—without any feedback that there was an error at all. The following code snippet directly before `if ($ok)` fixes this:
> 
> if (!$ok) {
> echo "<p><b>Form incomplete</b></p>";
> }

## 13.3.2 Radio Buttons

If a group of radio buttons is a mandatory field, then one of the buttons must have been selected. This can be verified by a simple check of `$_GET["Field name"]` or `$_POST["Field name"]` as in the following listing.

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
	$ok = true;
	if (!isset($_POST["Salutation"]) ||
		!is_string($_POST["Salutation"])) {
		$ok = false;
	}
	if (!isset($_POST["FirstName"]) ||
		!is_string($_POST["FirstName"]) ||
		trim($_POST["FirstName"]) == "") {
		$ok = false;
	}
	if (!isset($_POST["LastName"]) ||
		!is_string($_POST["LastName"]) ||
		trim($_POST["LastName"]) == "") {
		$ok = false;
	}
	if (!isset($_POST["Email"]) ||
		!is_string($_POST["Email"]) ||
		trim($_POST["Email"]) == "") {
		$ok = false;
	}
	if (!isset($_POST["Promo"]) ||
	    !is_string($_POST["Promo"]) ||
	    trim($_POST["Promo"]) == "") {
	  $ok = false;
	}
	if (!isset($_POST["Comments"]) ||
	    !is_string($_POST["Comments"]) ||
	    trim($_POST["Comments"]) == "") {
	  $ok = false;
	}
}
```

Listing 13.10 The Radio Button Group Is a Mandatory Field (Excerpt from "form-validation-radiobuttons.php")

## 13.3.3 Checkboxes

The validation of a checkbox is carried out in the same way as the validation of radio buttons: It is only necessary to check whether a value has been passed to the PHP script for the form element. The following code (as always, changes are highlighted in bold) does this for the terms and conditions checkbox in our example.

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
  $ok = true;
  if (!isset($_POST["Salutation"]) ||
      !is_string($_POST["Salutation"])) {
    $ok = false;
  }
  if (!isset($_POST["FirstName"]) ||
      !is_string($_POST["FirstName"]) ||
      trim($_POST["FirstName"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["LastName"]) ||
      !is_string($_POST["LastName"]) ||
      trim($_POST["LastName"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Email"]) ||
      !is_string($_POST["Email"]) ||
      trim($_POST["Email"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Promo"]) ||
      !is_string($_POST["Promo"]) ||
      trim($_POST["Promo"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Comments"]) ||
      !is_string($_POST["Comments"]) ||
      trim($_POST["Comments"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Terms"]) ||
      !is_string($_POST["Terms"])) {
    $ok = false;
  }
}
```

Listing 13.11 The Checkbox Is a Mandatory Field (Excerpt from “form-validation-checkboxes.php”)

## 13.3.4 Selection Lists

At first glance, checking a selection list is similar to the previous checks. However, there are some special features here. With a selection list in which several elements are displayed at once (<select size="..." > or alternatively multiple selection lists), it is possible to submit the form so that nothing is selected. This looks different with a conventional selection list so that nothing is selected. This can be seen very clearly in the list in the following example:

```
<select name="Number">
    <option value="0">Please select</option>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
    <option value="4">4</option>
</select>
```

A list element is always activated here when the form is sent. You must therefore note in your PHP script which element corresponds to the _not filled in_ status. In the example, this is the top value with the value attribute 0. The following listing shows the corresponding query in context.

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
    $ok = true;
    if (!isset($_POST["Salutation"]) ||
        !is_string($_POST["Salutation"])) {
        $ok = false;
    }
    if (!isset($_POST["FirstName"]) ||
        !is_string($_POST["FirstName"]) ||
        trim($_POST["FirstName"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["LastName"]) ||
        !is_string($_POST["LastName"]) ||
        trim($_POST["LastName"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Email"]) ||
        !is_string($_POST["Email"]) ||
        trim($_POST["Email"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Promo"]) ||
        !is_string($_POST["Promo"]) ||
        trim($_POST["Promo"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Number"]) ||
        !is_string($_POST["Number"]) ||
        $_POST["Number"] == "0") {
        $ok = false;
    }
    if (!isset($_POST["Comments"]) ||
        !is_string($_POST["Comments"]) ||
        trim($_POST["Comments"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Terms"]) ||
        !is_string($_POST["Terms"])) {
        $ok = false;
    }
}
```

Listing 13.12 The Selection List Is a Mandatory Field (Excerpt from “form-validation-select-lists.php”)

> Tip
> 
> Once again, you will see the double check, first with isset() and second directly via the value in the selection list. This avoids embarrassing error messages if a joker tries to send a completely empty form (without a selection list) to your script.

With multiple selection lists, several elements are always displayed at once. If the user does not want to make any entries, then no information is sent to the web server. The check using isset() is therefore sufficient here.

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
    $ok = true;
    if (!isset($_POST["Salutation"]) ||
        !is_string($_POST["Salutation"])) {
        $ok = false;
    }
    if (!isset($_POST["FirstName"]) ||
        !is_string($_POST["FirstName"]) ||
        trim($_POST["FirstName"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["LastName"]) ||
        !is_string($_POST["LastName"]) ||
        trim($_POST["LastName"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Email"]) ||
        !is_string($_POST["Email"]) ||
        trim($_POST["Email"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Promo"]) ||
        !is_string($_POST["Promo"]) ||
        trim($_POST["Promo"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Number"]) ||
        !is_string($_POST["Number"]) ||
        $_POST["Number"] == "0") {
        $ok = false;
    }
    if (!isset($_POST["Section"]) ||
        !is_array($_POST["Section"])) {
        $ok = false;
    }
    if (!isset($_POST["Comments"]) ||
        trim($_POST["Comments"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Terms"]) ||
        !is_string($_POST["Terms"])) {
        $ok = false;
    }
}
```

Listing 13.13 The Multiple Selection List Is a Mandatory Field (Excerpt from "form-validation-multiselectlists.php")

### Tip

If you have a multiple selection list with several entries ("Please select" option, hyphens, etc.), then you must of course perform a somewhat more complex form of check. First, you need a helper function that determines whether an array only contains "garbage." In our example, these are empty strings and zeroes; adapt this to your requirements:

```
function array_empty($a) {
    if (!is_array($a)) {
        return true;
    }
    foreach ($a as $value) {
        if ($value != "" && $value != "0") {
            return false;
        }
    }
    return true;
}
```

The multiple selection list check is then called up as follows:

```
if (!isset($_POST["Section"]) ||
    !is_array($_POST["Section"]) ||
    array_empty($_POST["Section"])) {
    $ok = false;
}
```

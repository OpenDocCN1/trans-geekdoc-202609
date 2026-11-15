Let's explain what happens here: Initially, it is assumed that the form must be displayed, which is why $ok is set to false. If, on the other hand, the form has just been sent, then the PHP script initially assumes that everything is OK ($ok = true). If no error occurs (if ($ok)), then the form data is output. However, if an error occurs (if (!$ok)), then the form itself is output. Of course, this also occurs if the page is called up directly without sending the form. This is why there is the if (!$ok) stand-alone query at the end of the script.

> **Tip**
> 
> In the event of an error, the form is displayed directly—without any feedback that there was an error at all. The following code snippet directly before `if ($ok)` fixes this:
> 
> if (!$ok) {
> echo "<p><b>Form incomplete</b></p>";
> }

# 13.3.2 Radio Buttons

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
```
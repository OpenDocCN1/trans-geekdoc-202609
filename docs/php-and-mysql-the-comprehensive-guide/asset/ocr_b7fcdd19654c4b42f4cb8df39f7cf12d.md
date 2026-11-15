```
<h1>Form Data</h1>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST[
"Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Terms = (isset($_POST["Terms"]) && is_string($_POST["Terms"])) ?
$_POST["Terms"] : "";
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Comments = nl2br(htmlspecialchars($Comments));
$Terms = htmlspecialchars($Terms);
echo "<br>Salutation:</b> $Salutation<br />";
echo "<br>First name:</b> $Firstname<br />";
echo "<br>Last name:</b> $Lastname<br />";
echo "<br>Email:</b> $Email<br />";
echo "<br>Promo:</b> $Promo<br />";
echo "<br>Comments:</b> $Comments<br />";
echo "<br>Terms &amp; conditions:</b> $Terms<br />";
?>
```

Listing 13.5 Output of the Checkbox (Excerpt from “form-output-checkboxes.php”)

![](bbox=[0.14, 0.72, 0.62, 0.89])

Figure 13.6 The Terms and Conditions Have Been Accepted
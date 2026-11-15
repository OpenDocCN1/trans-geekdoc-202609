Listing 13.3 shows the code with which the contents of the text fields are output (see also Figure 13.4). It is simple for text and password fields, but there is a special feature for multiline text fields: line breaks are also possible within the text. These are converted correctly using the `nl2br()` PHP function.

> **Note**
> 
> When converting with `nl2br()`, you must first use `htmlspecialchars()` and only then replace line breaks with `<br />`. The reason is that if you did it in the reverse order, you would first get `<br />` and then, thanks to `htmlspecialchars()`, the characters `&lt;br /&gt;`, which is certainly not what you want.

```
<body>
<h1>Form Data</h1>
<?php
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
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Comments = nl2br(htmlspecialchars($Comments));
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Comments:</b> $Comments<br />";
?>
<h1>World Cup ticket service</h1>
<form method="post">
```

# Listing 13.3 Output of the Text Field Data (Excerpt from "form-output-textfields.php")

> **Tip**
> 
> You can access hidden form fields (`<input type="hidden" />`) in exactly the same way!
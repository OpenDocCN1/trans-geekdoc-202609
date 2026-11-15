
```php
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Comments = nl2br(htmlspecialchars($Comments));
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Comments:</b> $Comments<br />";
?>
```

### Listing 13.4 Output of the Radio Button (Excerpt from “form-output-radiobuttons.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_411_0.png)

### Figure 13.5 The Salutation Is Recognized

## 13.2.5 Checkboxes

Some HTML instructions recommend placing checkboxes into groups and giving each checkbox in the group the same name. However, this is nonsensical because there is no grouping of checkboxes. Each checkbox stands alone; HTML does not offer restrictions of the “Only three of these five checkboxes may be selected” type. You would have to use JavaScript for this.

Under this premise, it is easy to understand how access to a checkbox works with PHP: $_GET["Field"] or $_POST["Field"] contains the value of the checkbox if it has been selected. If it has not been selected, the array element does not exist.

> **Tip**
>
> There are always people who omit the value attribute from checkboxes. In this case, browsers transfer the "on" value if the checkbox has been selected. Nevertheless, you should not rely on this and should always use the value attribute instead.

```php
<h1>Form Data</h1>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"])) ?
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
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Comments = nl2br(htmlspecialchars($Comments));
$Terms = htmlspecialchars($Terms);
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Comments:</b> $Comments<br />";
echo "<b>Terms &amp; conditions:</b> $Terms<br />";
?>
```

### Listing 13.5 Output of the Checkbox (Excerpt from “form-output-checkboxes.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_412_0.png)

### Figure 13.6 The Terms and Conditions Have Been Accepted

## 13.2.6 Selection Lists

Even with selection lists, there is very simple access using $_GET["Field name"] or $_POST["Field name"]. You receive the value (value attribute) of the list element (<option>) that has been selected by the user.

> **Tip**
>
> Again, the question arises: What happens if there is no value attribute? The answer in this case is that the label is used—that is, what is between <option> and </option>. The same applies here: do not rely on this; instead, always set the value attribute for each list element.

```php
<h1>Form Data</h1>
<?php

$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Number = (isset($_POST["Number"]) && is_string($_POST["Number"])) ?
$_POST["Number"] : "";
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$AGB = (isset($_POST["AGB"]) && is_string($_POST["AGB"])) ?
$_POST["AGB"] : "";
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Number = htmlspecialchars($Number);
$Comments = nl2br(htmlspecialchars($Comments));
$AGB = htmlspecialchars($AGB);
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Number of tickets:</b> $Number<br />";
echo "<b>Comments:</b> $Comments<br />";
echo "<b>Terms &amp; conditions:</b> $AGB<br />";
?>
```

### Listing 13.6 Output of the Selected List Element (Excerpt from "form-output-selectlists.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_414_0.png)

### Figure 13.7 The Data from the Selection List

The situation is slightly different with multiple selection lists as several values can be returned at once. You may have already noticed a special feature in the HTML code of the selection list. It is printed here once again:

```html
<select name="Section[]" size="4" multiple="multiple">
<option value="north">North</option>
<option value="south">South</option>
<option value="west">West</option>
<option value="east">East</option>
</select>
```

The name of the list therefore ends with []. You may have guessed what this is intended to do: It makes it clear to PHP that this is a multiple selection list and that the data from it should be stored in an array. And that's the whole trick: In $_GET["field name"] or $_POST["field name"], multiple lists contain an array with the values of all selected list elements. (We can therefore dispense with the is_string() check and use is_array() instead!) The code in the following listing reads this data.

```php
<h1>Form Data</h1>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Number = (isset($_POST["Number"]) && is_string($_POST["Number"])) ?
$_POST["Number"] : "";
$Section = (isset($_POST["Section"]) && is_array($_POST["Section"])) ?
$_POST["Section"] : [];
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Terms = (isset($_POST["Terms"]) && is_string($_POST["Terms"]))
? $_POST["Terms"] : "";
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Number = htmlspecialchars($Number);
$Section = htmlspecialchars(implode(", ", $Section));
$Comments = nl2br(htmlspecialchars($Comments));
$Terms = htmlspecialchars($Terms);
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Number of tickets:</b> $Number<br />";
echo "<b>Section:</b> $Section<br />";
echo "<b>Comments:</b> $Comments<br />";
echo "<b>Terms &amp; conditions:</b> $Terms<br />";
?>
```

### Listing 13.7 Output of the Selected List Elements (Excerpt from "form-output-multiselect-lists.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_415_0.png)

### Figure 13.8 Now It Works with the Multiple List

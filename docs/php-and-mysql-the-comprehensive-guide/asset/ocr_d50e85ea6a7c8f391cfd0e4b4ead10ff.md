# # 13.4.1 Preparations

To be able to implement the prefiling as easily as possible, small changes are necessary in the previous script. It is clear what needs to be done: The previous form entries must be evaluated and possibly entered into the form. For this reason, the script needs easy access to what the user has or has not entered. Exactly this information is already read out:

```
```php
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
$Number = (isset($_POST["Number"]) && is_string($_POST["Number"])) ?
$_POST["Number"] : "";
$Section = (isset($_POST["Section"]) && is_array($_POST["Section"])) ?
$_POST["Section"] : [];
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Terms = (isset($_POST["Terms"]) && is_string($_POST["Terms"])) ?
$_POST["Terms"] : "";
```
```

This is very practical. If the user has selected one of the radio buttons for the salutation,
this information is in $Salutation. If nothing was clicked, this information is also in
$Salutation because the variable then contains an empty character string. This data is
only determined if the form has been completed in full. However, we also need this
data if there are errors in the form. For this reason, the complete block is moved to the
beginning of the PHP code. It then continues depending on the field type.

# # 13.4.2 Text Fields

For the single-line text fields—that is, <input type="text" /> and <input type="pass-
word" />—the prefilled value is in the value attribute. However, it would be a fatal mis-
take to use a construct like the following:

```
```html
<input type="text" name="Field " value=""><?=$Field?> />
```
```

What would happen if a user had previously entered, for example, ">><PHP<<" in the
field? This would result in the following HTML code:

```
```html
<input type="text" name="Field " value=""><PHP<<"" />
```
```
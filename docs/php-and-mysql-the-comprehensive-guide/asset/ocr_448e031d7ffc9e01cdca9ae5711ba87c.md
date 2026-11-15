```
```php
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
```
```

# Listing 13.11 The Checkbox Is a Mandatory Field (Excerpt from “form-validation-checkboxes.php”)

# 13.3.4 Selection Lists

At first glance, checking a selection list is similar to the previous checks. However, there are some special features here. With a selection list in which several elements are displayed at once (<select size="..." > or alternatively multiple selection lists), it is possible to submit the form so that nothing is selected. This looks different with a conventional selection list so that nothing is selected. This can be seen very clearly in the list in the following example:

```
```html
<select name="Number">
    <option value="0">Please select</option>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
    <option value="4">4</option>
</select>
```
```

A list element is always activated here when the form is sent. You must therefore note in your PHP script which element corresponds to the _not filled in_ status. In the example, this is the top value with the value attribute 0. The following listing shows the corresponding query in context.

```
```html
<body>
<?php
$ok = false;
```
```
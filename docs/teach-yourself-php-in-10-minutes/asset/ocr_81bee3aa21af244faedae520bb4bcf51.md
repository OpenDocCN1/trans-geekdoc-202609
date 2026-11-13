# # Highlighting Fields That Require Attention

Rather than bombard the user with a list of warning messages, it's more user-friendly to highlight the fields in the form that require attention.

The technique to use here is very similar to the previous example, but rather than append each warning message to $err , you should give each field its own warning text. If you use an array of warnings, it's simple to see whether the form has been successfully validated by counting the elements in $warnings .

You write each rule to add an element to $warnings if validation of that field fails, as shown in the following example:

```
if (!eregi("^[^@]+@([a-z\-]+\.)+[a-z]{2,4}$",
    $_POST["email"]))
$warnings["email"] = "Invalid Format";
```

Then in the form itself, you can display this warning text next to the corresponding field:

```
<TR>
<TD>Email Address</TD>
<TD><INPUT TYPE=TEXT SIZE=30 NAME="email"
VALUE="<?php echo $_POST["email"]; ?>"></TD>
<TD><b><?php echo $warnings["email"]; ?></b></TD>
</TR>
```

Listing 13.2 shows a revised register.php file that uses this technique to highlight missing or invalid field values.

# ## Listing 13.2. Form Validation Using Inline Warnings

```
<?php

$required = array("name" => "Your Name",
    "email" => "Email Address");

foreach($required as $field => $label) {
    if (!$_POST[$field]) {
    $warnings[$field] = "Required";
    }
}

if ($_POST["email"] &
```
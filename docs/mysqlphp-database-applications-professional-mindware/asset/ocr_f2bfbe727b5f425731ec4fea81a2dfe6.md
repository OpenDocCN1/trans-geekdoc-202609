All the expected attributes should be passed to the function. Most of the other functions look similar to this one, the only real exceptions being the checkbox and radio button.

# **CHECKBOX_FIELD()**  This function creates an HTML checkbox.

```
function checkbox_field ($name="", $value="", $label="", $match="")
{
    $checked = ($value == $match || $label == $match) ? "checked" : "";
    $output = <<<EOQ
<nobr><input type=checkbox name="$name" value="$value" $checked>
$label</nobr>
EOQ;
    return $output;
}
```

The only thing that may be of interest in this function is how you should note in your function call if a checkbox is to be checked by default. You do this by adding an argument called $match. If $match equals either $label or $value it will be checked by default. The radio_field function works in the same way.

# **FUNCTIONS FROM /BOOK/FUNCTIONS/TABLES.PHP**

Until style sheets are a reliable means for positioning pieces of a Web page, it is likely that you'll be using tables extensively. These functions make creating tables easier.

# **START_TABLE()**  This function creates an opening <table> tag.

```
function start_table ($atts="")
{
    $attlist = get_attlist($atts);
    $output = <<<EOQ
<p>
<table $attlist>
EOQ;
    return $output;
}
```

Again, this function calls the get_attlist() function to add attributes to the opening table tag. Add an array of attributes to the function call to have attributes added to the resulting tag.

# **END_TABLE()**  This function creates the closing </table> tag.
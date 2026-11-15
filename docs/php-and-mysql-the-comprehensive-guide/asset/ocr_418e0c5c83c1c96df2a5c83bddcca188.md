```
}
?>2</option>
<option value="3"<?php
if ($Number == "3") {
    echo " selected=\"selected\"";
}
?>3</option>
<option value="4"<?php
if ($Number == "4") {
    echo " selected=\"selected\"";
}
?>
?>4</option>
</select><br />
```

# Listing 13.18 Selection Lists Are Prefilled (Excerpt from "form-prefill-selectlists.php")

With multiple selection lists (<select multiple>), this is a little more difficult as there is not just one value, but several possible ones. Fortunately, PHP includes the in_array()function,4 which checks whether an element is in an array. And the prefilling of a multiple selection list works in exactly the same way: For each element, it must be checked whether the value is in the array that was read from $_GET or $_POST.

> **Note**
> 
> Now you also understand why we have declared $Section as an empty array if the user has not selected anything. The in_array() function only works with arrays, but also with empty ones. We have therefore avoided an error message at this point by programming with foresight.

```
Desired section in the stadium
<select name="Section[]" size="4" multiple="multiple">
<option value="north"<?php
if (in_array("north", $Section)) {
    echo " selected=\"selected\"";
}
?>
>>North</option>
<option value="south"<?php
if (in_array("south", $Section)) {
    echo " selected=\"selected\"";
}
?>
>>South</option>
<option value="east"<?php
if (in_array("east", $Section)) {
```

4 You can learn (almost) everything about arrays in Chapter 8.
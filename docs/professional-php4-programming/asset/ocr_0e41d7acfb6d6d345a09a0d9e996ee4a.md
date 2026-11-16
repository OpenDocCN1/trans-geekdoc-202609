The email_me field is a checkbox. The value from a checkbox variable has to be dealt with carefully. If the checkbox is checked when the form is submitted, the value will be the value attribute of the input tag. If no value is specified then the checkbox variable is set to "on". If the checkbox is left unchecked, the value will be blank or null, not "off". Hence, we have to work a bit harder to handle checkboxes. We will use an if statement to test the value of the checkbox variable and handle it accordingly:

```
<?php
if ($email_me == "Yes") {
    echo $email_me;
} else {
    echo("No");
}
?>
</td>
<tr>
<td>Cities where I can work</td>
<td>
```

The last field is a list box. This is the most complex input to handle, especially if the multiple attribute is set. Recall that the input variable for multiple list boxes has to be an array. Here we use the foreach to loop through the $pref_cities array:

```
<?php
foreach($pref_cities as $city){
    echo($city . "<br>");
}
?>
</td>
</tr>
</table>
```

The above script results in an output like this:

![](bbox=[0.08, 0.65, 0.88, 0.89])
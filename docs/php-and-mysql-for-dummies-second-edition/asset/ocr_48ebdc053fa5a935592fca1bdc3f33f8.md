```
```php
{
    if (!ereg("^[A-Za-z '-]{1,50}$",$_POST[$field]) )
    {
        $bad_format[$field] = "bad";
    }
}
elseif ($field == "phone")
{
    if(!ereg("^[0-9]( -)[7,20]([(xx)](ext)|(ex))?[ -]?[0-9][1,7])?$",$value) )
    {
        $bad_format[$field] = "bad";
    }
}
// end of foreach for $_POST
/* if any fields were not okay, display error message and form */
if (@sizeof($blank_array) > 0 or @sizeof($bad_format) > 0)
{
    if (@sizeof($blank_array) > 0)
    {
        /* display message for missing information */
        echo "<b>You didn't fill in one or more required fields.
            You must enter:</b><br>";
        /* display list of missing information */
        foreach($blank_array as $field => $value)
        {
            echo "&nbsp;&nbsp;&nbsp;{$label_array[$field]}<br>";
        }
    }
    if (@sizeof($bad_format) > 0)
    {
        /* display message for bad information */
        echo "<b>One or more fields have information that appears to
            be incorrect. Correct the format for:</b><br>";
        /* display list of bad information */
        foreach($bad_format as $field => $value)
        {
            echo "&nbsp;&nbsp;&nbsp;{$label_array[$field]}<br>";
        }
    }
}
/* redisplay form */
echo "<p><hr>
<form action='checkAll.php' method='POST'>
<center>
<table width='95%' border='0' cellspacing='0' cellpadding='2'>
<tr><td align='right'><B>{$label_array['first_name']}:</B><br></td>
    <td><input type='text' name='first_name' size='65' maxlength='65'
            value='$first_name' > </td>
</tr>
<tr><td align='right'><B>{$label_array['last_name']}:</B></td>
    <td> <input type='text' name='last_name' size='65' maxlength='65'
            value='$last_name' > </td>
</tr>
```
```
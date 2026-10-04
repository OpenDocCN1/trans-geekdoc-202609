# 232 Part III: Simple Applications

+   - "<b>Date blocked:</br> $block_dt <br>"
- "<b>Date released:</br> $release_dt <br>"
- "<b>Date Last Modified:</br> $modify_dt <br>"
- hidden_field("old_domain"

);

UL_LIST() This function turns an array or a string into an unordered HTML list.

```
function ul_list($values=")
{
    $output .= "<ul>\n";
    if (is_array($values))
    {
        while (list($value,$values))
        {
            $output .= \= <li>$value</li>\n";
        }
    } else
    {
        $output .= "<li>$values</li>\n";
    }
    $output .= "</ul>\n";
    return $output;
}
```

With this function you can create a bulleted list. Most frequently, an array will be passed to the function, each member of which will be prepended with a <li> tag. The function also prepend a string with <li> if the contents of $Values is a string.

# FUNCTIONS /BOOK/FUNCTIONS/FORMS.PHP

Most of these functions are fairly straightforward and don't require any explanation. We will show a couple of them for examples.

# TEXT_FIELD() This prints out an HTML text field.

```
function text_field($name="", $value="", $size=10, maxlen="")
{
    $output = <<E00
<input type=text name="$name" value="$value" size="$size" maxlength="$maxlen">
E00
    return $output;
}
```
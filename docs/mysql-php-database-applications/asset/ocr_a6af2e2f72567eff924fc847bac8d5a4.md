```
function paragraph ()
{
    static $_defaults = array(
        'values' => array()
        . 'allowed' => array('Common','align')
        . 'start' => NULL
    );
    static $_simple = array('values');
    $p = func_get_args();
    $p = parse_arguments($p, $_simple, $_defaults);
    $attlist = get_attlist($p);
    $output = "\n<p $attlist>\n";
    if ($p['start'] !== NULL)
    {
        return $output;
    }
    $output .= implode("\n",(array)$p['values'])
        .end_paragraph($p)
    ;
    return $output;
}
```

The first thing to understand about this function is that by default it will print not only the opening <p> tag along with its attributes, but also the closing </p> tag and everything that could occur between the two. This could include anchor tags, image tags, or just about anything else. The following function call would work just fine, and in fact is used within the survey application:

```
print paragraph(anchor_tag('block_domain.php','Return to Domain
List'));
```

One argument exists in this function call, and that's another function call with two arguments. In effect, when one function call is nested inside another, PHP executes the internal one first. So first the anchor_tag() function is called, creating a string like '<a href="admin_block.php">'. Then the outer function is executed, so the call to the paragraph function will actually look something like this:

```
print paragraph('<a href="admin_block.php">Return to Domain
List</a>');
```

Note how flexible this becomes. By looping through the number of arguments you can send any number of additional function calls to the paragraph function. And you can happily mix text and function calls together, because by the time
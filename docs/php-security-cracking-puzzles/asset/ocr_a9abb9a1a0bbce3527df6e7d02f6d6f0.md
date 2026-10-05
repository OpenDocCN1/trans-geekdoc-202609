# 128 Part II: Solutions

```
$Pattern = "^##(http://)?[-a-z0-9_\.]+\(([-a-z0-9_]+\]+\.(html|php|pl|cgi))?\([-a-z0-9_@&\;=\=\-!/\*\$]+)?$#i";
if (preg_match($Pattern, $_POST['name']))
{
    echo "The URL format is correct.";
}
else
{
    echo "The URL format is incorrect.";
}
?>
```

# 11.2.7. Converting Text URLs to Hyperlinks

Text URLs can be converted to hyperlinks using the regular expression considered in Section 11.2.6. The complete code using this expression is shown in Listing 11.2.8.

Listing 11.2.8. Converting text URLs to hyperlinks

```
<?php
// Extracting the contents of the index.htm file
$Scontent = file_get_contents("text.txt");
$Scontent = nl2br($Scontent);

// The regular expression
$Pattern = "#http://[-a-z0-9_\.]+\(([-a-z0-9_]+\]+\.(html|php|pl|cgi))?\([-a-z0-9_@&\=\=\-!/\*\$]+)?$#i";

$Pattern = "#http://[-a-z0-9_\.]+\(([-a-z0-9_]+\]+\.(html|php|pl|cgi))?\([-a-z0-9_@&\=\=\-!/\*\$]+)?$#i";
$replacement = "<a href=\\\0\\</a>";

// Extracting the HTML page title
echo preg_replace($Pattern, $replacement, $Scontent);
?>
```
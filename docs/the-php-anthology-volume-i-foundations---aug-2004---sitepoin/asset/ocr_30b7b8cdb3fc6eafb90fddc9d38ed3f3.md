```
}
// Generates the bottom of the page
function addFooter($page, $year, $copyright)
{
    $page .= <<<EOD
<div align="center">&copy; $year $copyright</div>
</body>
</html>
EOD;
    return $page;
}

// Initialize the page variable
$page = '';

// Add the header to the page
$page = addHeader($page, 'A Procedural Script');

// Add something to the body of the page
$page .= <<<EOD
<p align="center">This page was generated with a procedural
script</p>
EOD;

// Add the footer to the page
$page = addFooter($page, date('Y'), 'Procedural Designs Inc.');

// Display the page
echo $page;
?>
```

Of note in this example is our first look at **heredoc syntax**, which is an alternative method of writing PHP strings. Instead of surrounding the text with quotes, you begin it with <<<EOD and a new line, and end it with a new line and then EOD. The PHP Manual[4] can offer more detail on this if you're curious.

This procedural example uses two functions, addHeader and addFooter, along with a single global variable, $page. Perhaps this isn’t a far cry from procedural scripts you’ve written yourself; maybe you’ve included in every page a file that contains functions such as addHeader and addFooter.

[4] http://www.php.net/types.string#language.types.string.syntax.heredoc
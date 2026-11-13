The $feed variable is a placeholder for the generated XML that is constructed once the RSS feed is successfully loaded. The RSS feed is read in using the simplexml library that is shipped with PHP 5. This isn't the only XML parsing library available for PHP, but it is the most efficient and easiest to use.

```
$feed = "";
$xml = simplexml_load_file($rssFeed);
```

At this point, you can begin building the foreach loop, which is responsible for constructing the XML document passed back to the ActionScript.

```
$feed .= "<items>\n";

foreach($xml->item as $item)
{
    $desc = $item->description;

    $desc = preg_replace('/[[...\\]]/', '', $desc);

    $feed .= "  <entry>\n";
    $feed .= "    <name>" . $item->title . "</name>\n";
    $feed .= "    <desc><![CDATA[" . $desc . "]]></desc>\n";
    $feed .= "  </entry>\n";
}

$feed .= "</items>\n";
```

The loop takes each element of the XML and loops through the item nodes.

You will notice the description is assigned to a $desc variable. The reason for this is because the description needs to be cleaned before it is returned. The cleaning process is accomplished using preg_replace(), a regular expression function that removes unescaped and improper characters.

```
$desc = preg_replace('/[[...\\]]/', '', $desc);
```

This book does not provide an in-depth walkthrough on regular expressions (regex); however, there is a very good guide found at http://php.net/manual/en/reference.pcre.pattern.syntax.php.

The last portion of the PHP code sets the header type and outputs the XML to ActionScript.

```
header('Content-type: text/xml');
print '<?xml version="1.0" encoding="UTF-8"?>' . "\n";
print $feed;
```

You will notice the PHP required to build the RSS application is not in depth; a lot of that is due to simplexml being such a great library. This example could be extended to pull in more of the information contained within the RSS feed. For example, you could display the title of the entry, the date, and even the URL where the original entry is located.
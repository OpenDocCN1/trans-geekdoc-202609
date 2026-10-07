# ...cont'd

```
<html><head><title>Read DOM</title></head><body>
```

```
?php

# load an xml document into the DOM
$dom = new DomDocument();
$dom -> load("books.xml");

# print the root element name
echo("Root element name is: ");
echo($dom -> documentElement -> nodeName);
echo("<hr>");

## print a list of all topics
echo("Topics include:<ul">");
$topics = $dom -> getElementsByTagName("topic");
foreach($topics as $node) {
	echo("<li>" . $node -> textContent . "</li>");
}
echo("</ul>");

?>

</body></html>
```

![](bbox=[0.195, 0.078, 0.273, 0.178])

![](bbox=[0.288, 0.603, 0.943, 0.928])
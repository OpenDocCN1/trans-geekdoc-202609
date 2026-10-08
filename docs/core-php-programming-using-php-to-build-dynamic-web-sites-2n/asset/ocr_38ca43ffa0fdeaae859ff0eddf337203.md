# Core PHP Programming

![](bbox=[0.281, 0.096, 0.803, 0.456])

?

```
// create parser
if(!$parser = xml_parser_create())
{
    print("Could not create parser!<BR>\n");
    exit();
}

// get entire file
$data = implode(file("example.xml"), "");

// parse file into array
xml_parser_into_struct($parser, $data, &$structure, &$index);

// destroy parser
xml_parser_free($parser);

print("<Structure:<BR>\n");
print("<TABLE ORDER=\"1\">\
");
print("<TR>\n");
print("<TH>Tag</TH><TH>Type</TH><TH>Level</TH>\n");
print("<TH>-type</TH><TH>-level</TH>\n");
print("<TH>-level</TH><TH>\n
");
print("<TR><TH>Value</TH><TR>\n");

foreach($structure as $s) {
    print("<TR>\n");

    print("<td>${$s["tag"]}</td><td>\n");
    print("<td>${$s["type"]}</td><td>\n");
    print("<td>${$s["level"]}</td><td>\n");
    print("<td>${$s["value"]}</td><td>\n");

    print("<TR>\n");
}
```

IT-SC 513
```
}

//destroy parser
xml_parser_free($this->parser);
}
function cdataHandler($parser, $data) {
    print($data);
}
function startHandler($parser, $name, $attributes) {
    switch ($name) {
        case 'EXAMPLE':
            print("<HR>\n");
            break;
        case 'TITLE':
            print("<B>\n");
            break;
        case 'CODE':
            print("<PRE>\n");
            break;
        default:
            //ignore other tags
    }
}
function endHandler($parser, $name) {
    switch ($name) {
        case 'EXAMPLE':
            print("<HR>\n");
            break;
        case 'TITLE':
            print(\</B>\n");
            break;
        case 'CODE':
            print(\</PRE>\n");
            break;
        default:
            //ignore other tags
    }
}
```
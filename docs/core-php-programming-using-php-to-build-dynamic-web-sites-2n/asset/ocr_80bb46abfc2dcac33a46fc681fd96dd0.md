# Core PHP Programming

![](bbox=[0.198, 0.093, 0.758, 0.353])

```
Array (
    [scheme] => http
    [host] => www.leonatkinson.com
    [port] => 80
    [user] => leon
    [pass] => secret
    [path] => /test/test.php3
    [query] => name=Leon6occupation=Web+Engineer
)

<?php
$query = "http://leon:secret@www.leonatkinson.com:80";
$query .= "/test.test.php3";
$query .= "&name=Leon6occupation=Web+Engineer";
$url = parse_url($query);
for(reset($url); $index = key($url); next($url)) {
    print("$index: $url[\$index]<BR\n");
}
?>
```

# string_printable_decode(string text)

The quoted_printable_decode function converts a quoted string into 8-bit binary form. It reverses the action of the quotemeteta function. That, it removes backslashes preceding special characters. Table 9.7 lists these special characters.

| Character | Description |
| --- | --- |
| | Period |
| \ | Backslash |
| + | Plus |
| * | Asterisk |
| ? | Question Mark |
| [ | Left Square Bracket |
| ] | Right Square Bracket |
| ^ | Caret |
| ( | Left Parenthesis |
| ) | Right Parenthesis |

IT-SC book 268
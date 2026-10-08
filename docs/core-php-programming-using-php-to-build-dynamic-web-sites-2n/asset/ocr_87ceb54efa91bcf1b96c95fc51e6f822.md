# Core PHP Programming

| | | | |
|---|---|---||
| 118 | 76 | v | Lowercase V |
| 119 | 77 | w | Lowercase W |
| 120 | 78 | x | Lowercase X |
| 121 | 79 | y | Lowercase Y |
| 122 | 7A | z | Lowercase Z |
| 123 | 7B | { | Left Curly Bracket |
| 124 | 7C | | | Vertical Line |
| 125 | 7D | } | Right Curly Bracket |
| 126 | 7E | ~ | Tilde |
| 127 | 7F | | Delete |

If you are interested in how characters are rendered in a particular browser, the following script will print each character in a table.

```
<HTML>
<HEAD>
<TITLE>ASCII Characters</TITLE>
</HEAD>
<BODY>
<TABLE BORDER="1" CELLSPACING="0" CELLPADDING="5">
<?php
for($index=0; $index = 255; $index++) {
    print("<TR>");
    print("<TD>"$index</</TD>");
    print("<TD>"".chr($index)."</TD>");
    print("<TR>\n");
}
?>
</TABLE>
</BODY>
</HTML>
```
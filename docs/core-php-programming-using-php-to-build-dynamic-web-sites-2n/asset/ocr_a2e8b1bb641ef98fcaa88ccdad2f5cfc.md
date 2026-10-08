# string sql_regcase(string regular_expression)

The sql_regcase function translates a case-sensitive regular expression into a caseinsensitive regular expression. This is unnecessary when used with PHP's built-in expression functions but can be useful when creating regular expressions for external programs such as databases.

```
<?php
// print [Mm][Oo][Zz][Ii][Ll][Ll][Aa]
print(sql_regcase("Mozilla"));
?>
```

# string str_replace(string target, string replacement, string text)

The str_replace function attempts to replace all occurrences of target in text with replacement. This function is safe for replacing strings in binary data. It's also a much faster alternative to preg_replace. Note that str_replace is case sensitive.

```
<?php
$text = "Search results with keywords highlighted";nprint(str_replace("keywords", "<B>keywords</B>", $text));
?>
```

# string strip_tags(string text, string ignore)

The strip_tags function attends to remove all SGML tags from the text argument. This includes HTML and PHP tags. The optional ignore argument may contain tags to be left alone. This function uses the same algorithm as fgetss. If you want to preserve tags, you may wish to use htmlentities.

```
<?php
// create some test text
$text = "<P><B>Paragraph One</B><P>Paragraph Two";
// strip out all tags except paragraph and break
print(strip_tags($text, "<P><BR>"));
?>
```
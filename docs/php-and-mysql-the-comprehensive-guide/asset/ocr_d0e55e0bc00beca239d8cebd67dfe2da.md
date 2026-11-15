> **Tip**
> Alternatively, you can also use `file()`, which returns the same array, but all array entries still have the line jumps at the end.

This means that `$data` now contains an array of individual entries. These can be transformed back into their original form, an associative array, using `base64_decode()` and `unserialize()`. The last step is to output this data in formatted form. The following listing shows the complete code; Figure 25.9 shows the output.

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>

<?php
if (file_exists("guestbook.txt") &&
is_readable("guestbook.txt")) {
$data = file_get_contents("guestbook.txt");
$data = explode("\r\n", $data);
for ($i = 0; $i < count($data); $i++) {
$entry = unserialize(base64_decode($data[$i]));
if (is_array($entry)) {
printf("<p><a href=\"mailto:%s\"></a> wrote on/at %s:</p>
<h3>%</h3><p>%</p><hr noshade=\"noshade\" />,
urlencode($entry["email"]),
htmlspecialchars($entry["author"]),
htmlspecialchars($entry["date"]),
htmlspecialchars($entry["heading"]),
nl2br(htmlspecialchars($entry["entry"])))
};
}
}
?>
</body>
</html>
```

# Listing 25.9 Reading from the Guestbook ("gb-show.php")
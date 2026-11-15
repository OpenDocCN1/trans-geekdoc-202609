http://www.php.net/downloads.php.
Mac owners can find a binary distribution as a homebrew at http://
formulae.brew.sh/formula/php.

# Listing 35.2 The Input Data (“text.txt”)

When you execute the listing, URLs are determined—but not all of them (see Figure 35.2). A look at the source code also shows that a line break has been inserted after http:// php.net, so there is a second, empty URL. There is therefore (at least) one error that should be found.

![](bbox=[0.141, 0.29, 0.79, 0.44])

Figure 35.2 All URLs Found—but Isn’t Something Missing?

# 35.1 Debugging by Hand

The most obvious way to debug is simple: You simply enter echo or print or print_r() or var_dump() before or after critical function calls. This allows you to narrow down the cause of the problem. In Listing 35.3, you can see a first approach: The numbers of all lines that contain something are output.

```
<?php
$url = array();
$file = fopen("text.txt", "r");
$line_no = 0;
while (!feof($file)) {
	$line_no++;
	$line = fgets($file, 1024);
	if ($start = strpos($line, "http://")) {
		echo "Found what you were looking for in line $line_no.<br />";
		$end1 = strpos($line, "\""), $start+1);
		$end2 = strpos($line, " ", $start+1);
		if ($end1 == -1 && $end2 == -1) {
			$end = strlen($line);
		} elseif ($end1 == -1) {
			$end = $end2;
		}
```
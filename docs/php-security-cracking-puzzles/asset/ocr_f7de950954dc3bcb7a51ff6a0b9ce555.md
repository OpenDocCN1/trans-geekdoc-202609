# 300 Part II: Solutions

```
// Loading the contents of the page.
$contents = file_get_contents($url);
// The regular expression for URLs
$pattern = 
"<li>([\s]*<div>[\s]*a[\s]*class=yschtl[^"]]*href="([^"]+)">([\s]*.*?)<a></li>"
// Performing a search against the regular expression
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// Displaying the results of the search
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "<a href="$out[1][$i]">$out[2][$i]."<br>";
}?
```

# II.8.3. Extracting Links from Google

Unlike Yahoo, Google has no surprises — at least, it didn't when this book was written. A list of URLs can be produced using the script shown in Listing II.8.7.

# Listing II.8.7. Using the get_content() function

```
<?php
// Setting unlimited execution time for the script
set_time_limit(0);
// The page to search
$url = "http://www.google.com/search?hl=mysql&btnG=Google+Search";
// Loading the contents of the page
$contents = file_get_contents($url);
// The regular expression for URLs
$pattern = "<a([\s]+class=1\s*)href="([^"]+)"|isu"
// Performing a search against the regular expression
preg_match_all($pattern, $contents, $out, PREG_PATTERN_ORDER);
// Displaying the results of the search
for ($i = 0; $i < count($out[1]); $i++)
{
    echo "$out[1][$i]."<br>";
}?>
```
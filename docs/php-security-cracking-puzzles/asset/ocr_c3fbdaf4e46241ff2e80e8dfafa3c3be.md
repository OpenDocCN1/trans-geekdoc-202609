# 118 Part II: Solutions

To prevent unclosed tags from being interpreted, it is necessary to use a more complicated method of text processing. For example, consider the script shown in Listing II.1.25.

# Listing II.1.25. The script that processes only closed tags

```
<?php
// The source string
$text = 'This is [b]bold[/b] text';
// The resulting string
$result = ""
// Auxiliary variables
$lastocc = 0;
$sndocc = 1;
while($sndocc) {
// Start of the bold fragment
$fstocc = strpos($text, "[b]", $lastocc);
// Termination of the bold fragment
$sndocc += strpos($text, "[/b]", $fstocc);
if(($fstocc >= 0 && $sndocc > 0 && $lastocc > 0) ||
    ($fstocc == 0 && $sndocc > 0 && $lastocc == 0)) {
// Placing the fragment preceding the [b] tag into the $result string
$result .= substr($text, $lastocc, $fstocc - $lastocc);
// Bold fragment
$result .= "<b>".substr($text,
$fstocc - 3,
$sndocc - $fstocc - 3)."[/b>";
$lastocc = $sndocc + 4;
} else {
// Processing the remainder of the string
$result .= substr($text, $lastocc, strlen($text) - $lastocc);
// Exiting the loop
break;
}
echo $result;
?>
```
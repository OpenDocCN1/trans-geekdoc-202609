```
$numLines = substr_count( $myText, "\n" );
$startOfLine = 0;

// Move through each line in turn

for ( $i=0; $i < $numLines; $i++ ) {
    $originalLineLength = strpos( $myText, "\n", $startOfLine ) - $startOfLine;
    $justifiedLine = substr( $myText, $startOfLine, $originalLineLength );
    $justifiedLineLength = $originalLineLength;

// Keep adding spaces between words until the desired
// line length is reached

while ( $i < $numLines - 1 && $justifiedLineLength < $lineLength ) {
    for ( $j=0; $j < $justifiedLineLength; $j++ ) {
        if ( $justifiedLineLength < $lineLength && $justifiedLine[$j] == " " ) {
            $justifiedLine = substr_replace( $justifiedLine, " ", $j, 0 );
            $justifiedLineLength++;
            $j++;
        }
    }
}

// Add the justified line to the string and move to the
// start of the next line

$myTextJustified .= "$justifiedLine\n";
$startOfLine += $originalLineLength + 1;
}
?>
<h2>Original text:</h2>
<pre><?php echo $myText ?><pre>
<h2>Justified text:</h2>
<pre><?php echo $myTextJustified ?><pre>
</body>
</html>
```

Now run the script by visiting its URL in your Web browser. You should see a page like Figure 5-2. The first block of text is the original, unjustified text with a ragged right-hand margin. The second block of text is the justified version with both left and right margins aligned.
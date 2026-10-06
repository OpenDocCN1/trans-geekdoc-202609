# Chapter 5: Strings

Pass a negative argument to replace up that many characters from the end of the string:

```
$myString = "It was the best of times, it was the worst of times";

// Displays "It was the best of bananas the worst times,"
echo substr_replace($myString, "bananas", 19, -20) . "<br/>";
```

You can also pass a zero value to insert the replacement text into string rather than replacing characters:

```
$myString = "It was the best of times, it was the worst of times";

// Displays "It really was the best of times, it was the worst of times,"
echo substr_replace($myString, "really", 3, 0) . "<br/>";
```

# Try It Out | Justifying Text

You can use the string functions you've learned so far to write a script to justify lines of text. Justifying text means aligning text within a column so that the text is flush with both the left and right margins. Here's the script. Save it as justification.php in your root folder:

```
<DOCTYPE html PUBLIC "//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns:="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>Justifying Lines of Text</title>
  <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
  <h1>Justifying Lines of Text</h1>
</body>

<?php
// The text to justify
$myText = <<END_TEXT;
But think not that this famous town has
only harpooners, cannibals, and
bumpkins to show her visitors. Not at
all. Still New Bedford is a queer place.
Had it not been for us whalemen, that
tract of land would this day perhaps
have been in how howling condition as the
coast of Labrador.
END_TEXT;

$myText = str_replace("\rn", "\n", $myText);

$lineLength = 40; // The desired line length
$myTextJustified = "";
```
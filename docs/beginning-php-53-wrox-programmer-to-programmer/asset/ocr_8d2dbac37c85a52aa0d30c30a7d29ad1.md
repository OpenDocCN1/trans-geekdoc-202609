# Chapter 5: Strings

![](bbox=[0.235, 0.083, 0.863, 0.467])

# How It Works

The script starts by displaying an XHTML-page header, then defining a variable, $myText, containing the text to justify. The text is included in the script using the heredoc syntax. (The extra blank at the end of the text ensures that the line of text has a new character at the end of it; this is required by the algorithm that the script uses.)

After defining $myText, the script uses str_replace() to convert Windows line endings (a carriage return followed by a line feed) to UNIX line endings (a line feed on its own). Windows line endings occur if the script file was saved on a Windows machine, and they can confuse the justification algorithm (which expects each line to end with just a line feed):

```
$myText = str_replace("\r\n", "\n", $myText);
```

Next, the script sets a few more variables:

+   - lineLength: The desired length that each line of text is to. Try changing this different values to see what happens

+   - myTextJustified: This will contain the final, justified text

85
useful when combining JavaScript and HTML. For example, this is a valid JavaScript string, containing HTML that includes quoted attributes:

```
'<img src = "logo.gif" alt = "logo">'
```

Or, of course, we could switch the quote characters around:

```
"<img src = 'logo.gif' alt = 'logo'>"
```

Another useful aspect of strings is that they can be concatenated (joined together) using the '+' operator. Here, for example, we write out some text and the document title by concatenating them:

```
document.write("Document title is " + document.title);
```

You can concatenate different data types together with strings and they will be treated as a single string. Strings also have a number of properties and methods. The 'length' property, for example, returns the number of characters in a string, while the 'substring' method returns part of the string between two specified character positions. The following script uses both the 'length' property and the 'substring' method to display the last character of a string. Note that the substring returned by the method starts at the character position after the one specified by the first parameter, but includes the character at the position specified by the second parameter:

```
<!-- File: Example6-7.htm -->
<script type = "text/javascript">
<!--
var strFullString = "a string";
var intLength = strFullString.length;
var strSubString = strFullString.substring(intLength-1, intLength);
document.write("Last character is " + strSubString);
// -->
</script>
```

Figure 6.8 shows the result of the script in a browser.

# FIGURE 6.8 A substring displayed in a browser window

![](bbox=[0.2, 0.78, 0.9, 0.93])
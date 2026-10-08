# Core PHP Programming

This is an example of using a function to repeat a commonly-used piece of HTML code.<BR><BR><?php PrintTitle("how it works"); ?>\Any time a title needs to be created, the <CODE>PrintTitle</CODE> function is called with the text of the title.<BR>

<? PrintTitle("advantages"); ?>
The code is more readable<BR>Less text to type for each title<BR>Easy to change every title<BR>
</body>
</html>

The page in Listing 20.3 is a very simple submission form. Each of the input tags will be turned into a PHP variable when the button is clicked. This calls the script listed in Listing 20.4. A file named req.txt will be opened for appending, and each of the form fields will be written into the spreadsheet. Each field separated by tab characters, which allows you to input data into a spreadsheet easily.

# Listing 20.2 Dressing Up CGI Output

```
<HTML>
<HEAD>
<TITLE>Listing 20.2</TITLE>
</HEAD>
<body>
<h1>Color Chart</h1>
<P>The following chart displays the colors safe for displaying in all browsers. These colors should not dither on any computer with a color palette of at least 256 colors.</P>
<P>This chart will only display on browsers that support table cell background colors.</P>
?>
$color = array("00", "33", "66", "99", "CC", "FF");

for($Red = 0; $Red count <($color); $Red++) {
		print("<table>\n");
		for($Green = 0; $Green count <($color); $Green++) {
			print("<tr>\n");
```
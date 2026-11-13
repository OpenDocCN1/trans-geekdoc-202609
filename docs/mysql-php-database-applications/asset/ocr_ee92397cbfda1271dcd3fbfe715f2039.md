The following code creates a list box with three visible elements. Figure B-3 shows how this HTML code looks in the browser.

```
<form name="tester" action="script.php" method="GET">
<select name="side_dishes" multiple size="3">
<option value="1">potato</option>
<option value="2">pasta</option>
<option value="3">carrot</option>
<option value="4">celery</option>
<option value="5">mango</option>
</select>
</form>
```

If you want that select list to support multiple selections (by holding down Ctrl), you have to put square brackets after the name value. In other words, the opening line of the preceding select box would be as follows:

```
<select name="side_dishes[]" multiple size="3">
```

# textarea

The textarea element creates a large block for text entry. Add a rows and columns attribute to specify the size of the box. textarea is different from other form elements in that opening and closing tags surround the default text. For instance:

```
<textarea name="mytext" rows="5" columns="20">Here's the default text</textarea>
```

Keep in mind that if you have spaces or hard returns between your <textarea> tags, those characters will be carried to the form element.

Add the wrap attribute to change how text wraps when it reaches the end of a line in the box. If the value is wrap="physical", carriage returns are added at the end of line; if the value is wrap="virtual", the lines will appear to wrap but will be submitted as a single line. The latter is almost always the best choice for ease of processing on the server side – though "virtual" still preserves any manually inserted returns.

The attributes just listed came from the folks at Netscape, and you still might need to use them. The official W3C HTML 4.0 attribute values for wrap are none, hard, and soft, and these should work in the most of the recent browsers.
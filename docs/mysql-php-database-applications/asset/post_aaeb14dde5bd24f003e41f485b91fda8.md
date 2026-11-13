

### db_values_array()

This function builds an associative array out of the values in the MySQL table specified in the first argument. The data from the column named in the second argument are set to the keys of the array. If the third argument is not empty, the data from the column it names are the values of the array; otherwise, the values are equal to the keys. If the third argument is not empty, the data are ordered by the column that is named; otherwise, they are ordered by the key column. The optional fourth argument specifies any additional qualification for the query against the database table; if it is empty, all rows in the table are retrieved.

If either the first or second argument is empty, no query is run and an empty array is returned. The function presumes that whoever calls it knows what he or she is doing – that the table exists, that all the column names are correct, and so on.

```
array db_values_array ([string table name [, string value field [, string label field [, string sort field [, string where clause]]]]])
```

### From functions/html/

These functions create common HTML elements, including anchors and unordered lists.

### font_tag()

This function creates an HTML font tag. Default size is 2; default font face is sans-serif. Any additional attributes in the third argument are added to the tag. It is expecting an associative array, the key of which is the name of the attribute; the value of the array element is the attribute value.

```
string font_tag ([int size [, string typeface [, array attributes]]])
```

### anchor_tag()

This function creates an HTML anchor tag. The first argument is the href value; the second the string to be surrounded by the anchor. It is expecting an associative array, the key of which is the name of the attribute; the value of the array element is the attribute value.

```
string anchor_tag ([string href [, string text [, array attributes]]])
```

### image_tag()

This function returns an HTML image tag (). The first argument gives the URL of the image to be displayed. Additional attributes can be supplied as an array in the third argument.

```
string image_tag ([string src [,array attributes]])
```

### subtitle()

This function returns an HTML <h3> tag. It is used for the titles of secondary areas within pages in our examples. The reason to display these via a function rather than just literal <h3> tags is that this will enable you to change the format of these subtitles in one place, instead of in each script.

```
string subtitle(string string)
```

### paragraph()

This function returns a string inside HTML paragraph (<p>) tags. Attributes for the <p> tag can be supplied in the first argument. Any additional arguments are included inside the opening and closing <p> tags, separated by newlines.

```
string paragraph([array attributes [, mixed ...]])
```

### ul_list()

This function returns an HTML unordered (bulleted) list (<ul>) tags. If the argument is an array, each value from the array is included as a list item (<li>) in the list. Otherwise, the argument is simply included inside the <ul> tags as is.

```
string ul_list(mixed values)
```

The following functions create opening and closing <table> tags, as well as <tr> and <td> tags.

### start_table()

This function returns an opening HTML table tag inside a pair of paragraph (<p>...</p>) tags. Attributes for the table can be supplied as an array.

```
string start_table([array attributes])
```

### end_table()

This function returns a closing table tag.

```
string end_table(void)
```

### table_row()

This function returns a pair of HTML table row (<tr>) tags enclosing a variable number of table cell (<td>) tags. If any of the arguments to the function is an array, it is uses as attributes for the <tr> tag. All other arguments are used as values for the cells of the row. If an argument begins with a <td> tag, the argument is added to the row as is; otherwise, it is passed to the table_cell() function and the resulting string is added to the row.

```
string table_row ([array attributes], [indefinite number of string arguments])
```

### table_cell()

This function returns an HTML table cell (<td>) tag. The first argument is used as the value of the tag. Attributes for the <td> tag are supplied as an array in the second argument. By default the table cell is aligned left horizontally and to the top vertically.

```
string table_cell ([string value [, array attributes]])
```

### From functions/forms/

These functions create all common form elements, as well as the opening and closing <form> tags.

### start_form()

This function returns an HTML <form> tag. If the first argument is empty, the value of the global Apache variable SCRIPT_NAME is used for the action attribute of the <form> tag. Other attributes for the form can be specified in the optional second argument; the default method of the form is post. The behavior of this function on servers other than Apache has not been tested. It's likely that it will work, because SCRIPT_NAME is part of the CGI 1.1 specification.

```
string start_form ([string action, [array attributes]])
```

### end_form()

This function returns a closing form tag.

```
string end_form(void)
```

### text_field()

Returns an HTML <input type=text> form element. Default size is 10.

```
string text_field ([string name [, string value [, int size [, int maximum length]]]])
```

### textarea_field()

This function returns an HTML textarea field. The default size is 50 columns and 10 rows, and the default wrap mode is soft, which means no hard newline characters are inserted after line breaks in what the user types into the field. The alternative wrap mode is 'hard', which means that hard newlines are inserted.

```
string textarea_field([string name [, string value [, int cols [, int rows [, string wrap mode]]]]])
```

### password_field()

This function returns an HTML password field. This is like a text field, but the value of the field is obscured (only stars or bullets are visible for each character). The default size of the field is 10. A starting value and maximum data length may be supplied.

```
string password_field ([string name [, string value [, int size [, int maximum length]]]])
```

### hidden_field()

This function returns an HTML hidden-form element. A name and value may be supplied.

```
string hidden_field ([string name [, string value]])
```

### file_field()

This function returns a text field from an HTML form.

```
string file_field([string name])
```

This function returns an HTML file field. These are used to specify files on the user's local hard drive, typically for uploading as part of the form.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_719_0.png)

### submit_field()

This function returns an HTML submit field. The value of the field is the string displayed by the button displayed by the user's browser. The default value is Submit.

```
string submit_field ([string name [, string value]])
```

### image_field()

This function returns an HTML image field. An image field works like a submit field, except that the image specified by the URL given in the second argument is displayed instead of a button.

```
string image_field ([string name [, string src [, string value]]])
```

### reset_field()

This function returns an HTML reset field.

```
string reset_field ([string name [, string value]])
```

### checkbox_field()

This function returns an HTML checkbox field. The optional third argument is included immediately after the checkbox field, and the pair are included between a <nobr> tag and </nobr> tag – meaning that they are displayed together on the same line. If the value of the second or third argument matches that of the fourth argument, the checkbox is checked (that is, flipped on).

```
string checkbox_field ([string name [, string value [, string label [, string match]]]])
```

### radio_field()

This function returns an HTML radio button field. The optional third argument is included immediately after the radio button, and the pair are included between a <nobr> tag and </nobr> tag–meaning that they are displayed together on the same line. If the value of the second or third argument matches that of the fourth argument, the radio button is checked (that is, flipped on).

```
string radio_field ([string name [, string value [, string label [, string match]]]])
```

### select_field()

This function returns an HTML select field (popup field). If the optional second argument is an array, each key in the array is set to the value of an option of the select field, and the corresponding value from the array is the displayed string for that option. If the key or the value from the array matches the optional third argument, that option is designated as the default value of the select field.

```
string select_field ([string name [, array items [, string default value]]])
```


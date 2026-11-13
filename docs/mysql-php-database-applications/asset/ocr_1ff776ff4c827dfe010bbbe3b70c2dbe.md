# db_values_array()

This function builds an associative array out of the values in the MySQL table specified in the first argument. The data from the column named in the second argument are set to the keys of the array. If the third argument is not empty, the data from the column it names are the values of the array; otherwise, the values are equal to the keys. If the third argument is not empty, the data are ordered by the column that is named; otherwise, they are ordered by the key column. The optional fourth argument specifies any additional qualification for the query against the database table; if it is empty, all rows in the table are retrieved.

If either the first or second argument is empty, no query is run and an empty array is returned. The function presumes that whoever calls it knows what he or she is doing – that the table exists, that all the column names are correct, and so on.

```
array db_values_array ([string table name [, string value field [, string label field [, string sort field [, string where clause]]]]])
```

# From functions/html/

These functions create common HTML elements, including anchors and unordered lists.

# font_tag()

This function creates an HTML font tag. Default size is 2; default font face is sans-serif. Any additional attributes in the third argument are added to the tag. It is expecting an associative array, the key of which is the name of the attribute; the value of the array element is the attribute value.

```
string font_tag ([int size [, string typeface [, array attributes]]])
```

# anchor_tag()

This function creates an HTML anchor tag. The first argument is the href value; the second the string to be surrounded by the anchor. It is expecting an associative array, the key of which is the name of the attribute; the value of the array element is the attribute value.

```
string anchor_tag ([string href [, string text [, array attributes]]])
```

# image_tag()

This function returns an HTML image tag (<img>). The first argument gives the URL of the image to be displayed. Additional attributes can be supplied as an array in the third argument.

```
string image_tag ([string src [,array attributes]])
```
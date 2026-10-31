# CHECKBOX_FIELD()

This function returns an HTML checkbox field. The optional third argument will be included immediately after the checkbox field, and the pair is included inside an HTML <nobr> tag—meaning that they will be displayed together on the same line. If the value of the second or third argument matches that of the fourth argument, the checkbox will be ‘checked’ (i.e., flipped on).

```
string checkbox_field ([string name [, string value [, string label [, string match]]]])
```

# RADIO_FIELD()

This function returns an HTML radio button field. The optional third argument will be included immediately after the radio button, and the pair is included inside an HTML <nobr> tag—meaning that they will be displayed together on the same line. If the value of the second or third argument matches that of the fourth argument, the radio button will be ‘checked’ (i.e., flipped on).

```
string radio_field ([string name [, string value [, string label [, string match]]]])
```

# SELECT_FIELD()

This function returns an HTML select field (a popup field). If the optional second argument is an array, each key in the array will be set to the value of an option of the select field, and the corresponding value from the array will be the displayed string for that option. If the key or the value from the array matches the optional third argument, that option will be designated as the default value of the select field.

```
string select_field ([string name [, array items [, string default value]]])
```

# DB_SELECT_FIELD()

This function returns an HTML select field (popup field), based on the values in the MySQL database table specified by the second argument, as returned by the db_values_array() function (defined previously).

```
string db_select_field ([string name [, string table name [, string value field [, string label field [, string sort field [, string match text [, string where clause]]]]]]])
```

# DB_RADIO_FIELD()

This function returns a list of HTML radio button fields, separated by a non-breaking space HTML entity (&nbsp;) and a newline, based on the values in the MySQL database table named by the second argument, as returned by the db_values_array() function (defined previously).
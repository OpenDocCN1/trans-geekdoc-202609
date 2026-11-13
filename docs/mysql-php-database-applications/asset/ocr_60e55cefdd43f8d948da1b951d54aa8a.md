are inserted after line breaks in what the user types into the field. The alternative wrap mode is 'hard', which means that hard newlines are inserted.

```
string textarea_field([string name [, string value [, int cols [, int rows [, string wrap mode]]]]])
```

# password_field()

This function returns an HTML password field. This is like a text field, but the value of the field is obscured (only stars or bullets are visible for each character). The default size of the field is 10. A starting value and maximum data length may be supplied.

```
string password_field ([string name [, string value [, int size [, int maximum length]]]])
```

# hidden_field()

This function returns an HTML hidden-form element. A name and value may be supplied.

```
string hidden_field ([string name [, string value]])
```

# file_field()

This function returns a text field from an HTML form.

```
string file_field([string name])
```

This function returns an HTML file field. These are used to specify files on the user's local hard drive, typically for uploading as part of the form.

![](bbox=[0.148, 0.64, 0.865, 0.72])

# submit_field()

This function returns an HTML submit field. The value of the field is the string displayed by the button displayed by the user's browser. The default value is Submit.

```
string submit_field ([string name [, string value]])
```
+   - **numeric**: the field value may contain only numbers
+   - **nopunctuation**: there may not be any punctuation characters in the field
+   - **nonzero**: the field value must be a number other than 0
+   - **uploadedfile**: the field must contain an uploaded file, as verified by the PHP is_uploaded_file function[5]
+   - **maxfilesize**: the uploaded file contained in the field is constrained to a maximum size
+   - **mimetype**: the uploaded file contained in the field must be of a particular MIME type¹
+   - **filename**: the filename of the uploaded file contained in the field must match a regular expression
+   - **function**: when passed the value of the field, the specified function must return TRUE
+   - **regexp**: the value of the field must match the specified regular expression

You can apply one or more of the above rules to any QuickForm field with the addRule method:

```
addRule(element, message, type[, format[, validation[, reset[, force]]]])
```

Of the above arguments,

+   - **element**: is the name you have assigned to the element, using the addElement method
+   - **message**: is the text displayed to a user if they break this validation rule
+   - **type**: is the validation rule type (listed above)

[5] http://www.php.net/is-uploaded-file
See http://www.hiveemail.com/mime.types.php for a list of MIME types.
```
```php
foreach ($_POST as $field => $value)
{
    echo "$field, $value<br>";
}
```
```

The output from the `foreach` loop would be

```
```
name, Smith
interest, dog
hidvar, 3
```
```

The output shows three variables with these three values for the following reasons:

+   - **The user didn’t change the text in the text field.** The value `"Smith"` that the program displayed is still the text in the text field.
+   - **The user selected the radio button for dog.** The user can select only one radio button.
+   - **The program passed a hidden field named `hidvar`.** The program sets the value for hidden fields. The user can’t affect the hidden fields.

![](bbox=[0.069, 0.48, 0.163, 0.552])

# ## Post versus get

You use one of two methods to submit form information. The methods pass the form data differently and have different advantages and disadvantages.

+   - **get method:** The form data is passed by adding it to the URL that calls the form-processing program. For instance, the URL might look like this:

```
```
processForm.php?name=Smith&
  fname=Goliath
```
```

The advantages of this method are simplicity and speed. The disadvantages are that less data can be passed and that the information is displayed in the browser, which can be a security problem in some situations.

+   - **post method:** The form data is passed as a package in a separate communication with the processing program.

The advantages of this method are unlimited information passing and security of the data. The disadvantages are the additional overhead and slower speed.

For CGI programs that are not PHP, the program that processes the form must find the information and put the data into variables. In this case, the `get` method is much simpler and easier to use. Many programmers use the `get` method for this reason. However, PHP does all this work for you. The `get` and `post` methods are equally easy to use in PHP programs. Therefore, when using PHP, it’s almost always better to use the `post` method because you have the advantages of the post method (unlimited data passing, better security) without its main disadvantage (more difficult to use).
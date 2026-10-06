
## Chapter 9: Handling HTML Forms with PHP

```html
<label for="submitButton">A button</label>
<input type="submit" name="submitButton" id="submitButton" value="Submit Form" />
```

- A reset button — This type of button resets all fields back to their initial values (often empty). The value attribute contains the label text:

```html
<label for="resetButton">A reset button</label>
<input type="reset" name="resetButton" id="resetButton" value="Reset Form" />
```

- A file field — This allows the users to choose a file on their hard drive for uploading to the server ("Creating File Upload Forms" later in the chapter). The value attribute is usually ignored by the browser:

```html
<label for="fileSelectField">file select field</label>
<input type="file" name="fileSelectField" id="fileSelectField" value="" />
```

- A hidden field — This type is not displayed on the page; it simply stores the text in the value attribute. Hidden fields are great for passing additional information from the server, as you will see in the later:

```html
<label for="hiddenField">A hidden field</label>
<input type="hidden" name="hiddenField" id="hiddenField" value="" />
```

- An image field — This works like a button, but allows you to use your own button graphic of the standard gray button. You use the URL of the button graphic using the src attribute, and the graphic's width and height (in pixels) with the width and height attributes. As the submit button, the value attribute contains the value that is sent to the server when the button is clicked:

```html
<label for="imageField">An image field</label>
<input type="image" name="imageField" id="imageField" value="" src="asterisk.gif" width="23" height="23" />
```

- A push button — This type doesn't do anything when it's clicked, but you can make buttons trigger various events in the browser using JavaScript. The value attribute specifies the text label to display in the button:

```html
<label for="pushButton">A push button</label>
<input type="button" name="pushButton" id="pushButton" value="Click Me" />
```

- A pull-down menu — This allows a user to pick a single item from a predefined list of options. The size attribute's value of 1 tells the browser that you want the list to be in a pull-down menu. Within the select element, you create an option element for each of your options. Place the option label between the <option> ... </option> tags. Each option element can have an optional value attribute, which is the value sent to the server if that option is selected. If you do not include a value attribute, between the <option> ... </option> tags it is inserted:

```html
<label for="pullDownMenu">A pull-down menu</label>
<select name="pullDownMenu" id="pullDownMenu" size="1">
  <option value="option1">Option 1</option>
  <option value="option2">Option 2</option>
</select>
```

## Part III: Using PHP Practice

- A list box — This works like a pull-down menu, but it displays several options at once. To turn a pull-down menu into a list box, change the size attribute from 1 to 3:

```html
<label for="listBox">A list box</label>
<select name="listBox" id="listBox" size="3">
  <option value="option1">Option 1</option>
  <option value="option2">Option 2</option>
  <option value="option3">Option 3</option>
</select>
```

- A multi-select — This works like a list box, but it allows the user to select multiple items by holding down Ctrl (on Windows) or Command (on Mac). To turn a normal list into a multi-select, add the multiple attribute to the element:

```html
<label for="multiListBox">A multi-select</label>
<select name="multiListBox" id="multiListBox" size="3" multiple>
  <option value="option1">Option 1</option>
  <option value="option2">Option 2</option>
  <option value="option3">Option 3</option>
</select>
```

- A text area — This is similar to a text field, but it allows the user to enter multiple lines of text. Unlike a text field, you must specify the rows and columns for the element:

```html
<label for="textareaField">A text area</label>
<textarea name="textareaField" id="textareaField" rows="4" cols="50"></textarea>
```

## Capturing Form Data with PHP

You know how to create an HTML form, and how data is sent to the server. How do you write a PHP script to handle that data when it arrives?

First of all, the form's action attribute needs to contain the URL of the PHP script that will handle the form. For example:

```html
<form action="form_handler.php" method="post">
```

Next, you need to create the form_handler.php script. When users send their forms, their data is sent to the server and the form_handler.php script runs. The script needs to read the data and act on it.

To read the data from a form, you use superglobals. You were introduced briefly to superglobals in Chapter 7. A superglobal is a built-in PHP variable that is available in any scope: the top level of your script, within a function, or within a class method. Chapter 7 discussed the $_GLOBALS superglobal array, which contains a list of global variables used in your applications. Here, you learn about three new superglobal arrays:

| Superglobal Array | Description |
|---|---|
| $_GET | Contains a list of all the field names and values sent by a form using the get method |
| $_POST | Contains a list of all the field names and values sent by a form using the post method |
| $_REQUEST | Contains the values of both the $_GET and $_POST arrays combined, along with the values of the $_COOKIE superglobal array |

You learn about the $_COOKIE superglobal arrays in the next chapter.

Each of these three superglobal arrays contains the field names from the form as array keys, with the field values themselves as array values. For example, say you created a form using the get method, and that form contained the following:

```html
<input type="text" name="emailAddress" value="" />
```

You could then access the value that the user entered into that field using either the $_GET or the $_REQUEST superglobal:

```php
<?php
$email = $_GET["emailAddress"];
$email = $_REQUEST["emailAddress"];
?>
```

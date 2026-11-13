+   reset — This form field creates a button that, when pressed, returns the form to the state it was in when the page loaded. Any data that the user has entered into the form is cleared.

+   file—Allows users to send files from their computer to a remote server. The field looks much like a text box that has a button labeled “Browse” placed next to it. When a user presses the Browse button, a file selection dialog box is displayed. The user can choose one file per file upload form field. A form can have multiple file upload fields. When using this input type, be sure to change the form enctype attribute to multipart/form-data. See Chapter 12 for a discussion of file uploads with PHP.

+   checkbox—The name and value of the checkbox is passed only if the checkbox is checked when the form is submitted. If the word “checked” appears in the tag, the checkbox will be checked by default. Remember to use name=box_name[] to pass multiple checkboxes as an array. See Chapter 4 for a discussion of passing arrays with PHP.

+   radio—Enable the user to select only one of several choices. Radio buttons with the same name attribute belong to the same group. The checked attribute signifies the default choice.

The following form makes use of all the form elements we just covered, except for the image type. Figure B-2 shows how it is rendered in the browser.

```
```html
<h2>Please Enter Personal Information</h2>
<form>
<input type="text" size="25" maxlength="15" name="name"
value="Name Here"><br>
<input type="password" size="25" maxlength="15" name="password"
value=""><br>
<input type="hidden" value="you can't see me">
<input type="checkbox" name="telemarket" value="yes" checked>If
checked, I have permission to clear out your bank account.
<p>
<b>What is your eye color?</b><br>
<input type="radio" name="eye_color" value="blue"
checked>blue<br>
<input type="radio" name="eye_color" value="green">green<br>
<input type="radio" name="eye_color" value="brown">brown<br>
<input type="radio" name="eye_color" value="red">red<br>
<input type="submit" name="submit" value="submit"> &nbsp; &nbsp;
<input type="Reset">
</form>
```
```
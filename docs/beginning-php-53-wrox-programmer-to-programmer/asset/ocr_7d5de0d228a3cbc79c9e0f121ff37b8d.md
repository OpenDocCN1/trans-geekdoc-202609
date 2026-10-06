# Chapter 9: Handling HTML Forms with PHP

# Try It Out Create an HTML Form

In this example, you create a Web form that contains a variety of form fields. Not only will you learn how to create the various types of form fields, but you can also see how the fields look and work in your Web browser.

Save the following file as web_form.html in your document root folder, then open it in your browser to see the:

```
<!DOCTYPE html PUBLIC "//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/DTD/XHTML-11-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" lang="en">
<head>
<title>An HTML Form</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>An HTML Form</h1>
<form action="get">
<div style="width:250px">
<label for="textField">A input field</label>
<input type="text" name="textField" id="textField" value="" />
<label for="passwordField">A password field</label>
<input type="password" name="passwordField" id="passwordField" value="" />
<label for="checkboxField">A checkbox field</label>
<input type="checkbox" name="checkboxField" id="checkboxField" value="" />
<label for="radioButtonField1">A radio button field</label>
<input type="radio" name="radioButtonField1" id="radioButtonField1" value="" />
<label for="radioButtonField2">Another radio button</label>
<input type="radio" name="radioButtonField2" id="radioButtonField2" value="" />
<label for="submitButton">A submit button</label>
<input type="submit" name="submitButton" id="submitButton" value="" />
<label for="resetButton">A reset button</label>
<input type="reset" name="resetButton" id="resetButton" value="" />
<label for="fileSelect">A file select field</label>
<input type="file" name="fileSelect" id="fileSelect" value="" />
</div>
</form>
</body>
</html>
```

223
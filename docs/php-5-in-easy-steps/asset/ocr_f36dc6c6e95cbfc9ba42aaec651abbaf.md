# Manipulating submitted values

PHP can do much more than simply display values from an HTML form. The submitted data is stored in PHP variables, each keyed against the name of its input field, and these variables can be manipulated by the script, just like other variables.

The HTML form in the example below allows the user to enter two numbers and then select an arithmetic operation to perform on them. When the form is submitted to the server, these values are sent to a PHP form handler called calc.php, listed opposite. The data is associated with the key names of "val1", "val2" and "calc" that have been used for the form's input fields.

![](bbox=[0.185, 0.135, 0.265, 0.345])

```
<html><head><title>Calculation Form</title></head>
<body>
<form action="calc.php" method="post">
Value 1: <input type="text" name="val1" size="10">
Value 2: <input type="text" name="val2" size="10"><br>
Calculation:
<input type="radio" name="calc" value="add">Add
<input type="radio" name="calc" value="sub">Subtract
<input type="radio" name="calc" value="mul">Multiply
<input type="radio" name="calc" value="div">Divide<br>
<input type="submit" value="Calculate">
<input type="reset" value="Clear">
</form>
</body></html>
```

![](bbox=[0.295, 0.675, 0.955, 0.945])
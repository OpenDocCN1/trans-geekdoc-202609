
If we examine the above script for changes, we find that there are only two. The first adds a ‘name’ attribute to the ‘submit’ input type to allow us to refer to it from within the PHP script:

```
<p><input type="submit" name="submit"/>
```

The second change is to associate all of the PHP statements within an ‘if’ construct. The expression to be evaluated within the ‘if’ construct is:

```
if (isset($_POST["submit"]) ) {
  ...
}
```

The ‘if’ statement contains a function, isset(). The function returns true if a variable has been set and false if it has not and that variable in this case is $_POST["submit"]. The value of $_POST["submit"] is true if the submit button has been clicked. This means that the PHP statements within the ‘if’ construct are only invoked after the form’s submit button is clicked. Therefore, the first time the script is executed no spurious text is output. The output from the above script is illustrated in Figure 10.8.

## 10.4 Invoking the correct script

In our previous examples, we have ‘hard coded’ into our form the name of the script to be invoked when the form is submitted, for example:

```
<form action='example10-3.php' method='post'>
```

### FIGURE 10.8 Working form with combined PHP and XHTML

![](img/b2471264f405d17994ef173e4b9cec92_306_0.png)

However, it would be great if we could write a script which always knew its name and would invoke that script automatically.

There is a server variable (we mentioned these in Lesson 1) which contains the name of the current script. It is:

```
$_SERVER["PHP_SELF"]
```

If we were to echo its contents as part of the form element this would ensure that the script would always call itself, no matter what name it had been saved as. The form element would look like this:

```
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
```

> NOTE  We shall be using $_SERVER ["PHP_SELF"] in all form scripts from this point on.

## 10.5 An example form

It’s about time we put our knowledge of forms being able to interact with PHP scripts to some good use. What we have below is a revised version of the answer to the Arabic to Roman date converter script which was the subject of Exercises:

```
<h2>Please enter a date in Arabic numerals:</h2>
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p>
<label for="intDate">Date: </label>
<input type="text" name="intDate" id="intDate"/></p>
<p><input type="submit" name="SubmitQuery"/></p>
</form>
<?php
// File: example10-4.php
if (isset($_POST["intDate"]) ) {
    $intDate = $_POST["intDate"];
    echo "<p>$intDate is written ";
    while ($intDate >= 1000) {
        echo "M";
        $intDate -= 1000;
    }
    if ($intDate >= 900) {
        echo ("CM");
        $intDate -= 900;
    }
    if ($intDate >= 500) {
echo "D";
$intDate -= 500;
}
if ($intDate >= 400) {
    echo ("CD");
    $intDate -= 400;
}
while ($intDate >= 100) {
    echo "C";
    $intDate -= 100;
}
if ($intDate >= 90) {
    echo ("XC");
    $intDate -= 90;
}
if ($intDate >= 50) {
    echo "L";
    $intDate -= 50;
}
if ($intDate >= 40) {
    echo ("XL");
    $intDate -= 40;
}
while ($intDate >= 10) {
    echo "X";
    $intDate -= 10;
}
if ($intDate >= 9) {
    echo ("IX");
    $intDate -= 9;
}
if ($intDate >= 5) {
    echo "V";
    $intDate -= 5;
}
if ($intDate >= 4) {
    echo ("IV");
    $intDate -= 4;
}
while ($intDate >= 1) {
    echo "I";
    $intDate -= 1;
}
echo " in Roman numerals</p>";
}
?>
```

![](img/b2471264f405d17994ef173e4b9cec92_308_0.png)

Figure 10.9 illustrates the output from the above script.

The above script is an improvement on the previous model solution because the form allows the user to repeatedly change the date they wish to convert without changing the

### FIGURE 10.9 Arabic to Roman numeral conversion

![](img/b2471264f405d17994ef173e4b9cec92_309_0.png)

script itself. Let's take a look at what the script is doing:

```
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p>
<label for="intDate">Date: </label>
<input type="text" name="intDate" id="intDate"/></p>
<p><input type="submit" name="SubmitQuery"/></p>
</form>
```

The form component is actually very simple compared to our last script in that it only contains a single input text field and a submit button.

Next, an ‘if’ construct checks to see if we have an intDate form data field:

```
if (isset($_POST["intDate"]) ) {
```

If so, then the form data field value is assigned to a variable:

```
$intDate = $_POST["intDate"];
```

The remainder of the script consists of a number of sets of ‘while’ and ‘if’ constructs. Each one performs exactly the same function for each of the Roman numerals. Consider the first ‘while’ and ‘if’ construct pair:

```
while ($intDate >= 1000) {
    echo "M";
    $intDate -= 1000;
}
if ($intDate >= 900) {
    echo ("CM");
    $intDate -= 900;
}
```

The first ‘while’ loop iterates displaying the value ‘M’ and subtracting 1000 from the value of $intDate until the value of $intDate is below 1000. Next, the ‘if’ construct checks to see if the remaining value of $intDate is greater or equal to 900. We need to check this for the special case of placing a ‘C’ in front of the ‘M’, to indicate 900. If the value of $intDate
is greater than 900 then the value ‘CM’ is displayed and the value of $intDate is reduced by 900. A number of ‘while’ and ‘if’ constructs repeat the processing of the date for each Roman numeral down to ‘I’.

| NOTE | If you think that the script design looks wasteful and that there should be a cleaner and better way of coding this script then you would be right. We shall return to this example later, in Chapter 12. |
|------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

## 10.6 Accessing form elements

So far we have illustrated how to access form data entered in input text fields. Input password field data is accessed in exactly the same way. We shall continue by examining how to access data from the various other form elements we can use.

### Radio buttons

The radio entry type is another form field we can interact with. It does not allow the user to enter any text but provides a series of ‘radio buttons’ from which the user can make a selection. Only one of the buttons grouped together can be selected. An example of the radio type is shown in the script below:

```
<h2>Please select your favourite color:</h2>
<form action='<?php echo $_SERVER["PHP_SELF"]; ?>' method='post'>
<p>
<label for="strBlue">Blue: </label>
<input type='radio' name='strColor' value='blue' id='strBlue'/>
<label for="strGreen">Green: </label>
<input type='radio' name='strColor' value='green' id='strGreen'/>
<label for="strYellow">Yellow: </label>
<input type='radio' name='strColor' value='yellow' id='strYellow'/>
<label for="strRed">Red: </label>
<input type = 'radio' name = 'strColor' value = 'red' id = 'strRed'/>
</p>
<p><input type = 'submit' name = 'submit'/></p></form>
<?php
// File: example10-5.php
if (isset($_POST["submit"]) ) {
$strColour=$_POST["strColor"];
echo "<p>Your favourite color is $strColor</p>";
}
?>
```

The script outputs a simple form which contains a series of labels and radio buttons:

```
<label for="strBlue">Blue: </label>
<input type='radio' name='strColor' value='blue' id='strBlue'/>
```

```
<label for="strGreen">Green: </label>
<input type='radio' name='strColor' value='green' id='strGreen'/>
<label for="strYellow">Yellow: </label>
<input type='radio' name='strColor' value='yellow' id='strYellow'/>
<label for="strRed">Red: </label>
<input type='radio' name='strColor' value='red' id='strRed'/>
```

Note that each of the radio buttons has a different value assigned to it but all the names are the same.

> NOTE In order to ensure that the form knows which buttons form a group, all grouped buttons must share the same name.

The PHP script which processes the form data assigns the value of the radio button field into variable $strColor:

```
if (isset($_POST["submit"]) ) {
    $strColour= $_POST["strColor"];
    echo "<p>Your favorite color is $strColor</p>";
}
```

A simple echo statement is then used to output the user's selected color. The output from the above script is shown in Figure 10.10.

### Checkboxes

Checkbox fields enable the user to select as many options as they like from a form. Each checkbox is given a unique name. An example of the use of the checkbox form field is

### FIGURE 10.10 Accessing radio button data

![](img/b2471264f405d17994ef173e4b9cec92_311_0.png)

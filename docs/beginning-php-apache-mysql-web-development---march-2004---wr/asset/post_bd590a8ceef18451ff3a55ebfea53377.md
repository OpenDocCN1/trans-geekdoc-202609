
![](img/7b817c5b51395b5dcaba58e6a2bc6daa_165_0.png)

- 6. Enter your name and click the Submit button.

The display page that appears, shown in Figure 5-5, is rather simple; it holds only debug information and a greeting.

## How It Works

As you see, this code uses logic similar to that in formprocess1.php. Two fields have been added (drop-down list box and a checkbox).

formprocess2.php does the same thing as formprocess1.php but with an added twist. It displays the debugging information only if the Debug checkbox is selected and greets you using any of the drop-down list choices in the subsections that follow.

## Chapter 5

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_166_0.png)

## INPUT Checkbox Type

The checkbox can represent only two possibilities: When checked, it passes the value on to the $_POST array, but otherwise it just doesn't send anything. This is a great way to represent Boolean typed data.

```
+ SELECT element
<SELECT name="Greeting">
<option value="Hello">Hello</option>
<option value="Hola">Hola</option>
<option value="Bonjour">Bonjour</option>
</SELECT>
```

The SELECT element (also known as list) allows you to display a fixed list of choices from which the user has to choose an element. The item selected won't be sent displayed but will be sent as its value. In this example, the value and its display are identical, but in a database-driven system you will probably see record IDs as the values and their text label as list choices. A good example is a product number and its name.

## Form Elements: Letting the User Work with Data

When using lists, be sure to set the value part of the OPTION items. If these are not set, the list looks all the same but is totally useless because all choices will send the null value.

## One Form, Multiple Processing

Forms always run in a predefined way based on how you code your processing script to handle the data that the user sends to the system. A single form can have more than one defined action by using different submit buttons.

## Try It Out Radio Button, Multi-Line List Boxes

In the following example, you create a form that prepares a search and creates a movie/actor/director interface.

- 1. Create a file named form3.php and open it in your text editor. Then type the following code:

```html
<<html>
<head>
  <TITLE>Add/Search Entry</TITLE>
</head>
<body>
<form action="formprocess3.php" method="post">
<table border="0" cellspacing="1" cellpadding="3" bgcolor="#353535" align="center">
<tr>
<td bgcolor="#ffffff" width="50%">
  Name
</td>
<td bgcolor="#ffffff" width="50%">
  <INPUT type="TEXT" name="Name">
</td>
</tr>
<tr>
<td bgcolor="#ffffff">
  What are you looking for
</td>
<td bgcolor="#ffffff">
  <SELECT name="MovieType">
  <option value="" SELECTED>Select a movie type...</option>
  <option value="Drama">Drama</option>
  <option value="Comedy">Comedy</option>
  <option value="Sci-Fi">Sci-Fi</option>
  <option value="War">War</option>
  <option value="Other">Other...</option>
  </SELECT>
</td>
</tr>
<tr>
<td bgcolor="#ffffff">
  Add what?
</td>
</tr>
</table>
</form>
</body>
</html>
```

```html
<td bgcolor="#ffffff">
<INPUT type="radio" name="type" value="Movie" CHECKED>
Movie<BR>
<INPUT type="radio" name="type" value="Actor">
Actor<BR>
<INPUT type="radio" name="type" value="Director">
Director<BR>
</td>
</tr>
<tr>
<td bgcolor="#ffffff" width="50%">
Display Debug info
</td>
<td bgcolor="#ffffff" width="50%">
<INPUT type="checkbox" name="Debug" CHECKED>
</td>
</tr>
<tr>
<td bgcolor="#ffffff" colspan="2" align="center">
<INPUT type="SUBMIT" name="Submit" value="Search">
<INPUT type="SUBMIT" name="Submit" value="Add">
</td>
</tr>
</table>
</form>
</body>
</html>
```

2. Create another file named formprocess3.php and edit it to the following code:

```php
<?php
if ($_POST['type'] == "Movie" && $_POST['Movie'] == "") {
  header("Location:form3.php");
}
$title = $_POST['Submit'] . ": " . $_POST['Name'];
<html>
<head>
<TITLE><?php echo $title?></TITLE>
</head>
<body>
<?php
if ($_POST['Debug'] == "on") {
<PRE>
<?php
print_r($_POST);
?>
</PRE>
}
<?php
$name = $_POST['Name'];
$name[0] = strtoupper($name[0]);

if ($_POST['type'] == "Movie") {
    $foo = $_POST['Movie'] . " " . $_POST['type'];
} else {
    $foo = $_POST['type'];
}
?>
<p align="center">
You searched for <?php echo $foo?> named <?php echo $name?>
</p>
</body>
</html>
```

- 3. Start your browser and open http://localhost/form3.php.

The form shown in Figure 5-6 appears. Notice that the form has two submit buttons. One labeled Search, the other Add.

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_169_0.png)

- 4. Type Kevin in the Name field.
5. Leave Movie Type as is; then move on to Item Type field, which you select Actor.
6. Clear the Debug checkbox if you like; then click the Search button.

The results appear, as shown in Figure 5-7.

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_170_0.png)

Now play around a bit with the form. Look at the output and how it changes when you modify the data.

## How It Works

You coded a simple form with two possible actions. Depending on the button you click and the data you enter, this code outputs different information. What's new in the form itself? A group of radio buttons and a new submit button have been added. Let's have a closer look at these.

## Form Elements: Letting the User Work with Data

### Radio Element

The radio button is a very simple element. By default, if no radio button is specified as CHECKED, no default choice is made. Always remember choosing the default value is a very important part of building a form. Users often leave defaults in forms (it is a form of laziness, to speak).

```
<INPUT type="radio" name="type" value="Movie" CHECKED>
Movie<BR>
<INPUT type="radio" name="type" value="Actor">
Actor<BR>
<INPUT type="radio" name="type" value="Director">
Director<BR>
```

For multiple radio buttons to be linked as a group and processed as a single form element, they need to share the same name and different values (quite obviously). In the preceding code, the name is always type. This tells the browser that selecting one of the radio buttons clears the others.

## Multiple Submit Buttons

As with radio buttons, submit buttons share the same name with a different value. Clicking one of these submits the form.

```
<INPUT type="SUBMIT" name="Submit" value="Search">
<INPUT type="SUBMIT" name="Submit" value="Add">
```

As you can see in the DEBUG block, the submit button sends its own information to the script. You can access the submit value through the $_POST['Submit'] array.

### Basic Input Testing

What about the processing script? What's new in here?

The following code checks that the item type is Movie, and if it is, it checks that the user has selected a valid movie type from the form. If he has not, he is redirected to the form page.

The test is a simple if with an and operator. (In simple parlance, if the item type is movie and the movie type is not specified, you go back to square one and get nothing.)

```php
if ($_POST['type'] == "Movie" && $_POST['MovieType'] == "") {
    header("Location:form3.php");
}
```

The header function allows you to send a raw HTTP header. It is useful for handling security problems and access restrictions. In this instance it redirects the user to the specified page.

> A very common error with beginning PHP users is that they fail to understand a simple fact: Once sent, the headers cannot be sent again. This means that any echo, any space, any tabulation before the call to the header function will trigger a warning in the script execution. Here are a few typical errors:

```php
<?php
header("Location:form3.php");
?>
```

This code will fail. The empty line starting the script will send the headers with a carriage return and a line feed (depending on the operating system).

```php
<?php
echo "foobar";
header("Location:form3.php");
?>
```

This code will fail. The echo function will send the headers with the text "foobar".

### Dynamic Page Title

This code is rather simple to understand: you don't start output as soon as you start executing the PHP script. What often happens is at the start of the scripts there will be a check for intrusion and context verification. In this instance, you dynamically set the page title using the action type and item type you will to handle the page.

```php
$title = $_POST['Submit'] . ": " . $_POST['type'] . " " . $_POST['Name'];
?>
<html>
<head>
<TITLE><?php echo $title?></TITLE>
...
```

### Ternary Operator

ThisThis line holds a ternary comparison operation. Ternary operators are not PHP-specific; many other languages, such as C, use them.

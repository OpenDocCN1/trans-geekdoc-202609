

| Method | Description |
|---|---|
| setAutoFill( $fill, $body ) | This function tells HTML_Table to pre-populate newly created empty table cells with a string value. $fill is the string to insert into empty cells when they're created. The optional $body argument works like its counterpart in addRow(). |
| toHtml() | Returns the HTML markup to display the table. Call this method once you've created your table to retrieve the HTML for inserting into the Web page. |

You can find a complete list of HTML_Table methods at http://pear.php.net/manual/en/package.html.html-table.php.

To create a table, you first create a new HTML_Table object to store the table data and other settings, then call various methods of that object to add data cells, format the table, and so on. When you're done, call the object's toHtml() method to retrieve the markup for displaying the table.

## Try It Out Displaying Fibonacci Numbers with HTML_Table

Chapter 4 featured a script that used looping to display the first few numbers of the Fibonacci sequence. The numbers were displayed in an HTML table by outputting the HTML markup for the table directly.

In this example, you rewrite this script to use HTML_Table to generate the markup. Save the following script as fibonacci2.php in your document root folder.

```php
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Fibonacci sequence using HTML_Table</title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style type="text/css">
th { text-align: left; background-color: #999; }
th, td { padding: 0.4em; }
tr.alt td { background: #ddd; }
</style>
</head>
<body>
<h2>Fibonacci sequence using HTML_Table</h2>
<?php
require_once ( "HTML/Table.php" );
$attrs = array( "cellspacing" => 0, "border" => 0, "style" => "width: 20em;
border: 1px solid #666;" );
$table = new HTML_Table( $attrs );
$table->addRow( array( "Sequence #", "Value" ), null, "th" );

$iterations = 10;

$num1 = 0;
$num2 = 1;

$table->addRow( array( "F<sub>0</sub>", "0" ) );
$table->addRow( array( "F<sub>1</sub>", "1" ) );

for ( $i=2; $i <= $iterations; $i++ )
{
    $sum = $num1 + $num2;
    $num1 = $num2;
    $num2 = $sum;
    $table->addRow( array( "F<sub>$i</sub>", $num2 ) );
}

$attrs = array( "class" => "alt" );
$table->altRowAttributes( 1, null, $attrs, true );
echo $table->toHtml();
?>
</body>
</html>
```

When you run the script, you should see a page more or less the same as the one produced by the script in Chapter 4. Figure 15-2 shows the result.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_490_0.png)

Figure 15-2

## How It Works

After creating an XHTML page header — including additional CSS rules to style the table — the script includes the HTML_Table PEAR package:

```
require_once ( "HTML/Table.php" );
```

Next, the script sets up an associative array of attributes for the opening `<table>` tag, then creates a new HTML_Table object with these attributes:

```
$attrs = array( "cellspacing" => 0, "border" => 0, "style" => "width: 20em;
border: 1px solid #666;" );
$table = new HTML_Table( $attrs );
```

The two-cell table header row is then created by calling the object’s addRow() method, passing in an array of cell data. Notice that the $type argument is set to "th" to ensure that header cells are created:

```
$table->addRow( array( "Sequence #", "Value" ), null, "th" );
```

The rest of the script is much like the script in Chapter 4, with calls to HTML_Table methods replacing the old HTML markup. After setting up the number of iterations and the two number variables, the first two non-header rows of the table are created:

```
$table->addRow( array( "F<sub>0</sub>", "0" ) );
$table->addRow( array( "F<sub>1</sub>", "1" ) );
```

Within the loop, new rows are added to the table, again by calling addRow():

```
$table->addRow( array( "F<sub>$i</sub>", $num2 ) );
```

After the loop, the altRowAttributes() method is called to set up the alternate table rows. Counting from the row after the header row, every second row is given a CSS class of “alt”:

```
$attrs = array( "class" => "alt" );
$table->altRowAttributes( 1, null, $attrs, true );
```

Finally, it’s just a case of calling the table object’s toHtml() method to display the table markup:

```
echo $table->toHtml();
```

You can see from this example how easy it is to create tables with HTML_Table. The resulting PHP code is also clean and easy to modify. Furthermore, once you start using HTML_Table methods such as setAutoGrow() and setCellContents() you can create — and modify — quite complex tables in just a few lines of code.

## Web Forms the Easy Way with HTML_QuickForm

Just as HTML_Table lets you create HTML tables programmatically — thereby making your code clean and flexible — the HTML_QuickForm package provides a class for creating Web forms without needing to include a single line of HTML in your scripts. What's more, HTML_QuickForm can process the forms it creates, relieving you of the burden of writing (and testing) your own validation, filtering, and error-reporting code.

In the following sections you take a brief look at the functionality available in the HTML_QuickForm package, and then you create a membership form script using the power of HTML_QuickForm.

### Installing HTML_QuickForm

Installation of HTML_QuickForm is much as you'd expect. On Ubuntu, for example, just run `pear install --alldeps HTML_QuickForm`:

```
$ pear install --alldeps HTML_QuickForm
downloading HTML_QuickForm-3.2.10.tgz ...
Starting to download HTML_QuickForm-3.2.10.tgz (101,851 bytes)
.................done: 101,851 bytes
downloading HTML_Common-1.2.4.tgz ...
Starting to download HTML_Common-1.2.4.tgz (4,519 bytes)
...done: 4,519 bytes
install ok: channel://pear.php.net/HTML_Common-1.2.4
install ok: channel://pear.php.net/HTML_QuickForm-3.2.10
$
```

Once installed, you should find that there are some example scripts in the doc/HTML_QuickForm/docs/ folder inside your PEAR folder. You can also read the full documentation for HTML_QuickForm at http://pear.php.net/manual/en/package.html.html-quickform.php.

### Working with HTML_QuickForm

To use HTML_QuickForm, you first create a new HTML_QuickForm object, and then call various methods to add elements — such as fields and labels — to the form. You can also add validation rules to make sure that the data entered for each field is correct, and filters to remove unacceptable data from each field. You can then call various methods to validate the form, process the form, or display the form in the page (including any error messages to display to the user).

Here are some of the most useful methods of the HTML_QuickForm class:

| Method | Description |
| :--- | :--- |
| `HTML_QuickForm (<br>$formName, $method,<br>$action, $target, $attrs,<br>$trackSubmit )` | The `HTML_QuickForm` constructor. All arguments are optional.<br><br>`$formName` is the name of the form, included in the `<form>` tag's name attribute. `$method` is the form sending method ("get" or "post", defaults to "post"). `$action` is the form's action attribute — that is, the URL to send the form to. Leave blank to send the form back to the current script.<br><br>`$target` is the target attribute, which lets you open the form handler URL in a new window, for example. `$attrs` is an array of HTML attributes (as name/value pairs) to add to the opening `<form>` tag.<br><br>Finally, `$trackSubmit`, if set to `true`, adds a hidden field to the form to track if it's been submitted or not. It defaults to `false`. |
| `addElement()` | Adds an element to the form, and returns the element object that was created. The arguments that you need to pass in depend on the element you're creating. For example, to add a text input control with a name of "age" and a label of "Your Age", you might write: `$form->addElement( "text", "age", "Your Age")`. You can also pass in an `HTML_QuickForm_element` object created with `createElement()`. |
| `createElement()` | Creates and returns a form element as an `HTML_QuickForm_element` object. You can then pass this element to `addElement()` to add it to the form, or `addGroup()` to add it to a group in the form. The exact arguments to pass in depend on the type of element you're creating. |
| `addGroup( $elements,<br>$name, $groupLabel,<br>$separator, $appendName )` | Adds a group of elements to the form. Element groups allow you to treat a bunch of elements much like a single element.<br><br>They're useful for visually grouping elements in a form, and also for logical grouping (such as creating a group of related radio buttons).<br><br>`$elements` is the array of elements to add. `$name` is the name of the group, and `$groupLabel` is the label to display next to the group in the form. `$separator` is the markup to use to separate elements in the group. Set `$appendName` to `true` to include the group name in each element name in the group (for example, "myGroup[myElement]" instead of just "myElement"). This setting defaults to `false`.<br><br>All arguments except `$elements` are optional. |


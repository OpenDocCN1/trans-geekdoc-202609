
The tasks are performed in three programs:

- ChoosePetCat.php: Creates the pet type form (task 1)
- ChoosePetName.php: Checks the pet category data and creates the pet information form (tasks 2 and 3)
- AddPet.php: Checks the pet name field, stores the new pet in the catalog database, and provides feedback (tasks 4, 5, and 6)

## Writing ChoosePetCat

The first program produces a Web page with an HTML form where the person adding a pet can select a pet type for the pet. To make the program easier to read and maintain, as I discuss in Chapter 10, keep some of the HTML statements used by the program in a separate file that you bring into the program by using an include statement. Listing 11-4 shows ChoosePetCat.php.

### Listing 11-4: Program That Lets User Select a Pet Type

```
<?php
    /* Program: ChoosePetCat.php
     * Desc:    Allows users to select a pet type. All the
     *          existing pet types from the PetType table
     *          are displayed. A section to enter a new
     *          pet type is provided. Selections are
     *          provided as radio buttons, with text
     *          fields for new category name and
     *          description.
     */
?>
<html>
<head><title>Pet Types</title></head>
<body>
<?php
    include("misc.inc");
    $connection = mysql_connect($host,$user,$password)
        or die ("couldn't connect to server");
    $db = mysql_select_db($database,$connection)
        or die ("Couldn't select database");

    /* gets types from PetType table in alphabetical order */
    $query="SELECT petType FROM PetType ORDER BY petType";  /*23 */
    $result = mysql_query($query)
        or die ("Couldn't execute query.");

    /* Display text before form */
    echo "<div style='margin-left: .1in'>";
    <p><h3>Select the category for the pet you are adding.</h3>
        If you are adding a pet in a category that is not
        listed, choose <b>New Category</b> and type the name
```

### Listing 11-4 (continued)

```
and description of the category. Press <b>Submit Category</b> when you have finished selecting an existing category or typing a new category.\n";

/* Create form containing selection list */
echo "<form action='ChoosePetName.php' method='POST'>\n";
echo "<table cellpadding='5' border='0'>\n";
echo "<tr>";
$counter=0;                                   #40
while ($row = mysql_fetch_array($result))     #41
{
    extract($row);
    echo "<td>";
    <input type='radio' name='category' value='$petType'>;
        if ($counter == 0)                    #46
        {
            echo "checked";
        }
    echo ">$petType </td>\n";                #50
    $counter++;                               #51
}
echo "</tr></table>\n";

include("NewCat_table.inc");                 #55

echo "<p><input type='submit' value='Submit Category'>\n";
echo "</form>\n";
?>
</div>
</body></html>
```

The following numbers correspond to the line numbers shown as comments at the end of lines in Listing 11-4. Only some of the lines are documented in the following list. Many of the tasks in the listing, such as connecting to the database, creating forms, and executing queries, are found in most of the programs in this application; refer to Listing 11-2 for an explanation. The following list provides a brief explanation of what the following lines do in the program:

- 23 A query that selects all the pet types from the PetType table and sorts them in alphabetical order.
- 40 Creates a counter with a starting value of 0. The counter will keep track of how many pet types are found in the database.
- 41 Starts a while loop that executes once for each pet type. The loop creates a list of radio buttons for the pet types, with one button selected. Here are the details of the while loop:
    - 45 Echoes a form field tag for a radio button with the value equal to $petType. This statement executes once in each loop, creating a radio button for each pet type. This statement echoes only the first part of the form field tag.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_339_0.png)

46 An if block that executes only in the first loop. It echoes the word "checked" as part of the form field. This ensures that one of the radio buttons is selected when displayed so that the form can't be submitted with no button selected, which would result in unsightly error messages or warnings. The counter was set up solely for this purpose.

Although adding "checked" to every radio button works in some browsers, it causes problems in other browsers. The extra programming required to add "checked" to only one radio button can prevent problems.

50 Echoes the remaining part of the form field tag for the radio button — the part that closes the tag.

51 Adds 1 to the counter to keep track of the number of times that the loop has executed. This is the last line in the while loop.

55 Creates a table that asks for the new pet type name and description. The HTML for the table is read in from another file called NewCat_table.inc. As I discuss in Chapter 10, the HTML — especially HTML that describes a form — is often kept in a separate file to make the main program easier to read and to make the form easier to modify when necessary. This file is shown in Listing 11-5.

### Listing 11-5: File Containing New Type Form

```
<?php
    /* Program:  NewCat_table.inc
     * Desc:     HTML code that displays a table for input of a
     *           new category
     */
?>
<table width='100%'>
<tr><td colspan=3><hr></td></tr>
<tr>
    <td align='center'>
        <input type='radio' name='category' value='new'>&nbsp;
    </td>
    <td align='right'>Category name:</td>
    <td><input type='text' name='newCat' size='20'
                maxlength='20'></td>
</tr>
<tr><td align='center'><b>New Category</b></td>
    <td align='right'>Category description:</td>
    <td><input type='text' name='newDesc' size='70'
                maxlength='255'>
    </td>
</tr>
<tr><td colspan=3><hr></td></tr>
</table>
```

This file is all HTML except for a section of PHP in the top that holds the header as comments. I could actually have done this with HTML comments, but I like the PHP comment style better.

## Writing ChoosePetName

This second program accepts the data from the form in the first program. It checks the information and asks for missing information. After the pet type information is received correctly, the program creates a form where a user can select a pet name for the new pet being added to the catalog and type the information for the pet. This program, as in the preceding program, brings in some of the HTML forms and tables from separate files by using the `include` statement. This program also calls a function that's in an `include` file. This program brings in two files. Listing 11-6 shows `ChoosePetName.php`.

### Listing 11-6: Program That Asks User for Pet Name

```
```php
<?php
  /* Program: ChoosePetName.php
   * Desc:     Allows the user to enter the information for
   *           the pet. First, the program checks for a new
   *           category and enters it into the pettype table
   *           if it is new. Then, all pets in the selected
   *           category are displayed with radio buttons.
   *           The user can enter a new name. Fields are
   *           provided to enter the description, price, and
   *           picture file name.
   */
?>
<?php
  if (@$_POST['newbutton'] == "Return to category page"
      or @$_POST['newbutton'] == "Cancel")
  {
    header("Location: ChoosePetCat.php");
  }
?>
<html>
<head><title>Add Pet</title></head>
<body>
<?php
  include("misc.inc");
  include("functions.inc");

  $connection = mysql_connect($host,$user,$password)
      or die ("Couldn't connect to server");
  $db = mysql_select_db($database,$connection)
      or die ("Couldn't select database");

  $category = $_POST['category'];
  /* If new was selected for pet category, check if text
     fields were filled in. If they were not filled in,
     display them again for the user to enter the category
```

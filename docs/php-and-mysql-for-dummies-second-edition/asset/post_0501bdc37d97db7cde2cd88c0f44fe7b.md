
This file is all HTML with no PHP. It displays the section of the pet name Web page where the user can enter a new pet name.

## Listing 11-9: HTML That Creates Table for Pet Info

```
<?php
    /* Program: PetInfo_table.inc
     * Desc:      Displays table to collect pet information
     */
?>
<b>Pet Information</b><br>
<p><table>
<tr><td align="right">Pet Category:</td>
    <td><b>&nbsp;&nbsp;<?php echo $category ?></b></td>
</tr>
<tr><td align="right">Pet Description:</td>
    <td><input type="text" name="petDescription"
            value="<?php echo $petDescription ?>"
            size="65" maxlength="255">
    </td></tr>
<tr><td align="right">Price:</td>
    <td><input type="text" name="price"
            value="<?php echo $price ?>" size="15"
            maxlength="15">
    </td></tr>
<tr><td align="right">Picture file name:</td>
    <td><input type="text" name="pix"
            value="<?php echo $pix ?>" size="25"
            maxlength="25">
    </td></tr>
<tr><td align="right">Pet color (optional):</td>
    <td><input type="text" name="petColor"
            value="<?php echo $petColor ?>" size="25"
            maxlength="25">
    </td></tr>
</table>
```

This file includes small PHP sections for the variable values. Otherwise, it is HTML.

In addition to HTML for tables and forms, the ChoosePetName.php program in Listing 11-6 calls a function. The function is stored in a file named functions.inc and is included in the beginning of the program. Listing 11-10 shows the function.

## Listing 11-10: Function AddNewType()

```
<?php
/* Function addNewType
 * Desc     Adds a new pet type and description to the
 *          PetType table. Checks for the new pet type
 *          first and does not add it to the table if
 *          it is already there.
 */
function addNewType($petType,$typeDescription)
{
    /* Prepare data */
    $petType = ucfirst(strip_tags(trim($petType)));
    $typeDescription =
        ucfirst(strip_tags(trim($typeDescription)));

    /* Check whether new category is already in PetType table.
       If it is not in table, add it to table. */
    $query = "SELECT petType FROM PetType
              WHERE petType='$petType'";
    $result = mysql_query($query) or
        die ("Couldn't execute query ");

    $ntype = mysql_num_rows($result); //
    if ($ntype < 1) // if new type is not in table
    {
        $query = "INSERT INTO PetType (petType,typeDescription)
                  VALUES ('$petType','$typeDescription')";
        $result = mysql_query($query)
            or DIE ("Couldn't execute query ");
    }
    return;
}
?>
```

The function cleans the data first. Then it checks whether the pet type is already in the PetType table. If it is not, the function adds it to the table.

## Writing AddPet

This last program accepts the data from the form in the second program. If new was selected for the pet name, it checks to see that a new name was typed in and prompts for it again if it was left blank. After the pet name is filled in, the program stores the pet information from the previous page. Notice that it does not check the other information because the other information is optional. This program, as in the previous program, brings in some of the HTML forms and tables from two separate files by using the include statement. Listing 11-11 shows AddPet.php.

## Listing 11-11: Program That Adds New Pet to Catalog

```php
<?php
  /* Program: AddPet.php
   * Desc:    Adds new pet to the database. A confirmation
   *          screen is sent to the user.
   */

  if (@$_POST['newbutton'] == "Cancel")                         #7
  {
      header("Location: ChoosePetCat.php");
  }
  $petName = $_POST['petName'];
  $newName = $_POST['newName'];
  $price = $_POST['price'];
  $pix = $_POST['pix'];
  $petColor = $_POST['petColor'];
  $category = $_POST['category'];
  $petDescription = $_POST['petDescription'];

  if ($petName == "new")                                        #18
  {
      if ($newName == "")                                       #20
      {
          include("NewName_form.inc");
          exit();
      }
      else                                                       #25
      {
          $petName=trim($newName);
          $petName=ucfirst(strtolower(strip_tags($petName)));
      }
  }
  if ($pix == "")                                               #31
      $pix = "na.gif";

?>
<html>
<head><title>Add Pet</title></head>
<body>
<?php
  include("misc.inc");
  $connection = mysql_connect($host,$user,$password)
      or die ("Couldn't connect to server");
  $db = mysql_select_db($database,$connection)
      or die ("Couldn't select database");
  /* Clean the data */
  $petDescription = strip_tags(trim($petDescription));
  $price = strip_tags(trim($price));
  $pix = strip_tags(trim($pix));
  $petColor = strip_tags(trim($petColor));

  $query = "INSERT INTO Pet
      (petName,petType,petDescription,price,pix) VALUES
('$petName','$category','$petDescription','$price',
'$pix');
$result = mysql_query($query)
    or die ("Couldn't execute query.");
$petID = mysql_insert_id();                      #55

echo "The following pet has been added to the
    Pet Catalog:<br>
    <ul>
    <li>Category: $category
    <li>Pet Name: $petName
    <li>Pet Description: $petDescription
    <li>Price: $price
    <li>Picture file: $pix \n";

if ($petColor != "")
{                                            #66
    if ($petName == "Goldfish" or $petName == "Parakeet")
    {
        $query = "SELECT petName FROM Color
                    WHERE petName='$petName'
                    AND petColor='$petColor'";
        $result = mysql_query($query)
            or die ("Couldn't execute query.");
        $num = mysql_num_rows($result);
        if ($num < 1)
        {
            $query = "INSERT INTO Color (petName,petColor,pix)
                        VALUES ('$petName','$petColor','$pix')";
            $result = mysql_query($query)
                or die ("Couldn't execute query.");
            echo "<li>Color: $petColor\n";
        }
    }
    echo "</ul>";
    echo "<a href='ChoosePetCat.php'>Add Another Pet</a>\n";
?>
</body></html>
```

Notice the line numbers shown as comments at the end of lines in Listing 11-11. The numbers in the following list correspond to the line numbers in the listing. I document only some of the lines in the following list because many of the most common tasks, such as connecting to the database, have been documented for the previous programs in this chapter.

- 7. Checks whether the user clicked the Cancel button. If so, returns to the first page.
- 18 Starts an if block that executes only if the user selected new for the pet name. If the new name is blank, it displays a form that asks for the new pet name (line 20) repeatedly until the user types one in. After the new name is filled in, $petName is set to the new name (line 25).
- 31 If the picture filename was not typed in, it is set to the default picture.
- 38 Lines 38-55 add the new pet to the database. The data is cleaned before it's added.
- 57 Starts echoing the feedback page.
- 66 Starts an if block that executes only if the color was filled in. The color is only stored for parakeets and goldfish. The Color table is checked to see whether the name and color are already there. If not, they are added to the Color table. The if block ends on line 85.

This program brings in an HTML file that creates the form to prompt the user for the pet name if the user forgot to type it in. Listing 11-12 shows the file that is included: NewName_form.inc.

## Listing 11-12: HTML That Asks User for a New Pet Name

```
<?php
/* Program: NewName_form.inc
 * Desc:      Displays form to collect a pet name
 */
?>
<b>You must type a pet name.</b>
<form action="AddPet.php" method="post">
<table><tr>
<td align="right">Pet name:</td>
<td><input type="text" name="newName"
value="<?php echo $newName ?>"
size="25" maxlength="25">
</td></tr>
</table>
<input type="hidden" name="category"
value="<?php echo $category ?>">
<input type="hidden" name="petName"
value="<?php echo $petName ?>">
<input type="hidden" name="petDescription"
value="<?php echo $petDescription ?>">
<input type="hidden" name="price"
value="<?php echo $price ?>">
<input type="hidden" name="pix" value="<?php echo $pix ?>">
<input type="hidden" name="petColor"
value="<?php echo $petColor ?>">
<p><input type="submit" name="newbutton"
value="Enter new pet name">
<input type="submit" name="newbutton" value="Cancel">
</form>
```

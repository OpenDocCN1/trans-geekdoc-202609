# Listing 8-11: **Program to Build a List of Check Boxes**

```
<?php
/* Program name: buildCheckbox.php
   Description:  Program displays a list of
                 checkboxes from database info.
*/
echo "<html>
      <head><title>Pet Types</title></head>
      <body>";
$user="catalog";
$host="localhost";
$password="";
$database = "PetCatalog";

$connection = mysql_connect($host,$user,$password)
    or die ("Couldn't connect to server");
$db = mysql_select_db($database,$connection)
    or die ("Couldn't select database");
$query = "SELECT DISTINCT petType FROM Pet
              ORDER BY petType";
$result = mysql_query($query)
    or die ("Couldn't execute query.");

echo "<div style='margin-left: .5in'>
<p>&nbsp;
<p><b>Which type of pet are you interested in?</b>
<p>Choose as many types of pets as you want:\n";

/* create form containing checkboxes */
echo "<form action='processform.php' method='POST'>\n";

while ($row = mysql_fetch_array($result))
{
    extract($row);
    echo "<input type='checkbox' name='interest[$petType]'
             value='$petType'>$petType\n";
    echo "<br>\n";
}
echo "<p><input type='submit' value='Select Type of Pet'>
      </form>\n";
?>
</div></body></html>
```

This program is very similar to the program in Listing 8-10 that builds a list of radio buttons. However, notice that the input field uses an array `$interest` as the name for the field. This is because more than one check box can be selected. This program will create an element in the array with a key/value pair for each check box that’s selected. For instance, if the user selects both *horse* and *dragon*, the following array is created:
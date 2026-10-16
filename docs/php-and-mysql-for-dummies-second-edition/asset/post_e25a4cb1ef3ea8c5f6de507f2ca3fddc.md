
## Listing 8-7: Program to Display HTML Form with Information

```php
<?php
/* Program name: displayAddress
 * Description: Script displays a form with address
 *              information obtained from the database.
 */
echo "<html>
    <head><title>Customer Address</title></head>
    <body>";
$labels = array( "firstName"=>"First Name:",
                "lastName"=>"Last Name:",
                "street"=>"Street Address:",
                "city" =>"City:",
                "state"=>"State:",
                "zip"=>"Zipcode:");
$user="admin";
$host="localhost";
$password="";
$database = "MemberDirectory";
$loginName = "gsmith";    // user login name

$connection = mysql_connect($host,$user,$password)
    or die ("Couldn't connect to server");
$db = mysql_select_db($database,$connection)
    or die ("Couldn't select database");
$query = "SELECT * FROM Member
          WHERE loginName='$loginName'";
$result = mysql_query($query)
    or die ("Couldn't execute query.");
$row = mysql_fetch_array($result);

echo "<p align='center'>
    <h1 align='center'>Address for $loginName</h1>\n";
echo "<br><p align='center'>
    <font size='+1'><b>Please check the information below
    and change any information that is incorrect.</b></font>
    <hr>";
echo "<form action='processAddress.php' method='POST'>
    <table width='95%' border='0' cellspacing='0'
    cellpadding='2'>\n";
foreach($labels as $field=>$label)
{
    echo "<tr>
        <td align='right' ><B>{$labels[$field]} </B></br></td>
        <td><input type='text' name='$field'
            value='$row[$field]' size='65' maxlength='65'>
        </td>
        </tr>";
}
echo "</table>
    <div align='center'><p><input type='submit'
        value='Submit Address' </p></div>
    </form>";
?>
</body></html>
```

Notice the following in the program in Listing 8-7:

- **The form statement transfers the action to the program** processAddress.php. This program processes the information in the form and updates the database with any information that the user changed. This is a program that you write yourself. Checking data in a form and saving information in the database are discussed later in this chapter in the sections “Checking the information” and “Putting Information into a Database”.
- **Each input field in the form is given a name.** The information in the input field is stored in a variable that has the same name as the input field.
- **The program gives the field names in the form the same names as the columns in the database.** This simplifies moving information between the database and the form, requiring no transfer of information from one variable to another.
- **The values from the database are displayed in the form fields with the value parameter in the input field statement.** The value parameter displays the appropriate value from the array $row, which contains data from the database.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_237_0.png)

For security reasons, always include maxlength in your HTML statement. maxlength defines the number of characters that a user is allowed to type into the field. If the information is going to be stored in a database, set maxlength to the same number as the width of the column in the database table.

Figure 8-6 shows the Web page resulting from the program in Listing 8-7. The information in the form is the information that is stored in the database.

## Building selection lists

One type of field that you can use in an HTML form is a selection list. Instead of typing into a field, your users select from a list. For instance, in a product catalog, you might provide a list of categories from which users select what they want to view. Or the form for users’ addresses might include a list of states that users can select. Or users might enter a date by selecting a month, day, and year from a list.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_237_1.png)

Use selection lists whenever feasible. When the user selects an item from a list, you can be sure that the item is accurate, with no misspelling, odd characters, or other problems introduced by users’ typing errors.

An HTML selection list for the categories in the Pet Catalog is formatted as follows:

When the user clicks the arrow on the select drop-down list box, the whole list drops down, as shown in Figure 8-8, and the user can select any item in the list. Notice that cat is selected until the user selects a different item.

When using PHP, your options can be variables. This capability allows you to build dynamic selection lists. For instance, you must maintain the static list of pet categories shown in the preceding example. If you add a new pet category, you must add an option tag manually. However, with PHP variables, you can build the list dynamically from the categories in the database. When you add a new category to the database, the new category is automatically added to your selection list without your having to change your PHP program. Listing 8-8 for program buildSelect.php builds a selection list of pet categories from the database.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_239_0.png)

Figure 8-8:
A selection field for the Pet Catalog with a drop-down list.

## Listing 8-8: Program to Build a Selection List

```php
<?php
/* Program name: buildSelect.php
 * Description: Program builds a selection list
 *              from the database.
 */
?>
<html>
<head><title>Pet Types</title></head>
<body>
<?php
$user="catalog";
$host="localhost";
$password="";
$database = "PetCatalog";

$connection = mysql_connect($host,$user,$password)
    or die ("couldn't connect to server");
$db = mysql_select_db($database,$connection)
or die ("Couldn't select database");
$query = "SELECT DISTINCT petType FROM Pet ORDER BY petType";
$result = mysql_query($query)
    or die ("Couldn't execute query.");

/* create form containing selection list */
echo "<form action='processform.php' method='POST'>
    <select name='petType'>\n";

while ($row = mysql_fetch_array($result))
{
    extract($row);
    echo "<option value='$petType'>$petType\n";
}
echo "</select>\n";
echo "<input type='submit' value='Select Type of Pet'>
    </form>\n";
?>
</body></html>
```

Notice the following in the program in Listing 8-8:

- **Using DISTINCT in the query:** DISTINCT causes the query to get each pet type only once. Without DISTINCT, the query would return each pet type several times if it appeared several times in the database.
- **Using ORDER BY in the query:** The pet types are sorted alphabetically.
- **echo statements before the loop:** The form and select tags are echoed before the while loop starts because they are echoed only once.
- **echo statements in the loop:** The option tags are echoed in the loop — one for each pet type in the database. No item is marked as selected, so the first item in the list is selected automatically.
- **echo statements after the loop:** The end form and select tags are echoed after the loop because they are echoed only once.

The selection list produced by this program is initially the same as the selection list shown in Figure 8-7, with cat selected. However, cat is selected in this program because it is the first item in the list — not because it's specifically selected as it is in the HTML tags that produce Figure 8-7. The drop-down list produced by this program is in alphabetical order, as shown in Figure 8-9.

You can also use PHP variables to set up which option is selected when the selection box is displayed. For instance, suppose that you want the user to select a date from month, day, and year selection lists. You believe that most people will select today's date, so you want today's date to be selected by default when the box is displayed. Listing 8-9 shows the program dateSelect.php, which displays a form for selecting a date and selects today's date automatically.

Figure 8-9: A selection field for the Pet Catalog produced by the program buildSelect.php.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_241_0.png)

## Listing 8-9: Program to Build a Date Selection List

```php
<?php
/* Program name: dateSelect.php
 * Description: Program displays a selection list that
 * customers can use to select a date.
 */
echo "<html>
<head><title>Select a date</title></head>
<body>";

/* create an array of months*/
$monthName = array(1=> "January", "February", "March",
"April", "May", "June", "July",
"August", "September", "October",
"November", "December");

$today = time(); //stores today's date
$f_today = date("M-d-Y",$today); //formats today's date

echo "<div align='center'>\n";

/* display today's date */
echo "<p>&nbsp;<h3>Today is $f_today</h3><hr>\n";

/* create form containing date selection list */
echo "<form action='processform.php' method='POST'>\n";

/* build selection list for the month */
$todayMO = date("m",$today); //get the month from $today
echo "<select name='dateMO'>\n";
for ($n=1;$n<=12;$n++)
{
 echo "<option value=$n\n";
 if ($todayMO == $n)
 {
```

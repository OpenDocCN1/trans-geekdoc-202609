
## Listing 8-13 (continued)

```
</tr>
<tr><td align='right'><B>|$label_array['last_name']|:</B></td>
<td> <input type='text' name='last_name' size='65' maxlength='65' value='$last_name'> </td>

</tr>
<tr><td align='right'><B>|$label_array['phone']|:</B></td>
<td> <input type='text' name='phone' size='65' maxlength='65' value='$phone'> </td>

</tr>
</table>
<p><input type='submit' value='Submit name and phone number'>
</form>
</center>";
exit();
}
echo "Welcome";
?>
</body></html>
```

Here are the differences between this program and the program in Listing 8-12:

- ✔ **This program creates two arrays for problem data.** It creates $blank_array, as did the previous program. But this program also creates $bad_format for fields that contain information that is not in an acceptable format.
- ✔ **This program loops through $bad_format to create a separate list of problem data.** If any fields are blank, it creates one error message and list of problem fields, as did the previous program. If any fields are in an unacceptable format, this program also creates a second error message and list of problem fields.

The Web page in Figure 8-14 results when the user accidentally types his or her first name into the Middle Name field and also types nonsense for his or her phone number. Notice that two error messages appear, showing that the First Name field is blank and that the Phone field contains incorrect information.

## Giving users a choice with multiple submit buttons

You can use more than one submit button in a form. For instance, in a customer order form, you might use a button that reads *Submit Order* and another button that reads *Cancel Order*. However, you can only list one program in the `action=programname` part of your `form` tag, meaning that the two buttons run the same program. PHP solves this problem. By using PHP, you can process the form differently, depending on which button the user clicks.

Figure 8-14:
The result of processing a form with both missing and incorrect information.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_259_0.png)

The following statements create a form with two submit buttons:

```
<form action="twoButtons.php" method="POST">
  <input type="text" name="last_name" maxlength="50"><br>
  <input type="submit" name="display_button"
    value="Show Address">
  <input type="submit" name="display_button"
    value="Show Phone Number">
</form>
```

Notice that the submit button fields have a name: display_button. The fields each have a different value. Whichever button the user clicks sets the value for $display_button. The program twoButtons.php in Listing 8-14 processes the preceding form.

## Listing 8-14: Program That Processes Two Submit Buttons

```
<?php
/* Program name: twoButtons.php
 * Description: Program displays different information
 *              depending on which submit button was
 *              pushed.
 */
```

## Listing 8-14 (continued)

```
*/
?>
<html>
<head><title>Member Address or Phone Number</title></head>
<body>
<?php
$user="admin";
$host="localhost";
$password="";
$database = "MemberDirectory";
$connection = mysql_connect($host,$user,$password)
    or die ("couldn't connect to server");
$db = mysql_select_db($database,$connection)
    or die ("Couldn't select database");
if ($_POST['display_button'] == "Show Address")
{
    $query = "SELECT street,city,state,zip FROM Member
              WHERE lastName='$_POST[last_name]'";
    $result = mysql_query($query)
        or die ("Couldn't execute query.");
    $row = mysql_fetch_array($result);
    extract($row);
    echo "$street<br>$city, $state  $zip<br>";
}
else
{
    $query = "SELECT phone FROM Member
              WHERE lastName='$_POST[last_name]'";
    $result = mysql_query($query)
        or die ("Couldn't execute query.");
    $row = mysql_fetch_array($result);
    echo "Phone: {$row['phone']}<br>";
}
?>
</body></html>
```

The program executes different statements, depending on which button is clicked. If the user clicks the button for the address, the program outputs the address for the name submitted in the form; if the user clicks the Show Phone Number button, the program outputs the phone number.

## Putting Information into a Database

Your application probably needs to store data in your database. For example, your database might store information that a user typed into a form for your use — a Member Directory is a good example of this. Or your database might store data temporarily during the application. Either way, you store data by sending SQL queries to MySQL. (I explain SQL queries in detail in Chapter 4.)

## Preparing the data

You need to prepare the data before storing it in the database. Preparing the data includes the following:

- Putting the data into variables
- Making sure that the data is in the format expected by the database
- Cleaning the data

## Putting the data into variables

You store the data by sending it to the database in an SQL query. You store the data in variables and include the variable names in the query. By using PHP, this process is simple. The user provides most of the data that you want to store via a form. As I discuss earlier in this chapter, PHP stores the data in a variable with the name of the form field, invisibly and automatically, without your having to store it yourself. You just use the variables that PHP provides. Occasionally, you want to store information that you generate yourself, such as today's date or a customer order number. You just need to store this information in a variable so that you can include it in a query.

## Using the correct format

When you design your database, you set the data type for each column. The data that you want to store must match the data type of the column that you want to store it in. For instance, if the column expects a data type integer, the data sent must be numbers. Or if the column expects data that's a date, the data that you send must be in a format that MySQL recognizes as a date. If you send incorrectly formatted data, MySQL still stores the data, but it might not store the value that you expected. Here's a rundown of how MySQL stores data for the most frequently used data types:

- **CHAR or VARCHAR**: Stores strings. MySQL stores pretty much any data sent to a character column, including numbers or dates, as strings. When you created the column, you specified a length. For example, if you specified `CHAR(20)`, only 20 characters can be stored. If you send a string longer than 20 characters, only the first 20 characters are stored. The remaining characters are dropped.
  
  Set the `maxlength` for any text input fields in a form to the same length as the column width in the database where the data will be stored. That way, the user can't enter any more characters than the database can store.
- **INT or DECIMAL**: Stores numbers. MySQL will try to interpret any data sent to a number column as a number, whether it makes sense or not. For instance, it might interpret a date as a number, and you could end up with a number like 2001.00. If MySQL is completely unable to interpret the data sent as a number, it stores 0 (zero) in the column.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_261_0.png)

- **DATE:** Stores dates. MySQL expects dates as numbers, with the year first, month second, and day last. The year can be two or four digits (2001 or 01). The date can be a string of numbers, or each part can be separated by a hyphen (-), a period (.), or a forward slash (/). Some valid date formats are 20011203, 980103, 2001-3-2, and 2000.10.01. If MySQL cannot interpret the data sent as a date, it stores the date as 0000-00-00.
- **ENUM:** Stores only the values that you allowed when you created the column. If you send data that is not allowed, MySQL stores a 0.

In many cases, the data is collected in a form and stored in the database as-is. For instance, users type their names in a form, and the program stores them. However, in some cases, the data needs to be changed before you store it. For instance, if a user enters a date into a form in three separate selection lists for month, day, and year (as I describe in the section, “Building selection lists,” earlier in this chapter), the values in the three fields must be put together into one variable. The following statements put the fields together:

```php
$expDate = $_POST['expYear']."-";
$expDate .= $_POST['expMonth']."-";
$expDate .= $_POST['expDay'];
```

Another case in which you might want to change the data before storing it is when you’re storing phone numbers. Users enter phone numbers in a variety of formats, using parentheses, dashes, dots, or spaces. Rather than storing these varied formats in your database, you might just store the numbers. Then when you retrieve a phone number from the database, you can format the number however you want before you display it. The following statement removes characters from the string:

```php
$phone = ereg_replace("[ ()-.]","",$_POST['phone']);
```

The function `ereg_replace` uses regular expressions to search for a pattern. The first string passed is the regular expression to match. If any part of the string matches the pattern, it is replaced by the second string. In this case, the regular expression is `[ ()-.]`, which means any one of the characters in the square brackets. The second string is `""`, which is a string with nothing in it. Therefore, any spaces, parentheses, dots, or hyphens in the string are replaced by nothing.

## Cleaning the data

The earlier section “Getting Information from the User,” which describes the use of HTML forms, discusses checking the data in forms. Users can type data into a text field, either accidentally or maliciously, that can cause problems for your application, your database, or your users. Checking the data and accepting only the characters expected for the information requested can prevent many problems. However, you can miss something. Also, in some

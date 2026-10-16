
166 Ends the case block for the New Member section of the login page.

168 Starts the case block for the default condition. If $do is not set to either "login" or "new", the program skips to this block. Because both the forms on the login page set $do, this block only executes the first time this program runs — when the user links to it from the storefront page and has not yet submitted either form. This section has only one statement: a statement that displays the login page.

This program shows the login page in many places. This is done with include statements that call the file login_form.inc. This file includes the HTML that produces the login page. The program Login.php does not produce any output at all. All the output is produced by login_form.inc. This type of application organization is discussed in Chapter 10. This is a good example of the use of include files. Just imagine this program, which is long enough, if the statements in login_form.inc, shown in Listing 12-3, were included in the Login program at each place where login_form is included. Whew, that would be a mess that only a computer could understand.

### Listing 12-3: File That Creates the Login Page

```php
<?php
/* File: login_form.inc
 * Desc: Displays login page. Page displays two forms--one
 *       form for entering an existing login name and
 *       password and another form for the information
 *       needed to apply for a new account.
 */
include("functions12.inc");          # 8
?>
<html>
<head><title>Members Only Login</title></head>
<body topmargin="0" leftmargin="0" marginheight="0"
      marginwidth="0">
<table border="0" cellpadding="5" cellspacing="0">
  <tr><td colspan="3" bgcolor="gray" align="center">
    <font color="white" size="+10">
      <b>Members Only Section</b></font></td></tr>
  <tr>
    <td width="33%" valign="top">
      <font size="+1"><b>Are you a member?</b></font>
      <p>
      <!-- form for customer login -->
      <form action="Login.php?do=login" method="POST">
      <table border="0">
<?php
        if (isset($message))
          echo "<tr><td colspan='2'>$message </td></tr>";
?>
<tr><td align=right><b>Username</b></td>
    <td><input type="text" name="fusername"
        size="20" maxlength="20">
    </td></tr>
<tr><td width="120" align="right"><b>Password</b>
</td>
    <td><input type="password" name="fpassword"
        size="20" maxlength="20"></td></tr>
<tr><td align="center" colspan="2">
    <br><input type="submit" name="log"
                value="Enter">
    </td></tr>
</table>
</form>
</td>
<td width="1" bgcolor="gray"></td>
<td width="67%">
<p><font size="+1"><b>Not a member yet?</b></font>
    Get discounts, a newsletter, advance notice of
    new pets, much more. Fill in the information
    below and join. It's easy and free! </b>
<!-- form for new member to fill in -->
<form action="Login.php?do=new" method="POST">
<p>
    <table border="0" width="100%">
<?php
        if (isset($message_new))                #55
            echo "<tr><td colspan='2'><b>$message_new</b>
                </td></tr>";
?>
        <tr><td align="right"><b>Member ID</b></td>
            <td><input type="text" name="newname"
                value="<?php echo @$newname ?>"
                size="20" maxlength="20"></td></tr>
        <tr><td align="right"><b>Password</b></td>
            <td><input type="password" name="newpass"
                value="<?php echo @$newpass ?>"
                size="10" maxlength="8"></td></tr>
        <tr><td align="right"><b>First Name</b></td>
            <td><input type="text" name="firstName"
                value="<?php echo @$firstName ?>"
                size="40" maxlength="40"></td></tr>
        <tr><td align="right"><b>Last Name</b></td>
            <td><input type="text" name="lastName"
                value="<?php echo @$lastName ?>"
                size="40" maxlength="40"></td></tr>
        <tr><td align="right"><b>Street</b></td>
            <td><input type="text" name="street"
                value="<?php echo @$street ?>"
                size="55" maxlength="50"></td></tr>
<tr><td align="right"><b>City</b></td>
    <td><input type="text" name="city"
        value="<?php echo @$city ?>"
        size="40" maxlength="40"></td></tr>
<tr><td align="right"><b>State</b></td>
    <td><select name="state">
<?php
    $stateName=getStateName();          #86
    $stateCode=getStateCode();          #87
    for ($n=1;$n<=50;$n++)
    {
        $state=$stateName[$n];
        $scode=$stateCode[$n];
        echo "<option value=\"$scode\"";
        if ($scode=="AL")
            echo " selected";
        echo ">$state\n";
    }
?>
    </select>
    &nbsp;&nbsp;&nbsp;&nbsp;<b>Zip</b>
    <input type="text" name="zip"
        value="<?php echo @$zip ?>"
        size="10" maxlength="10">
</td></tr>
<tr><td align=right><b>Phone</b></td>
    <td><input type="text" name="phone"
        value="<?php echo @$phone ?>"
        size="15" maxlength="20">
    &nbsp;&nbsp;&nbsp;<b>Fax</b>
    <input type="text" name="fax"
        value="<?php echo @$fax ?>"
        size="15" maxlength="20"></td></tr>
<tr><td align=right><b>Email Address</b></td>
    <td><input type="text" name="email"
        value="<?php echo @$email ?>"
        size="55" maxlength="67"></td></tr>
<tr><td>&nbsp;</td>
    <td align="center">
        <input type="submit"
            value="Become a Member"></td>
</tr>
</table>
</form>
</td>
</tr>
<tr><td colspan="3" bgcolor="gray">&nbsp;</td></tr>
</table>

<div align="center"><font size="-1">
    All comments and suggestions are appreciated. Please
    send comments to <a href="mailto:webmaster@petstore.com">
    webmaster@petstore.com</a> </font></div>
</body></html>
```

Notice the following points about `login_form`:

- Most of the statements are HTML, with a few small PHP sections here and there.
- The two forms that start on lines 23 and 51 set action to the same program, but add a different string to the URL — `do=login` or `do=new`.
- The error messages are shown on the login page by using small PHP sections. Each form has its section, and the message has different names for the two forms: `$message` and `$message_new`. On line 26, the variable `$message` is tested. If it has a value, the message is shown but is not if it has no value. If there was no error in the form, the message was never set, and no message is displayed. A similar statement on line 55 shows error messages for the new member form.
- A selection drop-down list (started on line 84) is provided for the customer to select the state, guarding against typing errors by the customer. Notice that lines 86 and 87 call functions. These functions are not PHP functions; they’re my functions. The functions are included in the program on line 8. The functions make arrays from a list of state names and a list of two-letter state codes. By using functions, you don’t need the two lists of 50 states in the program. The functions can be used repeatedly for many programs. The `functions12.inc` file contains the two functions as follows:

```php
<?php
function getStateCode()
{
    $stateCode = array(1=> "AL",
        "AK",
        "AZ",
        ...
        "WY" );
    return $stateCode;
}

function getStateName()
{
    $stateName = array(1=> "Alabama",
        "Alaska",
        "Arizona",
        ...
        "Wyoming" );
    return $stateName;
}
?>
```

A for loop then creates 50 options for the select list, using the two state arrays.

After running `Login.php`, if the user is successful with a login, the first page of the Members Only section is displayed. If the user is successful in obtaining a new user account, the `New_member.php` program is run.

## Writing New_member

The New Member Welcome page greets new members by name and provides information about their accounts. Members then have the choice of entering the Members Only section or returning to the main page. Listing 12-4 shows the program that displays the page that new members see.

### Listing 12-4: Program That Welcomes New Members

```php
<?php
/* Program: New_member.php
 * Desc:     Displays the new member welcome page. Greets
 *           member by name and gives user choice to enter
 *           restricted section or go back to main page.
 */
session_start();                                      # 7

if (@$_SESSION['auth'] != "yes")                      # 9
{
    header("Location: Login.php");
    exit();
}
include("dogs.inc");                                  #14
$connection = mysql_connect($host,$user,$password)
        or die("Couldn't connect to server.");         #16
$db = mysql_select_db($database, $connection)
        or die("Couldn't select database.");          #18
$sql = "SELECT firstName,lastName FROM Member
             WHERE loginName='{$_SESSION['logname']}'";
$result = mysql_query($sql)
        or die("Couldn't execute query 1.");
$row = mysql_fetch_array($result,MYSQL_ASSOC);
extract($row);
```

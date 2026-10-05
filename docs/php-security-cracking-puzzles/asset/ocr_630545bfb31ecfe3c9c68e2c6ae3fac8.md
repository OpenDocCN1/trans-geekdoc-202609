# Part I: Puzzles

```
$total = mysql_result($usr, 0);
}
// If the number of records is greater than zero,
// inserting the user data into the session
if($total > 0)
{
  $_SESSION['name'] = $_POST['name'];
  $_SESSION['password'] = $_POST['password'];
  // If the user has entered, welcoming him or her
if(isset($_SESSION['name']))
{
  // Establishing the connection to the database
  require_once("config.php");
  // Outputting the greeting
  echo "Hello, "._$_SESSION['name']."<br>";
  echo "Access to your confidential data<br>";
  // Outputting the user data
}
$query = "SELECT * FROM userslist WHERE name = '$_SESSION[name]'";
$usr = mysql_query($query);
if(!$$usr) exit(mysql_error());
$user = mysql_fetch_array($usr);
echo "Your email: "._$user['email']."<br>";
echo "Your URL: "._$user['url']."<br>";
}
```

How is it possible to bypass the authorization system presented in Listing I.7.4? Is there a way to protect the authorization system so that it would be impossible to bypass it?

# I.7.10. Encrypting Database-Stored Passwords

Develop a user registration and authorization system using the MySQL database management system with irreversible encryption of the password stored in the database. This would ensure password protection against direct viewing in case some vulnerability of the SQL injection is found in the system. The intruder will have to carry out an additional password attack. This attack might require considerable time, during which the password might be changed.
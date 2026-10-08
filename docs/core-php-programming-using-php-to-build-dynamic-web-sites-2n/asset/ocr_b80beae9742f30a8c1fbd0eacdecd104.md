# Core PHP Programming

![](bbox=[0.237, 0.093, 0.442, 0.243])

```
<?
/**
** define class for tracking users
 */
class user
{
    /*
    ** properties
    */
    var $name;
    var $password;
    var $last_login;

    /*
    ** methods
    */
    function user($inputName, $inputPassword)
    {
        $this->name = $inputName;
        $this->password = $inputPassword;
        $this->last_login = time();
    }

    // get the date of the last login
    function getLast()
    {
        return(Date("M d Y", $this->last_login));
    }
}

// create an instance
$currentUser = new user("Leon", "sdf123");

// get last login date
print($currentUser->getLast());
print("<BR>\n");

// print the user's name
print($currentUser->name);
print("<BR>\n");
?>
```
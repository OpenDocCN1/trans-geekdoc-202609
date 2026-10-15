Hirdesh Bhardwaj

```
if(mail($sendto,$subject,$message,$headers))
{

echo " Thanks for your feedback. We will contact you soon";

}

else
{

echo " There is some error in sending mail";

}

?>
```

# Example to create and send activation code to activate an user profile

Create a code if user is registered successful on the website

```
<?php

$name= $_REQUEST['txtName'];

$email=$_REQUEST['txtEmail'];

$password= $_REQUEST['txtPassword'];

$city= $_REQUEST['txtCity'];

include 'db.php';

// include your mail sending code file (notification.php) here

include_once("notification.php");
```
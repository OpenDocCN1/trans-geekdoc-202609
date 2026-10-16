# Listing 12-2 (continued)

```
/* send email to new member */                     #153
$emess = "A new Member Account has been setup. ";
$emess.= "Your new Member ID and password are: ";
$emess.= "\n\n\t$newname\n\t$newpass\n\n";
$emess.= "We appreciate your interest in Pet Store";
$emess.= " at PetStore.com. \n\n";
$emess.= "If you have any questions or problems,";
$emess.= " email webmaster@petstore.com";
$ehead="From: member-desk@petstore.com\r\n";       #161
$subj = "Your new Member Account from Pet Store";
$mailsend=mail("$email","$subj","$emess","$ehead");
header("Location: New_member.php");                #164
}
break;                                             #166

default:                                            #168
    include("login_form.inc");
}
?>
```

Some of the lines in Listing 12-2 have line numbers at the ends of the lines. The following list refers to the line numbers in the listing to discuss the program and how it works:

+   9 Starts a session. The session has to be started at the beginning of the program, even though the user hasn’t logged in yet.
+   
+   10 Reads in the file that sets the variables needed to connect to the database. The program is called dogs.inc, which is a misleading name that seems more secure than calling it mypasswords.inc.
+   
+   11 Starts a switch statement. The switch statement contains three sections, based on the value that was passed for do, obtained from the built-in array $_GET. The first section runs when the value pair passed for do is login; the second section runs when the value passed for do is new; and the third section is the default that runs if no value was passed for do. The third section just creates the login page and only runs when the customer first links to the login page.
+   
+   13 Starts the case block for the login section — the section that runs when the customer logs in. The login section of the form sends do=login in the URL, which causes this section of the switch statement to run.
+   
+   14 Lines 14–17 connect to MySQL and select the database.
+   
+   19 Lines 19–22 look in the database table Member for a row with the login name typed by the customer.
+   
+   23 Checks to see whether a row was found with a loginName field containing the Member ID typed by the customer. $num will equal 0 or 1, depending on whether the row was found.

# Part III: Using PHP Practice

Also, notice that the Member joinDate field is set:

```php
"joinDate" => date("Y-m-d")
```

PHP's date() function is used to generate a string representing the current date in the format YYYY-MM-DD. This string is then stored in the joinDate field, reflecting that the member completed their registration.

You can find out more about date() in Chapter 16.

Now that a Member has been created and populated with the submitted form, the script performs various checks on the data. First, it runs through the list of required fields; if any field was not filled in, its name is added to the $missingFields array:

```php
foreach ($requiredFields as $requiredField) {
    if (!$Member->getValue($requiredField)) {
        $missingFields[] = $requiredField;
    }
}
```

If any missing fields were encountered, an appropriate error message is added to the $errorMessages array:

```php
if ($errorMessages) {
    $errorMessages[] = '<p class="error">There were some missing fields in the form you submitted. Please complete the fields highlighted below and click Details to resend the form.</p>';
}
```

Error messages are also generated if the password fields do not match, or if the username or email address is already taken. For the username check, Member::getUsername() is called with the username; if it returns a Member object, the script knows that the username is taken and generates an error message. Similarly, for the email address, Member::getByEmailAddress() is called to determine if the entered email address exists in the database.

Finally, if no errors were raised, the script calls displayForm to display the form to the user, passing in the list of errors, the list of missing fields (if any), and the populated Member object containing the data entered by the user, for redisplaying the form. On the other hand, if the submitted data was correct, the member record is recorded in the members table by calling the Member object's insert():

```php
if ($errorMessages) {
    displayForm($errorMessages, $missingFields, $member);
} else {
    $member->insert();
    displayThanks();
}
```

The final function in the script, displayThanks(), simply displays a thank-you message to the member for registering.

# Chapter 14: Manipulating MySQL Data with PHP

## Testing the Application

Once you've created the register.php script, open your Web browser and enter the URL of the script to test the registration process. Try entering a few values in the form and submitting it to see what happens. Figure 14-1 shows the script in action; this example the user has forgotten to enter their email address. Notice how the script prompts them to reenter their password (it's never a good idea to redisplay an entered password in a form).

![](img/ede05b7b77968b82cbd9a513122fb183_454_0.png)

Figure 14-1

You've now extended your book club application to allow new members to register for the club. Along the way you learned how to add new member records to the members table using PHP and PDO.

## Creating a Members’ Area

Now members can sign up for your book club, you'll provide them with a members' area within your Web site that they can use to check out upcoming events, view the current reading list, and so on. For the purposes of this chapter, your members' area will just contain a few dummy pages, but hopefully by the time you've finished reading the chapter you'll have the skills to add some real-world functionality to the members' area if desired.

Members need to log in to the members' area, so you'll create a script that lets them do just that. The process involves displaying a login form, requesting their username and password. When you submit the form, you check their details against record in the members table. If they match, you display a welcome page, welcoming them to the members' area; otherwise you prompt them to check their login details and try again.

Similarly, you'll create a script that allows members to logout from the members' area. you'll include code to check that they are in fact logged in, and redirect them to the login page if they're not. At the same time, you'll enhance the LogEntry class so that the application can log views within the members' area to the accessLog database table.

## Adding an Authentication Method to the Member Class

First things first. For members to be able to log in to the members' area, you need to add a method to the Member class that checks a supplied username and password to make sure they're correct. This script will be used by the login script and add the authenticate() method to authenticate members when they

Open your Member.class.php file and add the authenticate() method to the end of the class, just after the insert() method:

```php
public function authenticate() {
    $conn = $this->connect();
    $sql = "SELECT * FROM TBL_MEMBERS WHERE username = :username\nAND password = :password";

    try {
        $stmt = $conn->prepare($sql);
        $stmt->bindValue("username", $this->data['username'], PDO::PARAM_STR);
        $stmt->bindValue("password", $this->data['password'], PDO::PARAM_STR);
        $stmt->execute();
        $row = $stmt->fetch();
        parent::disconnect($conn);
        if ($row) return new Member($row);
    } catch (PDOException $e) {
        parent::disconnect($conn);
        die("Query failed: " . $e->getMessage());
    }
}
```

This method gets the username and password stored in the object's username and password fields, and looks for a record in the members table. Notice that the password stored in the object needs to be encrypted so it can be compared with the password in the table. If a record is found, it returns a Member object. Otherwise, nothing is returned.

## Enhancing the LogEntry Class to Record Page Views

Each time a member views a page in the members' area, you are going to record the event in the accessLog table. To do this, you need to add a method to the LogEntry class. Open the LogEntry.php file and add the following record() method to the end of the class, after the getEntries() method:

```php
public function record() {
    $conn = parent::connect();
    $sql = "SELECT * FROM TBL_ACCESS_LOG WHERE memberId = :memberId\nAND pageUrl = :pageUrl";

    try {
        $stmt = $conn->prepare($sql);
        $stmt->bindValue(":memberId", $this->data["memberId"], PDO::PARAM_INT);
        $stmt->bindValue(":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR);
        $stmt->execute();

        if ($stmt = $stmt->fetch()) {
            $sql = "UPDATE TBL_ACCESS_LOG SET numVisits = numVisits + 1\nWHERE memberId = :memberId AND pageUrl = :pageUrl";
            $stmt = $conn->prepare($sql);
            $stmt->bindValue(":memberId", $this->data["memberId"], PDO::PARAM_INT);
            $stmt->bindValue(":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR);
            $stmt->execute();
        } else {
            $sql = "INSERT INTO TBL_ACCESS_LOG (memberId, pageUrl, numVisits) VALUES (:memberId, :pageUrl, 1)";
            $stmt = $conn->prepare($sql);
            $stmt->bindValue(":memberId", $this->data["memberId"], PDO::PARAM_INT);
            $stmt->bindValue(":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR);
            $stmt->execute();
        }
    } catch (PDOException $e) {
        parent::disconnect();
        die("Query failed: " . $e->getMessage());
    }
}
```

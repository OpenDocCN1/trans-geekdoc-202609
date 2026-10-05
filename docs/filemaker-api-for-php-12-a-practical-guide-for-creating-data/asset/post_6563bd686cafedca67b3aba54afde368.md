
Adobe. Obviously legacy coding lasts many years later. The good part about using Dreamweaver is when you write your code that there is no need to remember how to write this code from scratch. It just 

Next always start by including the connection to the database.

```php
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', $JumpMenu);
$fm->setProperty('hotspot', 'http://127.0.0.1/');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '12345');
```

To understand the main section of where we build for the jump menu you need to know what the final html code should look like before. Since the jump menu is repetitive, it's easy to use PHP and FileMaker to fill in the variables. When we done the jump menu it should look like the following code. Notice the onChange JavaScript that runs when the pop menu is changed.

```html
<form name="form" id="form">
<select name="jumpMenu" onChange="MM_jumpmenu('parent',this.1)">
<option selected>Jump Menu: Choose A Value Below</option>
<option value="http://localhost/JumpMenu.php?ValueList=Cat" selected>Cat</option>
<option value="http://localhost/JumpMenu.php?ValueList=Dog">Dog</option>
<option value="http://localhost/JumpMenu.php?ValueList=Bird">Bird</option>
</select>
</form>
```

Start by the Animal value list comes from the Demo layout and store them in the $variables.

```php
$layout=$fm->getLayout('Demo');
$values=$layout->getValueList('Animal');
```

Start the use the $menu variable to store the html code we'll be ready to echo the contents.

```php
$menu="<form name=\"form\" id=\"Form\">";
```

Next, the reference to the Dreamweaver MM_jumpMenu JavaScript in the header that runs only when the value is changed.

```php
$menu="<select name="jumpMenu" id="jumpMenu"
onChange="MM_jumpmenu('parent',this.0)">
```

Display the first row with any option to choose. I like this to give the user instructions about what to do with the menu. jump menu pre-selects the first value when the page is refreshed, you can't have a valid choice for the first menu item because you can't choose the first value. You can opt to enter a space to leave the first value empty if you want to provide a field label or instructions to next menu.

```php
$menu="<select selected>Jump Menu: Choose A Value Below</select>";
```

Next, we will use the values from the value list we stored earlier to dynamically populate the jump menu. Loop through all values and create the URL string to make it as dynamic as possible using the PHP function $_SERVER['PHP_SELF'] to capture the current URL string. Then all I have to add the name of the variable I want to use [ValueList] and the $value from the Animal value list. These two lines of PHP code I just dynamically populated the jump menu and didn't have to do any hard work to know anything how many items or what was in the value list.

```php
foreach($values as $value)
$menu .=<option value=\"" . $_SERVER['PHP_SELF']."?ValueList=" . $value . "\">";
```

Finally, close out the jump menu, the form, and echo the jump menu onto the screen.

```php
$menu .= '</select>';
$menu .= '</form>';
echo $menu;
```

Under normal circumstances the next part of your code is to take the jump menu selection, find the records from the database, and display them. I've included some sample code that might be helpful to see the jump menu in action. It's special. Your code will undoubtedly be more complex. However, this should get you started. Make sure the ValueList name=value pair is populated (using isset) with a value before the code runs. If it is, for the records using the Demo layout and Animal field.

```php
if($_GET['ValueList']) {
  $request = $fm->newFindCommand('Demo');
  $request->addVCriterion('Animal', $_GET['ValueList']);
  $result = $request->execute();
}
```

Always trap for errors just in case no records are found.

```php
if(FileMaker::isError($result)) {
  echo "Error: " . $result->getMessage();
  exit;
}
```

Display the results.

```php
$records = $result->getRecords();
foreach($records as $record) {
  echo 'RecordID ' . $record->getRecordID() . ': ' . $record->getField('Animal') . '<br/>';
}
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_325_0.png)

Figure-7-112: Jump Menu.

# Lesson 41: Multiple Email Attachments

**Objective:** In this lesson you will learn how to use PHP to send mail with multiple attachments. Although this lesson technically doesn't have anything to do with the FileMaker product line, many of you are embarking down the path of using PHP web sites in conjunction with FileMaker. Earlier in the book, I included a chapter on using FileMaker Server to send email from a web page. The advantage of FileMaker Server is that you can utilize the built-in SMTP authentication to connect to the email server when sending the message. This has obvious technical advantages and disadvantages.

**Difficulty:** Difficult

**Sample Files:**

PFiles/Advanced/Lesson41/MultipleEmailAttachments.php

**Page Navigation:**

![](img/5a2c5fda68d42e5d65f51850276e49ec_326_0.png)

FileMaker API Methods: N/A

**Code:**

The biggest advantage of using FileMaker Server is that it's cross-platform. You don't have to install PEAR or any special configuration of IIS on Windows Server. FileMaker Server makes the process work very comfortably. However, when it comes to sending uploaded attachments it takes quite a bit of additional code to upload, move, rename, and remove the file from the server. Whereas, using the PHP Mail function is self-contained and is capable of doing everything you need. As, as long as you're willing to lock down your email's form code you use Fort Knox to prevent email injection, bots, and spammers from controlling your mail server and turning it into a black-listed open relay.

The focus of this lesson will be to build proof PHP Mail with attachments. The assumption is that you'll have a web site that you use to allow customers to send you messages. You can do this easily by simply providing a mail link where the customers utilize their own mail application to send you a message — absolutely. That leaves your email address vulnerable to spiders crawling your web to acquire your email, which hides your email address, fights spam and is a more professional and sophisticated approach.

Included with this lesson is the sample document MultipleEmailAttachments.php. This code is fully functional as the only items you'll need to change for your own site are the email addresses in the code. For the remainder of this article I'm going to describe each section of code, including any pitfalls you might encounter. We take email for granted every single day. However, it's very complicated, expedient process. If one piece of code is out of place, the script won't send the mail correctly and it will use up 64-bit gibberish in your

```html
<html>
<head>
<title>E-mail with Attachment</title>
<style type="text/css">
.alert {
font-weight: bold;
color: #F00;
border: 1px solid #F00;
width: 300px;
padding: 3px;
</style>
</head>
<body>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_327_0.png)

7-113 Create an email form with an unlimited number of attachments.

The PHP code starts by checking if the request came from the POST method on your server. This is critical. You don't want to run this script if it comes from anywhere else than a request made from your server.

```php
<?php
if ($_SERVER['REQUEST_METHOD']=="POST") {
```

Next create the $error array (i.e. error string) to capture any possible errors the user may make by not entering fields. This array will be used to display the errors. The process is quite simple. The code checks the $_POST for form values: email, subject, and message. If any of them have been left blank $error variable will be set to 1. Then this as a Boolean value 1 where there is an error and 0 means there are no errors. This keeps the error checking simple (simple is good). Then adding the error message will be added to the array using $error[ The brackets the variable represent adding a new value to the array. The final part of this section shows if $error == 1. If there were errors the $alert html code will be created with the DIV tag and alert class we created at the beginning of the page. Finally, by using the foreach method we can display all of the alert messages stored in the $error variable. If you scroll down the code you'll see that the $alert variable is displayed at the top of the form.

```php
$error=array();
if(empty($_POST['email']))
{
  $error=1;
  $error[]="Please enter your email address";
}
if(empty($_POST['subject']))
{
  $error=1;
  $error[]="Please enter a subject";
}
if(empty($_POST['message']))
```

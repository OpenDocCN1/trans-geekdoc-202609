# Multi Page Form Page 1

http://192.168.1.18/PHPFiles/Advanced/Lesson42/page2.php

Bill To>> Ship To>>> Confirm:
First Name: Tool

Last Name: Duel
Address: 12608 Carmel Count-
City: San Diego
State: CA
Zip: 92130

Figure 7-117 Second page in the multi form process.

Source of http://localhost/ToddDuelPHP/MultiPageForm/page...

```
<html>
<meta http-equiv="Content-Type" content="text/html; charset="UTF-8">
<title>Multi Page Form Page 1</title>
<body>
<form action="shipTo.php" method="post" id="form">
First Name: <input name="firstname" type="text" value="">
Last Name: <input name="lastname" type="text" value="Duel">
Address: <input name="shipaddress" type="text" value="12608 Carmel Count">
City: <input name="city" type="text" value="San Diego">
State: <input name="state" type="text" value="CA">
Zip: <input name="zip" type="text" value="92130">
<input type="hidden" name="bill" value="Total">
<input type="hidden" name="lastname" value="Duel">
<input type="hidden" name="shipaddress" value="12608 Carmel Count">
<input type="hidden" name="city" value="San Diego">
<input type="hidden" name="state" value="CA">
<input type="hidden" name="zip" value="92130">
<input name="next" type="submit" value="Next"
</form>
</body>
</html>
```

Figure 7-118 1st fields are stored as hidden fields.

page3
The last page is used to display all the summary information to the user before they click the submit button. Once they click the submit button data is inserted into the database. The process to create hidden fields in the form is exactly the same as the second page. Therefore, I'm not going to repeat that. What you should take away from this list is that each page is exactly the same code to create the hidden fields. All you have to do is create the form with the PHP code and point it to the next page.

I could have listed the lesson here. However, to make it I included the FileMaker PHP code to insert the data into the database. Let's take a look at the code to see how to insert all the information on the last page. By making sure the submit button was clicked using the POST method.

```
if(isset($_POST['submit'])) {
Make your connection to the database.
nrequire_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', 'MultiPageForm');
```

329
```
<input name="emailId" type="text" />
Phone No:
<input name="phoneNo" type="text" format="NNN NNN NNNN" />
Card Type:
<select name="cardType">
<option value="Visa"> Visa </option>
<option value="Master"> Master </option>
<option value="American Express " > American Express </option>
</select>
Card Number:
<input name="cardNumber" type="text" format="NNNN NNNN NNNN NNNN" />
Card Expiry Date:
(mm/dd/yyyy)
<input name="cardExpiryDate" type="text" format="NN\/NN\/NNNN" />
```

Once the user has added all their details, they are sent to the server and added to the database. The first step is handled by a <do> element of type accept. The action of the <do> element is to send an HTTP GET request to CreateUser.php passing the values of the <input> and <select> elements as URL parameters:

```
<do type="accept">
<go
href="CreateUser.php?fname=$ (fname:escape)&amp;lname=$ (lname:escape)&amp;userId=$ (
userId:escape)&amp;password=$ (password:escape)&amp;address=$ (address:escape)&amp;c
ity=$ (city:escape)&amp;country=$ (country:escape)&amp;zipCode=$ (zipCode:escape)&amp
;gender=$ (gender:escape)&amp;age=$ (age:escape)&amp;emailId=$ (emailId:escape)&amp;p
honeNo=$ (phoneNo:escape)&amp;cardType=$ (cardType:escape)&amp;cardNumber=$ (cardNumb
er:escape)&amp;cardExpiryDate=$ (cardExpiryDate:escape)" />
</do>
</p>
</card>
</wml>
```

# New User Registration

The script CreateUser.php creates a new user. It gets called from the new user registration card of the main page:

```
<?php
include("Common.php");
include("UserFactory.php");

setSessionHandlers();
```

Remove extra whitespace from the URL parameters:

```
$fname = trim($fname);
$lname = trim($lname);
$userId = trim($userId);
$password = trim($password);
$address = trim($address);
$city = trim($city);
```
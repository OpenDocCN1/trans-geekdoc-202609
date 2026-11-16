The function createUser() creates a user in the database:

```
function createUser($fname, $lname, $password, $userId,
	$address, $city, $country,
	$zipCode, $gender, $age,
	$emailId, $phoneNo, $cardType,
	$cardNumber, $cardExpiryDate )
{
```

Get the database connection:

```
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
	return $functionResult;
}
$link = $functionResult->returnValue;
```

SQL SELECT statement to verify if the users userId already exists in the database:

```
$checkUserQuery = "SELECT count(*) FROM UserProfile
	WHERE userId = " . "" . $userId . """;
if (!( $result = mysql_query($checkUserQuery, $link) )) {
	return new Function_Result("Internal Error: Could not
	execute SQL Statement", null);
}

if (!( $row = mysql_fetch_row($result) )) {
	return new Function_Result("Internal Error: Could not
	fetch row from result", null);
}

if ($row[0] > 0) {
```

Return error if the user exists:

```
return new Function_Result("User " . $userId . " exists", null);
}
mysql_free_result($result);
```

SQL INSERT statement to insert the row corresponding to the user in the UserProfile table:

```
$insertUserStmt = "INSERT INTO UserProfile(fname, lname, userId,
	password, address, city, country, zipCode,
	gender, age, emailId, phoneNumber, cardNo,
	expiryDate, cardType, accountBalance) VALUES ("
	. """ . $fname . ""," . """ . $lname . ""," .
	. """ . $userId . ""," .
```
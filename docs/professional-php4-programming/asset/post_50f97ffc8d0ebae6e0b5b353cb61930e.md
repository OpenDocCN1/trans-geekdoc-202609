
## The Shipping_Address Class

The script ShippingAddress.php contains the class definition of Shipping_Address class:

```php
<?php
class Shipping_Address
{
    var $streetAddress;
    var $city;
    var $country;
    var $zipCode;
}
```

The constructor sets the value of member variables streetAddress, city, country, and zipCode:

```php
function Shipping_Address($streetAddress, $city, $country, $zipCode)
{
    $this->streetAddress = $streetAddress;
    $this->city = $city;
    $this->country = $country;
    $this->zipCode = $zipCode;
}
```

The following functions return the values of the member variables:

```php
function getStreetAddress()
{
    return $this->streetAddress;
}

function getCity()
{
    return $this->city;
}

function getCountry()
{
    return $this->country;
}

function getZipCode()
{
    return $this->zipCode;
}
?>
```

## The Credit_Card Class

The script CreditCard.php contains the class definition of Credit_Card class:

```php
<?php
class Credit_Card
{
    var $cardNumber;
    var $expiryDate;
    var $cardType;
}
```

The constructor sets the value of member variables cardNumber, cardType and expiryDate:

```php
function Credit_Card($cardNumber, $cardType, $expiryDate)
{
    $this->cardNumber = $cardNumber;
    $this->cardType = $cardType;
    $this->expiryDate = $expiryDate;
}
```

The remaining functions return the values of the member variables:

```php
function getCardNumber()
{
    return $this->cardNumber;
}

function getCardType()
{
    return $this->cardType;
}

function getExpiryDate()
{
    return $this->expiryDate;
}
}
?>
```

## The Transaction Class

The script Transaction.php contains the definition of Transaction class:

```php
<?php
class Transaction
{
    var $userId;
    var $item;
    var $quantity;
    var $date;
    var $status;
    var $orderNo;
}
```

The constructor sets the value of member variables userId, item, quantity, date, status, and orderNo:

```php
function Transaction($userId, $item, $quantity,
                     $date, $status, $orderNo)
{
    $this->userId = $userId;
    $this->item = $item;
    $this->quantity = $quantity;
    $this->date = $date;
    $this->status = $status;
    $this->orderNo = $orderNo;
}

function getUserId()
{
    return $this->userId;
}

function getItem()
{
    return $this->item;
}

function getQuantity()
{
    return $this->quantity;
}

function getDate()
{
    return $this->date;
}

function getStatus()
{
    return $this->status;
}

function getOrderNo()
{
    return $this->orderNo;
}
}
?>
```

## The User Class

The script User.php contains the class definition of User class:

```php
<?php
include_once("ShoppingCart.php");
include_once("UserStorage.php");
include_once("ShippingAddress.php");
include_once("CreditCard.php");
include_once("Common.php");
include_once("Transaction.php");
include_once("BookItem.php");
include_once("MusicItem.php");

class User
{
    var $firstName;
    var $lastName;
    var $password;
    var $gender;
    var $age;
    var $emailId;
    var $phoneNumber;
    var $accountBalance;
    var $shippingAddress;
    var $creditCard;
    var $userStorage;
}
```

The constructor sets the value of member variables:

```php
function User($firstName, $lastName, $userId, $password, $gender,
              $age, $emailId, $phoneNumber, $accountBalance,
              $shippingAddress, $creditCard)
{
    $this->firstName = $firstName;
    $this->lastName = $lastName;
    $this->userId = $userId;
    $this->password = $password;
    $this->gender = $gender;
    $this->age = $age;
    $this->emailId = $emailId;
    $this->phoneNumber = $phoneNumber;
    $this->accountBalance = $accountBalance;
    $this->shippingAddress = $shippingAddress;
    $this->creditCard = $creditCard;
```

Create a User_Storage object for the User object:

```php
    $this->userStorage = new User_Storage($userId);
}
```

The following functions return various member variables:

```php
function getFirstName()
{
    return $this->firstName;
}

function getLastName()
{
    return $this->lastName;
}

function getUserId()
{
    return $this->userId;
}

function getGender()
{
    return $this->gender;
}

function getAge()
{
    return $this->age;
}

function getEmailId()
{
    return $this->emailId;
}

function getPhoneNumber()
{
    return $this->phoneNumber;
}

function getShippingAddress()
{
    return $this->shippingAddress;
}

function getCreditCard()
{
    return $this->creditCard;
}

function getAccountBalance()
{
    return $this->accountBalance;
}
```

This function checks the password of the user. The function returns true, if the password match succeeds, else false is returned:

```php
function checkPassword($password)
{
```

It calculates the hash of the clear text password:

```php
    $cryptPassword = crypt($password, CRYPT_STD_DES);
```

Compare the hash of the clear text password with the stored hash value. Note that the hash of the clear text password is stored in the database:

```php
    if ($this->password == $cryptPassword) {
        return TRUE;
    } else {
        return FALSE;
    }
}
```

The function checkOut() implements the checkout logic. It returns true on success, else false is returned if the shopping cart is empty:

```php
function checkOut($shoppingCart)
{
    $transactions = array();
```

Get the shopping cart items:

```php
    $shoppingCartItems = $shoppingCart->getItems();
    for ($i = 0; $i < sizeof($shoppingCartItems); $i++) {
        $shoppingCartItem = $shoppingCartItems[$i];
        $item = $shoppingCartItem->getItem();
```

Create a transaction object for each shopping cart entry:

```php
        $transactions[] =
            new Transaction($this->userId, $item,
                $shoppingCartItem->getQuantity(),
                getDateString(),
                "Pending", null);
```

Update the account balance of the user:

```php
        $this->accountBalance += $shoppingCartItem->getQuantity() * $item->getPrice();
    }
    $storage = $this->userStorage;
    if (sizeof($transactions) > 0) {
```

Call the User_Storage object to save the transactions in the database:

```php
        $storage->saveTransactions($this->accountBalance,
            $transactions);
        return TRUE;
    } else {
        return FALSE;
    }
}
```

The function getTransactions(), returns the transactions of the user:

```php
function getTransactions()
{
    $storage = $this->userStorage;
```

Call the getTransactions() function of the $storage object:

```php
    $funcResult = $storage->getTransactions();
    return $funcResult->returnValue;
}
}
?>
```

## The User_Storage Class

The script UserStorage.php contains the definition of User_Storage class:

```php
<?php
include_once("Common.php");
include_once("Transaction.php");
include_once("BookItem.php");
include_once("MusicItem.php");

class User_Storage
{
    var $userId;
}
```

The constructor sets the member variable userId:

```php
function User_Storage($userId)
{
    $this->userId = $userId;
}
```

The function getTransactions() returns the transactions of the user:

```php
function getTransactions()
{
    $transactions = array();
```

Get the database connection:

```php
    $functionResult = getDBConnection();
    if ($functionResult->returnValue == null) {
        return $functionResult;
    }
    $link = $functionResult->returnValue;
```

The SELECT statement retrieves the details of book item transactions of the user:

```php
    $selectStmt = "SELECT Transaction.itemNo, title, author, quantity,
			 date, status, orderNo, itemType
			 FROM BookShop, Transaction
			 WHERE BookShop.itemNo = Transaction.itemNo
			 AND userId = " . "'" . $this->userId . "'";
// Execute the query
if (!($result = mysql_query($selectStmt, $link))) {
    return Function_Result("Internal Error: Could not
execute sql query", null);
}
while (($row = mysql_fetch_array($result, MYSQL_NUM))) {
```

For each retrieved row create a transaction object and add the object to $transactions array:

```php
    $item = new Book_Item($row[0], $row[7], null, $row[1], $row[2]);
    $transaction = new Transaction($this->userId, $item, $row[3],
            $row[4], $row[5], $row[6]);
    $transactions[] = $transaction;
}
mysql_free_result($result);
```

The SELECT statement to retrieves the details of music item transactions of the user:

```php
    $selectStmt = "SELECT Transaction.itemNo, title, artist, quantity,
            date, status, orderNo, itemType
            FROM MusicShop, Transaction
            WHERE MusicShop.itemNo = Transaction.itemNo
            AND userId = " . "'" . $this->userId . "'";

// Execute the query
if (!($result = mysql_query($selectStmt, $link))) {
    return Function_Result("Internal Error: Could not
            execute sql query", null);
}

while (($row = mysql_fetch_array($result, MYSQL_NUM))) {
```

For each retrieved row, create a transaction object and add the object to $transactions array:

```php
    $item = new Music_Item($row[0], $row[7], null,
            $row[1], $row[2]);
    $transaction = new Transaction($this->userId, $item,
            $row[3], $row[4],
            $row[5], $row[6]);
    $transactions[] = $transaction;
}
mysql_free_result($result);
return new Function_Result(null, $transactions);
}
```

The function saveTransactions() saves the account balance and the transactions of the user:

```php
function saveTransactions($accountBalance, $transactions)
{
    // Get DB Connection
    $functionResult = getDBConnection();
    if ($functionResult->returnValue == null) {
        return $functionResult;
    }

    $link = $functionResult->returnValue;
```

The following SQL statement is used to insert the transactions in the Transaction table:

```php
    $insertStmt = "INSERT INTO Transaction(userId, itemNo,
            quantity, date, status) VALUES ";
    for ($i = 0; $i < sizeof($transactions); $i++) {
        $transaction = $transactions[$i];
```

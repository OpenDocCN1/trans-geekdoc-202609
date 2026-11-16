```
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
```

The constructor sets the value of member variables:

```
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
    $this->creditCard= $creditCard;
}
```

Create a User_Storage object for the User object:

```
$this->userStorage = new User_Storage($userId);
}
```

The following functions return various member variables:

```
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
```
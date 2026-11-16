# The Shipping_Address Class

The script ShippingAddress.php contains the class definition of Shipping_Address class:

```
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

```
function Shipping_Address($streetAddress, $city, $country, $zipCode)
{
    $this->streetAddress = $streetAddress;
    $this->city = $city;
    $this->country = $country;
    $this->zipCode = $zipCode;
}
```

The following functions return the values of the member variables:

```
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
,
```

# The Credit_Card Class

The script CreditCard.php contains the class definition of Credit_Card class:

```
<?php
class Credit_Card
{
    var $cardNumber;
    var $expiryDate;
    var $cardType;
```
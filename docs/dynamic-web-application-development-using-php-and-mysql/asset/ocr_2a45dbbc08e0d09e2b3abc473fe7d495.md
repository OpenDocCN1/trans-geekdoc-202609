```
$this->strName = $strName;
}
}
```

Four objects are created. The first and second are of class Person:

```
$objSimon = new Person("Simon");
$objSimon2 = new Person("Simon");
```

The third is of class AnotherPerson:

```
$objSimon3 = new AnotherPerson("Simon");
```

The fourth is of type Person as it is created from an instance already created:

```
$objSimon4 = $objSimon;
```

$objSimon and $objSimon2 are compared using the comparison operator (==) and the result is true:

```
if ($objSimon == $objSimon2)
    echo '<p>$objSimon == $objSimon2</p>';
```

$objSimon and $objSimon3 are compared using the comparison operator (==) and the result is false as the classes are not the same:

```
if ($objSimon == $objSimon3)
    echo '<p>$objSimon == $objSimon3</p>';
```

$objSimon and $objSimon4 are compared using the comparison operator (==) and the result is true:

```
if ($objSimon == $objSimon4)
    echo '<p>$objSimon == $objSimon4</p>';
```

$objSimon and $objSimon2 are compared using the identity operator (===) and the result is false as they are not the same instance of the object:

```
if ($objSimon === $objSimon2)
    echo '<p>$objSimon === $objSimon2</p>';
```

$objSimon and $objSimon3 are compared using the identity operator (===) and the result is false as they are not the same instance of the object:

```
if ($objSimon === $objSimon3)
    echo '<p>$objSimon === $objSimon3</p>';
```

$objSimon and $objSimon4 are compared using the identity operator (===) and the result is true:

```
if ($objSimon === $objSimon4)
    echo '<p>$objSimon === $objSimon4</p>';
?>
```
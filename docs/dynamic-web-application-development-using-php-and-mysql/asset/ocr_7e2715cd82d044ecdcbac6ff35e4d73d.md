It then puts them in an array and uses a foreach loop to cycle through the array and display the contents of the object using the display() method:

```
$arrPeople = array($objSimon, $objLiz, $objIan, $objBilly, $objHayley);
foreach($arrPeople as $objThePerson)
    echo($objThePerson->display() );
```

To allow the above script to work as intended we must change the visibility of the display() method in the person class back to public so it looks like this:

```
function display() {
    echo "Firstname: " . $this->strFirstname;
    echo "<br/>Surname: " . $this->strSurname . "<br/>";
}
```

We also removed the invocation to the display() method from within the constructor, so that the constructor of the person class now looks like this:

```
function __construct ($strFirstname, $strSurname) {
    $this->setFirstname($strFirstname);
    $this->setSurname($strSurname);
}
```

The output from the above script is illustrated in Figure 16.5.

# FIGURE 16.5 Objects and arrays

![](bbox=[0.2, 0.57, 0.9, 0.94])
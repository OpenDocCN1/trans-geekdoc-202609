```
private function display() {
    echo "<p>Firstname: " . $this->strFirstname . "</p>";
    echo "<p>Surname: " . $this->strSurname . "</p>";
}
function setDisplayFirstnameSurname($strFirstname, $strSurname) {
    $this->setFirstname($strFirstname);
    $this->setSurname($strSurname);
    $this->display();
}
}
$objSimon = new person;
$objSimon->setDisplayFirstnameSurname("Simon", "Stobart");
?>
```

The above script creates a new method called display(), which displays the values of the two data members:

```
private function display() {
    echo "<p>Firstname: " . $this->strFirstname . "</p>";
    echo "<p>Surname: " . $this->strSurname . "</p>";
}
```

Note that the display() method is declared as private, which stops it being invoked from outside with a call such as this:

```
$objSimon->display();
```

| NOTE | There is no real reason to define this method as private other than to illustrate the use of a private method. |

The script also creates a new method called setDisplayFirstnameSurname():

```
function setDisplayFirstnameSurname($strFirstname, $strSurname) {
    $this->setFirstname($strFirstname);
    $this->setSurname($strSurname);
    $this->display();
}
```

This method receives both the firstname and surname as arguments. It then invokes the setFirstname() and setSurname() methods to assign the appropriate values to the class data members. Finally it invokes method display() to output the current values of these data members. The output produced is the same as shown in Figure 16.2.
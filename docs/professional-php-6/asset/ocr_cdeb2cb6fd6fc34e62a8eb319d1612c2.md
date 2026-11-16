```
public function __toString() {
    return $this->firstname . ' ' . $this->lastname;
}

public function getEmployer() {
    return DataManager::getEmployer($this->id);
}

public function validate() {
    parent::validate();

    //add individual-specific validation
}

}
?>
```

That's short and sweet. Inheritance makes this easy. The Individual class sets up a few new properties that make accessing the first and last name of the individual easier, instead of having to use the rather ugly name1 and name2 properties defined in the Entity class. It also defines a new method, getEmployer(), which requires a new function in the DataManager. You get to that function as soon as you have your Organization class, which is shown in the following code. Create a file called class.Organization.php and enter this code into it:

```
<?php

require_once('class.Entity.php');
require_once('class.Individual.php');

class Organization extends Entity {

    public function __construct($userID) {
        parent::__construct($userID);
        $this->propertyTable['name'] = 'name1';
    }

    public function __toString() {
        return $this->name;
    }

    public function getEmployees() {
        return DataManager::getEmployees($this->id);
    }

    public function validate() {
        parent::validate();

        //do organization-specific validation
    }

}
?>
```
```
public function displayDetails() {
parent::displayDetails();
echo ", Salary: $ " . $this->salary;
}
}
?>
```

In this Employer class, the displayDetails() method of the Person class is redefined to include the employee's salary. When we call this method on an object in the Employer class, the specific redefinition in the Employer class is used, overriding the method inherited from the Person class. In other words, when we invoke the displayDetails() method on an object created from the Employer class, it's the version of this method defined in the Employer class that will be executed, rather than the one defined in the Person class.

The advantage of redefining methods as part of the inheritance process lies in the ability to customize the behavior of inherited methods to suit the specific needs of the child class. This allows for greater modularity and extensibility of code, as a child class can extend or modify the behavior of inherited methods without altering the code of the parent class. In this way, each class can have its own specific functionality while benefiting from the common features defined in the parent class, which encourages code reuse and facilitates maintenance.

Note that a child class can always redefine the methods of the parent class if these methods are declared as public or protected in the parent class. This allows the child class to customize the behavior of inherited methods to suit its specific needs. However, if the parent class method is declared as private, it cannot be
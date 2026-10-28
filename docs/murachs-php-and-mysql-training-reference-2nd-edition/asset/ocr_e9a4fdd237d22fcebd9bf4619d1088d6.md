# A superclass

```
```php
class Person {
    private $firstName, $lastName, $phone, $email;

    public function __construct($first, $last) {
        $this->firstName = $first;
        $this->lastName  = $last;
    }

    public function getFirstName()       { return $this->firstName;       }
    public function setFirstName($value)  { $this->firstName = $value;    }
    public function getLastName()        { return $this->lastName;        }
    public function setLastName($value)  { $this->lastName = $value;      }
    public function getPhone()           { return $this->phone;            }
    public function setPhone($value)     { $this->phone = $value;          }
    public function getEmail()           { return $this->email;            }
    public function setEmail($value)     { $this->email = $value;          }
}
```
```

# A subclass

```
```php
class Employee extends Person {
    private $ssn, $hireDate;

    public function __construct($first, $last, $ssn, $hireDate) {
        $this->ssn = $ssn;
        $this->hireDate = $hireDate;

        // Call Person constructor to finish initialization
        parent::__construct($first, $last);
    }

    public function getSSN()             { return $this->ssn;           }
    public function setSSN($value)       { $this->ssn = $value;          }
    public function getHireDate()        { return $this->hireDate;       }
    public function setHireDate($value)  { $this->hireDate = $value;     }
}
```
```

# Code that uses the subclass

```
```php
$emp = new Employee('John', 'Doe', '999-14-3456', '8-25-1996');
$emp->setPhone('919-555-4321');    // Inherited from Person Class
```
```

# Description

+   - *Inheritance* provides a way to create a new class based on an existing class. The new class *inherits* the properties and methods of the existing class.
+   - A class that inherits from a class is called a *subclass, derived class,* or *child class.* A class that is inherited by another class is called a *superclass, base class,* or *parent class.*
+   - A subclass can *extend* the superclass by adding new properties and methods. It can also *override* a method from the superclass with its own version of the method.
+   - A subclass can call a method from the superclass by prefixing the method name with the parent keyword and a double colon. The parent keyword is a reference to the superclass.

Figure 14-13  How to inherit a class
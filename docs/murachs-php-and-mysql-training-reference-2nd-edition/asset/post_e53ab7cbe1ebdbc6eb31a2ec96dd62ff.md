
## How to use the protected access modifier

So far, this chapter has used public and private access modifiers to control the visibility of properties and methods. When you use inheritance, you can also use the protected modifier to control when a property is inherited. Figure 14-14 shows a table that summarizes how the three keywords work. For each keyword, there are two questions that must be answered. First, does the keyword allow the property or method to be accessed outside of the class? Second, does the keyword allow the property or method to be accessed by a subclass?

The answers to these questions show that a public property or method can always be accessed outside the current class. Conversely, a private property or method can never be accessed outside the current class. In contrast, a protected property or method can't be accessed outside the current class, but it can be accessed by subclasses.

To show how the protected modifier works, two classes are defined in this figure. The first class is the Person class. This class is similar to the Person class in the previous figure, except that the firstName and lastName properties are protected instead of private.

In the Person class, this change has no practical difference. When a subclass inherits from the Person class, however, the two protected properties are accessible within the subclass declaration. As a result, the getFullName method in the Employee class can access both of these protected properties as if they were defined in the Employee class.

If the firstName and lastName properties were defined as private in the Person class, the getFullName method in the Employee class would have to use the inherited getFirstName and getLastName methods to access the values in these properties. To see an example of this, you can look ahead to the next figure.

When you design your classes, you should be as restrictive as possible when choosing your access modifiers. If you initially give too much access to a property, you can't restrict the property later without breaking your application. For example, if you start with a public property and later change it to protected or private, any code outside the class declaration that relies on the public property no longer works and needs to be rewritten to use a get or set method instead. If, however, you start with a private property and later change it to protected or public, any code that uses get and set methods to access the private property still works.

### How the access modifiers work

| Modifier | Access outside class? | Access from subclass? |
|---|---|---|
| `public` | Yes | Yes |
| `protected` | No | Yes |
| `private` | No | No |

### A superclass

```php
class Person {
    protected $firstName, $lastName;
    private   $phone, $email;

    // The constructor and the get and set methods are the same
    // as the Person class in figure 14-13
}
```

### A subclass

```php
class Employee extends Person {
    private $ssn, $hireDate;

    // The constructor and the get and set methods are the same
    // as the Employee class in figure 14-13

    // This method uses the protected properties from the Person class
    public function getFullName() {
        return $this->lastName . ', ' . $this->firstName;
    }
}
```

### Description

- Public and protected properties and methods are inherited by the subclass.
- Private properties and methods are not inherited by the subclass.

Figure 14-14 — How to use the protected access modifier

## How to create abstract classes and methods

An abstract class is a class that can't be used to create an object. However, abstract classes are useful when you want to provide a superclass that other classes can inherit, but you don't want objects to be created from the superclass. Then, you can code a subclass that inherits the abstract class, and you can create objects from that subclass.

Figure 14-15 shows how to work with abstract classes. To declare an abstract class, you include the abstract keyword in the class declaration as shown in the Person class.

Within an abstract class, you can use the abstract keyword to create abstract methods. An abstract method is a method that does not have any code to execute. It forces the subclass to implement the method, but it leaves all of the details of the implementation to the subclass. In this figure, for example, the Person class includes an abstract method named getFullName.

You can declare an abstract method by coding the abstract keyword followed by an access modifier, the function keyword, the method name, and the method parameters in parentheses. Note that an abstract method does not include a set of braces or any statements within those braces.

The first example in this figure defines an abstract class named Person that can be used as a superclass for other classes such as the Customer and Employee classes. This superclass defines an abstract method named getFullName that must be implemented by any subclasses.

The second example defines a Customer class that inherits the Person class. Since this subclass isn't declared as abstract, it's known as a concrete class. Note that this subclass provides an implementation of the abstract getFullName method. If this class didn't implement this method, PHP would issue a fatal error.

The third example attempts to create an object from the abstract Person class. This code generates a fatal error. Instead, you must create an object from the concrete Customer class as shown in the fourth example.

### An abstract class with an abstract method

```php
abstract class Person {
    private $firstName, $lastName, $phone, $email;

    // The constructor and the get and set methods are the same
    // as the Person class in figure 14-13

    // An abstract method
    abstract public function getFullName();
}
```

### A concrete class that implements an abstract class

```php
class Customer extends Person {
    private $cardNumber, $cardType;

    public function __construct($first, $last, $phone, $email) {
        $this->setPhone($phone);
        $this->setEmail($email);
        parent::__construct($first, $last);
    }

    public function getCardNumber()    { return $this->cardNumber; }
    public function setCardNumber($value)  { $this->cardNumber = $value; }
    public function getCardType()      { return $this->cardType; }
    public function setCardType($value)    { $this->cardType = $value; }

    // Concrete implementation of the abstract method
    public function getFullName() {
        return $this->getFirstName() . ' ' . $this->getLastName();
    }
}
```

### Code that attempts to create an object from the abstract class

```php
$customer = new Person('John', 'Doe');    // Fatal error
```

### Code that creates and uses an object from the concrete class

```php
$customer = new Customer('John', 'Doe', '919-555-4321', 'jdoe@example.com');
echo '<p>' . $customer->getFullName() . '</p>';
```

### Description

- An *abstract class* is a class that can't be used to create an object. It's useful as a superclass for other classes.
- An *abstract method* is a method that specifies the name and parameters for the method but doesn't provide a code block that implements the method.
- An abstract method can only be coded in an abstract class. However, an abstract class isn't required to have an abstract method.
- A *concrete class* is a class that can be used to create an object. A concrete subclass of an abstract class must provide an implementation for all abstract methods in the abstract class. Otherwise, PHP issues a fatal error.

Figure 14-15 — How to create abstract classes and methods

## How to create final classes and methods

Occasionally, you may need to make sure that a method doesn't get overridden by a method in a subclass. To do that, you can use the final keyword to create a final method as shown in figure 14-16. You may also need to make sure that a class doesn't get extended by a subclass. To do that, you can use the final keyword to create a final class.

The first example shows how to declare a final method. Here, the code declares the getFirstName method in the Person class as final. As a result, when the Employee class in the second example attempts to override the getFirstName method, it generates a fatal error.

The third example shows how to declare a final class. Here, the code declares the Employee class as final. Then, when the PartTime class in the fourth example attempts to inherit the Employee class, it generates a fatal error.

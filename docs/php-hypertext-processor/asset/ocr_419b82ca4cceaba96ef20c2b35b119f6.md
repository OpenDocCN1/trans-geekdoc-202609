```
$maths->getTitle();

$physics->getPrice();
$chemistry->getPrice();
$maths->getPrice();
```

This will produce the following result:

```
Physics for High School
Advanced Chemistry
Algebra
10
15
7
```

# Destructor

Like a constructor function you can define a destructor function using function __destruct(). You can release all the resources with-in a destructor.

# Inheritance

PHP class definitions can optionally inherit from a parent class definition by using the extends clause. The syntax is as follows:

```
class Child extends Parent {
  <definition body>
}
```

The effect of inheritance is that the child class (or subclass or derived class) has the following characteristics:

+   * Automatically has all the member variable declarations of the parent class.

+   * Automatically has all the same member functions as the parent, which (by default) will work the same way as those functions do in the parent.

Following example inherit Books class and adds more functionality based on the requirement.

```
class Novel extends Books{
  var publisher;
  function setPublisher($par){
  $this->publisher = $par;
  }
```
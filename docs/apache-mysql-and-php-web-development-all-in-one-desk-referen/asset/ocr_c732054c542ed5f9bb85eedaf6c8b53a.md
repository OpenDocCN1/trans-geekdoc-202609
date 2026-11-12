Then I get rid of the object by calling unset. The unset keyword destroys the object but does not call any member functions. Therefore, if I want a destructor, my job is to include a function that performs some cleanup work, and then I have to call the function manually before I delete the object with the unset keyword. That's what I do in the preceding sample, and it works.

Here's the output from this code in a browser:

Starting! Destroying!

Notice also that I included a commented-out line. If you uncomment the line, you will see that the object is indeed gone because trying to use it results in a runtime error:

```
Fatal error: Call to a member function on a non-object in
destructor.php on line 16
```

# Coding for Dynamic Binding

PHP, like many interpreted languages, has powerful support for something called dynamic binding. (If you're an OOP — Object-Oriented Purist — you'll know this as polymorphism.) Take a look at the following code:

```
<?php
class A {
 function foo() {
 print "This is foo for class A!<br>\n";
 }
}

class B {
 function foo() {
 print "This is foo for class B!<br>\n";
 }
}

function Process($obj) {
 $obj->foo();
}

$objA = new A();
$objB = new B();
Process($objA);
Process($objB);
?>
```
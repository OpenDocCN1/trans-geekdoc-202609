# # PHP's Limitations

As mentioned throughout the chapter, there are many limitations to PHP's object-oriented implementation. Here we will discuss several common limitations of PHP such as no static members, no destructors, and no multiple inheritance.

# ## No Static Members

Although PHP allows programmers to use the class-function call operator (as seen in the Inheritance section) to call methods statically, PHP does not allow us to specify static members. So what is a static member? A static member is like a global variable but it is tied to class namespace (as opposed to an object namespace). This means that the variable is used by all instances of a class rather than by each instance.

So why do we need static members? For one reason, sometimes it's convenient for a set of instances of an object type to use the same piece of data rather than duplicating it across several instances of the same class, thus saving memory. The second reason is because we may want to keep track of a property that pertains to all the instances of a class, such as how many objects of a class have been instantiated at a particular point in time.

Although many languages like Java support static members, PHP does not directly support this type of variable. However, with a combination of global variables and static methods, we can achieve static-like members that operate in the same way. Let us illustrate this technique by writing an Apple class that has a static member to keep track of the number of instances of the Apple class in memory:

```
<?php
// Apple.php
class Apple
{
    var $isEaten;
}
```

In our constructor of our Apple class, we have the following code, which says that we want to access the variable $numberOfApples in the global namespace and increment it by one, thus showing that one apple object has been instantiated:

```
function Apple()
{
    global $numberOfApples;
    $numberOfApples++;
    $this->isEaten = false;
}
```

Likewise, our eat() method decrements the global variable $numberOfApples shown here:

```
function eat()
{
    if (!$this->isEaten()) {
        global $numberOfApples;
        $numberOfApples--;
    }
    $this->isEaten = true;
}
```
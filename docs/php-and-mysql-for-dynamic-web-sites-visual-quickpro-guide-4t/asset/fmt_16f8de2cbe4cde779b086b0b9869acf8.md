
# OOP Fundamentals

If you’ve never done any Object-Oriented Programming before, both the concept and the syntax can be quite foreign. Simply put, all applications, or scripts, involve *taking actions with information*: validating it, manipulating it, storing it in a database, and so forth. Philosophically, procedural programming is written with a focus on the actions: do this, then this, then this; OOP is data-centric, focusing more on the kinds of information being used.

## OOP vs. Procedural

Discussions as to the merits of OOP vs. procedural programming can quickly escalate to verbal wars, with each side fiercely advocating for their approach. PHP is somewhat unique in that you have a choice (by comparison, C is strictly a procedural language and Java object-oriented). In my opinion, each programming style has its strengths and weaknesses, but neither is “better” than the other.

Procedural programming is arguably faster to learn and use, particularly for smaller projects. But procedural code can be harder to maintain and expand, especially in more complicated sites, and has the potential to be buggier.

Code written using OOP, on the other hand, may be easier to maintain, specifically on larger projects, and may be more appropriate in team environments. But OOP is harder to master, and when not done well, is that much more challenging to remedy.

In time, you’ll naturally come up with your own opinions and preferences. The real lesson, to me, is to take advantage of the fact that PHP allows for both syntaxes, and not to limit yourself to just one style regardless of the situation.

## Class Definition and Members

As a theoretical example, you might have a class called `Car`. Note that class names conventionally begin with an uppercase letter. The properties of a `Car` would include `make`, `model`, `year`, `odometer`, and so forth: all information that can be known about a car. A `Car`’s properties can be set, changed, and retrieved, and the values of the properties distinguish *this* `Car` from *that* `Car`. A `Car`’s methods—the things that the car can do—would include: `start()`, `drive()`, `park()`, and `turnOff()`. These actions are common to all `Car`s.

In the introduction to this chapter, I stated that you can *use* OOP without really *knowing* it. By that I mean that it’s very easy, and common enough, to use an existing class definition for your own needs. In fact, the reusability of code—particularly code created by others—is one of the key benefits of OOP. What actually takes a lot of effort, at least to do it right, is to master the design process: understanding what members to define and, more importantly, how to implement sophisticated OOP concepts such as:

- Inheritance
- Access control
- Overriding methods
- Scope resolution
- Abstraction
- And so on

When you’re interested in learning how to properly create your own classes, you can look into these subjects in my *PHP 5 Advanced: Visual QuickPro Guide*, among other resources, but in this chapter, let’s focus on using existing classes instead of creating your own custom ones.

## OOP Syntax in PHP

So let’s say someone has gone through the process of designing and defining a `Car` class. Most classes are not used directly; rather, you create an *instance* of that class—a specific variable of the class’s type. That instance is called an *object*. In PHP, an instance is created using the `new` keyword:

```
$obj = new ClassName();
$mine = new Car();
```

Whereas the code `$name = 'Larry'` creates a variable of type string, the above code creates a variable of type `Car`. Everything that’s part of `Car`’s definition—every property (i.e., variable) and method (i.e., function)—is now embedded in `$mine`.

Behind the scenes (i.e., in the class definition), a special method called the *constructor* is automatically invoked when a new object of that type is generated. The constructor normally provides whatever initial setup would be required by the subsequent usage of that object. For example, the `MySQLi` class’s constructor establishes a connection to the database and the `DateTime` class’s constructor creates a reference to an exact date and time (both the `MySQLi` and `DateTime` classes will be explicitly used in this chapter).

If the constructor takes arguments, like any function can, those may be provided when the object is created:

```
$mine = new Car('Honda', 'Fit', 2008);
```

Once you have an object, you reference its properties (i.e., variables) and call its methods (i.e., functions) using the syntax `$object_name->member_name`:

```
$mine->color = 'Purple';
$mine->start();
```

The first line (theoretically) assigns the value *Purple* to the object’s `color` property. The second line invokes the object’s `start()` method. As with any function call, the parentheses are required. If the method takes arguments, those can be provided, too:

```
$mine->drive('Forward');
```

Sometimes you’ll use an object’s properties as you would any other variable:

```
$mine->odometer += 20;
echo "My car currently has $mine->odometer miles on it.";
```

If an object’s method returns a value, the method can be invoked in the same manner as any function that returns a value:

```
// The fill() method takes a number of
// gallons being added and returns
// how full the tank is:
$tank = $mine->fill(8.5);
```

And that’s really enough to know about OOP in order to start using it. As you’ll see, the examples over the next few pages will replicate functionality explained earlier in the book, so that the contrasting approaches to the same end result should help you better understand what’s going on.

> **Tip**
>
> In documentation, you’ll see the `ClassName::method_name()` syntax. This is a way of specifying to which class a method belongs.

> **Tip**
>
> One of the major changes in PHP 5.3 is support for *namespaces*. Namespaces, in layman’s terms, provide a way to group multiple class definitions under a single title. Namespaces are useful for organizing code, as well as preventing conflicts (e.g., differentiating between my `Car` class and your `Car` class).

> **Tip**
>
> Classes can also have their own constants, just as they have their own variables and functions. Class constants are normally used without an instance of that class, as in:
>
> ```
> echo ClassName::CONSTANT_NAME;
> ```

> **Tip**
>
> OOP in PHP has changed dramatically from PHP 3 to PHP 4 to PHP 5. The syntax discussed in this chapter will only work with PHP 5 and above.

## More OOP Classes

There are more OOP classes defined in PHP than just those illustrated in this chapter, although I think the `MySQLi` and `DateTime` classes are the two most obviously accessible and usable. The largest body of classes can be found in the *Standard PHP Library* (SPL), built into PHP as of version 5.0, and greatly expanded in version 5.3.

The SPL provides high-end classes in several categories: exception handling, *iterators* (loops that can work on any collection of data), custom data types, and more. The SPL is definitely for more advanced PHP programmers and is most beneficial for otherwise strongly or entirely OOP-based code.

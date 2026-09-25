   

Index

[Use type hinting for function parameters and return values](#part0003.xhtml#a9EW)

[Implement interfaces to define clear contracts for classes](#part0004.xhtml#a9EJ)

[Utilize traits for code reuse across multiple classes](#part0005.xhtml#a9ER)

[Employ namespaces to organize and avoid naming conflicts](#part0006.xhtml#a9H3)

[Use anonymous functions (closures) for compact, inline functionality](#part0007.xhtml#a9ES)

[Prefix interface names with 'I' (e.g., ILogger)](#part0008.xhtml#a9FE)

[Use 'is' prefix for boolean methods](#part0009.xhtml#a9FV)

[Prefix abstract classes with 'Abstract'](#part0010.xhtml#a9EG)

[Use 'able' suffix for classes implementing capabilities](#part0011.xhtml#a9H9)

[Prefix private methods with an underscore](#part0012.xhtml#a9GX)

[Avoid abbreviations in variable and function names](#part0013.xhtml#a9H0)

[Use intention-revealing names (e.g., getUsersByRole instead of getUsers)](#part0014.xhtml#a9FF)

[Avoid using similar names with different meanings](#part0015.xhtml#a9EV)

[Use opposite pairs consistently (e.g., start/stop, open/close)](#part0016.xhtml#a9EP)

[Meaningful and Distinct Naming](#part0017.xhtml#a9H8)

[Strict Types Declaration](#part0018.xhtml#a9FP)

[Implement magic methods for cleaner syntax](#part0019.xhtml#a9G6)

[Use generators for memory-efficient iteration](#part0020.xhtml#a9EX)

[Employ late static binding for more flexible inheritance](#part0021.xhtml#a9EU)

[Utilize SPL data structures for specialized data handling](#part0022.xhtml#a9F1)

[Comment on why something is done, not what is done](#part0023.xhtml#a9H7)

[Use PHPDoc blocks for classes, methods, and properties](#part0024.xhtml#a9ED)

[Explain workarounds or hacks with comments](#part0025.xhtml#a9F6)

[Comment on non-obvious optimizations](#part0026.xhtml#a9FG)

[Use TODO comments for future improvements or known issues](#part0027.xhtml#a9H1)

[Keep comments up-to-date with code changes](#part0028.xhtml#a9G9)

[Remove commented-out code](#part0029.xhtml#a9F8)

[Use clear and concise language in comments](#part0030.xhtml#a9GW)

[Avoid redundant comments that repeat the code](#part0031.xhtml#a9HC)

[Use inline comments sparingly, only when necessary](#part0032.xhtml#a9G2)

[Utilize dependency injection for better testability](#part0033.xhtml#a9HD)

[Use null coalescing operator (??) for concise null checks](#part0034.xhtml#a9GT)

[Implement \_\_invoke() method for callable objects](#part0035.xhtml#a9GJ)

[Use yield from for nested generators](#part0036.xhtml#a9GC)

[Employ array unpacking for merging arrays](#part0037.xhtml#a9GF)

[Use consistent indentation (spaces or tabs)](#part0038.xhtml#a9FM)

[Limit line length to improve readability (e.g., 80-120 characters)](#part0039.xhtml#a9EA)

[Use blank lines to separate logical sections of code](#part0040.xhtml#a9GZ)

[Align assignment operators when declaring multiple variables](#part0041.xhtml#a9EC)

[Use parentheses to clarify operator precedence](#part0042.xhtml#a9EF)

[Use early returns to reduce nesting](#part0043.xhtml#a9F0)

[Prefer foreach loops over for loops when possible](#part0044.xhtml#a9F2)

[Use switch statements for multiple conditions on the same variable](#part0045.xhtml#a9FD)

[Employ guard clauses to handle edge cases early](#part0046.xhtml#a9HA)

[Use ternary operators for simple conditional assignments](#part0047.xhtml#a9GH)

[Utilize the null coalescing operator (??) for default values](#part0048.xhtml#a9G3)

[Use the spaceship operator (<=>) for concise comparisons](#part0049.xhtml#a9G8)

[Employ the null safe operator (?->) for safe property/method access](#part0050.xhtml#a9FT)

[Use match expressions for cleaner switch-like functionality](#part0051.xhtml#a9EB)

[Implement iterators for custom object traversal](#part0052.xhtml#a9HB)

[Use type declarations for class properties](#part0053.xhtml#a9GN)

[Employ arrow functions for short, single-expression closures](#part0054.xhtml#a9G5)

[Utilize the spread operator (...) for variadic functions](#part0055.xhtml#a9EN)

[Use named arguments for improved readability in function calls](#part0056.xhtml#a9H4)

[Implement \_\_debugInfo() for custom object debugging output](#part0057.xhtml#a9EH)

[Declare variables close to their usage](#part0058.xhtml#a9GE)

[Use descriptive variable names](#part0059.xhtml#a9GS)

[Avoid global variables, use dependency injection](#part0060.xhtml#a9FY)

[Use constants for fixed values](#part0061.xhtml#a9EE)

[Employ static variables for persistent state within functions](#part0062.xhtml#a9GU)

[Extract complex conditions into well-named methods](#part0063.xhtml#a9GR)

[Create separate methods for different levels of abstraction](#part0064.xhtml#a9GY)

[Use pure functions that don't modify state](#part0065.xhtml#a9FS)

[Implement single responsibility principle for classes and methods](#part0066.xhtml#a9GB)

[Separate query operations from command operations](#part0067.xhtml#a9E9)

[Use type-safe enums with SplEnum](#part0068.xhtml#a9EY)

[Implement fluent interfaces for method chaining](#part0069.xhtml#a9FX)

[Use final classes when inheritance is not needed](#part0070.xhtml#a9F4)

[Employ static analysis tools like PHPStan for code quality](#part0071.xhtml#a9FA)

[Utilize scalar type declarations for primitive types](#part0072.xhtml#a9F9)

[Break long method chains into multiple lines](#part0073.xhtml#a9F3)

[Use intermediate variables to explain complex calculations](#part0074.xhtml#a9G0)

[Extract complex regular expressions into named constants](#part0075.xhtml#a9EK)

[Use array destructuring for cleaner multiple assignment](#part0076.xhtml#a9FR)

[Employ the null coalescing assignment operator (??=) for concise default assignments](#part0077.xhtml#a9GM)

[Extract configuration into separate files](#part0078.xhtml#a9ET)

[Move utility functions to a separate class or namespace](#part0079.xhtml#a9GV)

[Use traits for cross-cutting concerns](#part0080.xhtml#a9FK)

[Implement caching mechanisms as separate classes](#part0081.xhtml#a9GD)

[Extract complex validation logic into dedicated validator classes](#part0082.xhtml#a9FC)

[Use union types for more precise type hinting](#part0083.xhtml#a9GK)

[Implement \_\_serialize and \_\_unserialize for custom object serialization](#part0084.xhtml#a9GP)

[Use the Reflection API for dynamic code analysis](#part0085.xhtml#a9HE)

[Employ the \_\_set\_state magic method for var\_export compatibility](#part0086.xhtml#a9GA)

[Utilize the \_\_clone magic method for proper object cloning](#part0087.xhtml#a9G7)

[Use associative arrays for key-value pairs](#part0088.xhtml#a9F5)

[Employ SplFixedArray for memory-efficient numeric arrays](#part0089.xhtml#a9H6)

[Use SplObjectStorage for object-based hash tables](#part0090.xhtml#a9F7)

[Implement ArrayAccess for array-like object behavior](#part0091.xhtml#a9FJ)

[Use SplQueue and SplStack for efficient FIFO and LIFO operations](#part0092.xhtml#a9H5)

[Use try-catch blocks for expected exceptions](#part0093.xhtml#a9FU)

[Create custom exception classes for specific error types](#part0094.xhtml#a9FN)

[Use finally blocks for cleanup operations](#part0095.xhtml#a9EM)

[Implement logging in catch blocks for better debugging](#part0096.xhtml#a9EZ)

[Use type-hinting in catch blocks for specific exception handling](#part0097.xhtml#a9FZ)

[Create reusable traits for common functionality](#part0098.xhtml#a9G1)

[Implement abstract classes for shared behavior in class hierarchies](#part0099.xhtml#a9FW)

[Use dependency injection containers for managing object creation](#part0100.xhtml#a9FH)

[Employ the factory pattern for object instantiation](#part0101.xhtml#a9FB)

[Implement the strategy pattern for interchangeable algorithms](#part0102.xhtml#a9H2)

[Use the observer pattern for loose coupling between objects](#part0103.xhtml#a9GG)

[Implement the decorator pattern for dynamic behavior addition](#part0104.xhtml#a9G4)

Introduction

◆

Welcome to this comprehensive guide on writing better PHP code!

In the pages that follow, you'll discover 100 powerful techniques to enhance your programming skills and create more readable, maintainable code.

We'll explore PHP-specific features and best practices, all aimed at crafting code that your fellow developers will find a joy to read and work with.

Each technique is presented with clear examples, contrasting good practices with less optimal approaches.

This structure allows you to easily grasp and apply these concepts in your own projects.

Whether you're a seasoned PHP developer or just starting your journey, this book offers valuable insights to elevate your coding prowess.

Let's embark on this exciting adventure to master the art of writing clean, efficient, and reader-friendly PHP code!

1

# Use type hinting for function parameters and return values

* * *

Enhance code readability and maintainability by specifying data types for function parameters and return values.

* * *

The following code demonstrates the use of type hinting in PHP functions:

< Good Code >

<?php

// Good example: Using type hinting for parameters and return value

function calculateArea(float $length, float $width): float {

    // Calculate the area of a rectangle

    $area = $length \* $width;

    // Return the calculated area

    return $area;

}

// Usage example

$rectangleArea = calculateArea(5.5, 3.2);

echo "The area of the rectangle is: " . $rectangleArea;

?>

<Bad Code>

<?php

// Bad example: No type hinting used

function calculateArea($length, $width) {

    // Calculate the area of a rectangle

    $area = $length \* $width;

    // Return the calculated area

    return $area;

}

// Usage example

$rectangleArea = calculateArea(5.5, 3.2);

echo "The area of the rectangle is: " . $rectangleArea;

?>

In the good example, type hinting is used for both function parameters (float $length, float $width) and the return value (: float). This clearly indicates that the function expects two float values as input and returns a float value. The bad example lacks type hinting, making it less clear what types of data the function expects or returns.

<Memo>

Type hinting was introduced in PHP 5 and has been expanded in subsequent versions, with PHP 7 introducing return type declarations.

2

# Implement interfaces to define clear contracts for classes

* * *

Use interfaces to establish a clear contract for classes, improving code structure and maintainability.

* * *

The following code demonstrates the implementation of an interface in PHP:

< Good Code >

<?php

// Good example: Using an interface to define a contract

interface ShapeInterface {

    public function calculateArea(): float;

    public function calculatePerimeter(): float;

}

class Rectangle implements ShapeInterface {

    private float $length;

    private float $width;

    public function \_\_construct(float $length, float $width) {

        $this->length = $length;

        $this->width = $width;

    }

    public function calculateArea(): float {

        return $this->length \* $this->width;

    }

    public function calculatePerimeter(): float {

        return 2 \* ($this->length + $this->width);

    }

}

// Usage example

$rectangle = new Rectangle(5.5, 3.2);

echo "Rectangle Area: " . $rectangle->calculateArea() . "\\n";

echo "Rectangle Perimeter: " . $rectangle->calculatePerimeter();

?>

<Bad Code>

<?php

// Bad example: No interface used, less clear structure

class Rectangle {

    private $length;

    private $width;

    public function \_\_construct($length, $width) {

        $this->length = $length;

        $this->width = $width;

    }

    public function calculateArea() {

        return $this->length \* $this->width;

    }

    public function calculatePerimeter() {

        return 2 \* ($this->length + $this->width);

    }

}

// Usage example

$rectangle = new Rectangle(5.5, 3.2);

echo "Rectangle Area: " . $rectangle->calculateArea() . "\\n";

echo "Rectangle Perimeter: " . $rectangle->calculatePerimeter();

?>

The good example uses an interface (ShapeInterface) to define a clear contract for shape classes. This ensures that any class implementing this interface must provide calculateArea() and calculatePerimeter() methods. The Rectangle class then implements this interface, adhering to the defined contract. In contrast, the bad example lacks an interface, making it less clear what methods a shape class should implement.

<Memo>

Interfaces in PHP can be implemented by classes using the 'implements' keyword, and a single class can implement multiple interfaces.

3

# Utilize traits for code reuse across multiple classes

* * *

Traits in PHP allow for horizontal code reuse, enabling the sharing of methods across unrelated classes.

* * *

The following code demonstrates the use of a trait to share a logging method across multiple classes:

< Good Code >

// Define a trait for logging

trait Logger {

    // Method to log messages

    public function log($message) {

        echo date('Y-m-d H:i:s') . ': ' . $message . PHP\_EOL;

    }

}

// Class using the Logger trait

class User {

    use Logger;

    private $name;

    public function \_\_construct($name) {

        $this->name = $name;

        $this->log("User {$this->name} created");

    }

    public function getName() {

        return $this->name;

    }

}

// Another class using the same Logger trait

class Order {

    use Logger;

    private $orderId;

    public function \_\_construct($orderId) {

        $this->orderId = $orderId;

        $this->log("Order #{$this->orderId} created");

    }

    public function getOrderId() {

        return $this->orderId;

    }

}

// Usage

$user = new User("John");

$order = new Order(1001);

<Bad Code>

// Class with duplicated logging logic

class User {

    private $name;

    public function \_\_construct($name) {

        $this->name = $name;

        echo date('Y-m-d H:i:s') . ': User ' . $this->name . ' created' . PHP\_EOL;

    }

    public function getName() {

        return $this->name;

    }

    public function log($message) {

        echo date('Y-m-d H:i:s') . ': ' . $message . PHP\_EOL;

    }

}

// Another class with duplicated logging logic

class Order {

    private $orderId;

    public function \_\_construct($orderId) {

        $this->orderId = $orderId;

        echo date('Y-m-d H:i:s') . ': Order #' . $this->orderId . ' created' . PHP\_EOL;

    }

    public function getOrderId() {

        return $this->orderId;

    }

    public function log($message) {

        echo date('Y-m-d H:i:s') . ': ' . $message . PHP\_EOL;

    }

}

// Usage

$user = new User("John");

$order = new Order(1001);

The good code example demonstrates the use of a trait to share the logging functionality across multiple classes. This approach promotes code reuse and reduces duplication. The Logger trait contains a single log method that can be used by any class that includes the trait.

In contrast, the bad code example shows the same logging logic duplicated in both the User and Order classes. This leads to code repetition and makes maintenance more difficult.

By using traits, we can keep our code DRY (Don't Repeat Yourself) and make it easier to update the logging functionality across all classes that use the trait.

<Memo>

Traits were introduced in PHP 5.4.0 and provide a mechanism for code reuse in single inheritance languages like PHP.

4

# Employ namespaces to organize and avoid naming conflicts

* * *

Namespaces in PHP help organize code into logical groups and prevent naming conflicts between classes, functions, and constants.

* * *

The following code demonstrates the use of namespaces to organize classes and avoid naming conflicts:

< Good Code >

<?php

// File: User.php

namespace App\\Models;

class User {

    private $name;

    public function \_\_construct($name) {

        $this->name = $name;

    }

    public function getName() {

        return $this->name;

    }

}

// File: Order.php

namespace App\\Models;

class Order {

    private $orderId;

    public function \_\_construct($orderId) {

        $this->orderId = $orderId;

    }

    public function getOrderId() {

        return $this->orderId;

    }

}

// File: UserController.php

namespace App\\Controllers;

use App\\Models\\User;

class UserController {

    public function createUser($name) {

        $user = new User($name);

        return $user;

    }

}

// Usage

use App\\Models\\User;

use App\\Models\\Order;

use App\\Controllers\\UserController;

$user = new User("John");

$order = new Order(1001);

$userController = new UserController();

<Bad Code>

<?php

// All classes in global namespace

class User {

    private $name;

    public function \_\_construct($name) {

        $this->name = $name;

    }

    public function getName() {

        return $this->name;

    }

}

class Order {

    private $orderId;

    public function \_\_construct($orderId) {

        $this->orderId = $orderId;

    }

    public function getOrderId() {

        return $this->orderId;

    }

}

class UserController {

    public function createUser($name) {

        $user = new User($name);

        return $user;

    }

}

// Usage

$user = new User("John");

$order = new Order(1001);

$userController = new UserController();

The good code example demonstrates the use of namespaces to organize classes into logical groups. The User and Order classes are placed in the App\\Models namespace, while the UserController is in the App\\Controllers namespace. This organization helps to avoid naming conflicts and makes the code structure more clear.

In contrast, the bad code example places all classes in the global namespace. This approach can lead to naming conflicts as the project grows and makes it harder to understand the logical structure of the code.

Using namespaces allows for better code organization, improves readability, and helps prevent naming collisions in larger projects. It also enables the use of the same class name in different contexts (e.g., you could have both App\\Models\\User and App\\Entities\\User).

<Memo>

Namespaces were introduced in PHP 5.3.0 to help solve the problem of name clashes between code you create, and internal PHP classes/functions/constants or third-party classes/functions/constants.

5

# Use anonymous functions (closures) for compact, inline functionality

* * *

Anonymous functions in PHP provide a concise way to create inline, single-use functions.

* * *

The following code demonstrates the use of an anonymous function as a callback for array\_map():

< Good Code >

<?php

// Using an anonymous function to square numbers in an array

$numbers = \[1, 2, 3, 4, 5\];

// Apply the anonymous function to each element

$squared = array\_map(function($n) {

    return $n \* $n;

}, $numbers);

// Output: Array (  => 1  => 4  => 9  => 16  => 25 )

print\_r($squared);

?>

<Bad Code>

<?php

// Not using an anonymous function

$numbers = \[1, 2, 3, 4, 5\];

// Define a separate function

function square($n) {

    return $n \* $n;

}

// Use the named function as a callback

$squared = array\_map('square', $numbers);

// Output: Array (  => 1  => 4  => 9  => 16  => 25 )

print\_r($squared);

?>

The good code example uses an anonymous function directly within array\_map(), making the code more compact and self-contained. The bad code defines a separate named function, which can clutter the global namespace and may be less readable for simple operations.

<Memo>

Anonymous functions were introduced in PHP 5.3 and are also known as closures. They can capture variables from the parent scope using the 'use' keyword.

6

# Prefix interface names with 'I' (e.g., ILogger)

* * *

Prefixing interface names with 'I' is a naming convention that clearly distinguishes interfaces from classes.

* * *

The following code demonstrates the use of an 'I' prefixed interface and its implementation:

< Good Code >

<?php

// Interface name prefixed with 'I'

interface ILogger {

    public function log($message);

}

// Class implementing the interface

class FileLogger implements ILogger {

    public function log($message) {

        // Implementation details

        file\_put\_contents('log.txt', $message . PHP\_EOL, FILE\_APPEND);

    }

}

// Usage

$logger = new FileLogger();

$logger->log('This is a log message.');

?>

<Bad Code>

<?php

// Interface without 'I' prefix

interface Logger {

    public function log($message);

}

// Class implementing the interface

class FileLogger implements Logger {

    public function log($message) {

        // Implementation details

        file\_put\_contents('log.txt', $message . PHP\_EOL, FILE\_APPEND);

    }

}

// Usage

$logger = new FileLogger();

$logger->log('This is a log message.');

?>

The good code example uses 'ILogger' as the interface name, clearly indicating it's an interface. This helps developers quickly distinguish between interfaces and concrete classes. The bad code example doesn't use the 'I' prefix, which might lead to confusion, especially in larger codebases.

<Memo>

While prefixing interfaces with 'I' is common in some programming communities (especially those with a background in languages like C#), it's not a universal standard in PHP. Some developers prefer not to use this convention, arguing that it adds unnecessary noise to the code.

7

# Use 'is' prefix for boolean methods

* * *

Prefix boolean methods with 'is' to improve code readability

* * *

The following code demonstrates the use of 'is' prefix for boolean methods in PHP:

< Good Code >

class User {

    private $active;

    // Good: Method name clearly indicates it returns a boolean

    public function isActive(): bool {

        return $this->active;

    }

    // Usage

    public function performAction() {

        if ($this->isActive()) {

            // Perform action for active user

        }

    }

}

<Bad Code>

class User {

    private $active;

    // Bad: Method name doesn't clearly indicate it returns a boolean

    public function active(): bool {

        return $this->active;

    }

    // Usage

    public function performAction() {

        if ($this->active()) {

            // Is this checking if the user is active or doing something else?

        }

    }

}

In the good example, the method name 'isActive()' clearly indicates that it returns a boolean value. This makes the code more readable and self-explanatory. In contrast, the bad example uses 'active()', which could be mistaken for a method that performs an action rather than returning a state.

<Memo>

This naming convention is part of the broader concept of "Clean Code" and is commonly used in many object-oriented programming languages, not just PHP.

8

# Prefix abstract classes with 'Abstract'

* * *

Use 'Abstract' prefix for abstract classes to enhance code clarity

* * *

The following code illustrates the use of 'Abstract' prefix for abstract classes in PHP:

< Good Code >

// Good: Class name clearly indicates it's an abstract class

abstract class AbstractController {

    abstract public function index();

    public function render() {

        // Common rendering logic

    }

}

class UserController extends AbstractController {

    public function index() {

        // Implementation for user index

    }

}

<Bad Code>

// Bad: Class name doesn't indicate it's an abstract class

abstract class Controller {

    abstract public function index();

    public function render() {

        // Common rendering logic

    }

}

class UserController extends Controller {

    public function index() {

        // Implementation for user index

    }

}

In the good example, prefixing the abstract class with 'Abstract' (AbstractController) immediately informs other developers that this is an abstract class. It clarifies the nature of the class without having to look at its implementation. The bad example doesn't provide this immediate clarity, potentially leading to confusion.

<Memo>

This naming convention is widely used in many frameworks and libraries, including popular PHP frameworks like Symfony and Laravel.

9

# Use 'able' suffix for classes implementing capabilities

* * *

Append 'able' to class names that implement specific capabilities or behaviors.

* * *

The following code demonstrates the use of the 'able' suffix in class naming for better readability and understanding of class capabilities.

< Good Code >

// Good example: Using 'able' suffix for classes implementing capabilities

// Interface defining sortable behavior

interface Sortable {

    public function sort(): array;

}

// Class implementing the Sortable interface

class SortableList implements Sortable {

    private $items = \[\];

    public function \_\_construct(array $items) {

        $this->items = $items;

    }

    // Implementation of the sort method

    public function sort(): array {

        sort($this->items);

        return $this->items;

    }

}

// Usage

$list = new SortableList(\[3, 1, 4, 1, 5, 9\]);

$sortedList = $list->sort();

print\_r($sortedList);

<Bad Code>

// Bad example: Not using 'able' suffix for classes implementing capabilities

// Interface without clear naming convention

interface DoSort {

    public function performSort(): array;

}

// Class with unclear naming

class ListThing implements DoSort {

    private $stuff = \[\];

    public function \_\_construct(array $stuff) {

        $this->stuff = $stuff;

    }

    // Unclear method name

    public function performSort(): array {

        sort($this->stuff);

        return $this->stuff;

    }

}

// Usage

$thing = new ListThing(\[3, 1, 4, 1, 5, 9\]);

$sortedStuff = $thing->performSort();

print\_r($sortedStuff);

The good example uses the 'able' suffix in both the interface (Sortable) and the implementing class (SortableList). This naming convention immediately conveys the capability of the class. The method names are also clear and consistent (sort()).

In contrast, the bad example uses unclear names like 'DoSort' and 'ListThing', which don't effectively communicate the purpose or capabilities of the interface and class. The method name 'performSort()' is also less intuitive than simply 'sort()'.

<Memo>

The 'able' suffix is commonly used in object-oriented programming across various languages, not just PHP. It's part of a broader naming convention that helps developers quickly understand a class's purpose or capabilities.

10

# Prefix private methods with an underscore

* * *

Use an underscore prefix for private methods to visually distinguish them from public methods.

* * *

The following code examples demonstrate the use of underscore prefixes for private methods to improve code readability and method visibility understanding.

< Good Code >

// Good example: Using underscore prefix for private methods

class UserManager {

    private $users = \[\];

    public function addUser(string $username, string $email): void {

        if ($this->\_isValidEmail($email)) {

            $this->users\[\] = \[

                'username' => $username,

                'email' => $email

            \];

            $this->\_notifyAdmin($username);

        }

    }

    // Private method with underscore prefix

    private function \_isValidEmail(string $email): bool {

        return filter\_var($email, FILTER\_VALIDATE\_EMAIL) !== false;

    }

    // Another private method with underscore prefix

    private function \_notifyAdmin(string $username): void {

        // Simulating admin notification

        echo "Admin notified about new user: $username\\n";

    }

}

// Usage

$manager = new UserManager();

$manager->addUser('john\_doe', 'john@example.com');

<Bad Code>

// Bad example: Not using underscore prefix for private methods

class UserManager {

    private $users = \[\];

    public function addUser(string $username, string $email): void {

        if ($this->isValidEmail($email)) {

            $this->users\[\] = \[

                'username' => $username,

                'email' => $email

            \];

            $this->notifyAdmin($username);

        }

    }

    // Private method without underscore prefix

    private function isValidEmail(string $email): bool {

        return filter\_var($email, FILTER\_VALIDATE\_EMAIL) !== false;

    }

    // Another private method without underscore prefix

    private function notifyAdmin(string $username): void {

        // Simulating admin notification

        echo "Admin notified about new user: $username\\n";

    }

}

// Usage

$manager = new UserManager();

$manager->addUser('john\_doe', 'john@example.com');

In the good example, private methods (\_isValidEmail and \_notifyAdmin) are prefixed with an underscore. This visual cue immediately indicates to other developers that these methods are intended for internal use within the class.

The bad example doesn't use the underscore prefix, making it less obvious which methods are private and which are public without checking the method declarations.

Both examples function identically, but the good example enhances code readability and helps prevent accidental misuse of private methods.

<Memo>

While using an underscore prefix for private methods is a common convention in PHP, it's important to note that PHP doesn't enforce any special meaning to methods prefixed with an underscore. The visibility is controlled by the 'private' keyword, not the underscore itself.

11

# Avoid abbreviations in variable and function names

* * *

Using full words in variable and function names makes the code more readable and understandable.

* * *

When writing PHP code, it's important to use descriptive names for variables and functions. Avoiding abbreviations helps other developers understand the purpose of the code without needing additional context.

< Good Code >

<?php

// Good example: Using full words for variable and function names

// Function to calculate the total price of items in a cart

function calculateTotalPrice($items) {

    $totalPrice = 0;

    foreach ($items as $item) {

        $totalPrice += $item\['price'\] \* $item\['quantity'\];

    }

    return $totalPrice;

}

// Array of items in the cart

$shoppingCartItems = \[

    \['price' => 10, 'quantity' => 2\],

    \['price' => 5, 'quantity' => 3\]

\];

// Calculate the total price of items in the cart

$total = calculateTotalPrice($shoppingCartItems);

echo "Total Price: $" . $total;

?>

<Bad Code>

<?php

// Bad example: Using abbreviations for variable and function names

// Function to calculate the total price of items in a cart

function calcTotPr($itms) {

    $totPr = 0;

    foreach ($itms as $itm) {

        $totPr += $itm\['pr'\] \* $itm\['qty'\];

    }

    return $totPr;

}

// Array of items in the cart

$shpCrtItms = \[

    \['pr' => 10, 'qty' => 2\],

    \['pr' => 5, 'qty' => 3\]

\];

// Calculate the total price of items in the cart

$tot = calcTotPr($shpCrtItms);

echo "Total Price: $" . $tot;

?>

In the good example, the function name calculateTotalPrice and variable names like $shoppingCartItems are clear and descriptive. This makes the code easier to read and understand. In the bad example, abbreviations like calcTotPr and $shpCrtItms make the code harder to follow, especially for someone who is not familiar with the abbreviations used.

<Memo>

Did you know? The practice of using descriptive names in code is often referred to as "self-documenting code." This means the code itself provides enough context and information that separate documentation is less necessary.

12

# Use intention-revealing names (e.g., getUsersByRole instead of getUsers)

* * *

Names should clearly indicate the purpose and behavior of the function or variable.

* * *

When naming functions and variables, it's crucial to choose names that reveal the intention behind their use. This helps other developers quickly understand what the code is supposed to do without needing to read through the entire implementation.

< Good Code >

<?php

// Good example: Using intention-revealing names

// Function to get users by their role

function getUsersByRole($role) {

    // Assume $db is a database connection

    global $db;

    $query = $db->prepare("SELECT \* FROM users WHERE role = :role");

    $query->bindParam(':role', $role);

    $query->execute();

    return $query->fetchAll();

}

// Get all admin users

$adminUsers = getUsersByRole('admin');

foreach ($adminUsers as $user) {

    echo $user\['name'\] . "<br>";

}

?>

<Bad Code>

<?php

// Bad example: Using non-descriptive names

// Function to get users

function getUsers($r) {

    // Assume $db is a database connection

    global $db;

    $query = $db->prepare("SELECT \* FROM users WHERE role = :role");

    $query->bindParam(':role', $r);

    $query->execute();

    return $query->fetchAll();

}

// Get all admin users

$admins = getUsers('admin');

foreach ($admins as $u) {

    echo $u\['name'\] . "<br>";

}

?>

In the good example, the function name getUsersByRole clearly indicates that the function retrieves users based on their role. This makes the code more understandable and maintainable. In the bad example, the function name getUsers is vague and does not provide enough context about what the function does, making it harder for other developers to understand its purpose.

<Memo>

Fun fact: Intention-revealing names are a key principle in the SOLID design principles, specifically under the Single Responsibility Principle (SRP). This principle states that a class or function should have only one reason to change, and clear naming helps achieve this by making the purpose of the code explicit.

13

# Avoid using similar names with different meanings

* * *

Use distinct and meaningful variable names to improve code readability.

* * *

The following code demonstrates the importance of using distinct variable names:

< Good Code >

// Good example: Using distinct and meaningful variable names

function calculateTotalPrice($basePrice, $taxRate, $shippingCost) {

    // Calculate the tax amount

    $taxAmount = $basePrice \* ($taxRate / 100);

    // Calculate the total price including tax and shipping

    $totalPrice = $basePrice + $taxAmount + $shippingCost;

    return $totalPrice;

}

// Usage

$finalPrice = calculateTotalPrice(100, 8, 5);

echo "Total price: $" . $finalPrice;

<Bad Code>

// Bad example: Using similar names with different meanings

function calc($price, $rate, $cost) {

    // Confusing variable names

    $p = $price \* ($rate / 100);

    $price = $price + $p + $cost;

    return $price;

}

// Usage

$price = calc(100, 8, 5);

echo "Price: $" . $price;

In the good example, we use distinct and meaningful variable names like $basePrice, $taxRate, and $shippingCost. This makes the code more readable and self-explanatory. The bad example uses similar and vague names like $price and $p, which can lead to confusion and potential errors.

<Memo>

Using meaningful variable names is part of the "self-documenting code" principle, which aims to make code more understandable without extensive comments.

14

# Use opposite pairs consistently (e.g., start/stop, open/close)

* * *

Maintain consistency in naming conventions for opposite actions to enhance code clarity.

* * *

The following code illustrates the importance of using consistent opposite pairs in method names:

< Good Code >

// Good example: Using consistent opposite pairs

class FileHandler {

    private $fileHandle;

    public function openFile($filename) {

        $this->fileHandle = fopen($filename, 'r');

        echo "File opened successfully.\\n";

    }

    public function closeFile() {

        if ($this->fileHandle) {

            fclose($this->fileHandle);

            echo "File closed successfully.\\n";

        }

    }

    public function startProcessing() {

        echo "Starting file processing...\\n";

        // Processing logic here

    }

    public function stopProcessing() {

        echo "Stopping file processing...\\n";

        // Cleanup logic here

    }

}

// Usage

$handler = new FileHandler();

$handler->openFile('example.txt');

$handler->startProcessing();

$handler->stopProcessing();

$handler->closeFile();

<Bad Code>

// Bad example: Inconsistent naming for opposite actions

class FileHandler {

    private $file;

    public function initializeFile($filename) {

        $this->file = fopen($filename, 'r');

        echo "File initialized.\\n";

    }

    public function endFile() {

        if ($this->file) {

            fclose($this->file);

            echo "File ended.\\n";

        }

    }

    public function beginOperation() {

        echo "Beginning operation...\\n";

        // Processing logic here

    }

    public function finish() {

        echo "Finishing...\\n";

        // Cleanup logic here

    }

}

// Usage

$handler = new FileHandler();

$handler->initializeFile('example.txt');

$handler->beginOperation();

$handler->finish();

$handler->endFile();

The good example uses consistent opposite pairs like openFile/closeFile and startProcessing/stopProcessing. This makes the code more intuitive and easier to understand. The bad example uses inconsistent terms like initializeFile/endFile and beginOperation/finish, which can lead to confusion about the intended actions.

<Memo>

Consistent naming conventions are a key aspect of the "principle of least astonishment" in software design, which states that a component of a system should behave in a way that users expect it to behave.

15

# Meaningful and Distinct Naming

* * *

Use clear, descriptive names for variables, functions, and classes to enhance code readability.

* * *

The following example demonstrates the importance of using distinct and meaningful names in PHP code:

< Good Code >

// Good example: Clear and distinct naming

class UserAuthenticationController

{

    public function authenticateUserCredentials($username, $password)

    {

        // Authentication logic here

    }

    public function validateUserInput($input)

    {

        // Input validation logic here

    }

}

$authController = new UserAuthenticationController();

$authController->authenticateUserCredentials('john\_doe', 'secure\_password');

<Bad Code>

// Bad example: Names that vary in small ways

class XYZControllerForEfficientHandlingOfStrings

{

    public function XYZControllerForEfficientHandlingOfStringsFunction($x, $y)

    {

        // Authentication logic here

    }

    public function XYZControllerForEfficientHandlingOfStringsValidation($z)

    {

        // Input validation logic here

    }

}

$c = new XYZControllerForEfficientHandlingOfStrings();

$c->XYZControllerForEfficientHandlingOfStringsFunction('a', 'b');

In the good example, we use clear and distinct names for the class (UserAuthenticationController) and its methods (authenticateUserCredentials, validateUserInput). This makes the code's purpose immediately apparent.

In the bad example, we use long, repetitive names that don't clearly convey the purpose of the class or methods. The variable names are also non-descriptive (x, y, z), making it hard to understand what data they represent.

<Memo>

The concept of using meaningful names is part of the "Clean Code" philosophy, popularized by Robert C. Martin in his book of the same name.

16

# Strict Types Declaration

* * *

Use strict\_types declaration to enable stricter type checking in PHP, reducing potential type-related errors.

* * *

The following example shows how to use strict\_types declaration in PHP:

< Good Code >

<?php

declare(strict\_types=1);

// Function with type hints and return type declaration

function addNumbers(int $a, int $b): int

{

    return $a + $b;

}

// Correct usage

$result = addNumbers(5, 10);

echo $result; // Outputs: 15

// This will throw a TypeError

// $result = addNumbers(5, "10");

<Bad Code>

<?php

// Without strict\_types declaration

// Function without type hints

function addNumbers($a, $b)

{

    return $a + $b;

}

// This works, but may lead to unexpected results

$result = addNumbers(5, "10");

echo $result; // Outputs: 15

// This also "works", but is likely not intended

$result = addNumbers("5", "10");

echo $result; // Outputs: 15

In the good example, we use declare(strict\_types=1) at the beginning of the file. This enables strict type checking. We also use type hints for function parameters and return type declaration. This ensures that only integers can be passed to the function and returned from it.

In the bad example, without strict types, PHP will attempt to coerce values to the appropriate type. This can lead to unexpected behavior, as seen when passing a string "10" instead of an integer 10.

<Memo>

Strict types were introduced in PHP 7.0, providing a way to opt-in to stricter type checking and improving code reliability.

17

# Implement magic methods for cleaner syntax

* * *

Use \_\_toString, \_\_get, and \_\_set magic methods to create more intuitive and readable code.

* * *

The following code demonstrates the use of magic methods in a Person class:

< Good Code >

class Person {

    private $data = \[\];

    // Magic method to convert object to string

    public function \_\_toString() {

        return $this->data\['name'\] ?? 'Unnamed Person';

    }

    // Magic method to get properties

    public function \_\_get($property) {

        return $this->data\[$property\] ?? null;

    }

    // Magic method to set properties

    public function \_\_set($property, $value) {

        $this->data\[$property\] = $value;

    }

}

// Usage

$person = new Person();

$person->name = "John Doe";  // Uses \_\_set

$person->age = 30;           // Uses \_\_set

echo $person;                // Uses \_\_toString

echo $person->name;          // Uses \_\_get

<Bad Code>

class Person {

    public $name;

    public $age;

    public function getName() {

        return $this->name;

    }

    public function setName($name) {

        $this->name = $name;

    }

    public function getAge() {

        return $this->age;

    }

    public function setAge($age) {

        $this->age = $age;

    }

    public function getPersonInfo() {

        return $this->name ?? 'Unnamed Person';

    }

}

// Usage

$person = new Person();

$person->setName("John Doe");

$person->setAge(30);

echo $person->getPersonInfo();

echo $person->getName();

The good code example uses magic methods (\_\_toString, \_\_get, \_\_set) to create a more intuitive and flexible interface. This allows for dynamic property access and setting, as well as easy string conversion. The bad code example uses traditional getters and setters, which can lead to more verbose and less flexible code.

<Memo>

Magic methods in PHP are special methods that override PHP's default action when certain actions are performed on an object.

18

# Use generators for memory-efficient iteration

* * *

Implement generators to handle large datasets without excessive memory usage.

* * *

The following code demonstrates the use of a generator function to process a large file:

< Good Code >

function readLargeFile($filePath) {

    $handle = fopen($filePath, 'r');

    while (!feof($handle)) {

        yield trim(fgets($handle));

    }

    fclose($handle);

}

// Usage

$filePath = 'large\_file.txt';

foreach (readLargeFile($filePath) as $line) {

    echo "Processing line: $line\\n";

    // Process each line

}

<Bad Code>

function readLargeFile($filePath) {

    $lines = \[\];

    $handle = fopen($filePath, 'r');

    while (!feof($handle)) {

        $lines\[\] = trim(fgets($handle));

    }

    fclose($handle);

    return $lines;

}

// Usage

$filePath = 'large\_file.txt';

$allLines = readLargeFile($filePath);

foreach ($allLines as $line) {

    echo "Processing line: $line\\n";

    // Process each line

}

The good code example uses a generator function, which yields each line of the file one at a time. This approach is memory-efficient as it doesn't load the entire file into memory at once. The bad code example reads the entire file into an array before processing, which can lead to high memory usage for large files.

<Memo>

Generators were introduced in PHP 5.5 and provide an easy way to implement simple iterators without the overhead or complexity of implementing a class that implements the Iterator interface.

19

# Employ late static binding for more flexible inheritance

* * *

Use self::class instead of static::class for more flexible and dynamic inheritance in PHP.

* * *

Late static binding allows for more flexible inheritance by using the 'static' keyword instead of 'self'. This is particularly useful when dealing with inherited static methods.

< Good Code >

class ParentClass {

    public static function getClassName() {

        // Use static::class for late static binding

        return static::class;

    }

}

class ChildClass extends ParentClass {

    // No need to override getClassName()

}

// Usage

echo ParentClass::getClassName(); // Outputs: ParentClass

echo ChildClass::getClassName();  // Outputs: ChildClass

<Bad Code>

class ParentClass {

    public static function getClassName() {

        // Using self::class, which always refers to the current class

        return self::class;

    }

}

class ChildClass extends ParentClass {

    // Forced to override to get the correct class name

    public static function getClassName() {

        return self::class;

    }

}

// Usage

echo ParentClass::getClassName(); // Outputs: ParentClass

echo ChildClass::getClassName();  // Outputs: ChildClass, but requires overriding

In the good example, we use static::class which employs late static binding. This allows the method to return the correct class name even when called from a child class, without the need to override the method in each child class. The bad example uses self::class, which always refers to the class in which it's used, requiring each child class to override the method to return the correct class name.

<Memo>

Late static binding was introduced in PHP 5.3.0 and provides a way to reference the called class in a static context.

20

# Utilize SPL data structures for specialized data handling

* * *

Leverage PHP's Standard PHP Library (SPL) data structures for efficient and specialized data handling.

* * *

SPL provides a set of standard data structures which can be more efficient and appropriate for specific use cases compared to general-purpose arrays.

< Good Code >

// Using SplFixedArray for a fixed-size, integer-indexed array

$fixedArray = new SplFixedArray(5);

for ($i = 0; $i < 5; $i++) {

    $fixedArray\[$i\] = $i \* 2;

}

// Using SplQueue for a queue data structure

$queue = new SplQueue();

$queue->enqueue('first');

$queue->enqueue('second');

$firstOut = $queue->dequeue();

// Using SplObjectStorage for object-based storage

$storage = new SplObjectStorage();

$obj1 = new stdClass();

$obj2 = new stdClass();

$storage->attach($obj1, 'data for obj1');

$storage->attach($obj2, 'data for obj2');

// Checking if an object exists in storage

var\_dump($storage->contains($obj1)); // true

<Bad Code>

// Using a regular array as a fixed-size array

$fixedArray = array();

for ($i = 0; $i < 5; $i++) {

    $fixedArray\[$i\] = $i \* 2;

}

// Using an array as a queue

$queue = array();

array\_push($queue, 'first');

array\_push($queue, 'second');

$firstOut = array\_shift($queue);

// Using an array for object-based storage

$storage = array();

$obj1 = new stdClass();

$obj2 = new stdClass();

$storage\[spl\_object\_hash($obj1)\] = 'data for obj1';

$storage\[spl\_object\_hash($obj2)\] = 'data for obj2';

// Checking if an object exists in storage

var\_dump(isset($storage\[spl\_object\_hash($obj1)\])); // true

The good example demonstrates the use of SPL data structures (SplFixedArray, SplQueue, and SplObjectStorage) which are optimized for their specific purposes. These provide better performance and more appropriate methods for their intended use cases. The bad example uses regular arrays to accomplish the same tasks, which can be less efficient and require more manual work to maintain the desired behavior.

<Memo>

The Standard PHP Library (SPL) was introduced in PHP 5.0.0 and provides a collection of interfaces and classes for solving common problems.

21

# Comment on why something is done, not what is done

* * *

Explain the reasoning behind code, not just describe its actions.

* * *

The following code demonstrates how to properly comment on the 'why' rather than the 'what' in PHP:

< Good Code >

// We need to ensure the user is logged in before accessing sensitive data

if (!$user->isLoggedIn()) {

    // Redirect to login page if not authenticated

    header('Location: /login.php');

    exit;

}

// Retrieve user's account balance

$balance = $user->getAccountBalance();

// Check if balance is below minimum threshold

if ($balance < MINIMUM\_BALANCE) {

    // Notify user of low balance to prevent overdraft

    sendLowBalanceNotification($user);

}

<Bad Code>

// Check if user is logged in

if (!$user->isLoggedIn()) {

    // Redirect to login page

    header('Location: /login.php');

    exit;

}

// Get balance

$balance = $user->getAccountBalance();

// If balance is low

if ($balance < MINIMUM\_BALANCE) {

    // Send notification

    sendLowBalanceNotification($user);

}

The good code example provides clear explanations for why each action is taken, such as ensuring authentication before accessing sensitive data and notifying users of low balances to prevent overdrafts. The bad code example merely describes what the code does without explaining the reasoning behind it, making it harder for other developers to understand the purpose and importance of each step.

<Memo>

Comments explaining 'why' are often called "intent comments" and can significantly improve code maintainability.

22

# Use PHPDoc blocks for classes, methods, and properties

* * *

Utilize PHPDoc blocks to provide comprehensive documentation for classes, methods, and properties.

* * *

The following example demonstrates the proper use of PHPDoc blocks in a PHP class:

< Good Code >

/\*\*

\* Represents a user account in the system.

\*

\* This class handles user-related operations such as

\* authentication, profile management, and account balance.

\*/

class User

{

    /\*\*

     \* The user's current account balance.

     \*

     \* @var float

     \*/

    private $balance;

    /\*\*

     \* Authenticates the user with given credentials.

     \*

     \* @param string $username The user's username

     \* @param string $password The user's password

     \* @return bool True if authentication is successful, false otherwise

     \* @throws AuthenticationException If the authentication service is unavailable

     \*/

    public function authenticate(string $username, string $password): bool

    {

        // Authentication logic here

    }

    /\*\*

     \* Retrieves the user's current account balance.

     \*

     \* @return float The current balance

     \*/

    public function getAccountBalance(): float

    {

        return $this->balance;

    }

}

<Bad Code>

class User

{

    private $balance;

    public function authenticate($username, $password)

    {

        // Authentication logic here

    }

    public function getAccountBalance()

    {

        return $this->balance;

    }

}

The good code example uses PHPDoc blocks to provide detailed information about the class, its properties, and methods. It includes descriptions, parameter types, return types, and potential exceptions. This makes the code more self-documenting and easier for other developers to understand and use. The bad code example lacks any documentation, making it difficult for others to quickly grasp the purpose and usage of the class and its members.

<Memo>

PHPDoc is based on JavaDoc and is supported by many IDEs for code completion and type hinting.

23

# Explain workarounds or hacks with comments

* * *

Provide clear comments to explain any workarounds or hacks in your code.

* * *

When you use a workaround or hack in your PHP code, it's crucial to add comments explaining why it's necessary and how it works.

< Good Code >

<?php

// Workaround for PHP bug #12345: array\_merge\_recursive() does not preserve keys

// This hack ensures keys are preserved by using a custom function

function array\_merge\_recursive\_distinct(array &$array1, array &$array2) {

    $merged = $array1;

    foreach ($array2 as $key => &$value) {

        if (is\_array($value) && isset($merged\[$key\]) && is\_array($merged\[$key\])) {

            $merged\[$key\] = array\_merge\_recursive\_distinct($merged\[$key\], $value);

        } else {

            $merged\[$key\] = $value;

        }

    }

    return $merged;

}

?>

<Bad Code>

<?php

function array\_merge\_recursive\_distinct(array &$array1, array &$array2) {

    $merged = $array1;

    foreach ($array2 as $key => &$value) {

        if (is\_array($value) && isset($merged\[$key\]) && is\_array($merged\[$key\])) {

            $merged\[$key\] = array\_merge\_recursive\_distinct($merged\[$key\], $value);

        } else {

            $merged\[$key\] = $value;

        }

    }

    return $merged;

}

?>

In the good example, comments clearly explain the reason for the workaround and how it addresses a specific PHP bug. This makes the code more understandable for other developers. In the bad example, the lack of comments leaves the purpose and functionality of the workaround unclear.

<Memo>

PHP has a long history of bugs and quirks, and developers often need to implement workarounds. Documenting these workarounds helps maintain code quality and readability.

24

# Comment on non-obvious optimizations

* * *

Add comments to explain any non-obvious optimizations in your code.

* * *

When you implement optimizations that are not immediately clear, it's important to comment on them to help other developers understand the reasoning behind your choices.

< Good Code >

<?php

// Optimization: Using isset() instead of strlen() for checking empty strings

// isset() is faster because it is a language construct and does not incur function call overhead

function isEmptyString($str) {

    return !isset($str\[0\]);

}

?>

<Bad Code>

<?php

function isEmptyString($str) {

    return !isset($str\[0\]);

}

?>

In the good example, the comment explains why isset() is used instead of strlen(), providing context for the optimization. This helps other developers understand the performance benefits. In the bad example, the lack of comments makes the optimization non-obvious and harder to understand.

<Memo>

PHP's isset() function is often used for performance optimizations because it is a language construct and operates faster than many built-in functions.

25

# Use TODO comments for future improvements or known issues

* * *

TODO comments help track future improvements or known issues in the code.

* * *

Using TODO comments in your PHP code is a simple yet effective way to remind yourself or inform others about areas that need further work or have known issues.

< Good Code >

<?php

// TODO: Refactor this function to improve performance

function calculateSum($numbers) {

    $sum = 0;

    foreach ($numbers as $number) {

        $sum += $number;

    }

    return $sum;

}

// TODO: Handle edge cases for empty arrays

$result = calculateSum(\[1, 2, 3, 4, 5\]);

echo $result;

?>

<Bad Code>

<?php

function calculateSum($numbers) {

    $sum = 0;

    foreach ($numbers as $number) {

        $sum += $number;

    }

    return $sum;

}

$result = calculateSum(\[1, 2, 3, 4, 5\]);

echo $result;

?>

In the good example, TODO comments clearly indicate areas that need improvement or additional handling. This makes it easier for developers to understand what needs to be addressed in the future. The bad example lacks these comments, making it harder to track necessary changes or improvements.

<Memo>

The term "TODO" is commonly used in many programming languages and IDEs to mark tasks that need to be completed. Some IDEs even provide special features to list all TODO comments in a project.

26

# Keep comments up-to-date with code changes

* * *

Ensure comments accurately reflect the current state of the code.

* * *

Keeping comments up-to-date with code changes is crucial for maintaining code readability and preventing confusion among developers.

< Good Code >

<?php

// This function calculates the sum of an array of numbers

function calculateSum($numbers) {

    $sum = 0;

    foreach ($numbers as $number) {

        $sum += $number;

    }

    return $sum;

}

// Calculate the sum of the given array

$result = calculateSum(\[1, 2, 3, 4, 5\]);

echo $result;

?>

<Bad Code>

<?php

// This function multiplies all numbers in an array

function calculateSum($numbers) {

    $sum = 0;

    foreach ($numbers as $number) {

        $sum += $number;

    }

    return $sum;

}

// Calculate the sum of the given array

$result = calculateSum(\[1, 2, 3, 4, 5\]);

echo $result;

?>

In the good example, comments accurately describe the function and its purpose, making it easier for other developers to understand the code. In the bad example, the comment incorrectly states that the function multiplies numbers, which can lead to confusion and errors.

<Memo>

Consistently updating comments is a best practice in software development. Some teams even include comment updates as part of their code review process to ensure accuracy and clarity.

27

# Remove commented-out code

* * *

Delete unused code instead of commenting it out to improve code readability and maintainability.

* * *

The following example demonstrates how to handle unused code properly:

< Good Code >

<?php

function calculateTotal($price, $quantity) {

    $total = $price \* $quantity;

    $tax = $total \* 0.1;

    return $total + $tax;

}

$result = calculateTotal(10, 5);

echo "Total: $" . number\_format($result, 2);

?>

<Bad Code>

<?php

function calculateTotal($price, $quantity) {

    $total = $price \* $quantity;

    $tax = $total \* 0.1;

    return $total + $tax;

    // Old calculation method

    // $oldTotal = $price \* $quantity \* 1.15;

    // return $oldTotal;

}

$result = calculateTotal(10, 5);

echo "Total: $" . number\_format($result, 2);

// echo "Old total: $" . number\_format($oldResult, 2);

?>

The good code example shows a clean implementation without any commented-out code. The bad code example includes unnecessary commented-out code that clutters the function and reduces readability. Instead of keeping old code as comments, it's better to remove it entirely and rely on version control systems to track code history.

<Memo>

Version control systems like Git allow developers to access previous versions of code, making it unnecessary to keep old code as comments in the current version.

28

# Use clear and concise language in comments

* * *

Write comments that are brief, informative, and easy to understand to enhance code comprehension.

* * *

The following example shows how to write effective comments:

< Good Code >

<?php

// Calculate the final price including tax

function calculateFinalPrice($basePrice, $taxRate) {

    // Apply tax to the base price

    $taxAmount = $basePrice \* $taxRate;

    $finalPrice = $basePrice + $taxAmount;

    return $finalPrice;

}

// Example usage

$basePrice = 100;

$taxRate = 0.08;

$result = calculateFinalPrice($basePrice, $taxRate);

echo "Final price: $" . number\_format($result, 2);

?>

<Bad Code>

<?php

// This function will take the base price and tax rate as inputs and then

// it will calculate the final price by adding the tax amount to the base price

// The tax amount is calculated by multiplying the base price with the tax rate

function calculateFinalPrice($basePrice, $taxRate) {

    // Here we calculate the tax amount

    $taxAmount = $basePrice \* $taxRate;

    // Now we add the tax amount to the base price to get the final price

    $finalPrice = $basePrice + $taxAmount;

    // Finally, we return the calculated final price

    return $finalPrice;

}

// Now we will use the function to calculate the final price

$basePrice = 100; // This is the base price

$taxRate = 0.08; // This is the tax rate (8%)

$result = calculateFinalPrice($basePrice, $taxRate);

echo "Final price: $" . number\_format($result, 2); // Output the result

?>

The good code example uses concise and informative comments that add value without being overly verbose. The bad code example contains excessive comments that state the obvious and make the code harder to read. Good comments should explain why something is done, not what is being done, as the code itself should be self-explanatory.

<Memo>

The concept of "self-documenting code" suggests that well-written code should be readable and understandable without extensive comments, with comments used only for complex logic or important notes.

29

# Avoid redundant comments that repeat the code

* * *

Write self-explanatory code and avoid comments that merely restate what the code does.

* * *

The following examples demonstrate how to avoid redundant comments in PHP code:

< Good Code >

function calculateTotalPrice($price, $quantity, $taxRate) {

    $subtotal = $price \* $quantity;

    $tax = $subtotal \* $taxRate;

    return $subtotal + $tax;

}

<Bad Code>

// Function to calculate total price

function calculateTotalPrice($price, $quantity, $taxRate) {

    // Calculate subtotal

    $subtotal = $price \* $quantity;

    // Calculate tax

    $tax = $subtotal \* $taxRate;

    // Return total price

    return $subtotal + $tax;

}

The good code example is self-explanatory and doesn't need comments. The function name and variables clearly convey their purpose. The bad code example includes redundant comments that simply repeat what the code does, adding unnecessary clutter without providing additional value.

<Memo>

Clean Code, a book by Robert C. Martin, emphasizes that good code should be self-documenting, reducing the need for explanatory comments.

30

# Use inline comments sparingly, only when necessary

* * *

Reserve inline comments for explaining complex logic or non-obvious decisions in your code.

* * *

The following examples show appropriate and excessive use of inline comments in PHP:

< Good Code >

function processUserData($userData) {

    $cleanedData = array\_map('trim', $userData);

    // Use regex to validate email format

    if (!preg\_match('/^\[\\w\\-\\.\]+@\[\\w\\-\\.\]+\\.\\w+$/', $cleanedData\['email'\])) {

        throw new InvalidArgumentException('Invalid email format');

    }

    return $cleanedData;

}

<Bad Code>

function processUserData($userData) {

    // Trim whitespace from all user data

    $cleanedData = array\_map('trim', $userData);

    // Check if email is valid

    if (!preg\_match('/^\[\\w\\-\\.\]+@\[\\w\\-\\.\]+\\.\\w+$/', $cleanedData\['email'\])) {

        // Throw an exception if email is invalid

        throw new InvalidArgumentException('Invalid email format');

    }

    // Return the cleaned data

    return $cleanedData;

}

In the good code example, the inline comment is used only to explain the purpose of the complex regex pattern. The bad code example overuses comments, explaining obvious operations like trimming whitespace and returning data. Such comments add unnecessary verbosity without improving code comprehension.

<Memo>

The concept of "Self-Documenting Code" suggests that well-written code should be readable and understandable without extensive comments, relying on clear naming conventions and logical structure.

31

# Utilize dependency injection for better testability

* * *

Dependency injection improves code testability by decoupling components and allowing easier mocking of dependencies.

* * *

The following code demonstrates dependency injection in a UserService class:

< Good Code >

// Good code: Using dependency injection

class UserService {

    private $database;

    // Constructor injection

    public function \_\_construct(DatabaseInterface $database) {

        $this->database = $database;

    }

    public function getUserById($id) {

        // Use the injected database object

        return $this->database->query("SELECT \* FROM users WHERE id = ?", \[$id\]);

    }

}

// Usage

$database = new MySQLDatabase();

$userService = new UserService($database);

$user = $userService->getUserById(1);

<Bad Code>

// Bad code: Tightly coupled, hard to test

class UserService {

    private $database;

    public function \_\_construct() {

        // Direct instantiation, tightly coupled

        $this->database = new MySQLDatabase();

    }

    public function getUserById($id) {

        return $this->database->query("SELECT \* FROM users WHERE id = ?", \[$id\]);

    }

}

// Usage

$userService = new UserService();

$user = $userService->getUserById(1);

The good code example uses dependency injection by accepting a DatabaseInterface in the constructor. This allows for easier testing as you can inject a mock database object. The bad code directly instantiates the database, making it difficult to test in isolation or swap implementations.

<Memo>

Dependency injection is one of the SOLID principles, specifically the Dependency Inversion Principle (DIP).

32

# Use null coalescing operator (??) for concise null checks

* * *

The null coalescing operator (??) provides a concise way to handle null checks and default values.

* * *

The following code demonstrates the use of the null coalescing operator:

< Good Code >

// Good code: Using null coalescing operator

function getUserName($user) {

    // Return user's name if set, otherwise return 'Guest'

    return $user\['name'\] ?? 'Guest';

}

// Usage

$user1 = \['name' => 'John'\];

$user2 = \[\];

echo getUserName($user1); // Outputs: John

echo getUserName($user2); // Outputs: Guest

<Bad Code>

// Bad code: Verbose null check

function getUserName($user) {

    // Check if 'name' is set and not null, otherwise return 'Guest'

    if (isset($user\['name'\]) && $user\['name'\] !== null) {

        return $user\['name'\];

    } else {

        return 'Guest';

    }

}

// Usage

$user1 = \['name' => 'John'\];

$user2 = \[\];

echo getUserName($user1); // Outputs: John

echo getUserName($user2); // Outputs: Guest

The good code uses the null coalescing operator (??) to concisely check if $user\['name'\] is set and not null. If it is, it returns the name; otherwise, it returns 'Guest'. The bad code achieves the same result but with a more verbose if-else statement, making it less readable and more prone to errors.

<Memo>

The null coalescing operator (??) was introduced in PHP 7.0 and is similar to the ternary operator but specifically designed for null checks.

33

# Implement \_\_invoke() method for callable objects

* * *

The \_\_invoke() method allows an object to be called as a function.

* * *

The \_\_invoke() method in PHP enables objects to be used as callable functions. This can make your code more flexible and readable by allowing objects to be invoked directly.

< Good Code >

<?php

class Greeter {

    private $greeting;

    public function \_\_construct($greeting) {

        $this->greeting = $greeting;

    }

    // Implementing the \_\_invoke method

    public function \_\_invoke($name) {

        return $this->greeting . ', ' . $name . '!';

    }

}

$greeter = new Greeter('Hello');

echo $greeter('World'); // Outputs: Hello, World!

<Bad Code>

<?php

class Greeter {

    private $greeting;

    public function \_\_construct($greeting) {

        $this->greeting = $greeting;

    }

    // No \_\_invoke method, using a regular method instead

    public function greet($name) {

        return $this->greeting . ', ' . $name . '!';

    }

}

$greeter = new Greeter('Hello');

echo $greeter->greet('World'); // Outputs: Hello, World!

In the good example, the \_\_invoke() method allows the Greeter object to be called as if it were a function, making the code more concise and readable. In the bad example, a regular method greet() is used, which requires an additional method call syntax, making the code slightly more verbose.

<Memo>

The \_\_invoke() method was introduced in PHP 5.3.0. It allows any instance of a class to be called as a function, providing a way to implement function-like behavior in objects.

34

# Use yield from for nested generators

* * *

The yield from expression simplifies working with nested generators.

* * *

The yield from expression in PHP allows you to delegate part of a generator's operations to another generator. This can make your code cleaner and easier to understand when dealing with nested generators.

< Good Code >

<?php

function innerGenerator() {

    yield 1;

    yield 2;

    yield 3;

}

function outerGenerator() {

    // Using yield from to delegate to innerGenerator

    yield from innerGenerator();

    yield 4;

    yield 5;

}

foreach (outerGenerator() as $value) {

    echo $value . ' '; // Outputs: 1 2 3 4 5

}

<Bad Code>

<?php

function innerGenerator() {

    yield 1;

    yield 2;

    yield 3;

}

function outerGenerator() {

    // Manually yielding values from innerGenerator

    foreach (innerGenerator() as $value) {

        yield $value;

    }

    yield 4;

    yield 5;

}

foreach (outerGenerator() as $value) {

    echo $value . ' '; // Outputs: 1 2 3 4 5

}

In the good example, yield from is used to delegate the yielding process to innerGenerator(), making the code more concise and easier to read. In the bad example, a foreach loop is used to manually yield values from innerGenerator(), which is more verbose and less elegant.

<Memo>

The yield from expression was introduced in PHP 7.0.0. It provides a way to yield all values from an iterable, simplifying the code when working with nested generators.

35

# Employ array unpacking for merging arrays

* * *

Use the spread operator (...) to merge arrays efficiently in PHP 7.4+.

* * *

The following code demonstrates how to merge two arrays using array unpacking:

< Good Code >

<?php

// Good practice: Using array unpacking for merging arrays

$fruits = \['apple', 'banana'\];

$vegetables = \['carrot', 'tomato'\];

// Merge arrays using the spread operator

$combined = \[...$fruits, ...$vegetables\];

// Output the result

print\_r($combined);

?>

<Bad Code>

<?php

// Bad practice: Using array\_merge() for combining arrays

$fruits = array('apple', 'banana');

$vegetables = array('carrot', 'tomato');

// Merge arrays using array\_merge()

$combined = array\_merge($fruits, $vegetables);

// Output the result

print\_r($combined);

?>

The good code example uses the spread operator (...) to unpack the arrays and merge them into a new array. This method is more readable and concise. The bad code example uses the traditional array\_merge() function, which is less intuitive and requires more typing. Both methods produce the same result, but the spread operator is generally preferred in modern PHP for its simplicity and readability.

<Memo>

The spread operator (...) was introduced in PHP 7.4 and can be used not only for arrays but also for unpacking arguments in function calls.

36

# Use consistent indentation (spaces or tabs)

* * *

Maintain consistent indentation throughout your PHP code for improved readability.

* * *

The following examples show the importance of consistent indentation in PHP code:

< Good Code >

<?php

// Good practice: Consistent indentation (using 4 spaces)

function calculateTotal($items) {

    $total = 0;

    foreach ($items as $item) {

        $price = $item\['price'\];

        $quantity = $item\['quantity'\];

        $total += $price \* $quantity;

    }

    return $total;

}

$cart = \[

    \['name' => 'T-shirt', 'price' => 15, 'quantity' => 2\],

    \['name' => 'Jeans', 'price' => 50, 'quantity' => 1\]

\];

$totalCost = calculateTotal($cart);

echo "Total cost: $" . $totalCost;

?>

<Bad Code>

<?php

// Bad practice: Inconsistent indentation

function calculateTotal($items) {

$total = 0;

    foreach ($items as $item) {

  $price = $item\['price'\];

        $quantity = $item\['quantity'\];

    $total += $price \* $quantity;

    }

return $total;

}

$cart = \[

\['name' => 'T-shirt', 'price' => 15, 'quantity' => 2\],

    \['name' => 'Jeans', 'price' => 50, 'quantity' => 1\]

\];

$totalCost = calculateTotal($cart);

echo "Total cost: $" . $totalCost;

?>

The good code example uses consistent indentation (4 spaces) throughout the script. This makes the code structure clear and easy to read. The bad code example has inconsistent indentation, mixing different numbers of spaces and even no indentation. This makes the code harder to read and understand, especially for other developers who might work on the same project. Consistent indentation helps in visualizing the code structure, nested blocks, and improves overall code maintainability.

<Memo>

The PHP-FIG (Framework Interop Group) recommends using either 4 spaces or 1 tab for indentation in their PSR-12 coding style guide, but emphasizes consistency within a project.

37

# Limit line length to improve readability (e.g., 80-120 characters)

* * *

Keeping line lengths within 80-120 characters makes code easier to read and maintain.

* * *

Long lines of code can be difficult to read and understand. Limiting line length helps in maintaining readability and makes it easier for developers to navigate through the code.

< Good Code >

<?php

// Good example with limited line length

function calculateTotalPrice($price, $taxRate, $discount) {

    $taxAmount = $price \* $taxRate;

    $discountAmount = $price \* $discount;

    $totalPrice = $price + $taxAmount - $discountAmount;

    return $totalPrice;

}

?>

<Bad Code>

<?php

// Bad example with long lines

function calculateTotalPrice($price, $taxRate, $discount) { $taxAmount = $price \* $taxRate; $discountAmount = $price \* $discount; $totalPrice = $price + $taxAmount - $discountAmount; return $totalPrice; }

?>

In the good example, the code is broken down into multiple lines, making it easier to read and understand. In the bad example, the entire function is written in a single line, which makes it difficult to follow and maintain.

<Memo>

The 80-character limit originated from the width of punch cards used in early computing. Many modern coding standards still recommend this limit for readability.

38

# Use blank lines to separate logical sections of code

* * *

Blank lines help to visually separate different sections of code, making it easier to read and understand.

* * *

Using blank lines to separate logical sections of code improves readability by providing visual breaks between different parts of the code, making it easier to follow the flow of the program.

< Good Code >

<?php

// Good example with blank lines separating logical sections

function calculateTotalPrice($price, $taxRate, $discount) {

    // Calculate tax amount

    $taxAmount = $price \* $taxRate;

    // Calculate discount amount

    $discountAmount = $price \* $discount;

    // Calculate total price

    $totalPrice = $price + $taxAmount - $discountAmount;

    return $totalPrice;

}

?>

<Bad Code>

<?php

// Bad example without blank lines

function calculateTotalPrice($price, $taxRate, $discount) {

    $taxAmount = $price \* $taxRate;

    $discountAmount = $price \* $discount;

    $totalPrice = $price + $taxAmount - $discountAmount;

    return $totalPrice;

}

?>

In the good example, blank lines are used to separate the calculation of tax, discount, and total price, making the code easier to read and understand. In the bad example, the lack of blank lines makes the code appear cluttered and harder to follow.

<Memo>

Using blank lines effectively can also help in debugging, as it allows developers to quickly identify and isolate different sections of code.

39

# Align assignment operators when declaring multiple variables

* * *

Aligning assignment operators improves readability and makes it easier to spot inconsistencies.

* * *

When declaring multiple variables, aligning the assignment operators can make the code more readable and maintainable.

< Good Code >

<?php

// Good example with aligned assignment operators

$firstName  = "John";  // Assigning first name

$lastName   = "Doe";   // Assigning last name

$age        = 30;      // Assigning age

$occupation = "Engineer"; // Assigning occupation

?>

<Bad Code>

<?php

// Bad example with unaligned assignment operators

$firstName = "John"; // Assigning first name

$lastName = "Doe"; // Assigning last name

$age = 30; // Assigning age

$occupation = "Engineer"; // Assigning occupation

?>

In the good example, the assignment operators are aligned, making it easier to read and understand the code at a glance. This alignment helps in quickly identifying the variables and their assigned values. In the bad example, the assignment operators are not aligned, which can make the code look messy and harder to read.

<Memo>

Aligning assignment operators is a common practice in many programming languages, not just PHP. It helps in maintaining a clean and organized codebase, especially in large projects.

40

# Use parentheses to clarify operator precedence

* * *

Using parentheses to clarify operator precedence ensures that the code behaves as expected and is easier to understand.

* * *

Operator precedence can sometimes be confusing. Using parentheses explicitly clarifies the intended order of operations.

< Good Code >

<?php

// Good example with parentheses to clarify operator precedence

$result = (2 + 3) \* 4; // Clearly indicates that 2 + 3 should be evaluated first

echo $result; // Outputs 20

?>

<Bad Code>

<?php

// Bad example without parentheses, leading to potential confusion

$result = 2 + 3 \* 4; // Without parentheses, multiplication is done first

echo $result; // Outputs 14, which might not be the intended result

?>

In the good example, parentheses are used to explicitly indicate that the addition should be performed before the multiplication. This makes the code's intention clear and avoids any confusion about the order of operations. In the bad example, the lack of parentheses can lead to misunderstandings, as the multiplication is performed before the addition due to operator precedence rules.

<Memo>

Operator precedence rules are defined by the language specification and can vary between languages. Using parentheses to clarify precedence is a good habit to develop, as it makes the code more readable and less prone to errors.

41

# Use early returns to reduce nesting

* * *

Using early returns in your functions can help reduce the level of nesting, making your code more readable and easier to maintain.

* * *

Early returns allow you to exit a function as soon as a condition is met, avoiding deep nesting and making the code flow clearer.

< Good Code >

function processOrder($order) {

    // Check if the order is valid

    if (!$order->isValid()) {

        return 'Invalid order';

    }

    // Check if the order is already processed

    if ($order->isProcessed()) {

        return 'Order already processed';

    }

    // Process the order

    $order->process();

    return 'Order processed successfully';

}

<Bad Code>

function processOrder($order) {

    // Check if the order is valid

    if ($order->isValid()) {

        // Check if the order is already processed

        if (!$order->isProcessed()) {

            // Process the order

            $order->process();

            return 'Order processed successfully';

        } else {

            return 'Order already processed';

        }

    } else {

        return 'Invalid order';

    }

}

In the good example, early returns are used to handle invalid or already processed orders immediately, reducing the need for nested if statements. This makes the function easier to read and understand. In the bad example, the nested if statements make the code harder to follow.

<Memo>

Early returns are a common practice in many programming languages, not just PHP. They help improve code readability and reduce complexity.

42

# Prefer foreach loops over for loops when possible

* * *

Using foreach loops instead of for loops can make your code more readable and less error-prone when iterating over arrays or collections.

* * *

foreach loops are specifically designed for iterating over arrays and collections, providing a simpler and more intuitive syntax compared to for loops.

< Good Code >

$items = \['apple', 'banana', 'cherry'\];

// Using foreach loop

foreach ($items as $item) {

    echo $item . "\\n"; // Output each item

}

<Bad Code>

$items = \['apple', 'banana', 'cherry'\];

// Using for loop

for ($i = 0; $i < count($items); $i++) {

    echo $items\[$i\] . "\\n"; // Output each item

}

In the good example, the foreach loop directly iterates over each item in the array, making the code more concise and easier to read. In the bad example, the for loop requires managing the loop counter and calling the count function, which can be more error-prone and less readable.

<Memo>

foreach loops are not only more readable but also more efficient in some cases, as they avoid repeatedly calling the count function within the loop condition.

43

# Use switch statements for multiple conditions on the same variable

* * *

Switch statements can improve code readability when dealing with multiple conditions for a single variable.

* * *

The following code demonstrates how to use a switch statement to handle different cases for a user's role:

< Good Code >

// Determine user permissions based on role

function getUserPermissions($role) {

    switch ($role) {

        case 'admin':

            // Admin has full access

            return \['read', 'write', 'delete', 'manage'\];

        case 'editor':

            // Editor can read, write, and delete

            return \['read', 'write', 'delete'\];

        case 'author':

            // Author can read and write

            return \['read', 'write'\];

        case 'subscriber':

            // Subscriber can only read

            return \['read'\];

        default:

            // Default case for unknown roles

            return \['none'\];

    }

}

// Usage

$userRole = 'editor';

$permissions = getUserPermissions($userRole);

print\_r($permissions);

<Bad Code>

// Determine user permissions based on role

function getUserPermissions($role) {

    if ($role == 'admin') {

        return \['read', 'write', 'delete', 'manage'\];

    } elseif ($role == 'editor') {

        return \['read', 'write', 'delete'\];

    } elseif ($role == 'author') {

        return \['read', 'write'\];

    } elseif ($role == 'subscriber') {

        return \['read'\];

    } else {

        return \['none'\];

    }

}

// Usage

$userRole = 'editor';

$permissions = getUserPermissions($userRole);

print\_r($permissions);

The good code example uses a switch statement, which is more readable and maintainable when dealing with multiple conditions for a single variable. Each case is clearly defined, making it easier to add or modify roles in the future. The bad code example uses a series of if-elseif statements, which can become harder to read and maintain as the number of conditions increases.

<Memo>

Switch statements in PHP support "fall-through" behavior, where execution continues to the next case if a break statement is omitted. This can be useful in certain scenarios but should be used cautiously to avoid unintended behavior.

44

# Employ guard clauses to handle edge cases early

* * *

Guard clauses help improve code readability by handling edge cases early in a function, reducing nesting and complexity.

* * *

The following code demonstrates how to use guard clauses to validate input parameters in a function:

< Good Code >

// Calculate discount based on purchase amount

function calculateDiscount($purchaseAmount) {

    // Guard clause: Check for invalid input

    if (!is\_numeric($purchaseAmount) || $purchaseAmount < 0) {

        throw new InvalidArgumentException("Invalid purchase amount");

    }

    // Guard clause: No discount for small purchases

    if ($purchaseAmount < 100) {

        return 0;

    }

    // Calculate discount

    if ($purchaseAmount >= 500) {

        return $purchaseAmount \* 0.1; // 10% discount

    } else {

        return $purchaseAmount \* 0.05; // 5% discount

    }

}

// Usage

try {

    $discount = calculateDiscount(250);

    echo "Discount: $" . number\_format($discount, 2);

} catch (InvalidArgumentException $e) {

    echo "Error: " . $e->getMessage();

}

<Bad Code>

// Calculate discount based on purchase amount

function calculateDiscount($purchaseAmount) {

    if (is\_numeric($purchaseAmount) && $purchaseAmount >= 0) {

        if ($purchaseAmount >= 100) {

            if ($purchaseAmount >= 500) {

                return $purchaseAmount \* 0.1; // 10% discount

            } else {

                return $purchaseAmount \* 0.05; // 5% discount

            }

        } else {

            return 0;

        }

    } else {

        throw new InvalidArgumentException("Invalid purchase amount");

    }

}

// Usage

try {

    $discount = calculateDiscount(250);

    echo "Discount: $" . number\_format($discount, 2);

} catch (InvalidArgumentException $e) {

    echo "Error: " . $e->getMessage();

}

The good code example uses guard clauses to handle edge cases early in the function. This approach reduces nesting and makes the code more readable. Invalid inputs and special cases (no discount for small purchases) are handled first, allowing the main logic to be more straightforward. The bad code example uses nested if statements, which can be harder to follow and maintain, especially as more conditions are added.

<Memo>

Guard clauses are a key principle in the "early return" pattern, which can significantly improve code readability and reduce the cognitive load on developers reading the code.

45

# Use ternary operators for simple conditional assignments

* * *

Simplify conditional assignments using ternary operators for improved readability.

* * *

The following code demonstrates the use of a ternary operator for a simple conditional assignment:

< Good Code >

// Good code: Using a ternary operator for simple conditional assignment

$isAdult = ($age >= 18) ? true : false;

// Explanation:

// If $age is greater than or equal to 18, $isAdult is set to true

// Otherwise, $isAdult is set to false

<Bad Code>

// Bad code: Using a traditional if-else statement for simple conditional assignment

if ($age >= 18) {

$isAdult = true;

} else {

$isAdult = false;

}

// Explanation:

// This code does the same thing as the good example,

// but it's more verbose and less readable

The good code example uses a ternary operator (?:) to concisely assign a boolean value based on a condition. This approach is more readable and compact compared to the traditional if-else statement used in the bad code example. Both code snippets achieve the same result, but the ternary operator version is more elegant and easier to understand at a glance.

<Memo>

The ternary operator is also known as the conditional operator and is the only operator in PHP that takes three operands.

46

# Utilize the null coalescing operator (??) for default values

* * *

Use the null coalescing operator to assign default values efficiently.

* * *

The following code shows how to use the null coalescing operator for assigning default values:

< Good Code >

// Good code: Using the null coalescing operator for default values

$username = $\_GET\['username'\] ?? 'Guest';

// Explanation:

// If $\_GET\['username'\] is set and not null, its value is assigned to $username

// Otherwise, 'Guest' is assigned as the default value

<Bad Code>

// Bad code: Using isset() and ternary operator for default values

$username = isset($\_GET\['username'\]) ? $\_GET\['username'\] : 'Guest';

// Explanation:

// This code does the same thing as the good example,

// but it's more verbose and less efficient

The good code example uses the null coalescing operator (??) to assign a default value if the specified variable is null or not set. This approach is more concise and easier to read compared to the bad code example, which uses isset() and a ternary operator to achieve the same result. The null coalescing operator simplifies the code and makes it more maintainable.

<Memo>

The null coalescing operator was introduced in PHP 7.0 and is particularly useful for handling undefined array keys or object properties.

47

# Use the spaceship operator (<=>) for concise comparisons

* * *

The spaceship operator simplifies comparison operations in PHP, making code more readable and concise.

* * *

The following code demonstrates how to use the spaceship operator to compare values and sort an array:

< Good Code >

// Using the spaceship operator for comparison and sorting

$fruits = \['apple', 'banana', 'cherry'\];

// Sort the array using the spaceship operator

usort($fruits, function($a, $b) {

    // The spaceship operator returns -1, 0, or 1

    return $a <=> $b;

});

// Output the sorted array

foreach ($fruits as $fruit) {

    echo $fruit . "\\n";

}

// Compare numbers using the spaceship operator

$result = 5 <=> 10;

echo "Comparison result: " . $result . "\\n";

<Bad Code>

// Not using the spaceship operator for comparison and sorting

$fruits = \['apple', 'banana', 'cherry'\];

// Sort the array using a traditional comparison function

usort($fruits, function($a, $b) {

    if ($a < $b) {

        return -1;

    } elseif ($a > $b) {

        return 1;

    } else {

        return 0;

    }

});

// Output the sorted array

foreach ($fruits as $fruit) {

    echo $fruit . "\\n";

}

// Compare numbers without using the spaceship operator

$a = 5;

$b = 10;

if ($a < $b) {

    $result = -1;

} elseif ($a > $b) {

    $result = 1;

} else {

    $result = 0;

}

echo "Comparison result: " . $result . "\\n";

The good code example uses the spaceship operator (<=>) for both sorting and comparison. This operator returns -1 if the left operand is less than the right, 0 if they are equal, and 1 if the left operand is greater. It simplifies comparison logic, making the code more concise and easier to read.

The bad code example uses traditional comparison methods, which are more verbose and prone to errors. The sorting function is longer and less intuitive, and the number comparison requires multiple if-else statements.

<Memo>

The spaceship operator was introduced in PHP 7.0 and is also known as the combined comparison operator.

48

# Employ the null safe operator (?->) for safe property/method access

* * *

The null safe operator allows for safe access to object properties or methods without causing errors when dealing with null values.

* * *

The following code demonstrates how to use the null safe operator to safely access object properties and methods:

< Good Code >

// Using the null safe operator for safe property/method access

class User {

    public $name;

    public function getEmail() {

        return 'user@example.com';

    }

}

$user = null;

// Safely access property

$name = $user?->name;

echo "Name: " . ($name ?? 'Unknown') . "\\n";

// Safely call method

$email = $user?->getEmail();

echo "Email: " . ($email ?? 'Not available') . "\\n";

// Chaining with the null safe operator

$user = new User();

$user->name = 'John';

$upperName = $user?->name?->toUpper();

echo "Upper name: " . ($upperName ?? 'N/A') . "\\n";

<Bad Code>

// Not using the null safe operator for property/method access

class User {

    public $name;

    public function getEmail() {

        return 'user@example.com';

    }

}

$user = null;

// Unsafe property access

if ($user !== null && isset($user->name)) {

    $name = $user->name;

} else {

    $name = 'Unknown';

}

echo "Name: " . $name . "\\n";

// Unsafe method call

if ($user !== null && method\_exists($user, 'getEmail')) {

    $email = $user->getEmail();

} else {

    $email = 'Not available';

}

echo "Email: " . $email . "\\n";

// Chaining without the null safe operator

$user = new User();

$user->name = 'John';

$upperName = 'N/A';

if ($user !== null && isset($user->name) && is\_string($user->name)) {

    $upperName = strtoupper($user->name);

}

echo "Upper name: " . $upperName . "\\n";

The good code example uses the null safe operator (?->) to access object properties and methods. This operator checks if the object is null before attempting to access its properties or methods, preventing null reference errors. It also allows for easy chaining of operations.

The bad code example uses traditional null checks and isset() functions, which make the code more verbose and harder to read. It requires multiple conditions to safely access properties and methods, increasing the complexity of the code.

<Memo>

The null safe operator was introduced in PHP 8.0 and is particularly useful when working with APIs or databases where null values are common.

49

# Use match expressions for cleaner switch-like functionality

* * *

PHP 8.0 introduced match expressions, offering a more concise and powerful alternative to switch statements.

* * *

The following code demonstrates how to use match expressions to handle different cases based on a value:

< Good Code >

// Good example using match expression

function getStatusMessage($statusCode) {

    // Use match expression to return appropriate message

    return match ($statusCode) {

        200 => 'OK',

        404 => 'Not Found',

        500 => 'Internal Server Error',

        default => 'Unknown Status',

    };

}

// Usage

$message = getStatusMessage(404);

echo $message; // Outputs: Not Found

<Bad Code>

// Bad example using switch statement

function getStatusMessage($statusCode) {

    // Use switch statement to return appropriate message

    switch ($statusCode) {

        case 200:

            return 'OK';

            break;

        case 404:

            return 'Not Found';

            break;

        case 500:

            return 'Internal Server Error';

            break;

        default:

            return 'Unknown Status';

            break;

    }

}

// Usage

$message = getStatusMessage(404);

echo $message; // Outputs: Not Found

The match expression provides a more concise syntax compared to the switch statement. It automatically returns the result of the matched expression, eliminating the need for break statements. The match expression also performs strict comparisons by default, reducing potential bugs. The good example demonstrates cleaner, more readable code that achieves the same functionality as the switch statement in the bad example.

<Memo>

Match expressions were introduced in PHP 8.0 and are inspired by similar constructs in languages like Rust and Ruby.

50

# Implement iterators for custom object traversal

* * *

Implementing the Iterator interface allows custom objects to be easily traversed in foreach loops.

* * *

The following code demonstrates how to implement an iterator for a custom object:

< Good Code >

// Good example implementing Iterator interface

class MyCollection implements Iterator {

    private $items = \[\];

    private $position = 0;

    public function \_\_construct(array $items) {

        $this->items = $items;

    }

    // Required Iterator methods

    public function current() {

        return $this->items\[$this->position\];

    }

    public function key() {

        return $this->position;

    }

    public function next() {

        ++$this->position;

    }

    public function rewind() {

        $this->position = 0;

    }

    public function valid() {

        return isset($this->items\[$this->position\]);

    }

}

// Usage

$collection = new MyCollection(\['apple', 'banana', 'cherry'\]);

foreach ($collection as $key => $value) {

    echo "$key: $value\\n";

}

<Bad Code>

// Bad example without implementing Iterator

class MyCollection {

    private $items = \[\];

    public function \_\_construct(array $items) {

        $this->items = $items;

    }

    public function getItems() {

        return $this->items;

    }

}

// Usage

$collection = new MyCollection(\['apple', 'banana', 'cherry'\]);

$items = $collection->getItems();

foreach ($items as $key => $value) {

    echo "$key: $value\\n";

}

The good example implements the Iterator interface, allowing the object to be directly used in a foreach loop. This approach encapsulates the iteration logic within the class, promoting better object-oriented design. The bad example exposes the internal array, which breaks encapsulation and requires additional steps to iterate over the items. Implementing Iterator makes the code more intuitive and easier to use, especially when working with complex custom objects.

<Memo>

PHP's Iterator interface is part of the Standard PHP Library (SPL) and provides a standardized way to make objects traversable.

51

# Use type declarations for class properties

* * *

Enhance code readability and maintainability by using type declarations for class properties in PHP.

* * *

The following code demonstrates the use of type declarations for class properties in PHP 7.4 and later versions:

< Good Code >

class User {

    // Declare public properties with type hints

    public string $name;

    public int $age;

    public ?string $email; // Nullable string type

    // Constructor with type-hinted parameters

    public function \_\_construct(string $name, int $age, ?string $email = null) {

        $this->name = $name;

        $this->age = $age;

        $this->email = $email;

    }

    // Method with type-hinted return value

    public function getInfo(): string {

        return "Name: {$this->name}, Age: {$this->age}";

    }

}

// Usage

$user = new User("John Doe", 30, "john@example.com");

echo $user->getInfo(); // Outputs: Name: John Doe, Age: 30

<Bad Code>

class User {

    // Properties without type declarations

    public $name;

    public $age;

    public $email;

    // Constructor without type hints

    public function \_\_construct($name, $age, $email = null) {

        $this->name = $name;

        $this->age = $age;

        $this->email = $email;

    }

    // Method without return type declaration

    public function getInfo() {

        return "Name: " . $this->name . ", Age: " . $this->age;

    }

}

// Usage

$user = new User("John Doe", "30", "john@example.com");

echo $user->getInfo(); // Outputs: Name: John Doe, Age: 30

The good code example uses type declarations for class properties, constructor parameters, and method return types. This approach provides several benefits:

Improved code readability: Developers can quickly understand the expected data types.

Enhanced IDE support: IDEs can offer better code completion and error detection.

Reduced bugs: PHP will throw a TypeError if an incompatible value is assigned.

Self-documenting code: Type declarations serve as built-in documentation.

The bad code example lacks type declarations, making it more prone to errors and harder to understand at a glance.

<Memo>

Property type declarations were introduced in PHP 7.4, further improving PHP's type system and code quality.

52

# Employ arrow functions for short, single-expression closures

* * *

Use arrow functions to write more concise and readable code for simple, single-expression closures in PHP.

* * *

The following code demonstrates the use of arrow functions for short, single-expression closures in PHP 7.4 and later:

< Good Code >

// Using arrow function for array\_map

$numbers = \[1, 2, 3, 4, 5\];

$squared = array\_map(fn($n) => $n \* $n, $numbers);

print\_r($squared); // Outputs: Array ( \[0\] => 1 \[1\] => 4 \[2\] => 9 \[3\] => 16 \[4\] => 25 )

// Using arrow function with use keyword

$multiplier = 3;

$tripled = array\_map(fn($n) => $n \* $multiplier, $numbers);

print\_r($tripled); // Outputs: Array ( \[0\] => 3 \[1\] => 6 \[2\] => 9 \[3\] => 12 \[4\] => 15 )

// Arrow function in usort

$fruits = \['apple', 'banana', 'cherry'\];

usort($fruits, fn($a, $b) => strlen($b) - strlen($a));

print\_r($fruits); // Outputs: Array ( \[0\] => banana \[1\] => cherry \[2\] => apple )

<Bad Code>

// Using traditional anonymous function for array\_map

$numbers = \[1, 2, 3, 4, 5\];

$squared = array\_map(function($n) {

    return $n \* $n;

}, $numbers);

print\_r($squared);

// Using anonymous function with use keyword

$multiplier = 3;

$tripled = array\_map(function($n) use ($multiplier) {

    return $n \* $multiplier;

}, $numbers);

print\_r($tripled);

// Anonymous function in usort

$fruits = \['apple', 'banana', 'cherry'\];

usort($fruits, function($a, $b) {

    return strlen($b) - strlen($a);

});

print\_r($fruits);

The good code example uses arrow functions, which offer several advantages:

Conciseness: Arrow functions are more compact, reducing boilerplate code.

Improved readability: The shorter syntax makes the code easier to scan and understand.

Implicit return: For single expressions, the return keyword is not needed.

Automatic variable inheritance: Variables from the parent scope are available without the 'use' keyword.

The bad code example uses traditional anonymous functions, which are more verbose and can be harder to read, especially for simple operations.

<Memo>

Arrow functions were introduced in PHP 7.4 as a more concise syntax for defining simple closures, inspired by similar features in languages like JavaScript and C#.

53

# Utilize the spread operator (...) for variadic functions

* * *

Use the spread operator to handle variable numbers of arguments in functions, improving code flexibility and readability.

* * *

The following code demonstrates the use of the spread operator in a function that calculates the sum of an arbitrary number of arguments.

< Good Code >

/\*\*

\* Calculate the sum of an arbitrary number of arguments

\*

\* @param float ...$numbers Variable number of numeric arguments

\* @return float The sum of all provided numbers

\*/

function calculateSum(...$numbers) {

    // Use array\_sum() to add up all the numbers

    return array\_sum($numbers);

}

// Example usage

$result = calculateSum(1, 2, 3, 4, 5);

echo "Sum: " . $result; // Output: Sum: 15

<Bad Code>

// Poor implementation without spread operator

function calculateSum() {

    $sum = 0;

    $args = func\_get\_args();

    for ($i = 0; $i < func\_num\_args(); $i++) {

        $sum += $args\[$i\];

    }

    return $sum;

}

$result = calculateSum(1, 2, 3, 4, 5);

echo "Sum: " . $result; // Output: Sum: 15

The good code example uses the spread operator (...) to collect all arguments into an array, making the function more flexible and easier to read. It also utilizes the built-in array\_sum() function for efficient calculation. The bad code example relies on older methods like func\_get\_args() and func\_num\_args(), which are less intuitive and require more manual processing.

<Memo>

The spread operator was introduced in PHP 5.6 and provides a concise way to unpack arrays or traversable objects into function arguments or array elements.

54

# Use named arguments for improved readability in function calls

* * *

Employ named arguments in function calls to enhance code clarity and make the purpose of each argument explicit.

* * *

The following code showcases the use of named arguments in a function call, improving readability and reducing errors.

< Good Code >

/\*\*

\* Create a user profile

\*

\* @param string $username User's username

\* @param string $email User's email address

\* @param int $age User's age

\* @param string $country User's country (optional)

\* @return array Created user profile

\*/

function createUserProfile(

    string $username,

    string $email,

    int $age,

    string $country = 'Unknown'

) {

    return \[

        'username' => $username,

        'email' => $email,

        'age' => $age,

        'country' => $country

    \];

}

// Using named arguments

$profile = createUserProfile(

    username: 'john\_doe',

    email: 'john@example.com',

    age: 30,

    country: 'USA'

);

print\_r($profile);

<Bad Code>

// Without named arguments

function createUserProfile($username, $email, $age, $country = 'Unknown') {

    return \[

        'username' => $username,

        'email' => $email,

        'age' => $age,

        'country' => $country

    \];

}

// Potentially confusing order of arguments

$profile = createUserProfile('john\_doe', 'john@example.com', 30, 'USA');

print\_r($profile);

The good code example uses named arguments, making it clear which value corresponds to which parameter. This approach improves readability and reduces the risk of passing arguments in the wrong order. The bad code example relies on positional arguments, which can be error-prone, especially when dealing with multiple parameters or optional arguments.

<Memo>

Named arguments were introduced in PHP 8.0, allowing developers to pass arguments to functions based on their parameter names rather than their positions.

55

# Implement \_\_debugInfo() for custom object debugging output

* * *

Use \_\_debugInfo() to control object output during debugging.

* * *

The \_\_debugInfo() magic method allows you to customize the information displayed when var\_dump() is called on an object.

< Good Code >

class User {

    private $id;

    private $name;

    private $email;

    private $password; // Sensitive information

    public function \_\_construct($id, $name, $email, $password) {

        $this->id = $id;

        $this->name = $name;

        $this->email = $email;

        $this->password = $password;

    }

    // Implement \_\_debugInfo() to control debug output

    public function \_\_debugInfo() {

        return \[

            'id' => $this->id,

            'name' => $this->name,

            'email' => $this->email,

            // Password is omitted for security reasons

        \];

    }

}

// Usage

$user = new User(1, 'John Doe', 'john@example.com', 'secret123');

var\_dump($user);

<Bad Code>

class User {

    public $id;

    public $name;

    public $email;

    public $password; // Sensitive information exposed

    public function \_\_construct($id, $name, $email, $password) {

        $this->id = $id;

        $this->name = $name;

        $this->email = $email;

        $this->password = $password;

    }

}

// Usage

$user = new User(1, 'John Doe', 'john@example.com', 'secret123');

var\_dump($user); // Dumps all properties, including sensitive data

The good example implements \_\_debugInfo() to control what information is displayed during debugging. It omits sensitive data like passwords. The bad example exposes all properties, including sensitive information, which is a security risk.

<Memo>

The \_\_debugInfo() method was introduced in PHP 5.6.0 to provide developers with more control over object representation during debugging.

56

# Declare variables close to their usage

* * *

Define variables near where they are first used to improve code readability.

* * *

Declaring variables close to their usage helps in understanding the code flow and reduces the cognitive load on readers.

< Good Code >

function processOrder($orderId) {

    // Retrieve order details

    $order = getOrderById($orderId);

    // Calculate total

    $total = 0;

    foreach ($order\['items'\] as $item) {

        $itemPrice = $item\['price'\] \* $item\['quantity'\];

        $total += $itemPrice;

    }

    // Apply discount if applicable

    $discountCode = getDiscountCode($orderId);

    if ($discountCode) {

        $discountPercentage = getDiscountPercentage($discountCode);

        $discountAmount = $total \* ($discountPercentage / 100);

        $total -= $discountAmount;

    }

    // Process payment

    $paymentResult = processPayment($orderId, $total);

    return $paymentResult;

}

<Bad Code>

function processOrder($orderId) {

    $order = null;

    $total = 0;

    $itemPrice = 0;

    $discountCode = null;

    $discountPercentage = 0;

    $discountAmount = 0;

    $paymentResult = false;

    $order = getOrderById($orderId);

    foreach ($order\['items'\] as $item) {

        $itemPrice = $item\['price'\] \* $item\['quantity'\];

        $total += $itemPrice;

    }

    $discountCode = getDiscountCode($orderId);

    if ($discountCode) {

        $discountPercentage = getDiscountPercentage($discountCode);

        $discountAmount = $total \* ($discountPercentage / 100);

        $total -= $discountAmount;

    }

    $paymentResult = processPayment($orderId, $total);

    return $paymentResult;

}

The good example declares variables close to where they are used, making the code easier to follow. The bad example declares all variables at the beginning, which can make it harder to understand the code's flow and purpose of each variable.

<Memo>

This practice of declaring variables close to their usage is part of the broader concept of "locality of reference" in programming, which suggests that related elements should be kept close together in code.

57

# Use descriptive variable names

* * *

Choose variable names that clearly explain their purpose and content.

* * *

The following code demonstrates the difference between using descriptive and non-descriptive variable names in a function that calculates the total price of items in a shopping cart.

< Good Code >

// Function to calculate total price of items in a shopping cart

function calculateTotalPrice($itemPrices, $taxRate, $discountPercentage) {

    // Calculate subtotal

    $subtotal = array\_sum($itemPrices);

    // Apply discount

    $discountAmount = $subtotal \* ($discountPercentage / 100);

    $discountedTotal = $subtotal - $discountAmount;

    // Add tax

    $taxAmount = $discountedTotal \* ($taxRate / 100);

    $totalPrice = $discountedTotal + $taxAmount;

    return $totalPrice;

}

// Usage example

$prices = \[10.99, 24.99, 5.99\];

$tax = 8.5;

$discount = 10;

$finalPrice = calculateTotalPrice($prices, $tax, $discount);

echo "Total price: $" . number\_format($finalPrice, 2);

<Bad Code>

// Function to calculate something

function calc($a, $b, $c) {

    // Do some math

    $x = array\_sum($a);

    // More calculations

    $y = $x \* ($c / 100);

    $z = $x - $y;

    // Final step

    $w = $z \* ($b / 100);

    $v = $z + $w;

    return $v;

}

// Usage

$p = \[10.99, 24.99, 5.99\];

$t = 8.5;

$d = 10;

$f = calc($p, $t, $d);

echo "Result: $" . number\_format($f, 2);

The good code example uses descriptive variable names that clearly indicate their purpose, such as $itemPrices, $taxRate, and $discountPercentage. This makes the code more readable and self-explanatory. The bad code example uses single-letter variables like $a, $b, and $c, which make it difficult to understand the purpose of each variable without additional context or comments.

<Memo>

The practice of using descriptive variable names is part of a broader concept called "self-documenting code," which aims to make code more readable and maintainable without relying heavily on comments.

58

# Avoid global variables, use dependency injection

* * *

Instead of using global variables, pass dependencies as parameters to functions or methods.

* * *

The following code demonstrates the difference between using global variables and dependency injection in a simple logging system.

< Good Code >

// Logger class with dependency injection

class Logger {

    private $logFile;

    public function \_\_construct($logFile) {

        $this->logFile = $logFile;

    }

    public function log($message) {

        $timestamp = date('Y-m-d H:i:s');

        $logEntry = "$timestamp: $message\\n";

        file\_put\_contents($this->logFile, $logEntry, FILE\_APPEND);

    }

}

// Usage example

$logger = new Logger('/path/to/app.log');

function processOrder($orderId, Logger $logger) {

    // Process order logic here

    $logger->log("Order $orderId processed successfully");

}

// Using the logger

$orderId = 12345;

processOrder($orderId, $logger);

<Bad Code>

// Global variable for log file

$GLOBALS\['logFile'\] = '/path/to/app.log';

// Logger function using global variable

function logMessage($message) {

    global $logFile;

    $timestamp = date('Y-m-d H:i:s');

    $logEntry = "$timestamp: $message\\n";

    file\_put\_contents($logFile, $logEntry, FILE\_APPEND);

}

// Usage example

function processOrder($orderId) {

    // Process order logic here

    logMessage("Order $orderId processed successfully");

}

// Using the logger

$orderId = 12345;

processOrder($orderId);

The good code example uses dependency injection by passing the Logger object as a parameter to the processOrder function. This approach makes the code more modular, testable, and easier to maintain. The bad code example uses a global variable $GLOBALS\['logFile'\] and a global function logMessage, which can lead to tight coupling and make the code harder to test and modify.

<Memo>

Dependency injection is a key principle in object-oriented design and is one of the SOLID principles (specifically, the D in SOLID stands for Dependency Inversion Principle).

59

# Use constants for fixed values

* * *

Using constants for fixed values improves code readability and maintainability.

* * *

Constants are a great way to define values that do not change throughout the execution of a script. They make the code easier to understand and modify.

< Good Code >

<?php

// Define a constant for the tax rate

define('TAX\_RATE', 0.08);

// Function to calculate the total price including tax

function calculateTotalPrice($price) {

    // Use the constant TAX\_RATE

    return $price + ($price \* TAX\_RATE);

}

// Example usage

$price = 100;

$totalPrice = calculateTotalPrice($price);

echo "Total Price: $" . $totalPrice; // Outputs: Total Price: $108

?>

<Bad Code>

<?php

// Function to calculate the total price including tax

function calculateTotalPrice($price) {

    // Hardcoded tax rate

    return $price + ($price \* 0.08);

}

// Example usage

$price = 100;

$totalPrice = calculateTotalPrice($price);

echo "Total Price: $" . $totalPrice; // Outputs: Total Price: $108

?>

In the good example, the tax rate is defined as a constant, making it easy to update and understand. In the bad example, the tax rate is hardcoded, which makes the code less flexible and harder to maintain.

<Memo>

PHP constants are defined using the define() function or the const keyword. Constants are automatically global and can be accessed from any part of the script.

60

# Employ static variables for persistent state within functions

* * *

Static variables retain their value between function calls, providing a way to maintain state within a function.

* * *

Static variables are useful when you need to keep track of information across multiple calls to the same function without using global variables.

< Good Code >

<?php

// Function to generate a unique ID

function generateUniqueId() {

    // Static variable to keep track of the last ID

    static $lastId = 0;

    $lastId++;

    return $lastId;

}

// Example usage

echo generateUniqueId(); // Outputs: 1

echo generateUniqueId(); // Outputs: 2

echo generateUniqueId(); // Outputs: 3

?>

<Bad Code>

<?php

// Function to generate a unique ID

function generateUniqueId() {

    // Non-static variable to keep track of the last ID

    $lastId = 0;

    $lastId++;

    return $lastId;

}

// Example usage

echo generateUniqueId(); // Outputs: 1

echo generateUniqueId(); // Outputs: 1

echo generateUniqueId(); // Outputs: 1

?>

In the good example, the static variable $lastId retains its value between function calls, allowing the function to generate a unique ID each time it is called. In the bad example, the variable $lastId is reinitialized to 0 on each call, resulting in the same ID being returned every time.

<Memo>

Static variables in PHP are declared using the static keyword. They are initialized only once and retain their value between function calls, making them ideal for counting or accumulating values.

61

# Extract complex conditions into well-named methods

* * *

Improve code readability by extracting complex conditions into separate, well-named methods.

* * *

The following code demonstrates how to extract a complex condition into a well-named method for better readability.

< Good Code >

class Order {

    private $items;

    private $totalAmount;

    // Other properties and methods...

    public function isEligibleForDiscount() {

        return $this->hasMinimumItems() && $this->exceedsMinimumAmount();

    }

    private function hasMinimumItems() {

        return count($this->items) >= 5;

    }

    private function exceedsMinimumAmount() {

        return $this->totalAmount > 100;

    }

}

// Usage

$order = new Order();

if ($order->isEligibleForDiscount()) {

    // Apply discount

}

<Bad Code>

class Order {

    private $items;

    private $totalAmount;

    // Other properties and methods...

    public function isEligibleForDiscount() {

        return count($this->items) >= 5 && $this->totalAmount > 100;

    }

}

// Usage

$order = new Order();

if ($order->isEligibleForDiscount()) {

    // Apply discount

}

The good code example extracts the complex condition into a well-named method isEligibleForDiscount(). It further breaks down the condition into two separate methods: hasMinimumItems() and exceedsMinimumAmount(). This approach makes the code more readable and self-explanatory.

The bad code example, while shorter, combines multiple conditions in a single line, making it harder to understand at a glance and potentially more difficult to maintain or modify in the future.

<Memo>

This technique is often referred to as "Extract Method" and is one of the refactoring patterns described by Martin Fowler in his book "Refactoring: Improving the Design of Existing Code".

62

# Create separate methods for different levels of abstraction

* * *

Improve code organization by creating separate methods for different levels of abstraction.

* * *

The following code demonstrates how to separate different levels of abstraction into distinct methods for better readability and maintainability.

< Good Code >

class EmailSender {

    public function sendWelcomeEmail($user) {

        $emailContent = $this->prepareWelcomeEmailContent($user);

        $this->sendEmail($user->email, 'Welcome!', $emailContent);

    }

    private function prepareWelcomeEmailContent($user) {

        $template = $this->getWelcomeEmailTemplate();

        return str\_replace('{USERNAME}', $user->name, $template);

    }

    private function getWelcomeEmailTemplate() {

        return "Hello {USERNAME},\\n\\nWelcome to our platform!";

    }

    private function sendEmail($to, $subject, $content) {

        // Code to actually send the email

    }

}

// Usage

$emailSender = new EmailSender();

$emailSender->sendWelcomeEmail($user);

<Bad Code>

class EmailSender {

    public function sendWelcomeEmail($user) {

        $template = "Hello {USERNAME},\\n\\nWelcome to our platform!";

        $content = str\_replace('{USERNAME}', $user->name, $template);

        // Code to send email

        // ...

    }

}

// Usage

$emailSender = new EmailSender();

$emailSender->sendWelcomeEmail($user);

The good code example separates different levels of abstraction into distinct methods. The sendWelcomeEmail() method provides a high-level overview of the process, while lower-level details are handled by separate methods like prepareWelcomeEmailContent(), getWelcomeEmailTemplate(), and sendEmail(). This separation makes the code more modular, easier to understand, and simpler to maintain or extend.

The bad code example combines all operations in a single method, mixing high-level logic with low-level details. This approach can make the code harder to read, understand, and maintain, especially as the complexity of the operations increases.

<Memo>

This principle is related to the Single Responsibility Principle (SRP) from SOLID principles, which states that a class or method should have only one reason to change.

63

# Use pure functions that don't modify state

* * *

Write functions that always produce the same output for given inputs and don't modify external state.

* * *

The following code demonstrates a pure function that calculates the sum of an array without modifying the original data:

< Good Code >

/\*\*

\* Calculate the sum of an array of numbers

\*

\* @param array $numbers Array of numbers to sum

\* @return int The sum of all numbers in the array

\*/

function calculateSum(array $numbers): int

{

    // Use array\_reduce to sum all elements without modifying the original array

    return array\_reduce($numbers, function($carry, $item) {

        return $carry + $item;

    }, 0);

}

// Example usage

$myNumbers = \[1, 2, 3, 4, 5\];

$sum = calculateSum($myNumbers);

echo "Sum: " . $sum; // Output: Sum: 15

// Original array remains unchanged

print\_r($myNumbers); // Output: Array ( \[0\] => 1 \[1\] => 2 \[2\] => 3 \[3\] => 4 \[4\] => 5 )

<Bad Code>

/\*\*

\* Calculate the sum of an array of numbers (impure function)

\*

\* @param array $numbers Array of numbers to sum

\* @return int The sum of all numbers in the array

\*/

function calculateSum(array &$numbers): int

{

    $sum = 0;

    // Modify the original array while calculating the sum

    foreach ($numbers as &$number) {

        $sum += $number;

        $number \*= 2; // Modify each number in the array

    }

    return $sum;

}

// Example usage

$myNumbers = \[1, 2, 3, 4, 5\];

$sum = calculateSum($myNumbers);

echo "Sum: " . $sum; // Output: Sum: 15

// Original array is modified

print\_r($myNumbers); // Output: Array ( \[0\] => 2 \[1\] => 4 \[2\] => 6 \[3\] => 8 \[4\] => 10 )

The good code example demonstrates a pure function that calculates the sum of an array without modifying the original data. It uses array\_reduce to iterate through the array and sum its elements. The function always produces the same output for the same input and doesn't have any side effects.

The bad code example shows an impure function that modifies the original array while calculating the sum. It uses a reference parameter and modifies each element of the array during the calculation. This approach can lead to unexpected behavior and makes the code harder to reason about and test.

<Memo>

Pure functions are a key concept in functional programming and can lead to more predictable and easier-to-test code.

64

# Implement single responsibility principle for classes and methods

* * *

Design classes and methods that have a single, well-defined responsibility to improve code organization and maintainability.

* * *

The following code demonstrates the Single Responsibility Principle by separating user data management and email functionality:

< Good Code >

/\*\*

\* User class responsible for managing user data

\*/

class User

{

    private $name;

    private $email;

    /\*\*

     \* Constructor to initialize user data

\*

     \* @param string $name User's name

     \* @param string $email User's email

     \*/

    public function \_\_construct(string $name, string $email)

    {

        $this->name = $name;

        $this->email = $email;

    }

    /\*\*

     \* Get user's email

\*

     \* @return string User's email

     \*/

    public function getEmail(): string

    {

        return $this->email;

    }

    // Other user-related methods...

}

/\*\*

\* EmailService class responsible for sending emails

\*/

class EmailService

{

    /\*\*

     \* Send a welcome email to a user

\*

     \* @param User $user User to send email to

     \* @return bool True if email sent successfully, false otherwise

     \*/

    public function sendWelcomeEmail(User $user): bool

    {

        $to = $user->getEmail();

        $subject = "Welcome to our service!";

        $message = "Thank you for joining our platform.";

        // Email sending logic here...

        return mail($to, $subject, $message);

    }

    // Other email-related methods...

}

// Usage example

$user = new User("John Doe", "john@example.com");

$emailService = new EmailService();

$emailService->sendWelcomeEmail($user);

<Bad Code>

/\*\*

\* User class with mixed responsibilities

\*/

class User

{

    private $name;

    private $email;

    /\*\*

     \* Constructor to initialize user data

\*

     \* @param string $name User's name

     \* @param string $email User's email

     \*/

    public function \_\_construct(string $name, string $email)

    {

        $this->name = $name;

        $this->email = $email;

    }

    /\*\*

     \* Send a welcome email to the user

\*

     \* @return bool True if email sent successfully, false otherwise

     \*/

    public function sendWelcomeEmail(): bool

    {

        $to = $this->email;

        $subject = "Welcome to our service!";

        $message = "Thank you for joining our platform.";

        // Email sending logic here...

        return mail($to, $subject, $message);

    }

    // Other user-related and email-related methods mixed together...

}

// Usage example

$user = new User("John Doe", "john@example.com");

$user->sendWelcomeEmail();

The good code example demonstrates the Single Responsibility Principle by separating user data management (User class) from email functionality (EmailService class). This separation of concerns makes the code more modular, easier to maintain, and allows for better testing and future extensions.

The bad code example violates the Single Responsibility Principle by combining user data management and email sending functionality in a single User class. This approach makes the class less focused, harder to maintain, and more difficult to test or modify independently.

<Memo>

The Single Responsibility Principle is one of the five SOLID principles of object-oriented programming and design, introduced by Robert C. Martin.

65

# Separate query operations from command operations

* * *

Improve code readability by separating data retrieval (queries) from data modification (commands).

* * *

The following code demonstrates how to separate query and command operations in a user management system:

< Good Code >

// UserRepository.php

class UserRepository {

    // Query operation

    public function findUserById(int $id): ?User {

        // Database query to find user

        // Returns User object or null

    }

    // Command operation

    public function saveUser(User $user): void {

        // Database operation to save user

        // No return value

    }

}

// UserService.php

class UserService {

    private $userRepository;

    public function \_\_construct(UserRepository $userRepository) {

        $this->userRepository = $userRepository;

    }

    public function updateUserEmail(int $userId, string $newEmail): void {

        // Query

        $user = $this->userRepository->findUserById($userId);

        if ($user === null) {

            throw new UserNotFoundException();

        }

        // Modify

        $user->setEmail($newEmail);

        // Command

        $this->userRepository->saveUser($user);

    }

}

<Bad Code>

// UserManager.php

class UserManager {

    public function updateUserEmail($userId, $newEmail) {

        $db = new Database();

        $user = $db->query("SELECT \* FROM users WHERE id = $userId")->fetch();

        if ($user) {

            $db->query("UPDATE users SET email = '$newEmail' WHERE id = $userId");

            return true;

        }

        return false;

    }

}

The good code example separates concerns by using a repository pattern. It clearly distinguishes between query operations (findUserById) and command operations (saveUser). The UserService then uses these operations to perform a complex task.

The bad code example mixes querying and updating in a single method, making it harder to understand and maintain. It also doesn't separate database operations from business logic.

<Memo>

This principle is part of the Command Query Responsibility Segregation (CQRS) pattern, which can be scaled to separate read and write models in large, complex systems.

66

# Use type-safe enums with SplEnum

* * *

Enhance code clarity and type safety by using SplEnum for enumeration types.

* * *

The following code shows how to use SplEnum for creating a type-safe enumeration:

< Good Code >

// UserStatus.php

class UserStatus extends SplEnum {

    const \_\_default = self::ACTIVE;

    const ACTIVE = 1;

    const INACTIVE = 2;

    const SUSPENDED = 3;

}

// Usage

class User {

    private $status;

    public function setStatus(UserStatus $status) {

        $this->status = $status;

    }

    public function getStatus(): UserStatus {

        return $this->status;

    }

}

$user = new User();

$user->setStatus(new UserStatus(UserStatus::ACTIVE));

if ($user->getStatus()->equals(UserStatus::ACTIVE)) {

    echo "User is active";

}

<Bad Code>

// Without enum

class User {

    private $status;

    public function setStatus($status) {

        $this->status = $status;

    }

    public function getStatus() {

        return $this->status;

    }

}

$user = new User();

$user->setStatus(1); // What does 1 mean?

if ($user->getStatus() == 1) {

    echo "User is active"; // Unclear what 1 represents

}

The good code uses SplEnum to create a type-safe enumeration for UserStatus. This provides clear, meaningful constants for user statuses and ensures type safety when setting or checking the status.

The bad code uses arbitrary integers to represent user statuses, which can lead to confusion and errors. It's not clear what each number represents without additional context or documentation.

<Memo>

SplEnum is part of the Standard PHP Library (SPL) and requires the SPL Types extension to be installed. In PHP 8.1+, native enums are available as a language feature, providing an even more robust solution for enumeration types.

67

# Implement fluent interfaces for method chaining

* * *

Use method chaining to create more readable and expressive code.

* * *

The following code demonstrates how to implement a fluent interface for a simple User class:

< Good Code >

// Good example: Fluent interface implementation

class User {

    private $name;

    private $email;

    private $age;

    // Method to set name, returns $this for chaining

    public function setName($name) {

        $this->name = $name;

        return $this;

    }

    // Method to set email, returns $this for chaining

    public function setEmail($email) {

        $this->email = $email;

        return $this;

    }

    // Method to set age, returns $this for chaining

    public function setAge($age) {

        $this->age = $age;

        return $this;

    }

    // Method to get user info

    public function getInfo() {

        return "Name: {$this->name}, Email: {$this->email}, Age: {$this->age}";

    }

}

// Usage of fluent interface

$user = (new User())

    ->setName("John Doe")

    ->setEmail("john@example.com")

    ->setAge(30);

echo $user->getInfo();

<Bad Code>

// Bad example: Without fluent interface

class User {

    private $name;

    private $email;

    private $age;

    // Method to set name

    public function setName($name) {

        $this->name = $name;

    }

    // Method to set email

    public function setEmail($email) {

        $this->email = $email;

    }

    // Method to set age

    public function setAge($age) {

        $this->age = $age;

    }

    // Method to get user info

    public function getInfo() {

        return "Name: {$this->name}, Email: {$this->email}, Age: {$this->age}";

    }

}

// Usage without fluent interface

$user = new User();

$user->setName("John Doe");

$user->setEmail("john@example.com");

$user->setAge(30);

echo $user->getInfo();

The good example implements a fluent interface by returning $this in each setter method. This allows method chaining, making the code more readable and concise. The bad example doesn't use method chaining, resulting in multiple separate method calls, which can be less readable for complex operations.

<Memo>

Fluent interfaces were popularized by Martin Fowler and are commonly used in many modern PHP frameworks and libraries.

68

# Use final classes when inheritance is not needed

* * *

Declare classes as final to prevent inheritance when it's not necessary or intended.

* * *

The following code shows how to use final classes to prevent unintended inheritance:

< Good Code >

// Good example: Using final class

final class Configuration {

    private $settings = \[\];

    // Constructor to initialize settings

    public function \_\_construct(array $initialSettings = \[\]) {

        $this->settings = $initialSettings;

    }

    // Method to get a setting

    public function getSetting($key) {

        return $this->settings\[$key\] ?? null;

    }

    // Method to set a setting

    public function setSetting($key, $value) {

        $this->settings\[$key\] = $value;

    }

}

// Usage of final class

$config = new Configuration(\['debug' => true\]);

echo $config->getSetting('debug'); // Outputs: 1 (true)

<Bad Code>

// Bad example: Not using final class

class Configuration {

    protected $settings = \[\];

    // Constructor to initialize settings

    public function \_\_construct(array $initialSettings = \[\]) {

        $this->settings = $initialSettings;

    }

    // Method to get a setting

    public function getSetting($key) {

        return $this->settings\[$key\] ?? null;

    }

    // Method to set a setting

    public function setSetting($key, $value) {

        $this->settings\[$key\] = $value;

    }

}

// Unintended inheritance

class ExtendedConfiguration extends Configuration {

    // This could potentially break the intended behavior of Configuration

    public function overrideAllSettings(array $newSettings) {

        $this->settings = $newSettings;

    }

}

// Usage of non-final class

$config = new ExtendedConfiguration(\['debug' => true\]);

$config->overrideAllSettings(\['debug' => false, 'unsafe' => true\]);

echo $config->getSetting('debug'); // Outputs: (empty)

The good example uses a final class, preventing any inheritance. This ensures that the Configuration class behaves as intended and can't be extended in ways that might break its functionality. The bad example allows inheritance, which could lead to unexpected behavior if the class is extended inappropriately.

<Memo>

Using final classes can also slightly improve performance in PHP, as the engine doesn't need to check for overridden methods in child classes.

69

# Employ static analysis tools like PHPStan for code quality

* * *

Use PHPStan to detect potential errors and improve code quality automatically.

* * *

The following example demonstrates how to use PHPStan to analyze a simple PHP function:

< Good Code >

<?php

// File: example.php

/\*\*

\* Calculate the sum of two integers

\*

\* @param int $a First number

\* @param int $b Second number

\* @return int Sum of $a and $b

\*/

function add(int $a, int $b): int

{

    return $a + $b;

}

// Usage

$result = add(5, 3);

echo $result; // Outputs: 8

<Bad Code>

<?php

// File: example.php

function add($a, $b)

{

    return $a + $b;

}

$result = add("5", "3");

echo $result;

In the good example, we use type declarations for parameters and return type, which PHPStan can analyze. The bad example lacks type declarations, making it prone to type-related errors. Running PHPStan on the good code would yield no errors, while the bad code might generate warnings about potential type mismatches.

To use PHPStan:

Install PHPStan: composer require --dev phpstan/phpstan

Run analysis: vendor/bin/phpstan analyse example.php

<Memo>

PHPStan has different rule levels (0-9) for varying strictness of analysis. Level 0 is the loosest, while level 9 is the strictest.

70

# Utilize scalar type declarations for primitive types

* * *

Use scalar type declarations to enforce strict typing for primitive data types in PHP.

* * *

The following example shows how to use scalar type declarations in a function that calculates the area of a rectangle:

< Good Code >

<?php

declare(strict\_types=1);

/\*\*

\* Calculate the area of a rectangle

\*

\* @param float $length Length of the rectangle

\* @param float $width Width of the rectangle

\* @return float Area of the rectangle

\*/

function calculateRectangleArea(float $length, float $width): float

{

    return $length \* $width;

}

// Usage

$area = calculateRectangleArea(5.5, 3.2);

echo "Area: " . $area; // Outputs: Area: 17.6

<Bad Code>

<?php

function calculateRectangleArea($length, $width)

{

    return $length \* $width;

}

// Usage

$area = calculateRectangleArea("5.5", "3.2");

echo "Area: " . $area;

In the good example, we use declare(strict\_types=1) to enable strict type checking and float type declarations for parameters and return type. This ensures that only float values are accepted and returned. The bad example lacks type declarations, allowing any type of input, which can lead to unexpected results or errors.

Benefits of using scalar type declarations:

Improved code readability

Better error detection at runtime

Enhanced IDE support for autocompletion and type hinting

<Memo>

PHP 7.0 introduced scalar type declarations for int, float, string, and bool. Prior to this, only class names, self, array, and callable were allowed as type hints.

71

# Break long method chains into multiple lines

* * *

Improve code readability by splitting long method chains across multiple lines.

* * *

The following code demonstrates how to break a long method chain for better readability:

< Good Code >

// Good: Breaking long method chain into multiple lines

$result = $database->table('users')

    ->select('name', 'email')

    ->where('active', true)

    ->orderBy('created\_at', 'desc')

    ->limit(10)

    ->get();

<Bad Code>

// Bad: Long method chain on a single line

$result = $database->table('users')->select('name', 'email')->where('active', true)->orderBy('created\_at', 'desc')->limit(10)->get();

The good code example breaks the long method chain into multiple lines, with each method call on a new line and indented. This improves readability by making it easier to see each step in the chain. The bad code example puts everything on one line, making it harder to read and understand the individual method calls.

<Memo>

Many modern IDEs and code editors support automatic formatting that can help break long method chains into multiple lines.

72

# Use intermediate variables to explain complex calculations

* * *

Improve code clarity by using descriptive intermediate variables for complex calculations.

* * *

The following code shows how to use intermediate variables to make a complex calculation more understandable:

< Good Code >

// Good: Using intermediate variables for clarity

$basePrice = 100;

$taxRate = 0.08;

$discountPercentage = 0.1;

$priceAfterDiscount = $basePrice \* (1 - $discountPercentage);

$taxAmount = $priceAfterDiscount \* $taxRate;

$finalPrice = $priceAfterDiscount + $taxAmount;

echo "Final price: $" . number\_format($finalPrice, 2);

<Bad Code>

// Bad: Complex calculation without intermediate variables

$finalPrice = 100 \* (1 - 0.1) \* (1 + 0.08);

echo "Final price: $" . number\_format($finalPrice, 2);

The good code example uses descriptive intermediate variables to break down the complex calculation into smaller, more understandable steps. Each variable has a clear purpose, making the code self-explanatory. The bad code example performs the entire calculation in one line, making it difficult to understand the individual components and their purposes.

<Memo>

Using meaningful variable names not only improves code readability but can also serve as a form of self-documentation, reducing the need for additional comments.

73

# Extract complex regular expressions into named constants

* * *

Improve code readability by using named constants for complex regular expressions.

* * *

The following code demonstrates how to extract a complex regular expression into a named constant for better readability and maintainability.

< Good Code >

// Define a named constant for the complex regular expression

const EMAIL\_REGEX = '/^\[a-zA-Z0-9.\_%+-\]+@\[a-zA-Z0-9.-\]+\\.\[a-zA-Z\]{2,}$/';

// Use the named constant in the code

function validateEmail($email) {

    // Check if the email matches the defined regex pattern

    if (preg\_match(EMAIL\_REGEX, $email)) {

        return true;

    }

    return false;

}

// Example usage

$email = 'user@example.com';

if (validateEmail($email)) {

    echo "Valid email address";

} else {

    echo "Invalid email address";

}

<Bad Code>

// Complex regex directly in the function

function validateEmail($email) {

    // Directly use the complex regex in the preg\_match function

    if (preg\_match('/^\[a-zA-Z0-9.\_%+-\]+@\[a-zA-Z0-9.-\]+\\.\[a-zA-Z\]{2,}$/', $email)) {

        return true;

    }

    return false;

}

// Example usage

$email = 'user@example.com';

if (validateEmail($email)) {

    echo "Valid email address";

} else {

    echo "Invalid email address";

}

The good code example extracts the complex regular expression into a named constant EMAIL\_REGEX. This approach improves readability and makes it easier to update the regex if needed. The bad code example embeds the regex directly in the function, making it harder to read and maintain.

<Memo>

Regular expressions, often abbreviated as regex, are powerful tools for pattern matching and text manipulation in programming languages, including PHP.

74

# Use array destructuring for cleaner multiple assignment

* * *

Simplify code by using array destructuring to assign multiple variables at once.

* * *

The following code demonstrates how to use array destructuring for cleaner multiple variable assignments in PHP.

< Good Code >

// Function that returns an array of user details

function getUserDetails() {

    return \['John Doe', 30, 'john@example.com'\];

}

// Use array destructuring to assign multiple variables

\[$name, $age, $email\] = getUserDetails();

// Use the assigned variables

echo "Name: $name, Age: $age, Email: $email";

<Bad Code>

// Function that returns an array of user details

function getUserDetails() {

    return \['John Doe', 30, 'john@example.com'\];

}

// Assign variables individually

$userDetails = getUserDetails();

$name = $userDetails\[0\];

$age = $userDetails\[1\];

$email = $userDetails\[2\];

// Use the assigned variables

echo "Name: $name, Age: $age, Email: $email";

The good code example uses array destructuring to assign multiple variables in a single line, making the code more concise and readable. The bad code example assigns each variable individually, which is more verbose and prone to errors if the array structure changes.

<Memo>

Array destructuring was introduced in PHP 7.1 and provides a convenient way to unpack arrays into distinct variables.

75

# Employ the null coalescing assignment operator (??=) for concise default assignments

* * *

Use ??= to assign default values efficiently in PHP 7.4+

* * *

The following code demonstrates how to use the null coalescing assignment operator (??=) to set default values for variables:

< Good Code >

// Good code using null coalescing assignment operator

function getUserSettings($userId) {

    $settings = fetchUserSettings($userId);

    // Set default values using ??=

    $settings\['theme'\] ??= 'light';

    $settings\['notifications'\] ??= true;

    $settings\['language'\] ??= 'en';

    return $settings;

}

<Bad Code>

// Bad code without using null coalescing assignment operator

function getUserSettings($userId) {

    $settings = fetchUserSettings($userId);

    // Set default values using traditional method

    if (!isset($settings\['theme'\])) {

        $settings\['theme'\] = 'light';

    }

    if (!isset($settings\['notifications'\])) {

        $settings\['notifications'\] = true;

    }

    if (!isset($settings\['language'\])) {

        $settings\['language'\] = 'en';

    }

    return $settings;

}

The good code example uses the ??= operator to concisely set default values for array keys. This operator assigns the right-hand value only if the left-hand variable is null or doesn't exist. It's more readable and reduces the number of lines compared to the bad code example, which uses traditional if statements to check and set default values.

<Memo>

The null coalescing assignment operator (??=) was introduced in PHP 7.4 as a shorthand for the common pattern of checking and assigning default values.

76

# Extract configuration into separate files

* * *

Improve code maintainability by separating configuration from logic

* * *

The following example shows how to extract configuration settings into a separate file:

< Good Code >

// config.php

return \[

    'database' => \[

        'host' => 'localhost',

        'username' => 'user',

        'password' => 'password',

        'dbname' => 'myapp'

    \],

    'api\_key' => 'your\_api\_key\_here',

    'debug\_mode' => true

\];

// main.php

$config = require 'config.php';

// Use configuration

$dbHost = $config\['database'\]\['host'\];

$apiKey = $config\['api\_key'\];

<Bad Code>

// Bad practice: Mixing configuration with application logic

$dbHost = 'localhost';

$dbUsername = 'user';

$dbPassword = 'password';

$dbName = 'myapp';

$apiKey = 'your\_api\_key\_here';

$debugMode = true;

// Application logic

function connectToDatabase() {

    global $dbHost, $dbUsername, $dbPassword, $dbName;

    // Database connection code here

}

function makeApiCall() {

    global $apiKey;

    // API call code here

}

The good code example separates configuration into a dedicated file (config.php), which returns an array of settings. This approach makes it easier to manage and update configuration without modifying the main application code. The bad code example mixes configuration directly with application logic, making it harder to maintain and update settings across the application.

<Memo>

Separating configuration from code is a key principle in the 12-factor app methodology, which aims to build software-as-a-service apps that are scalable and maintainable.

77

# Move utility functions to a separate class or namespace

* * *

Organize utility functions into a dedicated class or namespace to improve code readability and maintainability.

* * *

Utility functions are often used across multiple parts of an application. By moving them to a separate class or namespace, you can keep your codebase clean and modular, making it easier for others to understand and maintain.

< Good Code >

<?php

namespace App\\Utils;

/\*\*

\* Utility class for common functions

\*/

class StringUtils {

    /\*\*

     \* Convert a string to camel case

     \*

     \* @param string $string

     \* @return string

     \*/

    public static function toCamelCase(string $string): string {

        $result = strtolower($string);

        preg\_match\_all('/\[a-zA-Z0-9\]+/', $result, $matches);

        $result = $matches\[0\]\[0\];

        for ($i = 1; $i < count($matches\[0\]); $i++) {

            $result .= ucfirst($matches\[0\]\[$i\]);

        }

        return $result;

    }

}

// Usage

echo \\App\\Utils\\StringUtils::toCamelCase('hello\_world'); // Outputs: helloWorld

?>

<Bad Code>

<?php

/\*\*

\* Convert a string to camel case

\*

\* @param string $string

\* @return string

\*/

function toCamelCase($string) {

    $result = strtolower($string);

    preg\_match\_all('/\[a-zA-Z0-9\]+/', $result, $matches);

    $result = $matches\[0\]\[0\];

    for ($i = 1; $i < count($matches\[0\]); $i++) {

        $result .= ucfirst($matches\[0\]\[$i\]);

    }

    return $result;

}

// Usage

echo toCamelCase('hello\_world'); // Outputs: helloWorld

?>

In the good example, the utility function toCamelCase is encapsulated within a StringUtils class under the App\\Utils namespace. This organization makes it clear where utility functions are located and avoids potential naming conflicts. In the bad example, the function is defined in the global scope, which can lead to clutter and conflicts in larger codebases.

<Memo>

Namespaces in PHP were introduced in version 5.3 to help avoid name collisions and to organize code into logical groups.

78

# Use traits for cross-cutting concerns

* * *

Utilize traits to encapsulate methods that are shared across multiple classes, promoting code reuse and reducing duplication.

* * *

Traits allow you to reuse sets of methods in multiple classes. This is particularly useful for cross-cutting concerns like logging, validation, or authorization, where the same functionality is needed in different parts of your application.

< Good Code >

<?php

namespace App\\Traits;

/\*\*

\* Trait for logging functionality

\*/

trait Logger {

    /\*\*

     \* Log a message

     \*

     \* @param string $message

     \*/

    public function log(string $message) {

        echo "\[LOG\]: " . $message . "\\n";

    }

}

class User {

    use \\App\\Traits\\Logger;

    public function createUser() {

        // User creation logic

        $this->log("User created successfully.");

    }

}

class Product {

    use \\App\\Traits\\Logger;

    public function createProduct() {

        // Product creation logic

        $this->log("Product created successfully.");

    }

}

// Usage

$user = new User();

$user->createUser(); // Outputs: \[LOG\]: User created successfully.

$product = new Product();

$product->createProduct(); // Outputs: \[LOG\]: Product created successfully.

?>

<Bad Code>

<?php

class User {

    /\*\*

     \* Log a message

     \*

     \* @param string $message

     \*/

    public function log($message) {

        echo "\[LOG\]: " . $message . "\\n";

    }

    public function createUser() {

        // User creation logic

        $this->log("User created successfully.");

    }

}

class Product {

    /\*\*

     \* Log a message

     \*

     \* @param string $message

     \*/

    public function log($message) {

        echo "\[LOG\]: " . $message . "\\n";

    }

    public function createProduct() {

        // Product creation logic

        $this->log("Product created successfully.");

    }

}

// Usage

$user = new User();

$user->createUser(); // Outputs: \[LOG\]: User created successfully.

$product = new Product();

$product->createProduct(); // Outputs: \[LOG\]: Product created successfully.

?>

In the good example, the Logger trait encapsulates the logging functionality, which is then used by both the User and Product classes. This promotes code reuse and keeps the logging logic consistent across different classes. In the bad example, the logging method is duplicated in both classes, leading to code redundancy and potential inconsistencies.

<Memo>

Traits were introduced in PHP 5.4 to enable developers to reuse methods across multiple classes without using inheritance, providing a flexible way to share functionality.

79

# Implement caching mechanisms as separate classes

* * *

Separate caching logic into dedicated classes for improved modularity and maintainability.

* * *

The following code demonstrates how to implement a caching mechanism as a separate class in PHP:

< Good Code >

// CacheInterface.php

interface CacheInterface {

    public function get($key);

    public function set($key, $value, $ttl = 3600);

}

// FileCache.php

class FileCache implements CacheInterface {

    private $cacheDir;

    public function \_\_construct($cacheDir) {

        $this->cacheDir = $cacheDir;

    }

    public function get($key) {

        $filename = $this->getCacheFilename($key);

        if (file\_exists($filename) && (filemtime($filename) + $this->ttl) > time()) {

            return unserialize(file\_get\_contents($filename));

        }

        return null;

    }

    public function set($key, $value, $ttl = 3600) {

        $filename = $this->getCacheFilename($key);

        file\_put\_contents($filename, serialize($value));

    }

    private function getCacheFilename($key) {

        return $this->cacheDir . '/' . md5($key) . '.cache';

    }

}

// Usage

$cache = new FileCache('/path/to/cache');

$data = $cache->get('my\_key');

if ($data === null) {

    $data = // ... expensive operation to get data

    $cache->set('my\_key', $data, 3600); // Cache for 1 hour

}

<Bad Code>

// Bad example: Caching logic mixed with business logic

function getUserData($userId) {

    $cacheFile = '/tmp/user\_' . $userId . '.cache';

    if (file\_exists($cacheFile) && (filemtime($cacheFile) + 3600) > time()) {

        return unserialize(file\_get\_contents($cacheFile));

    }

    // Fetch user data from database

    $userData = fetchUserFromDatabase($userId);

    // Cache the data

    file\_put\_contents($cacheFile, serialize($userData));

    return $userData;

}

The good code example separates the caching mechanism into a dedicated class (FileCache) that implements a CacheInterface. This approach allows for easy swapping of caching implementations (e.g., switching to Redis or Memcached) without changing the usage code. It also keeps the caching logic separate from business logic, improving code readability and maintainability.

The bad code example mixes caching logic directly within a business logic function. This approach makes the code less flexible, harder to test, and more difficult to maintain or change caching strategies.

<Memo>

Caching is a crucial technique for improving application performance, especially in high-traffic web applications. PHP has built-in support for various caching mechanisms, including OPcache for opcode caching and APCu for data caching.

80

# Extract complex validation logic into dedicated validator classes

* * *

Separate complex validation logic into dedicated validator classes for improved code organization and reusability.

* * *

The following code demonstrates how to extract complex validation logic into a dedicated validator class in PHP:

< Good Code >

// UserValidator.php

class UserValidator {

    public function validateUsername($username) {

        if (strlen($username) < 3 || strlen($username) > 20) {

            throw new ValidationException("Username must be between 3 and 20 characters.");

        }

        if (!preg\_match('/^\[a-zA-Z0-9\_\]+$/', $username)) {

            throw new ValidationException("Username can only contain letters, numbers, and underscores.");

        }

    }

    public function validateEmail($email) {

        if (!filter\_var($email, FILTER\_VALIDATE\_EMAIL)) {

            throw new ValidationException("Invalid email format.");

        }

        // Additional email validation logic (e.g., domain check) can be added here

    }

    public function validatePassword($password) {

        if (strlen($password) < 8) {

            throw new ValidationException("Password must be at least 8 characters long.");

        }

        if (!preg\_match('/\[A-Z\]/', $password) || !preg\_match('/\[a-z\]/', $password) || !preg\_match('/\[0-9\]/', $password)) {

            throw new ValidationException("Password must contain at least one uppercase letter, one lowercase letter, and one number.");

        }

    }

}

// Usage

$validator = new UserValidator();

try {

    $validator->validateUsername($username);

    $validator->validateEmail($email);

    $validator->validatePassword($password);

    // Proceed with user registration

} catch (ValidationException $e) {

    // Handle validation error

    echo $e->getMessage();

}

<Bad Code>

// Bad example: Validation logic mixed with user registration

function registerUser($username, $email, $password) {

    // Username validation

    if (strlen($username) < 3 || strlen($username) > 20) {

        return "Username must be between 3 and 20 characters.";

    }

    if (!preg\_match('/^\[a-zA-Z0-9\_\]+$/', $username)) {

        return "Username can only contain letters, numbers, and underscores.";

    }

    // Email validation

    if (!filter\_var($email, FILTER\_VALIDATE\_EMAIL)) {

        return "Invalid email format.";

    }

    // Password validation

    if (strlen($password) < 8) {

        return "Password must be at least 8 characters long.";

    }

    if (!preg\_match('/\[A-Z\]/', $password) || !preg\_match('/\[a-z\]/', $password) || !preg\_match('/\[0-9\]/', $password)) {

        return "Password must contain at least one uppercase letter, one lowercase letter, and one number.";

    }

    // Proceed with user registration

    // ...

}

The good code example extracts complex validation logic into a dedicated UserValidator class. This approach improves code organization, makes the validation rules more reusable across different parts of the application, and separates concerns. It also allows for easier testing of validation logic in isolation.

The bad code example mixes validation logic directly within the user registration function. This approach makes the function longer, harder to read, and less maintainable. It also makes it difficult to reuse the validation logic in other parts of the application.

<Memo>

PHP provides several built-in functions for data validation, such as filter\_var() with various filters. However, for complex validation rules, creating custom validator classes is often more flexible and maintainable.

81

# Use union types for more precise type hinting

* * *

Union types allow specifying multiple possible types for a parameter or return value, enhancing code clarity and type safety.

* * *

The following code demonstrates the use of union types in PHP 8.0+ to improve type hinting:

< Good Code >

/\*\*

\* Calculate the total price of an order

\*

\* @param array $items Array of order items

\* @param float|int $taxRate Tax rate as a decimal or percentage

\* @return float Total price including tax

\*/

function calculateTotalPrice(array $items, float|int $taxRate): float

{

    $subtotal = array\_sum(array\_column($items, 'price'));

    // Convert percentage to decimal if necessary

    $taxRateDecimal = $taxRate > 1 ? $taxRate / 100 : $taxRate;

    $taxAmount = $subtotal \* $taxRateDecimal;

    $total = $subtotal + $taxAmount;

    return round($total, 2);

}

// Usage examples

$orderItems = \[

    \['name' => 'Widget A', 'price' => 10.99\],

    \['name' => 'Widget B', 'price' => 15.50\],

\];

echo calculateTotalPrice($orderItems, 0.08);  // Tax rate as decimal

echo calculateTotalPrice($orderItems, 8);     // Tax rate as percentage

<Bad Code>

function calculateTotalPrice($items, $taxRate)

{

    $t = 0;

    foreach ($items as $i) {

        $t += $i\['price'\];

    }

    return $t + $t \* ($taxRate > 1 ? $taxRate / 100 : $taxRate);

}

$orderItems = \[

    \['name' => 'Widget A', 'price' => 10.99\],

    \['name' => 'Widget B', 'price' => 15.50\],

\];

echo calculateTotalPrice($orderItems, 0.08);

echo calculateTotalPrice($orderItems, 8);

The good code example uses union types (float|int) for the $taxRate parameter, allowing it to accept both decimal and percentage values. It also includes a detailed docblock, descriptive variable names, and clear logic. The bad code lacks type hinting, uses ambiguous variable names, and has less readable logic.

<Memo>

Union types were introduced in PHP 8.0, providing a way to specify multiple possible types for a single parameter or return value.

82

# Implement \_\_serialize and \_\_unserialize for custom object serialization

* * *

Using \_\_serialize and \_\_unserialize magic methods allows for more control over object serialization and deserialization processes.

* * *

The following code demonstrates how to implement \_\_serialize and \_\_unserialize methods for custom object serialization:

< Good Code >

/\*\*

\* Represents a user in the system

\*/

class User

{

    private string $username;

    private string $email;

    private array $preferences;

    public function \_\_construct(string $username, string $email)

    {

        $this->username = $username;

        $this->email = $email;

        $this->preferences = \[\];

    }

    /\*\*

     \* Custom serialization method

     \*

     \* @return array

     \*/

    public function \_\_serialize(): array

    {

        return \[

            'username' => $this->username,

            'email' => $this->email,

            'preferences' => $this->preferences,

        \];

    }

    /\*\*

     \* Custom unserialization method

     \*

     \* @param array $data

     \*/

    public function \_\_unserialize(array $data): void

    {

        $this->username = $data\['username'\];

        $this->email = $data\['email'\];

        $this->preferences = $data\['preferences'\] ?? \[\];

    }

    // Other methods...

}

// Usage

$user = new User('johndoe', 'john@example.com');

$serialized = serialize($user);

$unserialized = unserialize($serialized);

var\_dump($unserialized);

<Bad Code>

class User

{

    public $u;

    public $e;

    private $p;

    function \_\_construct($u, $e)

    {

        $this->u = $u;

        $this->e = $e;

        $this->p = \[\];

    }

}

$user = new User('johndoe', 'john@example.com');

$s = serialize($user);

$u = unserialize($s);

var\_dump($u);

The good code example implements \_\_serialize and \_\_unserialize methods, providing control over which properties are serialized and how they are reconstructed. It uses clear property names and includes type declarations. The bad code relies on PHP's default serialization, which may expose internal properties and doesn't handle complex objects well.

<Memo>

The \_\_serialize and \_\_unserialize magic methods were introduced in PHP 7.4 as a more efficient alternative to the older Serializable interface.

83

# Use the Reflection API for dynamic code analysis

* * *

Leverage PHP's Reflection API to analyze and manipulate code structure at runtime.

* * *

The following code demonstrates how to use the Reflection API to inspect a class and its methods:

< Good Code >

// Good example using Reflection API

class MyClass {

    public function myMethod($param1, $param2 = null) {

        // Method implementation

    }

}

// Use Reflection to analyze the class

$reflection = new ReflectionClass('MyClass');

// Get information about the class

echo "Class name: " . $reflection->getName() . "\\n";

// Analyze methods

foreach ($reflection->getMethods() as $method) {

    echo "Method: " . $method->getName() . "\\n";

    // Analyze method parameters

    foreach ($method->getParameters() as $param) {

        echo "  Parameter: " . $param->getName();

        if ($param->isOptional()) {

            echo " (optional)";

        }

        echo "\\n";

    }

}

<Bad Code>

// Bad example without using Reflection API

class MyClass {

    public function myMethod($param1, $param2 = null) {

        // Method implementation

    }

}

// Manually trying to analyze the class

$className = 'MyClass';

echo "Class name: $className\\n";

// Trying to get method information without Reflection

$methods = get\_class\_methods($className);

foreach ($methods as $method) {

    echo "Method: $method\\n";

    // No way to easily get parameter information

}

The good example uses the Reflection API to dynamically analyze the class structure. It provides detailed information about the class, its methods, and method parameters, including whether they are optional. This approach is more flexible and powerful.

The bad example attempts to analyze the class manually, which is limited in scope. It can only retrieve method names and cannot easily access parameter information or other detailed class structure data.

<Memo>

The Reflection API was introduced in PHP 5 and has been continuously improved in subsequent versions, making it a powerful tool for metaprogramming and code analysis.

84

# Employ the \_\_set\_state magic method for var\_export compatibility

* * *

Implement the \_\_set\_state magic method to ensure proper object reconstruction when using var\_export().

* * *

The following code shows how to implement \_\_set\_state for better var\_export() compatibility:

< Good Code >

// Good example with \_\_set\_state implementation

class ConfigObject {

    private $data;

    public function \_\_construct(array $data) {

        $this->data = $data;

    }

    public static function \_\_set\_state($array) {

        return new self($array\['data'\]);

    }

    public function getData() {

        return $this->data;

    }

}

// Usage

$config = new ConfigObject(\['key' => 'value'\]);

$exported = var\_export($config, true);

eval('$importedConfig = ' . $exported . ';');

// $importedConfig is now a proper ConfigObject instance

var\_dump($importedConfig->getData()); // Outputs: array(1) { \["key"\]=> string(5) "value" }

<Bad Code>

// Bad example without \_\_set\_state implementation

class ConfigObject {

    private $data;

    public function \_\_construct(array $data) {

        $this->data = $data;

    }

    public function getData() {

        return $this->data;

    }

}

// Usage

$config = new ConfigObject(\['key' => 'value'\]);

$exported = var\_export($config, true);

eval('$importedConfig = ' . $exported . ';');

// $importedConfig is not a proper ConfigObject instance

// Trying to use it will result in an error

// var\_dump($importedConfig->getData()); // This would cause an error

The good example implements the \_\_set\_state magic method, which allows the object to be properly reconstructed when using var\_export(). This method returns a new instance of the class with the exported data, ensuring that the object's state is correctly restored.

The bad example lacks the \_\_set\_state method. When var\_export() is used on this object and the result is evaluated, it creates a stdClass object instead of a ConfigObject instance. This leads to errors when trying to use methods specific to the ConfigObject class.

<Memo>

The \_\_set\_state magic method was introduced in PHP 5.1.0 specifically to address issues with var\_export() and object serialization.

85

# Utilize the \_\_clone magic method for proper object cloning

* * *

Implement the \_\_clone magic method to ensure deep copying of objects.

* * *

The following code demonstrates the proper use of the \_\_clone magic method for object cloning:

< Good Code >

class User {

    public $name;

    public $address;

    public function \_\_construct($name) {

        $this->name = $name;

        $this->address = new Address();

    }

    // Implement \_\_clone magic method for deep copying

    public function \_\_clone() {

        // Create a new instance of Address for the cloned User

        $this->address = clone $this->address;

    }

}

class Address {

    public $street;

    public $city;

}

// Usage

$user1 = new User("John");

$user1->address->street = "123 Main St";

$user1->address->city = "New York";

$user2 = clone $user1;

$user2->name = "Jane";

$user2->address->street = "456 Elm St";

// Output results

echo $user1->name . " lives at " . $user1->address->street . "\\n";

echo $user2->name . " lives at " . $user2->address->street . "\\n";

<Bad Code>

class User {

    public $name;

    public $address;

    public function \_\_construct($name) {

        $this->name = $name;

        $this->address = new Address();

    }

    // No \_\_clone method implemented

}

class Address {

    public $street;

    public $city;

}

// Usage

$user1 = new User("John");

$user1->address->street = "123 Main St";

$user1->address->city = "New York";

$user2 = clone $user1;

$user2->name = "Jane";

$user2->address->street = "456 Elm St";

// Output results

echo $user1->name . " lives at " . $user1->address->street . "\\n";

echo $user2->name . " lives at " . $user2->address->street . "\\n";

In the good code example, the \_\_clone magic method is implemented in the User class. This ensures that when an object is cloned, a deep copy is created for nested objects like Address. The bad code example lacks the \_\_clone method, resulting in a shallow copy where both User objects share the same Address instance. This can lead to unexpected behavior when modifying properties of nested objects.

<Memo>

The \_\_clone magic method was introduced in PHP 5 to provide more control over the object cloning process.

86

# Use associative arrays for key-value pairs

* * *

Utilize associative arrays to store and access data using meaningful keys.

* * *

The following code demonstrates the effective use of associative arrays for managing key-value pairs:

< Good Code >

// Using an associative array to store user information

$user = \[

    'name' => 'John Doe',

    'age' => 30,

    'email' => 'john@example.com',

    'roles' => \['admin', 'editor'\]

\];

// Accessing and displaying user information

echo "Name: " . $user\['name'\] . "\\n";

echo "Age: " . $user\['age'\] . "\\n";

echo "Email: " . $user\['email'\] . "\\n";

echo "Roles: " . implode(', ', $user\['roles'\]) . "\\n";

// Adding a new key-value pair

$user\['location'\] = 'New York';

// Checking if a key exists before using it

if (isset($user\['phone'\])) {

    echo "Phone: " . $user\['phone'\] . "\\n";

} else {

    echo "Phone number not provided.\\n";

}

<Bad Code>

// Using separate variables to store user information

$name = 'John Doe';

$age = 30;

$email = 'john@example.com';

$role1 = 'admin';

$role2 = 'editor';

// Displaying user information

echo "Name: " . $name . "\\n";

echo "Age: " . $age . "\\n";

echo "Email: " . $email . "\\n";

echo "Roles: " . $role1 . ", " . $role2 . "\\n";

// Adding a new piece of information

$location = 'New York';

// Checking if a variable is set before using it

if (isset($phone)) {

    echo "Phone: " . $phone . "\\n";

} else {

    echo "Phone number not provided.\\n";

}

The good code example uses an associative array to store user information, making it easy to manage and access related data. Keys are meaningful and self-explanatory. The bad code example uses separate variables, which can become unwieldy as the number of data points increases. The associative array approach also simplifies adding new key-value pairs and checking for the existence of specific keys.

<Memo>

Associative arrays in PHP are implemented as ordered maps, which maintain the order of elements as they are inserted.

87

# Employ SplFixedArray for memory-efficient numeric arrays

* * *

Use SplFixedArray for better memory management in numeric arrays.

* * *

The following code demonstrates the use of SplFixedArray for creating a memory-efficient numeric array:

< Good Code >

// Good example using SplFixedArray

$size = 1000000;

// Create a fixed-size array

$array = new SplFixedArray($size);

// Populate the array

for ($i = 0; $i < $size; $i++) {

    $array\[$i\] = $i \* 2;

}

// Access elements

echo "Element at index 500000: " . $array\[500000\] . "\\n";

// Memory usage

echo "Memory usage: " . memory\_get\_usage(true) / 1024 / 1024 . " MB\\n";

<Bad Code>

// Bad example using standard PHP array

$size = 1000000;

// Create a standard PHP array

$array = array();

// Populate the array

for ($i = 0; $i < $size; $i++) {

    $array\[\] = $i \* 2;

}

// Access elements

echo "Element at index 500000: " . $array\[500000\] . "\\n";

// Memory usage

echo "Memory usage: " . memory\_get\_usage(true) / 1024 / 1024 . " MB\\n";

The good example uses SplFixedArray, which is more memory-efficient for large numeric arrays. It pre-allocates memory for a fixed number of elements, reducing overhead. The bad example uses a standard PHP array, which is more flexible but consumes more memory, especially for large datasets.

<Memo>

SplFixedArray was introduced in PHP 5.3 and is part of the Standard PHP Library (SPL).

88

# Use SplObjectStorage for object-based hash tables

* * *

Implement SplObjectStorage for efficient object-based hash tables.

* * *

The following code illustrates the use of SplObjectStorage for creating an efficient object-based hash table:

< Good Code >

// Good example using SplObjectStorage

$storage = new SplObjectStorage();

// Create some sample objects

$obj1 = new stdClass();

$obj2 = new stdClass();

$obj3 = new stdClass();

// Store objects with associated data

$storage\[$obj1\] = 'Data for object 1';

$storage\[$obj2\] = 'Data for object 2';

$storage\[$obj3\] = 'Data for object 3';

// Check if an object exists and retrieve its data

if ($storage->contains($obj2)) {

    echo "Data for obj2: " . $storage\[$obj2\] . "\\n";

}

// Iterate over the storage

foreach ($storage as $obj) {

    echo "Object data: " . $storage\[$obj\] . "\\n";

}

// Count objects

echo "Number of objects: " . count($storage) . "\\n";

<Bad Code>

// Bad example using standard array

$storage = array();

// Create some sample objects

$obj1 = new stdClass();

$obj2 = new stdClass();

$obj3 = new stdClass();

// Store objects with associated data (not recommended)

$storage\[spl\_object\_hash($obj1)\] = 'Data for object 1';

$storage\[spl\_object\_hash($obj2)\] = 'Data for object 2';

$storage\[spl\_object\_hash($obj3)\] = 'Data for object 3';

// Check if an object exists and retrieve its data

if (isset($storage\[spl\_object\_hash($obj2)\])) {

    echo "Data for obj2: " . $storage\[spl\_object\_hash($obj2)\] . "\\n";

}

// Iterate over the storage (cumbersome)

foreach ($storage as $hash => $data) {

    echo "Object data: " . $data . "\\n";

}

// Count objects

echo "Number of objects: " . count($storage) . "\\n";

The good example uses SplObjectStorage, which is designed for efficient storage and retrieval of objects. It allows direct use of objects as keys and provides built-in methods for object management. The bad example attempts to mimic this behavior using a standard array and spl\_object\_hash(), which is less efficient and more prone to errors.

<Memo>

SplObjectStorage implements Countable, Iterator, Serializable, and ArrayAccess interfaces, making it versatile for various use cases.

89

# Implement ArrayAccess for array-like object behavior

* * *

Implement the ArrayAccess interface to allow objects to be accessed like arrays.

* * *

The following code demonstrates how to implement the ArrayAccess interface to create an object that behaves like an array:

< Good Code >

<?php

// Good example: Implementing ArrayAccess for a custom object

class CustomArray implements ArrayAccess {

    private $container = array();

    // Check if an offset exists

    public function offsetExists($offset): bool {

        return isset($this->container\[$offset\]);

    }

    // Get the value at a given offset

    public function offsetGet($offset): mixed {

        return isset($this->container\[$offset\]) ? $this->container\[$offset\] : null;

    }

    // Set the value at a given offset

    public function offsetSet($offset, $value): void {

        if (is\_null($offset)) {

            $this->container\[\] = $value;

        } else {

            $this->container\[$offset\] = $value;

        }

    }

    // Unset the value at a given offset

    public function offsetUnset($offset): void {

        unset($this->container\[$offset\]);

    }

}

// Usage example

$obj = new CustomArray();

$obj\['key'\] = 'value';

echo $obj\['key'\]; // Outputs: value

<Bad Code>

<?php

// Bad example: Not implementing ArrayAccess, using magic methods instead

class BadCustomArray {

    private $container = array();

    public function \_\_set($name, $value) {

        $this->container\[$name\] = $value;

    }

    public function \_\_get($name) {

        return $this->container\[$name\];

    }

}

// Usage example

$obj = new BadCustomArray();

$obj->key = 'value'; // Works, but not array-like syntax

echo $obj->key; // Outputs: value

The good example implements the ArrayAccess interface, allowing the object to be used with array syntax. This makes the code more intuitive and consistent with array operations. The bad example uses magic methods, which work but don't provide true array-like syntax and may be less performant.

<Memo>

The ArrayAccess interface was introduced in PHP 5.0 and is part of the Standard PHP Library (SPL).

90

# Use SplQueue and SplStack for efficient FIFO and LIFO operations

* * *

Utilize SplQueue and SplStack for efficient First-In-First-Out (FIFO) and Last-In-First-Out (LIFO) operations.

* * *

The following code demonstrates the use of SplQueue and SplStack for efficient queue and stack operations:

< Good Code >

<?php

// Good example: Using SplQueue and SplStack for FIFO and LIFO operations

// FIFO operation using SplQueue

$queue = new SplQueue();

$queue->enqueue('First');

$queue->enqueue('Second');

$queue->enqueue('Third');

echo "Queue (FIFO):\\n";

while (!$queue->isEmpty()) {

    echo $queue->dequeue() . "\\n";

}

// LIFO operation using SplStack

$stack = new SplStack();

$stack->push('First');

$stack->push('Second');

$stack->push('Third');

echo "\\nStack (LIFO):\\n";

while (!$stack->isEmpty()) {

    echo $stack->pop() . "\\n";

}

<Bad Code>

<?php

// Bad example: Using arrays for queue and stack operations

// FIFO operation using array

$queue = array();

array\_push($queue, 'First');

array\_push($queue, 'Second');

array\_push($queue, 'Third');

echo "Queue (FIFO):\\n";

while (!empty($queue)) {

    echo array\_shift($queue) . "\\n";

}

// LIFO operation using array

$stack = array();

array\_push($stack, 'First');

array\_push($stack, 'Second');

array\_push($stack, 'Third');

echo "\\nStack (LIFO):\\n";

while (!empty($stack)) {

    echo array\_pop($stack) . "\\n";

}

The good example uses SplQueue and SplStack, which are optimized for FIFO and LIFO operations respectively. These classes provide better performance and more appropriate methods for queue and stack operations. The bad example uses regular arrays with array\_push, array\_shift, and array\_pop, which are less efficient for large datasets and don't provide the semantic clarity of dedicated queue and stack classes.

<Memo>

SplQueue and SplStack are part of the Standard PHP Library (SPL) and were introduced in PHP 5.3.0.

91

# Use try-catch blocks for expected exceptions

* * *

Implement try-catch blocks to handle anticipated exceptions gracefully.

* * *

The following code demonstrates how to use try-catch blocks to handle file operations:

< Good Code >

// Good example: Using try-catch for file operations

try {

    // Attempt to open a file

    $file = fopen('important\_data.txt', 'r');

    if ($file === false) {

        // If fopen fails, throw a custom exception

        throw new Exception('Failed to open the file.');

    }

    // Read the file contents

    $content = fread($file, filesize('important\_data.txt'));

    // Close the file

    fclose($file);

    // Process the content

    echo "File contents: " . $content;

} catch (Exception $e) {

    // Handle the exception gracefully

    error\_log("Error: " . $e->getMessage());

    echo "An error occurred while reading the file. Please try again later.";

} finally {

    // Ensure the file is closed if it was successfully opened

    if (isset($file) && $file !== false) {

        fclose($file);

    }

}

<Bad Code>

// Bad example: Not using try-catch for file operations

$file = fopen('important\_data.txt', 'r');

$content = fread($file, filesize('important\_data.txt'));

fclose($file);

echo "File contents: " . $content;

The good example uses a try-catch block to handle potential exceptions when working with files. It checks if the file opens successfully, reads its contents, and ensures proper closure. If an error occurs, it's caught and handled gracefully. The bad example doesn't handle potential errors, which could lead to unexpected behavior or crashes if the file can't be opened or read.

<Memo>

PHP 7.1 introduced the ability to catch multiple exception types in a single catch block, further improving exception handling capabilities.

92

# Create custom exception classes for specific error types

* * *

Define custom exception classes to provide more detailed error information.

* * *

The following code shows how to create and use custom exception classes:

< Good Code >

// Good example: Using custom exception classes

// Define custom exception classes

class DatabaseConnectionException extends Exception {}

class QueryExecutionException extends Exception {}

// Function that may throw custom exceptions

function fetchUserData($userId) {

    try {

        // Simulate database connection

        if (rand(0, 1) == 0) {

            throw new DatabaseConnectionException("Failed to connect to the database.");

        }

        // Simulate query execution

        if (rand(0, 1) == 0) {

            throw new QueryExecutionException("Error executing the user query.");

        }

        // Simulated successful data retrieval

        return "User data for ID: " . $userId;

    } catch (DatabaseConnectionException $e) {

        // Handle database connection error

        error\_log("Database Connection Error: " . $e->getMessage());

        return null;

    } catch (QueryExecutionException $e) {

        // Handle query execution error

        error\_log("Query Execution Error: " . $e->getMessage());

        return null;

    }

}

// Usage

$userData = fetchUserData(123);

if ($userData === null) {

    echo "An error occurred while fetching user data.";

} else {

    echo $userData;

}

<Bad Code>

// Bad example: Not using custom exception classes

function fetchUserData($userId) {

    // Simulate database connection

    if (rand(0, 1) == 0) {

        return "Database connection error";

    }

    // Simulate query execution

    if (rand(0, 1) == 0) {

        return "Query execution error";

    }

    // Simulated successful data retrieval

    return "User data for ID: " . $userId;

}

// Usage

$result = fetchUserData(123);

echo $result;

The good example defines custom exception classes for specific error types (DatabaseConnectionException and QueryExecutionException). This allows for more precise error handling and logging. The function uses these custom exceptions to provide detailed information about what went wrong. The bad example simply returns error strings, making it harder to distinguish between different types of errors and handle them appropriately.

<Memo>

Custom exceptions in PHP can extend the built-in Exception class or any of its subclasses, allowing for a hierarchical structure of exception types.

93

# Use finally blocks for cleanup operations

* * *

Implement finally blocks to ensure resource cleanup, regardless of exceptions.

* * *

The following code demonstrates the use of a finally block for proper file handling in PHP:

< Good Code >

<?php

// Good example: Using a finally block for cleanup

try {

    // Open a file

    $file = fopen('example.txt', 'r');

    // Perform operations on the file

    $content = fread($file, filesize('example.txt'));

    // Process the content

    echo "File content: " . $content;

} catch (Exception $e) {

    // Handle any exceptions

    echo "An error occurred: " . $e->getMessage();

} finally {

    // Ensure the file is closed, regardless of exceptions

    if (isset($file) && is\_resource($file)) {

        fclose($file);

        echo "File closed successfully.";

    }

}

?>

<Bad Code>

<?php

// Bad example: Not using a finally block

$file = fopen('example.txt', 'r');

try {

    // Perform operations on the file

    $content = fread($file, filesize('example.txt'));

    // Process the content

    echo "File content: " . $content;

    // Close the file

    fclose($file);

} catch (Exception $e) {

    // Handle any exceptions

    echo "An error occurred: " . $e->getMessage();

    // Attempt to close the file, but may not always execute

    if (is\_resource($file)) {

        fclose($file);

    }

}

?>

The good code example uses a finally block to ensure that the file is always closed, regardless of whether an exception occurs or not. This prevents resource leaks and follows best practices for resource management.

The bad code example attempts to close the file in both the try and catch blocks, which can lead to duplicate code and potential oversight if the developer forgets to add the cleanup code in all necessary places.

<Memo>

The finally block was introduced in PHP 5.5 and is part of the exception handling mechanism, providing a way to execute code regardless of whether an exception was thrown or caught.

94

# Implement logging in catch blocks for better debugging

* * *

Use logging in catch blocks to record detailed error information for easier debugging and maintenance.

* * *

The following code demonstrates how to implement logging in catch blocks for better error tracking:

< Good Code >

<?php

// Good example: Implementing logging in catch blocks

require\_once 'path/to/log/library.php';

function processUserData($userId) {

    try {

        // Simulate database operation

        $userData = fetchUserDataFromDatabase($userId);

        // Process user data

        $result = performComplexOperation($userData);

        return $result;

    } catch (DatabaseException $e) {

        // Log database-related errors

        Logger::error("Database error occurred: " . $e->getMessage(), \[

            'userId' => $userId,

            'errorCode' => $e->getCode(),

            'stackTrace' => $e->getTraceAsString()

        \]);

        throw $e; // Re-throw the exception if needed

    } catch (Exception $e) {

        // Log general errors

        Logger::error("An unexpected error occurred: " . $e->getMessage(), \[

            'userId' => $userId,

            'errorCode' => $e->getCode(),

            'stackTrace' => $e->getTraceAsString()

        \]);

        throw $e; // Re-throw the exception if needed

    }

}

?>

<Bad Code>

<?php

// Bad example: Not implementing proper logging in catch blocks

function processUserData($userId) {

    try {

        // Simulate database operation

        $userData = fetchUserDataFromDatabase($userId);

        // Process user data

        $result = performComplexOperation($userData);

        return $result;

    } catch (Exception $e) {

        // Poor error handling without proper logging

        echo "An error occurred: " . $e->getMessage();

        return false;

    }

}

?>

The good code example implements detailed logging in the catch blocks, recording important information such as the error message, user ID, error code, and stack trace. This approach aids in debugging and allows for better error tracking and analysis.

The bad code example simply echoes the error message without proper logging, making it difficult to track and debug issues in a production environment.

<Memo>

Many PHP frameworks and applications use logging libraries such as Monolog, which provides a flexible and powerful logging system that can be integrated with various logging backends and services.

95

# Use type-hinting in catch blocks for specific exception handling

* * *

Improve code readability and error handling by using type-hinting in catch blocks to handle specific exceptions.

* * *

The following code demonstrates how to use type-hinting in catch blocks for better exception handling:

< Good Code >

try {

    // Some code that may throw exceptions

    $result = someRiskyOperation();

} catch (InvalidArgumentException $e) {

    // Handle specific InvalidArgumentException

    error\_log("Invalid argument: " . $e->getMessage());

} catch (RuntimeException $e) {

    // Handle specific RuntimeException

    error\_log("Runtime error: " . $e->getMessage());

} catch (Exception $e) {

    // Handle any other exceptions

    error\_log("Unexpected error: " . $e->getMessage());

}

<Bad Code>

try {

    // Some code that may throw exceptions

    $result = someRiskyOperation();

} catch (Exception $e) {

    // Handle all exceptions the same way

    error\_log("An error occurred: " . $e->getMessage());

}

The good code example uses type-hinting in catch blocks to handle specific exceptions separately. This approach allows for more precise error handling and logging. The bad code example catches all exceptions without distinguishing between different types, which may lead to less informative error handling.

<Memo>

PHP 7.1 introduced the ability to catch multiple exception types in a single catch block using the pipe symbol (|).

96

# Create reusable traits for common functionality

* * *

Improve code organization and reusability by creating traits for common functionality shared across multiple classes.

* * *

The following code demonstrates how to create and use a trait for logging functionality:

< Good Code >

// Define a trait for logging functionality

trait Loggable {

    protected function log($message) {

        // Implementation of logging logic

        error\_log("\[" . date('Y-m-d H:i:s') . "\] " . $message);

    }

}

// Use the trait in a class

class UserManager {

    use Loggable;

    public function createUser($username) {

        // User creation logic

        $this->log("User created: " . $username);

    }

}

// Use the trait in another class

class OrderProcessor {

    use Loggable;

    public function processOrder($orderId) {

        // Order processing logic

        $this->log("Order processed: " . $orderId);

    }

}

<Bad Code>

// Duplicate logging functionality in multiple classes

class UserManager {

    protected function log($message) {

        error\_log("\[" . date('Y-m-d H:i:s') . "\] " . $message);

    }

    public function createUser($username) {

        // User creation logic

        $this->log("User created: " . $username);

    }

}

class OrderProcessor {

    protected function log($message) {

        error\_log("\[" . date('Y-m-d H:i:s') . "\] " . $message);

    }

    public function processOrder($orderId) {

        // Order processing logic

        $this->log("Order processed: " . $orderId);

    }

}

The good code example defines a Loggable trait that encapsulates the logging functionality. This trait can be reused in multiple classes, reducing code duplication and improving maintainability. The bad code example repeats the logging logic in each class, leading to code duplication and potential inconsistencies.

<Memo>

Traits were introduced in PHP 5.4 to promote code reuse in single inheritance languages like PHP.

97

# Implement abstract classes for shared behavior in class hierarchies

* * *

Use abstract classes to define common behavior and structure for related classes.

* * *

The following code demonstrates the use of an abstract class to define shared behavior for different types of vehicles.

< Good Code >

// Abstract class for vehicles

abstract class Vehicle {

    protected $brand;

    protected $model;

    // Constructor

    public function \_\_construct($brand, $model) {

        $this->brand = $brand;

        $this->model = $model;

    }

    // Abstract method to be implemented by child classes

    abstract public function getType();

    // Shared method for all vehicles

    public function getInfo() {

        return "This is a " . $this->getType() . " - " . $this->brand . " " . $this->model;

    }

}

// Car class extending Vehicle

class Car extends Vehicle {

    public function getType() {

        return "Car";

    }

}

// Motorcycle class extending Vehicle

class Motorcycle extends Vehicle {

    public function getType() {

        return "Motorcycle";

    }

}

// Usage

$car = new Car("Toyota", "Corolla");

echo $car->getInfo(); // Outputs: This is a Car - Toyota Corolla

$motorcycle = new Motorcycle("Honda", "CBR");

echo $motorcycle->getInfo(); // Outputs: This is a Motorcycle - Honda CBR

<Bad Code>

// No abstract class, repetitive code

class Car {

    private $brand;

    private $model;

    public function \_\_construct($brand, $model) {

        $this->brand = $brand;

        $this->model = $model;

    }

    public function getInfo() {

        return "This is a Car - " . $this->brand . " " . $this->model;

    }

}

class Motorcycle {

    private $brand;

    private $model;

    public function \_\_construct($brand, $model) {

        $this->brand = $brand;

        $this->model = $model;

    }

    public function getInfo() {

        return "This is a Motorcycle - " . $this->brand . " " . $this->model;

    }

}

// Usage

$car = new Car("Toyota", "Corolla");

echo $car->getInfo();

$motorcycle = new Motorcycle("Honda", "CBR");

echo $motorcycle->getInfo();

The good code example uses an abstract class Vehicle to define shared properties and methods. This approach reduces code duplication and enforces a consistent structure across different vehicle types. The getType() method is declared abstract, ensuring that each child class implements it. In contrast, the bad code example repeats similar code in both Car and Motorcycle classes, leading to maintenance issues and violating the DRY (Don't Repeat Yourself) principle.

<Memo>

Abstract classes in PHP were introduced in PHP 5.0, released in July 2004.

98

# Use dependency injection containers for managing object creation

* * *

Implement a dependency injection container to manage object creation and dependencies.

* * *

The following code demonstrates the use of a simple dependency injection container to manage object creation and dependencies.

< Good Code >

// Simple Dependency Injection Container

class Container {

    private $services = \[\];

    public function register($name, $callback) {

        $this->services\[$name\] = $callback;

    }

    public function resolve($name) {

        if (!isset($this->services\[$name\])) {

            throw new Exception("Service not found: $name");

        }

        return call\_user\_func($this->services\[$name\], $this);

    }

}

// Database class

class Database {

    private $connection;

    public function \_\_construct($connection) {

        $this->connection = $connection;

    }

    public function query($sql) {

        // Simulated query execution

        return "Executed query: $sql on connection: $this->connection";

    }

}

// UserRepository class

class UserRepository {

    private $db;

    public function \_\_construct(Database $db) {

        $this->db = $db;

    }

    public function findUser($id) {

        return $this->db->query("SELECT \* FROM users WHERE id = $id");

    }

}

// Set up the container

$container = new Container();

$container->register('database', function($c) {

    return new Database('mysql:host=localhost;dbname=myapp');

});

$container->register('userRepository', function($c) {

    return new UserRepository($c->resolve('database'));

});

// Usage

$userRepo = $container->resolve('userRepository');

echo $userRepo->findUser(1);

<Bad Code>

// No dependency injection, hard-coded dependencies

class Database {

    private $connection;

    public function \_\_construct() {

        $this->connection = 'mysql:host=localhost;dbname=myapp';

    }

    public function query($sql) {

        return "Executed query: $sql on connection: $this->connection";

    }

}

class UserRepository {

    private $db;

    public function \_\_construct() {

        $this->db = new Database();

    }

    public function findUser($id) {

        return $this->db->query("SELECT \* FROM users WHERE id = $id");

    }

}

// Usage

$userRepo = new UserRepository();

echo $userRepo->findUser(1);

The good code example implements a simple dependency injection container that manages object creation and dependencies. This approach allows for better testability, flexibility, and separation of concerns. Dependencies are registered with the container and resolved when needed. In contrast, the bad code example hard-codes dependencies, making the code less flexible and harder to test or modify.

<Memo>

Dependency Injection is a key concept in the SOLID principles of object-oriented design, specifically the Dependency Inversion Principle.

99

# Employ the factory pattern for object instantiation

* * *

The factory pattern is a design pattern that provides an interface for creating objects in a superclass but allows subclasses to alter the type of objects that will be created.

* * *

Using the factory pattern in PHP helps in creating objects without specifying the exact class of the object that will be created. This promotes loose coupling and enhances code readability and maintainability.

< Good Code >

<?php

// Factory interface

interface ShapeFactory {

    public function createShape();

}

// Concrete factory for Circle

class CircleFactory implements ShapeFactory {

    public function createShape() {

        return new Circle();

    }

}

// Concrete factory for Square

class SquareFactory implements ShapeFactory {

    public function createShape() {

        return new Square();

    }

}

// Shape interface

interface Shape {

    public function draw();

}

// Concrete Circle class

class Circle implements Shape {

    public function draw() {

        echo "Drawing a Circle";

    }

}

// Concrete Square class

class Square implements Shape {

    public function draw() {

        echo "Drawing a Square";

    }

}

// Client code

function clientCode(ShapeFactory $factory) {

    $shape = $factory->createShape();

    $shape->draw();

}

// Using the factories

clientCode(new CircleFactory()); // Output: Drawing a Circle

clientCode(new SquareFactory()); // Output: Drawing a Square

?>

<Bad Code>

<?php

// Direct instantiation without factory pattern

class Circle {

    public function draw() {

        echo "Drawing a Circle";

    }

}

class Square {

    public function draw() {

        echo "Drawing a Square";

    }

}

// Client code

$circle = new Circle();

$circle->draw(); // Output: Drawing a Circle

$square = new Square();

$square->draw(); // Output: Drawing a Square

?>

In the good example, the factory pattern is used to create objects, which makes the code more flexible and easier to maintain. The client code does not need to know the exact class of the object it is creating, promoting loose coupling. In the bad example, direct instantiation is used, which makes the code less flexible and harder to maintain as any change in the object creation process would require changes in the client code.

<Memo>

The factory pattern is one of the most commonly used design patterns in object-oriented programming. It is part of the "Gang of Four" design patterns, which were introduced in the book "Design Patterns: Elements of Reusable Object-Oriented Software" by Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides.

100

# Implement the strategy pattern for interchangeable algorithms

* * *

The strategy pattern is a design pattern that enables selecting an algorithm's behavior at runtime. It defines a family of algorithms, encapsulates each one, and makes them interchangeable.

* * *

Using the strategy pattern in PHP allows you to define a family of algorithms, encapsulate each one, and make them interchangeable. This pattern lets the algorithm vary independently from clients that use it, promoting flexibility and code reuse.

< Good Code >

<?php

// Strategy interface

interface PaymentStrategy {

    public function pay($amount);

}

// Concrete strategy for Credit Card payment

class CreditCardPayment implements PaymentStrategy {

    public function pay($amount) {

        echo "Paying $amount using Credit Card";

    }

}

// Concrete strategy for PayPal payment

class PayPalPayment implements PaymentStrategy {

    public function pay($amount) {

        echo "Paying $amount using PayPal";

    }

}

// Context class

class ShoppingCart {

    private $paymentStrategy;

    public function \_\_construct(PaymentStrategy $paymentStrategy) {

        $this->paymentStrategy = $paymentStrategy;

    }

    public function checkout($amount) {

        $this->paymentStrategy->pay($amount);

    }

}

// Client code

$cart = new ShoppingCart(new CreditCardPayment());

$cart->checkout(100); // Output: Paying 100 using Credit Card

$cart = new ShoppingCart(new PayPalPayment());

$cart->checkout(200); // Output: Paying 200 using PayPal

?>

<Bad Code>

<?php

// Direct implementation without strategy pattern

class ShoppingCart {

    public function checkout($amount, $paymentType) {

        if ($paymentType == 'credit\_card') {

            echo "Paying $amount using Credit Card";

        } elseif ($paymentType == 'paypal') {

            echo "Paying $amount using PayPal";

        }

    }

}

// Client code

$cart = new ShoppingCart();

$cart->checkout(100, 'credit\_card'); // Output: Paying 100 using Credit Card

$cart->checkout(200, 'paypal'); // Output: Paying 200 using PayPal

?>

In the good example, the strategy pattern is used to encapsulate the payment algorithms, making them interchangeable and promoting code reuse. The context class (ShoppingCart) is not aware of the specific payment method being used, which makes the code more flexible and easier to maintain. In the bad example, the payment logic is hardcoded within the checkout method, making it less flexible and harder to maintain as any change in the payment logic would require changes in the ShoppingCart class.

<Memo>

The strategy pattern is also part of the "Gang of Four" design patterns. It is particularly useful in scenarios where multiple algorithms are applicable to a problem, and the best algorithm to use might vary depending on the context.

101

# Use the observer pattern for loose coupling between objects

* * *

Implement the observer pattern to create a flexible system where objects can subscribe to and receive updates from a subject without tight coupling.

* * *

The following code demonstrates the implementation of the observer pattern in PHP, showing a Subject class and an Observer interface.

< Good Code >

// Subject class

class Newsletter {

    private $observers = \[\];

    private $content;

    // Method to attach an observer

    public function attach(Subscriber $observer) {

        $this->observers\[\] = $observer;

    }

    // Method to set content and notify observers

    public function setContent($content) {

        $this->content = $content;

        $this->notify();

    }

    // Method to notify all observers

    private function notify() {

        foreach ($this->observers as $observer) {

            $observer->update($this->content);

        }

    }

}

// Observer interface

interface Subscriber {

    public function update($content);

}

// Concrete observer

class EmailSubscriber implements Subscriber {

    private $email;

    public function \_\_construct($email) {

        $this->email = $email;

    }

    public function update($content) {

        // Send email with new content

        echo "Sending email to {$this->email} with content: {$content}\\n";

    }

}

// Usage

$newsletter = new Newsletter();

$subscriber1 = new EmailSubscriber("user1@example.com");

$subscriber2 = new EmailSubscriber("user2@example.com");

$newsletter->attach($subscriber1);

$newsletter->attach($subscriber2);

$newsletter->setContent("New article published!");

<Bad Code>

class Newsletter {

    public $subscribers = \[\];

    public $content;

    function addSubscriber($email) {

        $this->subscribers\[\] = $email;

    }

    function setContent($c) {

        $this->content = $c;

        $this->sendEmails();

    }

    function sendEmails() {

        foreach ($this->subscribers as $s) {

            // Directly send email here

            echo "Sending to $s: $this->content\\n";

        }

    }

}

$n = new Newsletter();

$n->addSubscriber("user1@example.com");

$n->addSubscriber("user2@example.com");

$n->setContent("New article!");

The good code example implements the observer pattern correctly. It defines a Subject (Newsletter) and an Observer interface (Subscriber). The Newsletter class manages a list of observers and notifies them when the content changes. The EmailSubscriber class implements the Subscriber interface and handles the update. This approach allows for loose coupling and easy extension.

The bad code example doesn't use the observer pattern. It directly manages subscribers as email addresses and sends emails within the Newsletter class. This approach tightly couples the notification logic with the Newsletter class, making it harder to extend or modify the system.

<Memo>

The observer pattern is one of the behavioral design patterns and is also known as the publish-subscribe pattern. It's widely used in event-driven programming and graphical user interface (GUI) frameworks.

102

# Implement the decorator pattern for dynamic behavior addition

* * *

Use the decorator pattern to add new behaviors to objects dynamically without altering their structure.

* * *

The following code demonstrates the implementation of the decorator pattern in PHP, showing a base component and decorators that add functionality.

< Good Code >

// Component interface

interface Coffee {

    public function getCost();

    public function getDescription();

}

// Concrete component

class SimpleCoffee implements Coffee {

    public function getCost() {

        return 10;

    }

    public function getDescription() {

        return "Simple Coffee";

    }

}

// Base decorator

abstract class CoffeeDecorator implements Coffee {

    protected $decoratedCoffee;

    public function \_\_construct(Coffee $coffee) {

        $this->decoratedCoffee = $coffee;

    }

    public function getCost() {

        return $this->decoratedCoffee->getCost();

    }

    public function getDescription() {

        return $this->decoratedCoffee->getDescription();

    }

}

// Concrete decorators

class Milk extends CoffeeDecorator {

    public function getCost() {

        return $this->decoratedCoffee->getCost() + 2;

    }

    public function getDescription() {

        return $this->decoratedCoffee->getDescription() . ", Milk";

    }

}

class Sugar extends CoffeeDecorator {

    public function getCost() {

        return $this->decoratedCoffee->getCost() + 1;

    }

    public function getDescription() {

        return $this->decoratedCoffee->getDescription() . ", Sugar";

    }

}

// Usage

$coffee = new SimpleCoffee();

echo $coffee->getDescription() . " costs $" . $coffee->getCost() . "\\n";

$coffee = new Milk($coffee);

echo $coffee->getDescription() . " costs $" . $coffee->getCost() . "\\n";

$coffee = new Sugar($coffee);

echo $coffee->getDescription() . " costs $" . $coffee->getCost() . "\\n";

<Bad Code>

class Coffee {

    public $cost = 10;

    public $description = "Simple Coffee";

    public function addMilk() {

        $this->cost += 2;

        $this->description .= ", Milk";

    }

    public function addSugar() {

        $this->cost += 1;

        $this->description .= ", Sugar";

    }

    public function getInfo() {

        echo "$this->description costs $$this->cost\\n";

    }

}

$coffee = new Coffee();

$coffee->getInfo();

$coffee->addMilk();

$coffee->getInfo();

$coffee->addSugar();

$coffee->getInfo();

The good code example properly implements the decorator pattern. It defines a Coffee interface, a base SimpleCoffee class, and decorator classes (Milk and Sugar) that wrap and extend the functionality of the coffee object. This approach allows for flexible combination of decorators and easy addition of new decorators without modifying existing code.

The bad code example doesn't use the decorator pattern. Instead, it modifies the Coffee class directly with methods to add ingredients. This approach violates the Open/Closed Principle as adding new features requires modifying the existing Coffee class. It's less flexible and harder to maintain or extend.

<Memo>

The decorator pattern is a structural design pattern that allows behavior to be added to individual objects, either statically or dynamically, without affecting the behavior of other objects from the same class. It's often used to comply with the Single Responsibility Principle, as it allows functionality to be divided between classes with unique areas of concern.

Afterword

◆

Thank you for embarking on this journey through the world of PHP programming with me.

As you've discovered, this book is more than just a collection of coding techniques—it's a roadmap to crafting PHP code that speaks clearly to both machines and fellow developers.

Throughout these pages, we've explored 100 unique ways to elevate your PHP code from functional to exceptional.

We've delved into PHP-specific features and best practices, always with the goal of creating code that's not just effective, but a joy for others to read and maintain.

I hope you found the contrasting examples of good and bad code illuminating.

There's often a fine line between code that works and code that works beautifully, and I trust these illustrations have helped sharpen your discernment.

Now, I have a small favor to ask.

Your thoughts on this book are invaluable to me.

Whether you found it revolutionary or merely useful, challenging or straightforward, I want to hear from you.

Your feedback shapes the future of my writing and helps me better serve the PHP community.

If you can spare a moment, please consider leaving a review.

Share what resonated with you, what you'd like to see more of, or even what fell short of your expectations.

Don't worry if you're pressed for time—even a simple star rating would be deeply appreciated.

I read every single review, and your insights often spark ideas for future works.

Perhaps you have suggestions for topics you'd like to see covered? I'm all ears! Your voice plays a crucial role in shaping the resources available to PHP developers worldwide.

Remember, whether you found the book helpful, entertaining, disappointing, or difficult to read—your honest opinion matters.

It's through your feedback that we can collectively push the boundaries of what it means to write truly readable PHP code.

Thank you for your time, your trust, and your dedication to the craft of coding.

Here's to cleaner, more elegant PHP—and to the next time our paths cross in the vast landscape of programming literature.

Until then, happy coding!

## Working with PHP Object-Oriented Programming

To illustrate how directly defined class methods override trait methods, copy the block of code mentioned in step 9 into a separate file, `chap_04_oop_trait_methods_do_not_override_class_methods.php`. Add these lines of code:

```php
$customer = new Customer();
$customer->setId(100);
$customer->setName('Fred');
var_dump($customer);
```

As you can see from the following output, the `$id` property is stored as an integer, as defined in the Customer class, whereas the trait defines `$id` as an instance of `stdClass`:

```
Terminal
class Customer#1 (2) {
  protected $name =>
  string(4) "Fred"
  public $id =>
  int(100)
}

--------------
(program exited with code: 0)
Press return to continue
```

In step 10, you learned how to resolve duplicate method name conflicts when using multiple traits. Copy the block of code shown in step 11 into a separate file, `chap_04_oop_trait_multiple.php`. Add the following code:

```php
$a = new Test();
$a->setId(100);
$a->setName('Fred');
$a->setKey();
var_dump($a);

$a->setKeyDate();
var_dump($a);
```

Notice in the following output that `setKey()` yields the output produced from the new PHP 7 function, `random_bytes()` (defined in `NameTrait`), whereas `setKeyDate()` produces a key using the `date()` and `rand()` functions (defined in `IdTrait`):

![Output of trait multiple example](img/39390f6d56c5a83b28db083a8bd5185c_144_0.png)

## Implementing anonymous classes

PHP 7 introduced a new feature, **anonymous classes**. Much like anonymous functions, anonymous classes can be defined as part of an expression, creating a class that has no name. Anonymous classes are used in situations where you need to create an object *on the fly*, which is used and then discarded.

### How to do it…

1.  An alternative to `stdClass` is to define an anonymous class.

    In the definition, you can define any properties and methods (including magic methods). In this example, we define an anonymous class with two properties and a magic method, `__construct()`:

    ```php
    $a = new class (123.45, 'TEST') {
        public $total = 0;
        public $test = '';
        public function __construct($total, $test)
        {
            $this->total = $total;
            $this->test = $test;
        }
    };
    ```

2.  An anonymous class can extend any class.

    In this example, an anonymous class extends `FilterIterator`, and overrides both the `__construct()` and `accept()` methods. As an argument, it accepts `ArrayIterator $b`, which represents an array of 10 to 100 in increments of 10. The second argument serves as a limit on the output:

    ```php
    $b = new ArrayIterator(range(10, 100, 10));
    $f = new class ($b, 50) extends FilterIterator {
        public $limit = 0;
        public function __construct($iterator, $limit)
        {
            $this->limit = $limit;
            parent::__construct($iterator);
        }
        public function accept()
        {
            return ($this->current() <= $this->limit);
        }
    };
    ```

3.  An anonymous class can implement an interface.

    In this example, an anonymous class is used to generate an HTML color code chart. The class implements the built-in PHP `Countable` interface. A `count()` method is defined, which is called when this class is used with a method or function that requires `Countable`:

    ```php
    define('MAX_COLORS', 256 ** 3);

    $d = new class () implements Countable {
        public $current = 0;
        public $maxRows = 16;
        public $maxCols = 64;

        public function cycle()
        {
            $row = '';
            $max = $this->maxRows * $this->maxCols;
            for ($x = 0; $x < $this->maxRows; $x++) {
                $row .= '<tr>';
                for ($y = 0; $y < $this->maxCols; $y++) {
                    $row .= sprintf(
                        '<td style="background-color: #%06X">',
                        $this->current);
                    $row .= sprintf(
                        'title="#%06X">&nbsp;</td>',
                        $this->current);
                    $this->current++;
                    $this->current = ($this->current > MAX_COLORS) ? 0 : $this->current;
                }
                $row .= '</tr>';
            }
            return $row;
        }

        public function count()
        {
            return MAX_COLORS;
        }
    };
    ```

4.  Anonymous classes can use traits.

5.  This last example is a modification from the preceding one defined immediately. Instead of defining a class `Test`, we define an anonymous class instead:

    ```php
    $a = new class {
        use IdTrait, NameTrait {
            NameTrait::setKey insteadof IdTrait;
            IdTrait::setKey as setKeyDate;
        }
    };
    ```

### How it works...

In an anonymous class, you can define any properties or methods. Using the preceding example, you could define an anonymous class that accepts constructor arguments, and where you can access properties. Place the code described in step 2 into a test script `chap_04_oop_anonymous_class.php`. Add these `echo` statements:

```php
echo "\nAnonymous Class\n";
echo $a->total . PHP_EOL;
echo $a->test . PHP_EOL;
```

Here is the output from the anonymous class:

![Output of anonymous class](img/39390f6d56c5a83b28db083a8bd5185c_147_0.png)

In order to use *FilterIterator* you *must* override the `accept()` method. In this method, you define criteria for which elements of the iteration are to be included as output. Go ahead now and add the code shown in step 4 to the test script. You can then add these `echo` statements to test the anonymous class:

```php
echo "\nAnonymous Class Extends FilterIterator\n";
foreach ($f as $item) echo $item . ' ';
echo PHP_EOL;
```

In this example, a limit of 50 is established. The original `ArrayIterator` contains an array of values, 10 to 100, in increments of 10, as seen in the following output:

![Output of FilterIterator](img/39390f6d56c5a83b28db083a8bd5185c_148_0.png)

To have a look at an anonymous class that implements an interface, consider the example shown in steps 5 and 6. Place this code in a file, `chap_04_oop_anonymous_class_interfaces.php`.

Next, add code that lets you paginate through the HTML color chart:

```php
$$_->current = $_GET['current'] ?? 0;
$$_->current = hexdec($$_->current);
$factor = ($$_->maxRows * $$_->maxCols);
$next = $$_->current + $factor;
$prev = $$_->current - $factor;
$next = ($next < MAX_COLORS) ? $next : MAX_COLORS - $factor;
$prev = ($prev > 0) ? $prev : 0;
$next = sprintf('%06X', $next);
$prev = sprintf('%06X', $prev);
?>
```

Finally, go ahead and present the HTML color chart as a web page:

```html
<h1>Total Possible Color Combinations: <?= count($$); ?></h1>
<hr>
<table>
<?= $$_->cycle(); ?>
</table>
<a href="?current=<?= $prev ?>">PREV</a>
<a href="?current=<?= $next ?>">NEXT</a>
```

Notice that you can take advantage of the `Countable` interface by passing the instance of the anonymous class into the `count()` function (shown between `<H1>` tags). Here is the output shown in a browser window:

![Browser output of color chart](img/39390f6d56c5a83b28db083a8bd5185c_149_0.png)

Lastly, to illustrate the use of traits in anonymous classes, copy the `chap_04_oop_trait_multiple.php` file mentioned in the previous recipe to a new file, `chap_04_oop_trait_anonymous_class.php`. Remove the definition of the `Test` class, and replace it with an anonymous class:

```php
$a = new class() {
    use IdTrait, NameTrait {
        NameTrait::setKey insteadof IdTrait;
        IdTrait::setKey as setKeyDate;
    }
};
```

Remove this line:

```php
$a = new Test();
```

When you run the code, you will see exactly the same output as shown in the preceding screenshot, except that the class reference will be anonymous:

![Output of trait anonymous class](img/39390f6d56c5a83b28db083a8bd5185c_150_0.png)

# # 5 Interacting with a Database

In this chapter, we will cover the following topics:

-   Using PDO to connect to a database
-   Building an OOP SQL query builder
-   Handling pagination
-   Defining entities to match database tables
-   Tying entity classes to RDBMS queries
-   Embedding secondary lookups into query results
-   Implementing jQuery DataTables PHP lookups

## Introduction

In this chapter, we will cover a series of database connectivity recipes that take advantage of the **PHP Data Objects (PDO)** extension. Common programming problems such as **Structured Query Language (SQL)** generation, pagination, and tying objects to database tables, will be addressed. Finally, at the end, we will present code that processes secondary lookups in the form of embedded anonymous functions, and using jQuery DataTables to make AJAX requests.

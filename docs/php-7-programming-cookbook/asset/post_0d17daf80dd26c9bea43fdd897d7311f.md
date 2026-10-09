
## How to do it...

In this example we build on the library of iterator-based functions, adding a generator of our own design. In this case we will duplicate the functionality described in the section above on iterators where we stacked an `ArrayIterator`, `FilterIterator`, and `LimitIterator`.

Because we need access to the source array, the desired filter, page number, and number of items per page, we include the appropriate parameters into a single `filteredResultsGenerator()` function. We then calculate the offset based on the page number and limit (that is, number of items per page). Next, we loop through the array, apply the filter, and continue the loop if the offset has not yet been reached, or break if the limit has been reached:

```php
function filteredResultsGenerator(array $array, $filter, $limit = 10, $page = 0)
{
    $max    = count ($array);
    $offset = $page * $limit;

    foreach ($array as $key => $value) {
        if (!strpos($value, $filter) !== FALSE) continue;
        if (--$offset >= 0) continue;
        if (--$limit <= 0) break;
        yield $value;
    }
}
```

You'll notice the primary difference between this function and others is the **yield** keyword. The effect of this keyword is to signal the PHP engine to produce a Generator instance and encapsulate the code.

## How it works...

To demonstrate the use of the `filteredResultsGenerator()` function we'll have you implement a web application that scans a web page and produces a filtered and paginated list of URLs hoovered from `HREF` attributes.

First you need to add the code for the `filteredResultsGenerator()` function to the library file used in the previous recipe, then place the functions described previously into an include file, `chap_03_developing_functions_iterators_library.php`.

Next, define a test script, `chap_03_developing_functions_using_generator.php`, that includes both the function library as well as the file that defines `Application\Web\Hoover`, described in *Chapter 1, Building a Foundation*:

```php
include ( _DIR_ , DIRECTORY_SEPARATOR . 'chap_03_developing_functions_iterators_library.php');
include ( _DIR_ . '/../Application/Web/Hover.php');
```

You will then need to gather input from the user regarding which URL to scan, what string to use as a filter, how many items per page, and the current page number.

> The **null coalesce** operator (??) is ideal for getting input from the Web. It does not generate any notices if not defined. If the parameter is not received from user input, you can supply a default.

```php
$url    = trim(strip_tags($_GET['url'] ?? ''));
$filter = trim(strip_tags($_GET['filter'] ?? ''));
$limit  = (int) ($_GET['limit'] ?? 10);
$page   = (int) ($_GET['page'] ?? 0);
```

> **Best practice**
>
> Web security should always be a priority consideration. In this example you can use `strip_tags()` and also force the data type to integer (`int`) as measures to sanitize user input.

You are then in a position to define variables used in links for previous and next pages in the paginated list. Note that you could also apply a *sanity check* to make sure the next page doesn't go off the end of the result set. For the sake of brevity, such a sanity check was not applied in this example:

```php
$next   = $page + 1;
$prev   = $page - 1;
$base   = '?url=' . htmlspecialchars($url)
         . '&filter=' . htmlspecialchars($filter)
         . '&limit=' . $limit
         . '&page=';
```

We then need to create an `Application\Web\Hover` instance and grab `HREF` attributes from the target URL:

```php
$vac   = new Application\Web\Hover();
$list  = $vac->getAttribute($url, 'href');
```

Finally, we define HTML output that renders an input form and runs our generator through the htmlList() function described previously:

```html
<form>
  <table>
    <tr>
      <th>URL</th>
      <td>
        <input type="text" name="url"
          value="<?= htmlspecialchars($url) ?>"/>
      </td>
    </tr>
    <tr>
      <th>Filter</th>
      <td>
        <input type="text" name="filter"
          value="<?= htmlspecialchars($filter) ?>"/>
      </td>
    </tr>
    <tr>
      <th>Limit</th>
      <td>
        <input type="text" name="limit" value="<?= $limit ?>"/>
      </td>
    </tr>
    <tr>
      <th>&nbsp;</th>
      <td>
        <input type="submit" />
      </td>
    </tr>
    <tr>
      <td>&nbsp;</td>
      <td>
        <a href="<?= $base . $prev ?>">&lt;- PREV |
        <a href="<?= $base . $next ?>">NEXT --></td>
    </tr>
  </table>
</form>
<hr>
<?= htmlList(filteredResultsGenerator(
  $list, $filter, $limit, $page)); ?>
```

Here is an example of the output:

![](img/39390f6d56c5a83b28db083a8bd5185c_101_0.png)

# 4 Working with PHP Object-Oriented Programming

In this chapter we will cover:

- Developing classes
- Extending classes
- Using static properties and methods
- Using namespaces
- Defining visibility
- Using interfaces
- Using traits
- Implementing anonymous classes

## Introduction

In this chapter, we will consider recipes that take advantage of the **object-oriented programming (OOP)** capabilities available in PHP 7.0, 7.1, and above. Most of the OOP functionality available in PHP 7.x is also available in PHP 5.6. A new feature introduced in PHP 7 is support for **anonymous classes**. In PHP 7.1, you can modify the visibility of class constants.

Another radically new feature is the ability to **catch** certain types of error. This is discussed in greater detail in *Chapter 13, Best Practices, Testing, and Debugging*.

## Developing classes

The traditional development approach is to place the class into its own file. Typically, classes contain logic that implements a single purpose. Classes are further broken down into self-contained functions which are referred to as **methods**. Variables defined inside classes are referred to as **properties**. It is recommended to develop a test class at the same time, a topic discussed in more detail in *Chapter 13, Best Practices, Testing, and Debugging*.

### How to do it...

1. Create a file to contain the class definition. For the purposes of autoloading it is recommended that the filename match the classname. At the top of the file, before the keyword *class*, add a **DocBlock**. You can then define properties and methods. In this example, we define a class *Test*. It has a property `$test`, and a method `getTest()`:

```php
<?php
declare(strict_types=1);
/**
 * This is a demonstration class.
 *
 * The purpose of this class is to get and set
 * a protected property $test
 */
class Test
{

    protected $test = 'TEST';

    /**
     * This method returns the current value of $test
     *
     * @return string $test
     */
    public function getTest(): string
    {
        return $this->test;
    }
}
```

```php
/**
 * This method sets the value of $test
 *
 * @param string $test
 * @return Test $this
 */
public function setTest(string $test)
{
    $this->test = $test;
    return $this;
}
```

**Best practice**

It is considered best practice to name the file after the class. Although class names in PHP are not case sensitive, it is further considered best practice to use an uppercase letter for the first name of a class. You should not put executable code in a class definition file.

Each class should contain a **DocBlock** before the keyword class. In the DocBlock you should include a short description of the purpose of the class. Skip a line, and then include a more detailed description. You can also include @tags such as @author, @license and so on. Each method should likewise be preceded by a DocBlock that identifies the purpose of the method, as well as its incoming parameters and return value.

2. It's possible to define more than one class per file, but is not considered best practice. In this example we create a file, NameAddress.php, which defines two classes, Name and Address:

```php
<?php
declare (strict_types=1);
class Name
{
    protected $name = '';

    public function getName() : string
    {
        return $this->name;
    }

    public function setName(string $name)
    {

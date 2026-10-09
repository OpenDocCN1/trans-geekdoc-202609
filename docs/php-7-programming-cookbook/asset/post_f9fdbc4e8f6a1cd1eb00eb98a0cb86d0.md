
10. We could then define a simple function to display output, and call each iterator in turn to see the results on a simple array produced by range('A', 'Z'):

```php
function showElements($iterator)
{
    foreach($iterator as $item) echo $item . ' ';
    echo PHP_EOL;
}
$a = range('A', 'Z');
$i = new ArrayIterator($a);
showElements($i);
```

11. Here is a variation that produces every other letter by stacking a FilterIterator on top of an ArrayIterator:

```php
$f = new class ($i) extends FilterIterator {
    public function accept()
    {
        $current = $this->current();
        return !(ord($current) & 1);
    }
};
showElements($f);
```

12. And here's yet another variation that only produces F H J L N P, which demonstrates a LimitIterator that consumes a FilterIterator, which in turn consumes an ArrayIterator. The output of these three examples is as follows:

```php
$l = new LimitIterator($f, 2, 6);
showElements($l);
```

![](img/39390f6d56c5a83b28db083a8bd5185c_92_0.png)

13. Returning to our example that produces a list of country names, suppose, instead of only the country name, we wished to iterate through a multi-dimensional array consisting of country names and ISO codes. The simple iterators mentioned so far would not be sufficient. Instead, we will use ones that are known as **recursive** iterators.

14. First of all, we need to define a method that uses the database connection class mentioned previously to pull all columns from the database. As before, we return an ArrayIterator instance populated with data from the query:

```php
function fetchAllAssoc($sql, $connection)
{
    $iterator = new ArrayIterator();
    $stmt = $connection->pdo->query($sql);
    while($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
        $iterator->append($row);
    }
    return $iterator;
}
```

15. At first glance one would be tempted to simply wrap a standard ArrayIterator instance inside RecursiveArrayIterator. Unfortunately, this approach only performs a **shallow** iteration, and doesn't give us what we want: an iteration through all elements of the multi-dimensional array that is returned from a database query:

```php
$iterator = fetchAllAssoc($sql, $connection);
$shallow = new RecursiveArrayIterator($iterator);
```

16. Although this returns an iteration where each item represents a row from the database query, in this case we wish to provide an iteration that will iterate through all columns of all rows returned by the query. In order to accomplish this, we'll need to roll out the big brass by way of a RecursiveIteratorIterator.

17. Monty Python fans will revel in the rich irony of this class name as it brings back fond memories of the *The Department of Redundancy Department*. Fittingly, this class causes our old friend the RecursiveArrayIterator class to work overtime and perform a **deep** iteration through all levels of the array:

```php
$deep = new RecursiveIteratorIterator($shallow);
```

## How it works...

As a practical example, you can develop a test script which implements filtering and pagination using iterators. For this illustration, you could call the `chap_03_developing_functions_filtered_and_paginated.php` test code file.

First of all, following best practices, place the functions described above into an include file called `chap_03_developing_functions_iterators_library.php`. In the test script, be sure to include this file.

The data source is a table called iso_country_codes, which contains ISO2, ISO3, and country names. The database connection could be in a config/db.config.php file. You could also include the Application\Database\Connection class discussed in the previous chapter:

```php
define('DB_CONFIG_FILE', '/../config/db.config.php');
define('ITEMS_PER_PAGE', [5, 10, 15, 20]);
include ( __DIR__ . '/chap_03_developing_functions_iterators_library.php');
include ( __DIR__ . '/../Application/Database/Connection.php');
```

![](img/39390f6d56c5a83b28db083a8bd5185c_94_0.png)

Next, you can process input parameters for the country name and the number of items per page. The current page number will start at 0 and can be incremented (next page) or decremented (previous page):

```php
$name   = strip_tags($_GET['name'] ?? '');
$limit  = (int) ($_GET['limit'] ?? 10);
$page   = (int) ($_GET['page'] ?? 0);
$offset = $page * $limit;
$prev   = ($page > 0) ? $page - 1 : 0;
$next   = $page + 1;
```

Now you're ready to fire up the database connection and run a simple SELECT query. This should be placed in a try {} catch {} block. You can then place the iterators to be stacked inside the try {} block:

```php
try {
    $connection = new Application\Database\Connection(
        include __DIR__ . DB_CONFIG_FILE);
    $sql        = 'SELECT * FROM iso_country_codes';
    $arrayIterator = fetchCountryName($sql, $connection);
    $filteredIterator = nameFilterIterator($arrayIterator, $name);
    $limitIterator = pagination(
        $filteredIterator, $offset, $limit);
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

Now we're ready for the HTML. In this simple example we present a form that lets the user select the number of items per page and the country name:

```html
<form>
    Country Name:
<input type="text" name="name"
             value="<?= htmlespecialchars($name) ?>">
Items Per Page:
<select name="limit">
    <?php foreach (ITEMS_PER_PAGE as $item) : ?>
        <option<?= ($item == $limit) ? ' selected' : ' ?>>
            <?= $item ?></option>
    <?php endforeach; ?>
</select>
<input type="submit" />
</form>
<a href="?name=<?= $name ?>&limit=<?= $limit ?>
           &page=<?= $prev ?>">
    &lt; PREV</a>
<a href="?name=<?= $name ?>&limit=<?= $limit ?>
           &page=<?= $next ?>">
    NEXT &gt;</a>
<?= htmlList($limitIterator); ?>
```

The output will look something like this:

![](img/39390f6d56c5a83b28db083a8bd5185c_95_0.png)

Finally, in order to test the recursive iteration of the country database lookup, you will need to include the iterator's library file, as well as the Application\Database\Connection class:

```php
define('DB_CONFIG_FILE', '../config/db.config.php');
include (__DIR__ . '/chap_03_developing_functions_iterators_library.php');
include (__DIR__ . '/Application/Database/Connection.php');
```

As before, you should wrap your database query in a try { } catch { } block. You can then place the code to test the recursive iteration inside the try { } block:

```php
try {
    $connection = new Application\Database\Connection(
        include __DIR__ . DB_CONFIG_FILE);
    $sql    = 'SELECT * FROM iso_country_codes';
    $iterator = fetchAllAssoc($sql, $connection);
    $shallow = new RecursiveArrayIterator($iterator);
    foreach ($shallow as $item) var_dump($item);
    $deep    = new RecursiveIteratorIterator($shallow);
    foreach ($deep as $item) var_dump($item);
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

Here is what you can expect to see in terms of output from RecursiveArrayIterator:

![](img/39390f6d56c5a83b28db083a8bd5185c_96_0.png)

Here is the output after using *RecursiveIteratorIterator*:

![](img/39390f6d56c5a83b28db083a8bd5185c_97_0.png)

## Writing your own iterator using generators

In the preceding set of recipes we demonstrated the use of iterators provided in the PHP 7 SPL. But what if this set doesn't provide you with what is needed for a given project? One solution would be to develop a function that, instead of building an array that is then returned, uses the yield keyword to return values progressively by way of iteration. Such a function is referred to as a *generator*. In fact, in the background, the PHP engine will automatically convert your function into a special built-in class called *Generator*.

There are several advantages to this approach. The main benefit is seen when you have a large container to traverse (that is, parsing a massive file). The traditional approach has been to build up an array, and then return that array. The problem with this is that you are effectively doubling the amount of memory required! Also, performance is affected in that results are only achieved once the final array has been returned.

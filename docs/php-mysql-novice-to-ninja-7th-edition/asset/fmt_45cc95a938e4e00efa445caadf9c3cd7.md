
```php
public function getJokes() {
  $jokeCategories = $this->jokeCategoriesTable->find('categoryId', $this->id);

  $jokes = [];

  foreach ($jokeCategories as $jokeCategory) {
    $joke =  $this->jokesTable->find('id', $jokeCategory->jokeId)[0] ?? null;
    if ($joke) {
      $jokes[] = $joke;
    }           
  }

  usort($jokes, [$this, 'sortJokes']);

  return $jokes;
}

private function sortJokes($a, $b) {
  $aDate = new \DateTime($a->jokedate);
  $bDate = new \DateTime($b->jokedate);

  if ($aDate->getTimestamp() == $bDate->getTimestamp()) {
    return 0;
  }

  return $aDate->getTimestamp() > $bDate->getTimestamp() ? -1 : 1;
}
```

## Sorting Jokes with usort

There’s a lot going on here, so I’ll go through it line by line. Firstly, the `$jokes` array is sorted using the `usort` function: `usort($jokes, [$this, 'sortJokes'])`. To call a method in a class, rather than just a function, you can use an array containing the object you want to call the method on (in our case, the same instance, `$this`) and the name of the method to be called (`sortJokes`).

The `sortJokes` method starts by converting the dates from each of the `$a` and `$b` objects into `\DateTime` instances for easier comparison. The `getTimestamp` method returns a Unix timestamp—the number of seconds between January 1, 1970, and the date being represented. Using timestamps allows us to compare the dates as integers.

The `if` statement checks to see if the dates have the same timestamp. If so, it returns `0`, indicating that neither should be moved before or after the other in the sorted list.

If the dates are different, either `1` or `-1` is returned to sort the dates. Notice I’ve used `$a > $b`, which will sort the array in the opposite order to the example, and put the larger timestamps (later dates) first.

There’s a slight performance overhead in using `usort` instead of `ORDER BY` and having the database perform the sort, but unless you’re dealing with thousands of records, the difference between the two will be milliseconds at worst!

### Pagination with `LIMIT` and `OFFSET`

Now that you know how to sort the records, we can think a little about scalability. You’ve probably got fewer than a dozen jokes in your database at the moment. What will happen after the website has been online a few months and is starting to get popular? You might get users coming on and posting hundreds of jokes a day.

It won’t take long before the joke list page takes a very long time to load, because it’s displaying hundreds or thousands of jokes. The performance alone will put users off, but nobody is going to sit and read through a page of two thousand jokes.

A common approach is using **pagination** to display a sensible number—for example, ten jokes per page—and allow clicking a link to move between pages.

Before you continue, add at least 21 jokes to your database so we can test this correctly. Alternatively, for testing purposes, change `10` in the following sections to `2` to display two jokes per page.

#### What If I Don’t Know any Jokes?

Don’t worry if you can’t think of any jokes. Just add some test data like “joke one”, “joke two”, “joke three”, and so on.

Our first task is to display just the first ten jokes. Using SQL, this is incredibly easy. The `LIMIT` clause can be appended to any `SELECT` query to restrict the number of records returned:

```
SELECT * FROM `joke` ORDER BY `jokedate DESC` LIMIT 10
```

We’ll need to build this into the `findAll` and `find` methods of the `DatabaseTable` class as optional parameters, as we did with the `$orderBy` variable:

```
public function find(string $column, string $value, string $orderBy = null, int $limit = 0) {
    $query = 'SELECT * FROM `' . $this->table . '` WHERE `' . $column . '` = :value';

    $values = [
      'value' => $value
    ];

    if ($orderBy != null) {
      $query .= ' ORDER BY ' . $orderBy;
    }

    if ($limit > 0) {
        $query .= ' LIMIT ' . $limit;
    }

    $stmt = $this->pdo->prepare($query);
    $stmt->execute($values);

    return $stmt->fetchAll(\PDO::FETCH_CLASS | \PDO::FETCH_PROPS_LATE, $this->className, $this->constructorArgs);
}

public function findAll(string $orderBy = null, int $limit = 0) {
    $query = 'SELECT * FROM ' . $this->table;

    if ($orderBy != null) {
        $query .= ' ORDER BY ' . $orderBy;
    }

    if ($limit > 0) {
        $query .= ' LIMIT ' . $limit;
    }

    $stmt = $this->pdo->prepare($query);
    $stmt->execute();

    return $stmt->fetchAll(\PDO::FETCH_CLASS | \PDO::FETCH_PROPS_LATE, $this->className, $this->constructorArgs);
}
```

Then, to limit to ten jokes, open up the `Joke` controller class and provide the value `10` for the new `$limit` argument:

```
$jokes = $this->jokesTable->findAll('jokedate DESC', 10);
```

Also supply the new limit in the `Category` entity class:

```
$jokeCategories = $this->jokeCategoriesTable->find('categoryId', $this->id, null, 10);
```

You’ll notice I’ve supplied `null` for the `$orderBy` argument. Even though the argument is optional, to provide a value for `$limit`, a value for all the earlier arguments must be provided. However, as of PHP 8, named parameters can be used like so:

```
$jokeCategories = $this->jokeCategoriesTable->find(column: 'categoryId', 
                                                   value: $this->id, 
                                                   limit: 10);
```

With that in place, you’ll see only ten jokes on the joke list page. The problem now is how we’ll view the rest of the jokes!

The solution is to have different pages that can be accessed by a URL argument: `/joke/list/1/1` would view page `1` in the category with the ID `1`, or `/joke/list/1/2` to select which page 1 of category 2. We already have the first argument set up and working, so we just need to apply the second. However, what if we want to display page 2 of all jokes? To do that, we’ll need to use an identifier that isn’t a valid category ID, such as `all`, so that `/joke/list/all/3` is page 3 of all jokes.

Before that, let’s create the links in the template. We can easily use a `for` loop to display a set of links to different pages. The following code will display links to pages 1–10 in the `all` category:

```
for ($i = 1; $i <= 10; $i++) {
  echo '<a href="/joke/list/all/' . $i . '">' . $i . '</a>';    
}
```

The problem is, we need to know how many pages there will be. It’s actually very easy to work out. If we’re displaying ten jokes per page, the number of pages is the number of jokes in the database divided by ten, and then rounded up.

With 21 jokes in the system, `21/10` is `2.1`, and if we round up, it gives `3` pages (two pages of ten and a final page with just one joke). PHP’s `ceil` function can be used to round up any decimal number.

The template already has access to the `$totalJokes` variable, so we can display the pages at the end of `jokes.html.php`:

```
// …
<?php endif; ?>
</blockquote>
<?php endforeach; ?>

Select page:

<?php
// Calculate the number of pages
$numPages = ceil($totalJokes/10);

// Display a link for each page
for ($i = 1; $i <= $numPages; $i++):
?>
  <a href="/joke/list/all/<?=$i?>"><?=$i?></a>
<?php endfor; ?>

</div>
```

If you click the links, the second URL argument will be set. It’s now just a matter of using it to display different sets of jokes.

The SQL clause `OFFSET` can be used with `LIMIT` to do exactly what we want:

```
SELECT * FROM `joke` ORDER BY `jokedate` LIMIT 10 OFFSET 10
```

This query will return ten jokes, but instead of returning the *first* ten jokes, it will display ten jokes starting from joke ten.

We’ll need to turn page numbers into offsets. Page `1` will be `OFFSET 0`, page `2` will be `OFFSET 10`, page `3` will be `OFFSET 20`, and so on. This is a simple calculation: `$offset = ($page - 1) * 10`.

As we did with `limit`, let’s add `OFFSET` as an optional argument for the `findAll` and `find` methods:

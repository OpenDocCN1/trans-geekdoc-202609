
# Dynamic INSERT with PDO

## Building the Query

This will generate the first part of the query, and `$query` will store the following:

```
INSERT INTO `joke` (`authorId`, `:jokedate`, `joketext`) VALUES (
```

… when called with this array:

```
[
    'authorId' => 4,
    'joketext' => '!false - it\'s funny because it\'s true'
    'jokedate' = '2021-04-22'
]
```

The next part of the query should be the placeholders for the values:

```
VALUES (:authorId, :joketext)
```

These are the keys prefixed with a colon (`:`). Once again, we can use `foreach` to loop through the column names and add the placeholders before sending the query to the database:

```
function insertJoke($pdo, $values) {
    $query = 'INSERT INTO `joke` (';

    foreach ($values as $key => $value) {
        $query .= '`' . $key . '`,';
    }

    $query = rtrim($query, ',');

    $query .= ') VALUES (';

    foreach ($values as $key => $value) {
        $query .= ':' . $key . ',';
    }

    $query = rtrim($query, ',');

    $query .= ')';

    $stmt = $pdo->prepare($query);

    $stmt->execute($values);

}
```

## Using insertJoke

The `insertJoke` function can now be used to insert a joke using an array specifying which value will be placed in which column:

```
insertJoke($pdo, [
    'authorId' => 4,
    'joketext' => '!false - it\'s funny because it\'s true',
    'jokedate' = '2021-04-22'
    ]
);
```

Of course, it will cause an error if the wrong column names are used, but it’s clearer to anyone seeing this code which data is being placed into each of the columns. As we’ll see later, it also makes it easier to use the function with forms.

For now, amend your website to use the two new functions by replacing the existing ones in `DatabaseFunctions.php`. Then amend `editjoke.php` to use the new `updateJoke` function:

```
updateJoke($pdo, [
    'id' => $_POST['jokeid'],
    'joketext' => $_POST['joketext'],
    'authorId' => 1
]);
```

Finally, amend `addjoke.php` to use the new function.

[Structure2-ArrayFunctions-Error](https://github.com/spbooks/phpmysql7/tree/Structure2-ArrayFunctions-Error)

```
insertJoke($pdo, [
                    'authorId' => 1, 
                    'joketext' => $_POST['joketext'],
                    'jokedate' => date('Y-m-d')
            ]
 );
```

## Handling Dates

You might be wondering how you could set a specific date, rather than the current date, when inserting a date into the database.

Previously, we used the `date()` function. Using the new `insertJoke` function, you may attempt to set the joke like so:

```
insertJoke($pdo, ['authorId' => 1,
    'jokeText' => $_POST['joketext'],
    'jokedate' =>  date('Y-m-d')
]);
```

The `date()` function is simple and easy to use when we want to use the system date, but if we want to easily set a specific date, we can use a different tool. The PHP `DateTime` class can be used to represent dates in PHP and format them in any way. For example:

```
$date = new DateTime();

echo $date->format('d/m/Y H:i:s');
```

Like the simpler `date()` function, by default a new instance of `DateTime` (without a provided argument) will represent today’s date, and the string in the `format` method is the same as the format used in the `date()` function you’re already familiar with. If you were reading this on September 8, 2021 at around 7.00 p.m., this would print something like this:

```
08/09/2021 19:12:34
```

The biggest advantage of the `DateTime` class over the `date()` function is that you can give it a string that represents any date and have it convert it to a different date format. For example:

```
$date = new DateTime('5th March 2021');

echo $date->format('d/m/Y');
```

The string `d/m/Y` here represents day/month/year, which would print `05/03/2021`. The PHP `DateTime` class is very powerful and incredibly useful for handling dates in PHP. A full list of the available methods of formatting a date is available [in the PHP manual](http://php.net/manual/en/function.date.php).

The `DateTime` class can be used to represent any date and time. Today’s date could be induced in this format, like so:

```
// Don't give it a date so it uses the current date/time
$date = new DateTime();

echo $date->format('Y-m-d H:i:s');
```

The above will print something like this:

```
2021-09-08 19:16:34
```

This is the format that’s needed when you insert into a `DATETIME` field in MySQL.

The `insertJoke` function can already handle this. We can just pass the current date as one of the array keys to the function:

```
$date = new DateTime();

insertJoke($pdo, [
    'authorId' => 4,
    'joketext' => 'Why did the chicken cross the road? To get to the other side',
    'jokedate' => $date->format('Y-m-d H:i:s')
    ]
);
```

This will work fine. However, this isn’t really any different from just using the `date()` function, and every time we want to use the function, we need to remember the date format used by MySQL. This can be a bit of a pain, as it requires repeating the code for formatting the date (and remembering the string `Y-m-d H:i:s`) each time a date needs to be inserted.

Instead, a better approach would be to have the function format the date for us, saving some work each time it’s called:

```
function insertJoke($pdo, $values) {
    $query = 'INSERT INTO `joke` (';

    foreach ($values as $key => $value) {
        $query .= '`' . $key . '`,';
    }

    $query = rtrim($query, ',');

    $query .= ') VALUES (';

    foreach ($values as $key => $value) {
        $query .= ':' . $key . ',';
    }

    $query = rtrim($query, ',');

    $query .= ')';

    foreach ($values as $key => $value) {
        if ($value instanceof DateTime) {
            $values[$key] = $value->format('Y-m-d');
        }
    }

        $stmt = $pdo->prepare($query);

        $stmt->execute($values);
}
```

Using the above version of the function, a date `object` can be passed into the function without formatting it:

```
insertJoke($pdo, [
    'authorId' => 4,
    'joketext' => '!false - it\'s funny because it\'s true',
    'jokedate' =>  new DateTime()
    ]
);
```

The function will look for any date objects it’s been given and automatically format them to the format needed by MySQL. When the function is called, you don’t need to remember the exact format needed by MySQL; it’s done for you inside the function. The function will automatically convert any `DateTime` object it comes across into a string that MySQL can understand:

```
// Loop through the array of fields
foreach ($values as $key => $value) {
    // If any of the values are a DateTime object
    if ($value instanceof DateTime) {
        // Then replace the value in the array with the date in the format
        // Y-m-d H:i:s
        $values[$key] = $value->format('Y-m-d H:i:s');
    }
}
```

One operator you haven’t come across yet is the `instanceof` operator. This is a comparison operator like `==` or `!=`. However, instead of checking to see if the two values are the *same*, it checks to see whether the variable on the left (`$value`) is the same kind of object as the one on the right (`DateTime`). One important distinction is that the *value* is not being checked, only the *type*. It’s like saying “Is it a car?” rather than “Is it an E-Type Jaguar?”

Wherever a `DateTime` object is found in the array, it’s replaced with the equivalent date string in the format MySQL needs. This allows us to completely forget about the format MySQL actually needs and just supply `DateTime` objects to the `insertJoke` function.

With this code in place, if we wanted to specify a date to be set in the database, we could do it like so:

```
insertJoke($pdo, [
        'authorId' => 4,
        'joketext' => '!false - it\'s funny because it\'s true',
        'jokedate' =>  new DateTime('5th September 2021')
        ]
);
```

The `insertJoke` function will see the `DateTime` instance and automatically convert it to the format MySQL uses.

Let’s also add the automatic date formatting to the `updateJoke` function:

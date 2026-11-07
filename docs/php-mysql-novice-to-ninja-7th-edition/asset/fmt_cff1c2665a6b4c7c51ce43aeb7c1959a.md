
# Result Set Fetching and Template Rendering

Rows of a result set returned by `fetch` are represented as associative arrays, with the indices named after the table columns in the result set. If `$row` is a row in our result set, `$row['joketext']` is the value in the `joketext` column of that row.

Our goal in this code is to store away the text of all the jokes so that we can display them in a PHP template. The best way to do this is to store each joke as a new item in an array, `$jokes`:

```
while ($row = $result->fetch()) {
  $jokes[] = $row['joketext'];
}
```

With the jokes pulled out of the database, we can now pass them along to a PHP template `jokes.html.php`.

## Controller Code

To summarize, here’s the code of the controller for this example so far:

```
<?php

try {
    $pdo = new PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');

    $sql = 'SELECT `joketext` FROM `joke`';
    $result = $pdo->query($sql);

    while ($row = $result->fetch()) {
        $jokes[] = $row['joketext'];
    }
} catch (PDOException $e) {
    $error = 'Unable to connect to the database server: ' . $e->getMessage() . ' in ' .
  $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/jokes.html.php';
```

The `$jokes` variable is an array that stores a list of jokes. If you wrote out the contents of the array in PHP, it would look something like this:

```
$jokes = [];
$jokes[0] = 'A programmer was found dead in the shower. The instructions read: lather, rinse, repeat.';
$jokes[1] = '!false - it\'s funny because it\'s true';
$jokes[2] = 'A programmer\'s wife tells him to go to the store and "get a gallon of milk, and if they have eggs, get a dozen." He returns with 13 gallons of milk.';
```

However, the data has been retrieved from the database rather than being typed out manually in the code.

You’ll have noticed that there are two different variables being set—`$jokes` and `$error`—depending on whether or not the `try` block executed successfully.

## Template Rendering

In the `jokes.html.php` template, we need to display the contents of the `$jokes` array or the error message contained in the `$error` variable.

To check whether or not a variable has been assigned a value, we can use the `isset` function that we used earlier for checking if a form has been submitted. The template can include an `if` statement to determine whether to display the error or the list of jokes:

```
if (isset($error)) {
  ?>
  <p>
  <?php
  echo $error;
  ?>
  </p>
}
else {
  : display the jokes
}
```

There’s nothing new here, but to display the jokes, we need to display the contents of the `$jokes` array. Unlike other variables we’ve used up to this point, the `$jokes` array contains more than just a single value.

The most common way to process an array in PHP is to use a loop. We’ve already seen `while` loops and `for` loops. The `foreach` loop is particularly helpful for processing arrays:

```
foreach (array as $item) {
  ⋮ process each $item
}
```

Instead of a condition, the parentheses at the top of a `foreach` loop contain an array, followed by the keyword `as`, and then the name of a new variable that will be used to store each item of the array in turn. The body of the loop is then executed once for each item in the array. Each time that item is stored in the specified variable, so that the code can access it directly.

It’s common to use a `foreach` loop in a PHP template to display each item of an array in turn. Here’s how this might look for our `$jokes` array:

```
<?php
foreach ($jokes as $joke) {
    ?>
  ⋮ HTML code to output each $joke
<?php
}
?>
```

With this blend of PHP code to describe the loop and HTML code to display it, the code looks rather untidy. Because of this, it’s common to use an alternative way of writing the `foreach` loop when it’s used in a template:

```
foreach (array as $item):
  ⋮ process each $item
endforeach;
```

The two pieces of code are functionally identical, but the latter looks more friendly when mixed with HTML code. Here’s how this form of the code looks in a template:

```
<?php foreach ($jokes as $joke): ?>
  ⋮ HTML code to output each $joke
<?php endforeach; ?>
```

The same thing can be done with the `if` statement, making it nicer to look at inside HTML templates by avoiding the braces:

```
<?php if (isset($error)): ?>
  <p>
  <?php echo $error; ?>
  </p>
<?php else: ?>
  : display the jokes
<?php endif; ?>
```

With these new tools in hand, we can write our template to display the list of jokes.

### Example: MySQL-ListJokes

```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>List of jokes</title>
  </head>
  <body>
  <?php if (isset($error)): ?>
  <p>
    <?php echo $error; ?>
  </p>
  <?php else: ?>
  <?php foreach ($jokes as $joke): ?>
  <blockquote>
    <p>
    <?php echo htmlspecialchars($joke, ENT_QUOTES, 'UTF-8') ?>
    </p>
  </blockquote>
  <?php endforeach; ?>
  <?php endif; ?>
  </body>
</html>
```

Either the `$error` text is displayed on the page or each joke is displayed in a paragraph (`<p>`) contained within a block quote (`<blockquote>`), since we’re effectively quoting the author of each joke in this page.

Because jokes might conceivably contain characters that could be interpreted as HTML code (for example, `<`, `>`, or `&`), we must use `htmlspecialchars` to ensure they’re translated into HTML character entities (that is, `&lt;`, `&gt;`, and `&amp;`) so that they’ll be displayed correctly.

The following image shows what this page looks like once you’ve added a couple of jokes to the database.

![A list of jokes from the database](Images/jokelist.png)

### Using foreach with PDOStatement

Remember how we used a `while` loop in our controller to fetch the rows out of the `PDOStatement` result set one at a time?

```
while ($row = $result->fetch()) {
  $jokes[] = $row['joketext'];
}
```

It turns out that `PDOStatement` objects are designed to behave just like arrays when you pass them to a `foreach` loop. You can therefore slightly simplify your database processing code using a `foreach` loop instead of a `while` loop:

```
foreach ($result as $row) {
  $jokes[] = $row['joketext'];
}
```

I’ll be using this tidier `foreach` form in the rest of this book.

### Shorthand Echo Syntax

Another neat tool PHP offers is a shorthand way to call the `echo` command—which, as you’ve already seen, we need to use frequently. Our `echo` statements look like this:

```
<?php echo $variable; ?>
```

Instead, we can use this:

```
<?=$variable?>
```

This does exactly the same thing. `<?=` means `echo` and gives you a slightly shorter way to print variables. There’s a limitation to this, though: if you use `<?=`, you can only print. You can’t include `if` statements, `for` statements, and so on, although you can use concatenation, and it can be followed by a function call.

Here’s an updated template using the shorthand echo.

### Example: MySQL-ListJokes-Shorthand

```
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>List of jokes</title>
  </head>
  <body>
  <?php if (isset($error)): ?>
  <p>
    <?=$error?>
  </p>
  <?php else: ?>
  <?php foreach ($jokes as $joke): ?>
  <blockquote>
    <p>
    <?=htmlspecialchars($joke, ENT_QUOTES, 'UTF-8')?>
    </p>
  </blockquote>
  <?php endforeach; ?>
  <?php endif; ?>
  </body>
</html>
```

I’ll be using the shorthand notation when it’s applicable from this point on.

### Using the Shorthand

In versions of PHP prior to 5.4, this shorthand notation required a fairly uncommon PHP setting to be enabled, so it was discouraged for compatibility reasons. Using the shorthand notation may have caused your code to stop working when moving from a server that had it enabled to one that didn’t.

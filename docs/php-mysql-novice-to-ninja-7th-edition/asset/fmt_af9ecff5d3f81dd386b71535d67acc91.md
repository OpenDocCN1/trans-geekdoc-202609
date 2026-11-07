
You now have functions `getJoke` and `totalJokes`, which can be used anywhere you want to find a specific joke or count the number of jokes in the database. Rather than writing out a query, preparing it, creating a values array and executing the query, you can perform that entire process with a single short line of code, such as `getJoke($pdo, 1)`.

## Using Functions to Replace Queries

The `totalJokes` function allows for easily querying the database for the number of jokes in the table, and the `getJoke` function lets us quickly fetch a joke from the database. Let’s take the same approach and apply it to adding jokes to the database with an `INSERT` query:

```
function insertJoke($pdo, $joketext, $authorId) {
  $stmt = $pdo->prepare('INSERT INTO `joke` (`joketext`, `jokedate`, `authorId`)
      VALUES (:joketext, :jokedate, :authorId)');

  $values = [
    ':joketext' => $joketext, 
    ':authorId' => $authorId,
    ':jokedate' => date('Y-m-d')
  ];

  $stmt->execute($values);
}
```

The `insertJoke` function lets us very quickly insert a record into the `joke` table with a single line of code by providing it the database connection (`$pdo`), the text of the joke (`$joketext`), and the ID of the author (`$authorId`):

```
insertJoke($pdo, 'Why did the programmer quit his job? He didn\'t get arrays', 1);
```

Each of the columns in the database is an argument for the function, which can now be called repeatedly to quickly issue the relevant `INSERT` query with far less code than we’d have needed previously:

```
insertJoke($pdo, 'Why was the empty array stuck outside? It didn\'t have any keys', 1);

insertJoke($pdo, 'An SQL query goes into a bar, walks up to two tables and asks "Can I join you?"', 2);
```

This approach is considerably quicker and easier than having to write all the code for running the query each time you insert a joke: preparing the query, binding the parameters, and then finally executing the query.

Now, finally, you *could* use the following controller code for adding a joke:

```
if (isset($_POST['joketext'])) {
  try {
    include __DIR__ . '/../includes/DatabaseConnection.php';

    $sql = 'INSERT INTO `joke` (`joketext`, `jokedate`, `authorId`)
    VALUES (:joketext, :jokedate, :authorId)';

    $stmt = $pdo->prepare($sql);

    $values = [
      ':joketext' => $_POST['joketext'], 
      ':authorId' => 1,
      ':jokedate' => date('Y-m-d')
    ];

    $stmt->execute($values);

    header('location: jokes.php');
  }
  catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Database error: ' . $e->getMessage() . ' in ' .
    $e->getFile() . ':' . $e->getLine();
  }
}
```

But instead of this, you can put the `insertJoke` and `query` functions in the `DatabaseFunctions.php` file and then write the following much simpler version.

**Example: [Structure-AddJoke](https://github.com/spbooks/phpmysql7/tree/Structure-AddJoke)**

```
if (isset($_POST['joketext'])) {
  try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../includes/DatabaseFunctions.php';

    insertJoke($pdo, $_POST['joketext'], 1);

    header('location: jokes.php');
  }
  catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Database error: ' . $e->getMessage() . ' in ' .
    $e->getFile() . ':' . $e->getLine();
  }
}
```

You can see that I’ve put the `getJoke`, `totalJokes` and `insertJoke` functions into a file called `DatabaseFunctions.php` and included it as required.

For now, all jokes will have `1` set as the `authorId`. Later on, I’ll show you how to handle logins and associate the joke with the currently logged-in user.

## Updating Jokes

Along with inserting a joke, it’s useful to be able to update a record. Perhaps there was a spelling error in one of the jokes and it needs to be changed.

An update function needs more information than the insert function. It needs to know the ID of the record being updated, along with the new values for each column:

```
function updateJoke($pdo, $jokeId, $joketext, $authorId) {
  $stmt = $pdo->prepare('UPDATE `joke` SET 
                           `authorId` = :authorId, 
                           `joketext` = :joketext 
                         WHERE `id` = :id');

  $values = [
    ':joketext' => $joketext,
    ':authorId' => $authorId,
    ':id' => $jokeId
  ];

  $stmt->execute($values);

}
```

The `updateJoke` function can be called anywhere a joke needs to be updated:

```
updateJoke($pdo, 1, '!false - It\'s funny because it\'s true', 1);
```

The line above will update the joke whose ID is `1` with the supplied `authorId` and `jokeText`—the equivalent of running all the following code:

```
$stmt = $pdo->prepare('UPDATE `joke` SET 
                           `authorId` = :authorId, 
                           `joketext` = :joketext 
                         WHERE `id` = :id');

$values = [
  ':joketext' => '!false - It\'s funny because it\'s true',
  ':authorId' => 1,
  ':id' => 1
];

$stmt->execute($values);
```

This is a significant advantage. Anywhere in the code that a joke needs to be updated, the single function call can do it, saving a lot of typing and duplication of effort.

## Editing Jokes on the Website

Let’s make use of our new functions `getJoke` and `updateJoke` by adding a page that allows for editing the existing jokes. In essence, it’s the same as `addjoke.php`. It will display a form, and when the form is submitted it will send the data to the database.

However, there are two main differences:

*   When the edit page loads, it needs to retrieve the current joke text from the database in order to pre-fill the `<textarea>` with the current joke. After all, if it’s a simple typo, you don’t want to make the user re-type the whole joke!
*   When the form is submitted, it needs to run an `UPDATE` query rather than an `INSERT` query.

In the `public` directory, create the `editjoke.php`, which looks like this:

```
<?php
try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../includes/DatabaseFunctions.php';

    if (isset($_POST['joketext'])) {
        updateJoke($pdo, $_POST['jokeid'], $_POST['joketext'], 1);

        header('location: jokes.php');
    } else {
        $joke = getJoke($pdo, $_GET['id']);

        $title = 'Edit joke';

        ob_start();

        include  __DIR__ . '/../templates/editjoke.html.php';

        $output = ob_get_clean();
    }
} catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Database error: ' . $e->getMessage() . ' in ' .
    $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

There are a few main differences between this new `editjoke.php` page and the `addjoke.php` page.

Firstly, you may have noticed that the two include files have been included at the very top of the page. This is so the database functions are available whether or not the form has been submitted.

If the form hasn’t been submitted, we need to query the database for the current joke text. If it has been submitted, we’ll need to run the relevant update query.

Secondly, the `try` statement surrounds the `if` rather than having the `if` surround the `try`. The reason for this is simple: there may be an error in either the `if` or `else` block.

Speaking of the `else` block, that’s the next change. Instead of just loading the form, the `else` block has this line of code:

```
$joke = getJoke($pdo, $_GET['id']);
```

This part of the code selects a joke from the database by its ID, using the `getJoke` function from earlier. The ID of the joke being edited must be supplied using a `GET` variable—so that visiting `editjoke.php?id=4`, for example, will execute the query ``SELECT * FROM `joke` WHERE `id` = 4`` and store the resulting joke in the `$joke` array.

The `$joke` variable can now be used in the corresponding template file `editjoke.html.php`:

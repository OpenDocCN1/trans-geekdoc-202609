
```
public function find($column, $value) {
    $query = 'SELECT * FROM `' . $this->table . '` WHERE `' . $column . '` = :value';

    $values = [
        'value' => $value
    ];

    $stmt = $this->pdo->prepare($query);
    $stmt->execute($values);

    return $stmt->fetchAll(\PDO::FETCH_CLASS | \PDO::FETCH_PROPS_LATE, $this->className, $this->constructorArgs);
}
```

Finally, make the same change in the `findAll` method:

```
public function findAll() {
    $query = 'SELECT * FROM `' . $this->table . '`';

    $stmt = $this->pdo->prepare($query);
    $stmt->execute();

    return $stmt->fetchAll(\PDO::FETCH_CLASS | \PDO::FETCH_PROPS_LATE, $this->className, $this->constructorArgs);
}
```

Now that we’ve amended the `DatabaseTable` class, we can change the `Website` class where the `DatabaseTable` class is instantiated, and provide the class name and the arguments for the `$authorsTable` instance:

```
$this->jokesTable = new \Ninja\DatabaseTable($pdo, 'joke', 'id');
$this->authorsTable = new \Ninja\DatabaseTable($pdo, 'author', 'id', '\Ijdb\Entity\Author', [$this->jokesTable]);
```

With this change in place, when the `$authorsTable` instance is used to retrieve a record, like this:

```
$author = $authorsTable->find('id', 123)[0];
```

… the `$author` variable will be an instance of the `\Ijdb\Entity\Author` class, and any methods in the class (such as `addJoke`) will available for us to call.

As we’ve made a change to the `DatabaseTable` class, this will affect every instance of the class. When jokes are retrieved from the database, an object will also be retrieved. As we haven’t specified an entity class for jokes (yet!), objects returned from the `find` method on the `$jokesTable` instance will be an instance of the generic `stdClass` class.

If you load up the joke list page in your browser, at this point you’ll see this error:

```
Fatal error: uncaught Error: cannot use object of type stdClass as array in /app/classes/Ijdb/Controllers/Joke.php on line 21
```

Because we’ve replaced the arrays with objects, we’ll need to tweak anywhere we read a column from the database. We’ll fix this later, but first let’s get `editSubmit` working. Amend the `editSubmit` method to avoid all the value copying. Remove the following code:

```
public function editSubmit($id = null) {
    $author = $this->authentication->getUser();

    if (!empty($id)) {
      $joke = $this->jokesTable->find('id', $id)[0];

      if ($joke['authorId'] != $author['id']) {
       return;
      }
    }

    $joke = $_POST['joke'];
    $joke['jokedate'] = new \DateTime();
    $joke['authorId'] = $author['id'];

    $this->jokesTable->save($joke);

    header('location: /joke/list');
}
```

Replace it with this:

```
public function editSubmit() {
    $author = $this->authentication->getUser();

    if (!empty($id)) {
      $joke = $this->jokesTable->find('id', $id)[0];

      if ($joke->authorId != $author->id) {
       return;
      }
    }

    $joke = $_POST['joke'];
    $joke['jokedate'] = new \DateTime();

    $author->addJoke($joke);

    header('location: /joke/list');
}
```

This is because `getUser` now returns an instance of `Author` with all the properties already set and containing the `addJoke` method. Rather than manually describing the relationship by manually setting the `authorId`, the relationship is modeled in the `Author` class. I’ve also updated the check inside the second `if` statement to use the object notation for `$joke->authorId` and `$author->id`.

Before we can test that this works, we’ll also need to amend the `Authentication` class to use an object rather than an array. In the `isLoggedIn` method, remove this line:

```
if (!empty($user) && $user[0][$this->passwordColumn] === $_SESSION['password']) {
```

Replace it with this:

```
if (!empty($user) && $user[0]->{$this->passwordColumn} === $_SESSION['password']) {
```

This code looks complicated! However, let’s take a moment to understand what’s happening here.

The `$user[0]` variable now stores an instance of the `Author` class. The `Author` class has a property called `password`. To read this property, you could use this:

```
$user[0]->password
```

However, if you remember back to Chapter 11, you’ll recall that the `Authentication` class has a class variable, which stores the name of the database column that contains the password. It might not be `password` in every website you build.

Assuming the password column *is* `password`, once the variables have been evaluated, all we’re doing here is replacing `$user[0]['password']` with the object variant `$user[0]->password`. But this is complicated by the fact that we’re using a variable for the column name. We really need `$user[0][$this->passwordColumn]` to be replaced with `$user[0]->$this->passwordColumn`.

It’s possible to use a variable to access a property on an object using a string, as we do with an array:

```
$columnName = 'password';

// Read value stored under key 'password' from array
$password = $array[$columnName];

// Read value stored under property 'password' from object
$password = $object->$columnName;
```

Because the column name is stored in the class variable `$this->passwordColumn`, we need to perform something like `$user[0]->$this->passwordColumn`. However, this expression confuses PHP, because the arrow operator is being chained. This will evaluate `$user[0]->$this` first. Starting with `$this`, it will look up the value of `$this` and then look for a property with that name. As `$this` evaluates to an object, not a valid property name, we need to tell PHP to evaluate `$this->passwordColumn` prior to `$user[0]->$this->passwordColumn`.

By including braces around `{this->passwordColumn}` in the expression, PHP will evaluate the `$this->passwordColumn` column first. This is the equivalent of the following:

```
$columnName = $this->passwordColumn;

$user[0]->$columnName;
```

Now that the `isLoggedIn` method is using objects, we can do the same with this line in the `login` method:

```
public function login(string $username, string $password): bool {
    $user = $this->users->find($this->usernameColumn, strtolower($username));

    if (!empty($user) && password_verify($password, $user[0][$this->passwordColumn])) {
        session_regenerate_id();
        $_SESSION['username'] = $username;
        $_SESSION['password'] = $user[0][$this->passwordColumn];
        return true;
    } else {
        return false;
    }
}
```

The `login` method above needs the same modification as the `isLoggedIn` method, changing the array notation to the object notation.

**Example: [Relationships-DatabaseTableEntity](https://github.com/spbooks/phpmysql7/tree/Relationships-DatabaseTableEntity)**

```
public function login(string $username, string $password): bool {
    $user = $this->users->find($this->usernameColumn, strtolower($username));

    if (!empty($user) && password_verify($password, $user[0]->{$this->passwordColumn})) {
        session_regenerate_id();
        $_SESSION['username'] = $username;
        $_SESSION['password'] = $user[0]->{$this->passwordColumn};
        return true;
    } else {
        return false;
    }
}
```

Finally, update the `getUser` method's return value from `?array` to `?object` as the user is now being represented by an `author` object instead of an array.

After submitting the form, you’ll see an error on the list page, but you can check the new `editSubmit` method is working by logging in to the website and adding a joke. When you’re redirected to the list page, you’ll see an error, but you can check that the joke has been added by viewing the contents of the `joke` table in MySQL Workbench.

### Joke Objects

Now we’ll fix the joke list page. At the moment, it displays an error, thanks to this code in the controller:

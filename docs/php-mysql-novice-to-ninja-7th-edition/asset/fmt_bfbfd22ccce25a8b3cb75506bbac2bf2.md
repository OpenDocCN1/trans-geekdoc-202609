
Although it would be possible to create the `Joke` entity instance in the `addJoke` method, it makes more sense to place this functionality in the `DatabaseTable` class. Whenever `save` is called, it can return the relevant entity instance. By placing this logic inside the `save` method, any time any data is written to any database table, the `save` method will return an object representing that newly added record.

The `addJoke` method above should be changed to this:

```
public function addJoke($joke) {

  $joke['authorId'] = $this->id;

  return $this->jokesTable->save($joke);
}
```

This will just return the return value of the `save` method from the `DatabaseTable` class. That is, whatever the `save` method returns to the `addJoke` method will also be returned by the `addJoke` method.

We haven’t looked at the code for this class for a long time, but open up the `DatabaseTable` class and find the `save` method:

```
public function save($record) {
    try {
       if (empty($record[$this->primaryKey]) {
         unset($record[$this->primaryKey]);
       }
       $this->insert($record);
    } catch (PDOException $e) {
       $this->update($record);
    }
}
```

This calls either the `insert` or `update` method. The first thing we need to do here is create an instance of the relevant entity class. For jokes, it will be the `Joke` class; for authors, it will be the `Author` class; and so on.

To create the relevant entity, we can use this code:

```
$entity = new $this->className(...$this->constructorArgs);
```

This looks complicated. There are lots of variables in this line of code. It’s important to understand what’s happening here, so I’ll show you how this works.

The instance is created using `new $this->className`. Importantly, PHP evaluates `$this->className` prior to trying to create an object. If `$this->className` contains `\Ijdb\Entity\Joke`, the code evaluated will be `new \Ijdb\Entity\Joke(...)`.

Then, the `$this->constructorArguments` is unpacked using the *argument unpacking operator* we saw in Chapter 9. This takes the constructor arguments required for an entity instance and converts them into arguments.

Once this code has run, the `$entity` variable will store an object of the type defined in `$this->className`.

This line can be placed inside the `save` method, along with a line to return the newly created entity object:

```
public function save($record) {
  $entity = new $this->className(...$this->constructorArgs);
  try {
     if (empty($record[$this->primaryKey]) {
       unset($record[$this->primaryKey]);
     }
     $this->insert($record);
  } catch (PDOException $e) {
     $this->update($record);
  }

  return $entity;
}
```

With those lines in place, the `save` method will instantiate the relevant, empty entity class. The next stage is writing the data that was sent to the database to the class. This can be done with a simple `foreach`:

```
public function save($record) {
  $entity = new $this->className(...$this->constructorArgs);
  try {
     if (empty($record[$this->primaryKey]) {
       unset($record[$this->primaryKey]);
     }
     $this->insert($record);
  } catch (PDOException $e) {
     $this->update($record);
  }

  foreach ($record as $key => $value) {
    if (!empty($value)) {
      if ($value instanceof \DateTime) {
        $value = $value->format('Y-m-d H:i:s');
      }
      $entity->$key = $value;
    }
  }
  return $entity;
}
```

The important line here is `$entity->$key = $value;`. Each time `foreach` iterates, the `$key` variable is set to the column name—for example, `joketext`—and the `$value` variable is set to the value being written to that column. By using the `$key` variable after the object access operator (`->`), it will write to the property with the name of the column.

The `if (!empty($value))` check is in place to prevent values that are already set on the entity being overwritten with `null`. With this change in place, the `$entity` variable contains a fully constructed object after a record is saved.

Finally, `DateTime` instances are converted back into strings for storing in the entity.

It’s equivalent to manually setting each property on the object like so:

```
$entity->joketext = 'Why did the empty array get stuck outside? It didn\'t have any keys';

$entity->authorId = 1;

$entity->jokedate = '2018-06-22';
```

However, using the generic approach above, the property names and corresponding values come from the `$record` array. Any values in `$record` will be copied into the `$entity` object.

### Converting Arrays to Objects

This approach is a common method of converting an array to an object.

With the `foreach` in place, writing the values to the entity object, the `save` method will return the object with all the values that were passed as an array to the method.

This will work fine for records being updated, as the `$record` variable will include keys for all the columns in the database table.

A newly created record, however, won’t have the primary key set. When a joke is added, we pass the `save` method values for the `joketext`, `jokedate` and `authorId` columns, while the `id` is left blank.

The `id` primary key is actually created by MySQL inside the database. For `INSERT` queries, we’ll need to read the value from the database immediately after the record has been added.

Luckily, the PDO library provides a very simple method of doing this. After an `INSERT` query has been executed by the database, you can call the `lastInsertId` method on the `PDO` instance to read the ID of the last record inserted.

To implement this, let’s amend the `insert` method in our `DatabaseTable` class to return the last insert ID:

```
private function insert($values) {
    $query = 'INSERT INTO `' . $this->table . '` (';

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

    $values = $this->processDates($values);

    $stmt = $this->pdo->prepare($query);
    $stmt->execute($values);

    return $this->pdo->lastInsertId();
}
```

The only amendment here is the final line, returning the last insert ID. Now, the `save` method can read this value and set the primary key on the created entity object:

```
public function save($record) {
  $entity = new $this->className(...$this->constructorArgs);
  try {
     if (empty($record[$this->primaryKey]) {
       unset($record[$this->primaryKey]);
     }
     $insertId = $this->insert($record);

     $entity->{$this->primaryKey} = $insertId;
  } catch (PDOException $e) {
     $this->update($record);
  }

  foreach ($record as $key => $value) {
    if (!empty($value)) {
      if ($value instanceof \DateTime) {
        $value = $value->format('Y-m-d H:i:s');
      }
      $entity->$key = $value;
    }
  }
  return $entity;
}
```

As with the other methods in the `DatabaseTable` class, the name of the primary key column is stored in the `primaryKey` class variable. This column, and the newly generated value, are stored in the entity object. I’ve used the shorthand method with braces to set the primary key, but it’s the same as this:

```
$insertId = $this->insert($record);

$primaryKey = $this->primaryKey;

$entity->$primaryKey = $insertId;
```

The `save` method is now complete. Any time the `save` method is called, it will return an entity instance representing the record that’s just been saved.

### Assigning Categories to Jokes

This functionality is required to enable the `joke` controller to assign categories to a joke instance. We can amend the `editSubmit` method in the `Joke` controller to look like this:

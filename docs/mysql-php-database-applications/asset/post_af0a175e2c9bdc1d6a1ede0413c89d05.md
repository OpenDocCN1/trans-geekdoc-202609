
```
return FALSE;

}

$dbh->setFetchMode(DB_FETCHMODE_ASSOC);
}
return $dbh;
}
```

### build()

This method takes a list or array of arguments and uses them to set values for the properties of the object. We have a couple of points to make here:

- You can use built-in PHP functions to figure out what your objects' property names are at runtime, and use that information to pay attention only to incoming values that match those properties. This enables you do things like:

  $product->build($_POST);
  $style->build($_POST);

  knowing that each object picks out from $_POST only the fields that it needs.

- You can check to see if your class has a method with the same name as the property you've been given a value for. If it does, you can hand that new value off to that method. This capability makes it easier to ensure that only legal values are assigned to an object's properties -- that a $quantity property is never set to a negative number, for example.

```php
function build()
{

$args = func_get_args();
if (count($args) == 0)
{

return;
}

$simple = array_keys(get_object_vars($this));
$p = parse_arguments($args, $simple);
$args = array_key_remove($p, $simple);
foreach ($args as $k => $v)
{

if (method_exists($this, $k))
call_user_func(array($this,$k),$v);
else

$this->$k = $v;

}
}
```

### fetch_simple_query()

This method lives to be overwritten. The default is about as simple as the code here gets. Anticipating the ability of the database to substitute values into the text of a query, it just returns a query getting everything from a table to be named later. The purpose of the method is to allow child classes to substitute less simple queries in their place. Subsequent methods of the Base class can use these queries. Consider a common example: If you have a table that has multiple lookup values, like a product_type_id field, you can use a query that joins your main table with the lookup table and returns the appropriate product_type for storage in a property of the object:

```php
function fetch_simple_query()
{
    return 'select * from !';
}
```

### fetch_simple()

Using this method is another step along the path to retrieving a record from the database and storing it in the object, but fetch_simple() can have other uses as well. The method requires a table name and optionally accepts a field name, a value, and an operator (usually just an equals sign). It runs the query supplied by fetch_simple_query() and returns the result. Normally the table name will be the value from the $table property of the object, but you can also call this method directly, on any table, querying the value of any single field. That lets you do something like

$result = $p->fetch_simple('products','product','S%','like');

to get a DB result handle for all of the rows in the products table wherein the product name begins with s. If nothing else, it saves typing.

Notice that you can use the result of the dbh() method as if it were a property. Because it returns an object of the DB class (one of DB's subclasses, to be exact), it has its own properties and methods you can use, as shown in this example in which we populate an array with pieces of what will become (thanks to the dbh() function) a database query:

```php
function fetch_simple($table,$idfield=NULL,$id=NULL,$op='=')
{
    $result = FALSE;
    $bind = array($table);
    $query = $this->fetch_simple_query();
    if ($idfield !== NULL)
    {
        $query .= ' where ! ! ?';
        $bind[] = $idfield;
        $bind[] = nullop($id,$op);
    }

    $bind[] = $id;
}
$result = $this->dbh()->query($query,$bind);
return $result;
}
```

### fetch_record()

This method uses fetch_simple() to get a single record from a table in the database and return it:

```php
function fetch_record($table=NULL,$idfield=NULL,$id=NULL)
{
    if (empty($table))
        $table = $this->table;
    if (empty($idfield))
        $idfield = $this->idfield;
    if (empty($id))
        $id = $this->id;
    $result = $this->fetch_simple($table,$idfield,$id);
    if (!$result)
    {
        return FALSE;
    }
    $row = $result->fetchRow();
    $result->free();
    return $row;
}
```

### fetch_from_db()

Finally, we come to the method you'll see most frequently used in the actual child classes that work with a particular table. This method enables you to get the record corresponding to a supplied unique ID value, or the ID value already specified by the id property of your object, and to assign the values from that record to the properties of your object using the building-block methods described in the beginning of the section on object-orientation in this chapter:

```php
function fetch_from_db($id=NULL)
{
    if ($id !== NULL)
    {
        $this->id = $id;
    }
    $row = $this->fetch_record(
        $this->table
        , $this->idfield
        , $this->id
    );
    if (!$row)
        return FALSE;
    $this->build($row);
}
```

### fetch_all()

This is just a shortcut method for getting all the records from a table that match a particular field value. In practice, using DB's getAll() method is about as easy.

```php
function fetch_all($table=NULL,$idfield=NULL,$id=NULL,$op='=')
{
    if (empty($table)) { $table = $this->table; }
    $result = $this->fetch_simple($table,$idfield,$id,$op);
    if (!$result)
    {
        return FALSE;
    }
    $rows = array();
    while ($row = $result->fetchRow())
    {
        $rows[$row[$this->idfield]] = $row;
    }
    $result->free();
    return $rows;
}
```

### delete_from_db()

This method deletes a record from the database:

```php
function delete_from_db($id=NULL)
{
    if ($id == NULL)
    {
        $id = $this->id;
    }
    $result = $this->dbh()->query(
        'delete from ! where ! = ?',
        array($this->table, $this->idfield, $id)
    );
    return $result;
}
```

### fieldlist()

Now we begin building up to the other main purpose of a class, writing its values to the database. This method hands back a list of fields that, in theory, correspond to the fields of the table the object represents. If the list is not predefined—as it generally is—the method gets a list of fields from the database. (Note that this is a very MySQL-specific query in that it uses the MySQL reserved word describe.)

```php
function fieldlist()
{
    if (is_array($this->fields) && count($this->fields) > 0)
    {
        return $this->fields;
    }
    if ($this->dbh() && $this->table)
    {
        $this->fields = $this->dbh()->getCol(
            "describe ({$this->table})"
        );
        return $this->fields;
    }
    return NULL;
}
```

### data_fields()

You might have a table with 25 fields defined, but use only three of them in a form. When you write the record out to the database you don't want to unwittingly change the other 22 fields. This method returns an associative array of field names and values built from the properties of the object, leaving out properties that are NULL or set to empty strings when the corresponding fields in the table are integers:

```php
function data_fields()
{
    $fields = array();
    foreach ($this->fieldlist() as $f)
    {
        if (!isset($this->$f))
            continue;
        $v = $this->$f;
        if ($v == NULL)
            continue;
        if ($v == '' && strstr($f, '_id'))
            continue;
        $fields[$f] = $v;
    }
    return $fields;
}
```

### create_record()

This method inserts into the database a new record corresponding to the value stored in the properties of the object. It uses the PEAR DB class' nextId() function to get the next ID value for the table (rather than letting MySQL automatically assign it—though in practice PEAR itself is using MySQL's auto_increment feature to come up with the new ID value). Generating ID values is dead simple thanks to DB's autoPrepare() method, which takes a table name and an array of column names and values and gives you back a fully-baked insert query.

```php
function create_record()
{
    if ($this->what)
        $this->id = $this->dbh()->nextId($this->what);
    $data_fields = $this->data_fields();
    $stmt = $this->dbh()->autoPrepare(
        $this->table
        , array_keys($data_fields)
        , DB_AUTOQUERY_INSERT
    );
    $result = $this->dbh()->execute(
        $stmt
        , array_values($data_fields)
    );
    return $result;
}
```

### update_record()

This method updates the record in the database that corresponds to the current object, as indicated by the unique ID value in the $id property. Once again, DB makes it easy.

```php
function update_record()
{
    $data_fields = $this->data_fields();
    $stmt = $this->dbh()->autoPrepare(
        $this->table
        , array_keys($data_fields)
        , DB_AUTOQUERY_UPDATE
        , ' ! = ? '
    );
    $bind = array_values($data_fields);
    $bind[] = $this->idfield;
    $bind[] = $this->id;
    $result = $this->dbh()->execute($stmt,$bind);
    return $result;
}
```


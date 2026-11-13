create_record() This method inserts into the database a new record corresponding to the value stored in the properties of the object. It uses the PEAR DB class' nextId() function to get the next ID value for the table (rather than letting MySQL automatically assign it—though in practice PEAR itself is using MySQL's auto_increment feature to come up with the new ID value). Generating ID values is dead simple thanks to DB's autoPrepare() method, which takes a table name and an array of column names and values and gives you back a fully-baked insert query.

```
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

update_record() This method updates the record in the database that corresponds to the current object, as indicated by the unique ID value in the $id property. Once again, DB makes it easy.

```
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
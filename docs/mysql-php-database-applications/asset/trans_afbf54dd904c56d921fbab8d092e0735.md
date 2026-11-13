

```
return FALSE;

}

$dbh->setFetchMode(DB_FETCHMODE_ASSOC);
}
return $dbh;
}
```

### build()

这个方法接受参数列表或数组，并用它们来设置对象属性的值。这里有几点要说明：

- 你可以使用 PHP 内置函数来确定运行时对象的属性名称，并利用这些信息只关注与这些属性匹配的传入值。这样你可以做类似这样的事情：

  $product->build($_POST);
  $style->build($_POST);

  要知道每个对象只从 $_POST 中选取它需要的字段。

- 你可以检查你的类是否有一个与你赋值的属性同名的方法。如果有，你可以将这个新值交给那个方法。这种能力使得更容易确保只将合法值分配给对象的属性——例如，$quantity 属性永远不会被设置为负数。

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

这个方法生来就是为了被重写。默认实现大致就是这里展示的这么简单。预期数据库能够将值替换到查询文本中，它只是返回一个从稍后命名的表中获取所有内容的查询。这个方法的目的是允许子类用不那么简单的查询来替换它们。Base 类的后续方法可以使用这些查询。考虑一个常见的例子：如果你有一个表包含多个查找值，比如 product_type_id 字段，你可以使用一个查询将主表与查找表连接起来，并返回适合存储在对象属性中的 product_type：

```php
function fetch_simple_query()
{
    return 'select * from !';
}
```

### fetch_simple()

使用这个方法是从数据库检索记录并将其存储到对象路径上的又一步，但 fetch_simple() 也可以有其他用途。该方法需要一个表名称，并且可选地接受一个字段名、一个值和一个操作符（通常只是等号）。它运行由 fetch_simple_query() 提供的查询并返回结果。通常表名称将是对象 $table 属性的值，但你也可以直接在任何表上调用此方法，查询任何单个字段的值。这样你可以做类似这样的事

$result = $p->fetch_simple('products','product','S%','like');

来获取 products 表中所有产品名称以 s 开头的行的 DB 结果句柄。如果没有其他好处，至少省去了输入。

请注意，你可以将 dbh() 方法的结果当作属性来使用。因为它返回一个 DB 类的对象（确切说是 DB 的一个子类），它具有你可以使用的自己的属性和方法，如以下示例所示，我们用将要变成（多亏了 dbh() 函数）数据库查询的片段填充一个数组：

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

这个方法使用 fetch_simple() 从数据库中的表中获取单条记录并返回它：

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

最后，我们来看你在实际处理特定表的子类中最常见的方法。这个方法使你能够获取与提供的唯一 ID 值（或你的对象的 id 属性中已指定的 ID 值）对应的记录，并使用本章面向对象部分开头描述的构建块方法将该记录中的值分配给你对象的属性：

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

这只是一个快捷方法，用于获取表中与特定字段值匹配的所有记录。实际上，使用 DB 的 getAll() 方法也差不多容易。

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

这个方法从数据库中删除一条记录：

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

现在我们开始构建类的另一个主要目的：将值写入数据库。这个方法返回一个字段列表，理论上这些字段与对象所代表的表的字段对应。如果列表不是预定义的（通常也是如此），该方法从数据库获取字段列表。（请注意，这是一个非常特定于 MySQL 的查询，因为它使用了 MySQL 保留字 describe。）

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

你可能有一个定义了 25 个字段的表，但在表单中只使用其中三个。当你将记录写入数据库时，你不想无意中更改其他 22 个字段。这个方法返回从对象的属性构建的字段名和值的关联数组，排除那些为 NULL 或设置为空字符串的属性，前提是表中对应的字段是整数：

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

这个方法将对象属性中存储的值作为新记录插入数据库。它使用 PEAR DB 类的 nextId() 函数获取表的下一个 ID 值（而不是让 MySQL 自动分配——尽管在实践中 PEAR 本身正在使用 MySQL 的 auto_increment 功能来生成新的 ID 值）。由于 DB 的 autoPrepare() 方法，生成 ID 值非常简单，该方法接受表名和列名及值的数组，并给你返回一个完全成型的插入查询。

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

这个方法更新数据库中与当前对象对应的记录，由 $id 属性中的唯一 ID 值指示。同样，DB 让这变得很容易。

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


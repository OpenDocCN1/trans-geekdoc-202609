


$error_level = E_USER_ERROR;
user_error(
    "Database error - please contact the system administrator.",
    $error_level
);

## db_fetch_record()

此函数提供了一种从表中获取单条或多条记录的便捷方式。它使用了 DB 的标记替换系统，这只是一个花哨的说法，意为“占位符”。例如，您可以像这样使用 DB 运行查询：

```
$result = $dbh->query('select * from mytable where mykey = 1');
```

但是，您也可以向 DB::query() 传入两个参数：查询字符串本身，以及一个用于替换到字符串中的值数组：

```
$result = $dbh->query(
    'select * from mytable where mykey = ?'
    , array($mykey)
);
```

查询字符串中的标记字符 ? 告诉 DB 应使用参数数组中某个值的内容来替换它。如果查询字符串中有两个 ? 字符，它会在数组中查找两个值，以此类推。这非常好的一点在于——除了让您无需为要在查询中包含的每组新值构建新的查询字符串（这可不是件小事）——DB 会为您处理引号和转义字符。例如，这样的语句：

```
$mykey = 1;
$myname = "O'Reilly";
$result = $dbh->query(
    'select * from mytable where mykey = ? and myname = ?'
    , array($mykey, $myname)
);
```

将导致 MySQL 运行以下查询：

```
select * from mytable where mykey = 1 and myname = 'O\'Reilly'
```

虽然本书主要关于 PHP 和 MySQL，但值得注意的是，DB 可用于多种多样的数据库，并为每种数据库处理正确的引号和转义语法。如果您曾经不得不将代码（例如从 Sybase 或 PostgreSQL）移植到 MySQL，您就能体会到这一功能有多么宝贵。

您还可以使用 ! 标记字符替换查询中的文本部分，如下所示：

```
$mykey = 1;
$myname = "O'Reilly";
$result = $dbh->query(
    'select * from mytable where mykey = ? and ! = ?'
    , array($mykey, 'myname', $myname)
);
```

DB 将 ! 字符解释为指示它应该按原样放置参数列表中的相应值，而不加引号，因此您可以动态更改所查询的表或列的名称。您可能会想，看这个示例，为什么要将字符串 'myname' 放在参数列表中，而最初直接将其写入查询不是更简单吗？这只是为了表明，您不局限于在参数数组中使用变量。

DB 甚至会使用 & 标记字符为您获取整个文件的内容，如下所示：

```
$dbh->query(
    'insert into myfiles (filename, filecontents) values (?, &)'
    , array('my file', 'myfile.txt')
);
```

现在我们已经更多地了解了 DB 能为我们做什么，请看在 db_fetch_record() 函数中使用它的示例：

```
function db_fetch_record()
{
    static $_defaults = array(
        'table' => NULL
    ,   'key' => NULL
    ,   'value' => NULL
    ,   'columns' => ' *'
    ,   'extra' => NULL
    ,   'key_op' => '='
    ,   'key_join' => ' and '
    ,   'order_by' => NULL
    );
    static $_simple = array('table', 'key', 'value');
    $args = func_get_args();
    extract($_defaults);
    $p = parse_arguments($args, $_simple, $_defaults);
    extract($p, EXTR_IF_EXISTS);

    $query = 'select ! from !';
    $bind = array($columns, $table);
    $where = NULL;
    if (!empty($key) && !empty($value))
    {
        $where .= implode($key_join, array_fill(0, count($key), "! $key_op ?"));
        if (is_array($key) && is_array($value))
        {
            foreach ($key as $i => $k)
            {
                $bind[] = $k;
                $bind[] = $value[$i];
            }
        }
        else
        {
            $bind[] = $key;
            $bind[] = $value;
        }
    }
    if ($extra)
    {
        if ($where)
        {
            $where = " ($where) and ";
        }
        $where .= " ($extra) ";
    }
    if ($where)
    {
        $query .= ' where '.$where;
    }
    $order_by = (array)$order_by;
    if (count($order_by) > 0)
    {
        $query .= ' order by '.implode(',',$order_by);
    }
    $result = db_connect()->getAll($query, $bind,
    DB_FETCHMODE_ASSOC);
    if (!$result)
    {
        $private_error = 'could not fetch record: '
            . ' query=' . $query
            . ' bind=' . $bind
            . ' result=' . $result
            ;
        user_error("Could not fetch $table record", E_USER_ERROR);
        exit;
    }
    if (count($result) == 1)
    {
        $result = array_shift($result);
    }
    return $result;
}
```

如果结果数据集只有一行，则直接返回该行。否则，返回整个数据集。在这两种情况下，常量 DB_FETCHMODE_ASSOC（由 DB 库定义）告诉 DB::getAll() 方法将每行数据作为关联数组返回，以查询中的列名为键。

## db_values_array()

db_values_array() 函数与 db_fetch_record() 类似，它是编写完整查询的简写。不过，在此情况下，始终返回一个值列表，并假设特定的表结构：即表名是标签列名的复数形式，而键列名是标签列名加上 _id。您可以将这些假设的更正作为参数传递给函数（我们代码中的一个常见示例：状态查找表的名称通常是 'status'，而不是 'statuss'）。

```
function db_values_array ()
{
    static $_defaults = array(
        'label' => NULL
        , 'table' => NULL
        , 'value' => NULL
        , 'sort' => NULL
        , 'where' => NULL
    );
    static $_simple = array('label','table');
    $p = func_get_args();
    extract($_defaults);
    $p = parse_arguments($p, $_simple, $_defaults);
    extract($p, EXTR_IF_EXISTS);

    if (empty($label))
    {
        $label = str_replace('_id','',$value);
    }
    elseif (empty($value))
    {
        $value = $label.'_id';
    }
    if (empty($table))
    {
        $table = $label.'s';
    }
    if (empty($sort))
    {
        $sort = $label;
    }
    if (empty($where))
    {
        $where = '1=1';
    }

    $output = db_connect()->getAssoc(
        'select !.! from ! where ! order by !'
        , FALSE
        , array($value,$label,$table,$where,$sort)
    );
    return $output;
}
```

db_values_array() 最常见的用途是从数据库表中生成一个值列表，用于 SELECT 字段或一组选项字段（单选按钮或复选框）。

## nullop()

nullop() 函数在被检查的值等于 NULL 时返回 "is" 或 "is not"，否则返回 "=" 或 "<>"。我们使用 <> 而不是 !=，因为 ! 字符在 DB 代码中有特殊含义（参见前一章中描述的 db_fetch_record() 函数）：

```
function nullop($value=NULL,$op='=')
{
    if ($value === NULL)
    {
        if (strstr($op,'!='))
        {
            $op = 'is not';
        }
        else
        {
            $op = 'is';
        }
    }
    else
    {
        if (strstr($op, '!='))
        {
            $op = '<>';
        }
    }
    return $op;
}
```

## /content/functions 中的函数

这些函数将在整个应用程序中使用。本节将包含许多对第 9 章的引用，因为在该章中我们首次使用了许多这里将调用的函数。

## connect_validate_login()

在此示例中，我们使用 MySQL 自身的用户和密码表来设置可与本应用程序配合使用的帐户。对 MySQL 服务器的连接尝试成功与否，告诉我们用户名是否有效。我们通过将之前示例中使用的 authenticate() 函数拆分为几个部分来实现这一点，以便可以插入我们自己的验证代码——在此例中，即 connect_validate_login()。

```
function connect_validate_login()
{
    // if we haven't started a session yet, the references to
    $_SESSION
    // will come up invalid, so start one if we need to.
    check_session();
    if (!isset($_SESSION))
    {
        global $_SESSION;
    }

    static $__defaults = array(
        'application' => 'content'
        , 'username' => NULL
        , 'password' => NULL
        , 'database' => 'netsloth'
    );
    if ($_defaults['username'] == NULL)
    {
        if (isset($_SESSION['PHP_AUTH_USER']))
        {
            $_defaults['username'] = $_SESSION['PHP_AUTH_USER'];
        }
        if (isset($_SESSION['PHP_AUTH_PW']))
        {
            $_defaults['password'] = $_SESSION['PHP_AUTH_PW'];
        }
    }
    static $_simple = array('username','password');
    $args = func_get_args();
    $p = parse_arguments($args, $_simple, $_defaults);

    $ok = FALSE;

    $p['db_error_level'] = E_USER_NOTICE;
    ob_start();
    $dbh = @db_connect($p);
    ob_end_clean();
    if ($dbh)
    {
        $ok = TRUE;
    }
    else
    {
        $p['error_message'] = "Could not connect\n";
    }
    return $ok;
}
```

## fetch_story()

此函数使我们能够获取故事的记录。

```
function fetch_story ($args=NULL)
{
    $story_id=NULL;
    if (isset($_SESSION) && isset($_SESSION['PHP_AUTH_USER']))
    {
        $this_username=$_SESSION['PHP_AUTH_USER'];
    }
```

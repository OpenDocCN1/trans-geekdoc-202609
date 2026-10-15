
| 15 | 43 | person-1 | finance | B | 2016-03-26 04:42:52.573706 |
| 16 | 44 | person-2 | finance | B | 2016-03-26 04:42:52.573706 |
| 17 | 45 | person-3 | finance | B | 2016-03-26 04:42:52.573706 |
| 18 | 46 | person-4 | finance | B | 2016-03-26 04:42:52.573706 |
| 19 | 47 | person-5 | finance | B | 2016-03-26 04:42:52.573706 |
| 20 | 48 | person-1 | finance | B | 2016-03-26 04:43:35.389129 |
| 21 | 49 | person-2 | finance | B | 2016-03-26 04:43:35.389129 |
| 22 | 50 | person-3 | finance | B | 2016-03-26 04:43:35.389129 |
| 23 | 51 | person-4 | finance | B | 2016-03-26 04:43:35.389129 |
| 24 | 52 | person-5 | finance | B | 2016-03-26 04:43:35.389129 |

## 6. 存储过程

本章解释如何在 PostgreSQL 上使用存储过程并从 PHP 调用它们。

### 6.1 存储过程

存储过程是访问关系数据库系统的子程序。存储过程可以被应用程序访问。在本节中，我将向您展示如何在 PostgreSQL 中创建存储过程，然后从 PHP 调用它。

有三种存储过程模型：

- Stored Procedure without parameter. It can be return value or not
- Stored Procedure with input parameter
- Stored Procedure with input and output parameters

这些模型将在下一节中实现。首先，我们创建一个名为 `SPDemo` 的 PHP 类。然后，编写此骨架代码：

```php
<?php

include('dbinfo.php');

class SPDemo {
    private $msg = "";
    
    public function getMsg()
    {
        return $this->msg;
    }
}
```

将此代码保存为 `SPDemo.php`。

我们将添加几个函数来访问存储过程。在本章中，我们使用 `hrd_employee` 表从 postgres 数据库。

### 6.2 调用存储过程

要使用游标从 PHP 调用存储过程，我们执行以下步骤：

- Open connection to PostgreSQL using `pg_connect()`
- Do a transaction BEGIN and COMMIT
- Inside a transaction, we call `pg_query_params()` to call stored procedure

让我们开始。

首先，我们创建存储过程，名为 `get all employees`。编写此 SQL 语句。

```sql
DROP FUNCTION public.get_all_employees(refcursor);

CREATE OR REPLACE FUNCTION get_all_employees(ref refcursor) RETURNS refcursor AS $$
BEGIN
  OPEN ref FOR SELECT id,name,department,level,created FROM hrd_employee
  RETURN ref;
END;
$$ LANGUAGE plpgsql;
```

此存储过程调用查询以从 `hrd_employee` 表中检索数据。它返回一个游标。

运行此脚本到 PostgreSQL 数据库。如果成功，您可以在数据库中看到此存储过程。

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_64_0.png)

现在我们创建一个新函数，名为 `getAllEmployees()`，位于 `SPDemo.php` 中，并编写以下代码。

```php
<?php

include('dbinfo.php');

class SPDemo {
    private $msg = "";
    public function getMsg()
    {
        return $this->msg;
    }
    public function getAllEmployees() {
        $data = array();
        try {
            global $connString;
            $conn = pg_connect($connString);
            if( $conn === false )
            {
                $this->msg = "Unable to connect PostgreSQL Server.";
                return $data;
            }
        }
$cursor_name = "crp";
pg_query($conn,"BEGIN");
$query = "select * from get_all_employees($1);";

$params = array(&$cursor_name);
$res = pg_query_params($conn,$query,$params);
if($res === false)
{
    $this->msg = "Error in executing query.";
    return $data;
}

$res = pg_query($conn, "FETCH ALL FROM ".$cursor_name.";");
if($res === false)
{
    $this->msg = "Error in executing query.";
    return $data;
}
while($row = pg_fetch_row($res))
{
    array_push($data, array("id"=>$row[0],"name"=>$row[1],
    "department"=>$row[2],"level"=>$row[3],"created"=>$r
}

pg_query($conn,"COMMIT");
pg_close($conn);

} catch (Exception $e) {
    $this->msg = $e->getMessage();
}

return $data;
}
}
```

保存此代码。

现在调用函数 `getAllEmployees()`。创建文件 `PHP testsp.php` 并编写以下代码：

```php
<?php

include('SPDemo.php');

// call stored procedure
$obj = new SPDemo();
$data = $obj->getAllEmployees();
if($data) {
    foreach($data as $item) {
        $content = "";
```

```php
foreach($item as $key => $value) {
    $content = $content . $key . ": " . strval($value) . "\n";
}
echo $content . "\n";
}
}
```

保存此代码。

你可以执行文件 `testsp.php`。以下是一个示例输出。

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_66_0.png)

### 6.3 调用带参数的存储过程

在上一节中，我们调用了不带参数的存储过程。现在我们将调用带参数的存储过程。我们创建一个名为 `get_employee_by_id` 的存储过程，然后编写以下脚本。

```sql
DROP FUNCTION public.get_employee_by_id(refcursor,INT);

CREATE OR REPLACE FUNCTION get_employee_by_id(ref refcursor,empId INT) R

BEGIN

    OPEN ref FOR SELECT id,name,department,level,created FROM hrd_employee

    RETURN ref;

END;

$$ LANGUAGE plpgsql;
```

在 PostgreSQL 上将此脚本运行到 postgres 数据库。

在 PHP 文件 `SPDemo.php` 中，我们创建一个函数 `getEmployeesById()` 来调用存储过程，并编写以下代码。

```php
<?php

include('dbinfo.php');

class SPDemo {

    private $msg = "";

    public function getMsg()

    {

        return $this->msg;

    }

    public function getEmployeesById($id) {

        $data = array();

        try {

            global $connString;

            $conn = pg_connect($connString);

            if( $conn === false )

            {

                $this->msg = "Unable to connect PostgreSQL Server.";

                return $data;

            }

            $cursor_name = "gtm";

            pg_query($conn,"BEGIN");

            $query = "select * from get_employee_by_id($1,$2);";

            $params = array(&$cursor_name,&$id);
```

```php
$res = pg_query_params($conn,$query,$params);
if($res === false)
{
    $this->msg = "Error in executing query.";
    return $data;
}
$res = pg_query($conn, "FETCH ALL FROM ".$cursor_name.";");
if($res === false)
{
    $this->msg = "Error in executing query.";
    return $data;
}
while($row = pg_fetch_row($res))
{
    array_push($data, array("id"=>$row[0],"name"=>$row[1],
    "department"=>$row[2],"level"=>$row[3],"created"=>$r
}
pg_query($conn,"COMMIT");
pg_close($conn);
} catch (Exception $e) {
    $this->msg = $e->getMessage();
}
return $data;
}
}
```

现在调用函数 `getEmployeesById()`。打开 PHP 文件 `testsp.php` 并添加以下代码：

```php
<?php

include( 'SPDemo.php' );

$obj = new SPDemo();

// call stored procedure with parameter
$data = $obj->getEmployeesById(40);
if($data) {
    foreach($data as $item) {
        $content = "";
        foreach($item as $key => $value) {
            $content = $content . $key . ": " . strval($value) ."\n";
        }
        echo $content . "\n";
    }
}
```

我们向函数传入 Id=40。你可以根据你自己的数据更改此值。

保存此代码并运行它。以下是一个示例输出。

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_69_0.png)

### 6.5 调用带有输入和输出参数的存储过程

我们还可以调用带有输入和输出参数的存储过程。首先，我们创建一个名为 `func_compute` 的存储过程。编写以下代码。

```sql
DROP FUNCTION public.func_compute(INT,OUT INT);

CREATE OR REPLACE FUNCTION public.func_compute(var_a INT, OUT val_ret INT)
RETURNS INT
AS
$BODY$
BEGIN
    val_ret = var_a * 3;
END;
$BODY$
LANGUAGE plpgsql VOLATILE;
```

你可以看到我们将 `val_ret` 参数定义为 `OUT`。

回到 PHP 文件 `SPDemo.php`，我们创建一个函数 `compute()` 并编写以下代码。

```php
<?php
public function compute($var_a) {
    $ret = -1;
    try {
        global $connString;
        $conn = pg_connect($connString);
        if( $conn === false )
        {
            $this->msg = "Unable to connect PostgreSQL Server.";
            return $ret;
        }
        $query = "select val_ret from func_compute($1);";
        $params = array(&$var_a);
        $res = pg_query_params($conn,$query,$params);
        if($res === false)
        {
            $this->msg = "Error in executing query.";
            return $ret;
        }
        if($row = pg_fetch_row($res))
        {
            $ret = $row[0];
        }
    }
```

```php
pg_close($conn);
} catch (Exception $e) {
    $this->msg = $e->getMessage();
}
return $ret;
}
```

现在我们在 `testsp.php` 中测试这个函数。添加以下代码。

```php
<?php

include('SPDemo.php');

// call stored procedure
$obj = new SPDemo();

/// call stored procedure with input and output parameters
$val = $obj->compute(15);
echo "func_compute(15): " . $val;
```

保存此代码并运行 `testsp.php`。以下是一个示例输出。

![](img/c57c0fe41a78a4cec34dfc1c6ad7b9d6_73_0.png)

## 源代码

你可以从[http://www.aguskurniawan.net/book/phppostgres261.zip](http://www.aguskurniawan.net/book/phppostgres261.zip)下载本书的源代码。

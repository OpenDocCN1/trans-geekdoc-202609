
```php
<?php
    require_once( 'DB.php' );

    $bRollbackCondition = true;

    $oDB = DB::connect(
        'mysql://bt_user:bt_pass@207.44.182.3/book_test',
        true );
    if ( DB::isConnection( $oDB ) )
    {
        $aSQL = "select * from Employees where (
mgr_id = 2 )";
        $aValue = $oDB->getAll( $aSQL );
        if ( !DB::isError( $aValue ) )
        {
            print( '<pre>' );
            var_dump( $aValue );
            print( '</pre>' );
        }

        $oDB->autoCommit( false );

        $aSQL = "update Employees set mgr_id = 3 where
( mgr_id = 2 )";
        $oDB->query( $aSQL );
        if ( $bRollbackCondition == true )
        {
            $result = $oDB->rollback();
            print( "Updates rolled back<br>" );
        }
        else
        {
            $result = $oDB->commit();
            print( "Updates committed<br>" );
        }

        $aSQL = "select * from Employees where (
mgr_id = 2 )";
        $aValue = $oDB->getAll( $aSQL );
        if ( !DB::isError( $aValue ) )
        {
            print( '<pre>' );
            var_dump( $aValue );
            print( '</pre>' );
        }

        $oDB->disconnect();
    }
?>
```

### 代码清单 48：使用 commit()。

代码清单 48 中展示的非常简化的示例说明了如何使用 **commit()** 方法。代码使用一个简单的布尔值来决定是提交还是回滚事务，因此同一段代码也可以重用于 **rollback()** 方法。

```php
$SQL = "select * from Employees where (
    mgr_id = 2 )";
$AValue = $DB->getAll( $SQL );
if ( ! DB::isError( $AValue ) )
{
    print( '<pre>' );
    var_dump( $AValue );
    print( '</pre>' );
}

$DB->disconnect();
?>
```

### 代码清单 49：使用 rollback()。

代码清单 49 中展示的示例与代码清单 48 中的代码完全相同（**commit()** 示例），只是回滚条件标志被设置为 true。这会导致事务回滚。输出 25 中显示的输出清楚地证明了 UPDATE 查询已被回滚，因为随后 SELECT 查询返回的数据与 UPDATE 查询之前的数据相同。

```text
array(2) {
  [0]=>
  array(6) {
    [0]=>
    string(1) "1"
    [1]=>
    string(11) "Schwendiman"
    [2]=>
    string(5) "Blake"
    [3]=>
    string(3) "204"
    [4]=>
    string(1) "2"
    [5]=>
    string(1) "1"
  }
  [1]=>
  array(6) {
    [0]=>
    string(1) "3"
    [1]=>
    string(7) "McNulty"
    [2]=>
    string(4) "Kate"
    [3]=>
    string(3) "214"
    [4]=>
    string(1) "2"
    [5]=>
    string(1) "2"
  }
}
Updates rolled back
array(2) {
    [0] =>
    array(6) {
        [0] =>
        string(1) "1"
        [1] =>
        string(11) "Schwendiman"
        [2] =>
        string(5) "Blake"
        [3] =>
        string(3) "204"
        [4] =>
        string(1) "2"
        [5] =>
        string(1) "1"
    }
    [1] =>
    array(6) {
        [0] =>
        string(1) "3"
        [1] =>
        string(7) "McNulty"
        [2] =>
        string(4) "Kate"
        [3] =>
        string(3) "214"
        [4] =>
        string(1) "2"
        [5] =>
        string(1) "2"
    }
}
```

**输出 25：使用 rollback() 的示例。**

- 返回 DB_OK 或 DB_Error 对象。

## DB_common::numRows

`mixed numRows( mixed $result )`

**numRows()** 方法可用于返回 DB_result 对象中的行数。我不推荐使用此方法（见下文），但在代码清单 50 中提供了使用示例。

```php
<?php
```

## DB_common::createSequence

`mixed createSequence( string $seq_name )`

**createSequence()** 方法为数据库创建一个名为 _seq_name_ 的新序列。请参阅第 22 页开始的序列部分，了解序列的完整细节以及使用序列的示例。**createSequence()** 方法可能会被 **nextId()** 方法自动调用（见第 100 页的 **nextId()**）。

根据所使用的 DB 后端，您可能需要某些访问权限才能成功使用 **createSequence()** 方法。例如，代码清单 52 中的代码展示了具有受限访问权限的用户无法创建序列的情况。示例中的用户在 MySQL 数据库上只有 SELECT 权限。

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
  'mysql://bt_r_user:pass@207.44.182.3/book_test', true );
if ( DB::isConnection( $oDB ) )
{
  $result = $oDB->createSequence( 'NewSequence' );
  if ( !DB::isError( $result ) )
  {
    print( 'Sequence created<br>' );
  }
  else
  {
    print( $result->userinfo );
  }
  $oDB->disconnect();
}
else
{
  print( $oDB->userinfo );
}
?>
```

### 代码清单 52：使用 MySQL 的 createSequence()。

由于用户 **bt_r_user** 没有在 *book_test* 数据库上创建新表的权限，因此对 **createSequence()** 的调用失败，输出如输出 26 所示。其他数据库服务器对序列创建可能有不同的要求，这可能会影响 **createSequence()** 方法的使用。任何使用 PEAR::DB 序列的应用程序都应考虑这些差异。

```text
CREATE TABLE NewSequence_seq (id INTEGER UNSIGNED
AUTO_INCREMENT NOT NULL, PRIMARY KEY (id))
[Nativecode=1142 - create command denied to user:
'bt_r_user@xxx.xxx.xxx.xxx' for table
'NewSequence_seq']
```

**输出 26：** 在用户权限不足的 MySQL 数据库上使用 createSequence() 的输出。

- 返回 DB_OK 或 DB_Error 对象。

## DB_common::dropSequence

`mixed dropSequence( string $seq_name )`

**dropSequence()** 方法是 **createSequence()** 方法的对应方法。相同的关于安全性和用户权限的限制适用。有关详细信息，请参阅 **createSequence()** 方法说明（第 101 页）。

- 返回 DB_OK 或 DB_Error 对象。

## DB_common::tableInfo

`mixed tableInfo( mixed $result, mixed $mode = null )`

**tableInfo()** 方法用于返回有关表或查询的元数据信息。*result* 参数是通过 DB_result 对象可用的数据库特定值。与 **numRows()** 方法（第 98 页）一样，使用 **tableInfo()** 的首选编码方法是通过 **DB_result::tableInfo()** 方法。这只是更好的面向对象编程。

> 事实上，因为这是更好的实践，我不会在此处完整记录此方法，而是请您参考第 116 页的 **DB_result::tableInfo()** 方法了解详情。

唯一应该使用 **DB_common::tableInfo()** 的情况是当您需要获取与 DB_result 无关的表元数据时。在这种情况下，*result* 参数是一个字符串——表名。

```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
    if ( DB::isConnection( $oDB ) )
    {
        $result = $oDB->tableInfo( 'Employees' );
        if ( ! DB::isError( $result ) )
        {
            print( '<pre>' );
            var_dump( $result );
            print( '</pre>' );
        }

        $oDB->disconnect();
    }
?>
```

### 代码清单 53：使用 tableInfo()。

代码清单 53 中的示例说明了如何使用 **tableInfo()** 来获取有关 MySQL 数据库表的信息。对 **tableInfo()** 的调用结果是

## DB_common::getTables

`mixed getTables( void )`

getTables() 方法返回一个包含当前数据库中所有表的数组。

```php
<?php
require_once( 'DB.php' );

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
if ( DB::isConnection( $oDB ) )
{
$result = $oDB->getTables();
if ( !DB::isError( $result ) )
{
print( '<pre>' );
var_dump( $result );
print( '</pre>' );
}

$oDB->disconnect();
}
?>
```

### 代码清单 54：使用 getTables()。

代码清单 54 中示例的输出在输出 28 中给出。

```text
array(9) {
[0]=>
string(11) "Departments"
[1]=>
string(9) "Employees"
[2]=>
string(9) "Paychecks"
[3]=>
string(13) "UploadedFiles"
[4]=>
string(13) "seq_employees"
[5]=>
string(14) "seq_sequence_1"
[6]=>
string(14) "seq_sequence_2"
[7]=>
string(14) "sequence_1_seq"
[8]=>
string(14) "sequence_2_seq"
}
```

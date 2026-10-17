
```php
<?
  function connectDB($db) {
  global $host, $database, $username, $password;
  switch($db) {
    case ("psql"):
      $conn_string = "host=" . $host . " dbname=" . $database . " user=" . $username . " password=" . $password;
      $dbconn = pg_connect($conn_string) or die ("Error Connecting to PostgreSQL DB");
      return $dbconn;
      break;
    case ("mysql"):
      $dbconn = mysql_connect($host, $username, $password) or die ("Error Connecting to MySQL DB");
      return $dbconn;
      break;
    case("mssql"):
      $dbconn = mssql_connect($host, $username, $password) or die ("Error Connecting to MS SQL DB");
      return $dbconn;
      break;
    default;
      echo "<P>Invalid Database: $db";
      return 0;
    }
  }

  function selectDB($db) {
  global $database;
    switch($db) {
    case ("psql"):
      return 1;
      break;
    case ("mysql"):
      mysql_select_db($database) or die ("Error Connecting to MySQL DB");
      return 1;
      break;
    case("mssql"):
      mssql_select_db($database) or die ("Error Connecting to MS SQL DB");
      return 1;
      break;
    default;
      echo "<P>Invalid Database: $db";
      return 0;
    }
  }

  function queryDB($db, $query) {
    switch($db) {
    case ("psql"):
      if(!$result = @pg_exec($query)){
        $result = 0;
      }
      break;
    case ("mysql"):
      if(!$result = @mysql_query($query)){
        $result = 0;
      }
      break;
    case("mssql"):
      if(!$result = @mssql_query($query)){
        $result = 0;
      }
      break;
    default;
      echo "<P>Invalid Database: $db";
      $result = 0;
    }
    return $result;
  }

  function returnDBarray($db, $result) {
  if($result != "error") {
    switch($db) {
      case ("psql"):
        if(!$array = @pg_fetch_array($result)){
          $array = 0;
        }
        break;
      case ("mysql"):
        if(!$array = @mysql_fetch_array($result)){
          $array = 0;
        }
        break;
      case("mssql"):
        if(!$array = @mssql_fetch_array($result)){
          $array = 0;
        }
        break;
      default;
        echo "<P>Invalid Database: $db";
        $array = 0;
    }
    return $array;
  }
  }

  function closeDB($db,$dbconn) {
    switch($db) {
    case ("psql"):
      if(!@pg_close($dbconn)){
        return 0;
      } else {
        return 1;
      }
      break;
    case ("mysql"):
      if(!@mysql_close($dbconn)){
        return 0;
      } else {
        return 1;
      }
      break;
    case("mssql"):
      if(!@mssql_close($dbconn)){
        return 0;
      } else {
        return 1;
      }
      break;
    default;
      echo "<P>Invalid Database: $db";
      return 0;
    }
  }

  function numrowsDB($db, $result) {
    switch($db) {
    case ("psql"):
      if(!$rows = @pg_numrows($result)){
        return 0;
      } else {
        return $rows;
      }
      break;
    case ("mysql"):
      if(!$rows = @mysql_numrows($result)){
        return 0;
      } else {
        return $rows;
      }
      break;
    case("mssql"):
      if(!$rows = @mssql_numrows($result)){
        return 0;
      } else {
        return $rows;
      }
      break;
    default:
      echo "<P>Invalid Database: $db";
      return 0;
    }
  }
?>
```

### 脚本 `dbib.php` 逐行解释

#### 1. `connectDB` 函数

`connectDB($db)` 函数初始化数据库连接。

- **第 2-3 行**：定义全局变量 `$host`、`$database`、`$username` 和 `$password`。
- **第 4 行**：根据 `$db` 类型开始一个 `switch` 语句。
- **第 5-9 行 (psql)**：构建 `$conn_string`，使用 `pg_connect()` 连接到 PostgreSQL 并返回 `$dbconn`。
- **第 10-13 行 (mysql)**：使用 `mysql_connect()` 连接到 MySQL 并返回 `$dbconn`。
- **第 14-17 行 (mssql)**：使用 `mssql_connect()` 连接到 MS SQL 并返回 `$dbconn`。
- **第 18-21 行 (default)**：如果无效，则输出错误并返回 0。

#### 2. `selectDB` 函数

`selectDB($db)` 函数选择数据库。

- **第 24-25 行**：访问全局变量 `$database`。
- **第 26-29 行 (psql)**：返回 1。
- **第 30-33 行 (mysql)**：执行 `mysql_select_db($database)` 并返回 1。
- **第 34-37 行 (mssql)**：执行 `mssql_select_db($database)` 并返回 1。
- **第 38-41 行 (default)**：如果无效，则输出错误并返回 0。

#### 3. `queryDB` 函数

`queryDB($db, $query)` 函数执行查询。

- **第 44-50 行 (psql)**：使用 `@pg_exec($query)`，如果失败则将 `$result` 设置为 0。
- **第 51-55 行 (mysql)**：使用 `@mysql_query($query)`，如果失败则将 `$result` 设置为 0。
- **第 56-60 行 (mssql)**：使用 `@mssql_query($query)`，如果失败则将 `$result` 设置为 0。
- **第 61-66 行 (default)**：如果无效，则输出错误并返回 0。

#### 4. `returnDBarray` 函数

`returnDBarray($db, $result)` 函数将结果以数组返回。

- **第 69 行**：检查 `$result` 是否为 "error"。
- **第 71-75 行 (psql)**：使用 `@pg_fetch_array($result)`，如果失败则将 `$array` 设置为 0。
- **第 76-80 行 (mysql)**：使用 `@mysql_fetch_array($result)`，如果失败则将 `$array` 设置为 0。
- **第 81-85 行 (mssql)**：使用 `@mssql_fetch_array($result)`，如果失败则将 `$array` 设置为 0。
- **第 90 行**：返回数组 `$array`。

#### 5. `closeDB` 函数

`closeDB($db, $dbconn)` 函数关闭数据库连接。

- **第 95-102 行 (psql)**：使用 `@pg_close($dbconn)`，成功返回 1，失败返回 0。
- **第 103-109 行 (mysql)**：使用 `@mysql_close($dbconn)`，成功返回 1，失败返回 0。
- **第 110-116 行 (mssql)**：使用 `@mssql_close($dbconn)`，返回状态。

#### 6. `numrowsDB` 函数

`numrowsDB($db, $result)` 函数返回结果集的行数。

- **第 124-131 行 (psql)**：使用 `@pg_numrows($result)`，返回行数或 0。
- **第 132-138 行 (mysql)**：使用 `@mysql_numrows($result)`，返回行数或 0。
- **第 139-146 行 (mssql)**：使用 `@mssql_numrows($result)`，返回行数或 0。
- **第 147-151 行 (default)**：数据库类型无效时输出错误并返回 0。

- **38-39**：如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- **40**：返回 `0` (false)，这样任何调用该函数的都会知道函数执行失败。
- **41**：结束 `switch` 语句。
- **42**：结束函数声明。
- **44**：声明 `queryDB` 函数。该函数需要数据库类型 (`$db`) 和 SQL 查询 (`$query`) 作为参数。
- **45**：开始一个 `switch` 语句，根据 `$db` 的值检查应该运行哪一个分支。
- **46**：如果 `$db = "psql"`，则用户想要使用 PostgreSQL 数据库。
- **47**：使用 `pg_exec()` 执行查询并检查是否存在错误。
- **48**：如果有错误，将 `$result` 设置为 `0`。
- **49**：结束 `if` 语句。
- **50**：跳出 `switch` 语句，因为分支已经满足。
- **51**：如果 `$db = "mysql"`，则用户想要使用 MySQL 数据库。
- **52**：使用 `mysql_query()` 执行查询并检查是否存在错误。
- **53**：如果有错误，将 `$result` 设置为 `0`。
- **54**：结束 `if` 语句。
- **55**：跳出 `switch` 语句，因为分支已经满足。
- **56**：如果 `$db = "mssql"`，则用户想要使用 MS SQL 数据库。
- **57**：使用 `mssql_query()` 执行查询并检查是否存在错误。
- **58**：如果有错误，将 `$result` 设置为 `0`。
- **59**：结束 `if` 语句。
- **60**：跳出 `switch` 语句，因为分支已经满足。
- **61-62**：如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- **63**：返回 `0` (false)，这样任何调用该函数的都会知道函数执行失败。
- **64**：结束 `switch` 语句。
- **65**：将 `$result` 的值返回给调用该函数的函数。如果 `$result = 0`，则调用函数知道发生了错误。
- **66**：结束函数声明。
- **68**：声明 `returnDBarray` 函数。该函数需要数据库类型 (`$db`) 和上一个查询的结果集 (`$result`) 作为参数。
- **69**：验证结果不等于 `0`。如果等于，说明上一个查询出错。如果没有错误，则继续。
- **70**：开始一个 `switch` 语句，根据 `$db` 的值检查应该运行哪一个分支。
- **71**：如果 `$db = "psql"`，则用户想要使用 PostgreSQL 数据库。
- **72**：使用 `pg_fetch_array()` 获取数组并检查是否存在错误。
- **73**：如果有错误，将 `$array` 设置为 `0`。
- **74**：结束 `if` 语句。
- **75**：跳出 `switch` 语句，因为分支已经满足。
- **76**：如果 `$db = "mysql"`，则用户想要使用 MySQL 数据库。
- **77**：使用 `mysql_fetch_array()` 获取数组并检查是否存在错误。
- **78**：如果有错误，将 `$array` 设置为 `0`。
- **79**：结束 `if` 语句。
- **80**：跳出 `switch` 语句，因为分支已经满足。
- **81**：如果 `$db = "mssql"`，则用户想要使用 MS SQL 数据库。
- **82**：使用 `mssql_fetch_array()` 获取数组并检查是否存在错误。
- **83**：如果有错误，将 `$array` 设置为 `0`。
- **84**：结束 `if` 语句。
- **85**：跳出 `switch` 语句，因为分支已经满足。
- **86-87**：如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- **88**：将 `$array` 设置为 `0`，这样任何调用该函数的都会知道函数失败。
- **89**：结束 `switch` 语句。
- **90**：将 `$result` 的值返回给调用该函数的函数。如果 `$result = 0`，则调用函数知道发生了错误。
- **91**：结束检查 `$result` 不等于 `0` 的 `if` 语句。
- **92**：结束函数声明。
- **94**：声明 `closeDB` 函数。该函数需要数据库类型 (`$db`) 和数据库连接 (`$dbconn`) 作为参数。
- **95**：开始一个 `switch` 语句，根据 `$db` 的值检查应该运行哪一个分支。
- **96**：如果 `$db = "psql"`，则用户想要使用 PostgreSQL 数据库。
- **97**：`pg_close()` 并检查是否存在错误。
- **98**：如果有错误，返回 `0` 通知调用函数关闭失败。
- **99-100**：如果错误，通知调用函数关闭成功。
- **101**：结束 `if` 语句。
- **102**：跳出 `switch` 语句，因为分支已经满足。
- **103**：如果 `$db = "mysql"`，则用户想要使用 MySQL 数据库。
- **104**：`mysql_close()` 并检查是否存在错误。
- **105**：如果有错误，返回 `0` 通知调用函数关闭失败。
- **106-107**：如果错误，通知调用函数关闭成功。
- **108**：结束 `if` 语句。
- **109**：跳出 `switch` 语句，因为分支已经满足。
- **110**：如果 `$db = "mssql"`，则用户想要使用 MS SQL 数据库。
- **111**：`mssql_close()` 并检查是否存在错误。
- **112**：如果有错误，返回 `0` 通知调用函数关闭失败。
- **113-114**：如果错误，通知调用函数关闭成功。
- **115**：结束 `if` 语句。
- **116**：跳出 `switch` 语句，因为分支已经满足。
- **117-118**：如果没有一个分支被满足，则显示消息，说明发送给函数的 `$db` 值无效。
- **119**：返回 `0` 通知调用函数函数失败。
- **120**：结束 `switch` 语句。
- **121**：结束函数声明。

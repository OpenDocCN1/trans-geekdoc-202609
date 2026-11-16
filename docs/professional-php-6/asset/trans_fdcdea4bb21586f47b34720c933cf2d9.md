
## 第二部分：学习高级开发技术

这非常有趣，但所有内容都包含在此处，以展示如何解析连接字符串以实现灵活的 PostgreSQL 日志记录机制。此代码应保存在 Logger/class.pgsqlLoggerBackend.php：

```php
<?php

require_once('class.LoggerBackend.php');

class pgsqlLoggerBackend extends LoggerBackend {

private $logLevel;
private $Conn;
private $table = 'logdata';
private $messageField = 'message';
private $logLevelField = 'loglevel';
private $timestampField = 'logdate';
private $moduleField = 'module';

public function __construct($urlData) {
parent::__construct($urlData);

$this->logLevel = Config::getConfig('LOGGER_LEVEL');

$host = $urlData['host'];
$port = $urlData['port'];
$user = $urlData['user'];
$password = $urlData['pass'];
$arPath = explode('/', $urlData['path']);
$database = $arPath[1];

if(!strlen($database)) {
throw new Exception('pgsqlLoggerBackend: Invalid connection string. '
'No database name was specified');
}

$connStr = '';
if($host) {
$connStr .= "host=$host ";
}

if($port) {
$connStr .= "port=$port ";
}
if($user) {
$connStr .= "user=$user ";
}

if($password) {
$connStr .= "password=$password ";
}
$connStr .= "dbname=$database";

//Suppress native errors. We'll handle them with an exception
$this->hConn = pg_connect($connStr);

if(! is_resource($this->hConn)) {
    throw new Exception("Unable to connect to the database using $connStr");
}

//Take the query string in the form var=foo&bar=blah
//and convert it to an array like
// array('var' => 'foo', 'bar' => 'blah')
//Be sure to convert urlencoded values
$QueryData = $urlData['query'];
if(strlen($QueryData)) {
    $arTmpQuery = explode('&',$QueryData);

    $arQuery = array();
    foreach($arTmpQuery as $QueryItem) {
        $arQueryItem = explode('=', $QueryItem);
        $arQuery[urldecode($arQueryItem[0])] = urldecode($arQueryItem[1]);
    }
}

/* None of these items is mandatory. The defaults are
   established in the private member declarations at the top
   of the class. These variables establish the name of the
   table and the names of the fields within that table
   that store the various elements of the log entry.
*/

if(isset($arQuery['table'])) {
    $this->table = $arQuery['table'];
}

if(isset($arQuery['messageField'])) {
    $this->messageField = $arQuery['messageField'];
    if(isset($arQuery['logLevelField'])) {
        $this->logLevelField = $arQuery['logLevelField'];
    }
}

if(isset($arQuery['timestampField'])) {
    $this->timestampField = $arQuery['timestampField'];
}
if(isset($arQuery['moduleField'])) {
    $this->moduleField = $arQuery['moduleField'];
}
}

public function logMessage($msg, $logLevel = Logger::INFO, $module = null) {
    if($logLevel <= $this->logLevel) {
    $strLogLevel = Logger::levelToString($logLevel);

    $msg = pg_escape_string($msg);

    if(isset($module)) {
    $module = "" . pg_escape_string($module) . "";
    } else {
    $module = 'NULL';
    }
    }

    $arFields = array();
    $arFields[$this->messageField] = "" . pg_escape_string($msg) . "";
    $arFields[$this->logLevelField] = pg_escape_string($logLevel);
    $arFields[$this->timestampField] = "CURRENT_TIMESTAMP";
    $arFields[$this->moduleField] = $module;

    $sql = 'INSERT INTO ' . $this->table;
    $sql .= ' (' . join(', ', array_keys($arFields)) . ')';
    $sql .= ' VALUES (' . join(', ', array_values($arFields)) . ')';

    pg_exec($this->hConn, $sql);
    }
}
?>
```

在构造函数中，该类解析 URL 的查询部分，以确定表名以及存储日志信息的字段名称。假设将使用类似以下的 SQL 语句创建表。字段名称无关紧要（因为它们在连接字符串中是可配置的），但表中的数据类型应相同（或兼容的数据类型）：

```sql
create table logdata (
   message text,
   loglevel smallint,
   logdate timestamp,
   module varchar(255)
);
```

要使用新的 PostgreSQL 日志记录器，代码应类似于以下内容：

```php
<?php
require_once('class.Config.php');
require_once('class.Logger-enhanced.php');
Config::addConfig('LOGGER_LEVEL', Logger::INFO);

Logger::register('app', 'pgsql://steve:pass@localhost/mydb?table=logdata');

$log = Logger::getInstance('app');

if(isset($_GET['fooid'])) {
    //not written to the log - the log level is too high
    $log->logMessage('A fooid is present', Logger::DEBUG);

    //LOG_INFO is the default, so this would get printed
    $log->logMessage('The value of fooid is ' . $_GET['fooid']);
} else {
    //This will also be written and includes a module name
    $log->logMessage('No fooid supplied',
                     Logger::CRITICAL,
                     "Foo Module");

    throw new Exception('No foo id!');
}
?>
```

传递给 `Logger::register()` 的连接字符串指定了一个名为 `app` 的日志，该日志连接到运行在 `localhost` 上的 PostgreSQL 数据库。`LoggerBackend` 以用户 `steve` 的身份连接到名为 `mydb` 的数据库。写入日志条目的表称为 `logdata`。如果您未指定这些参数中的任何一个，将使用作为类私有成员变量声明的默认值。当然，此后端可以轻松修改以支持任何有 PHP 模块的数据库类型（包括 MySQL 和 SQL Server）。

此示例使用了原生 PostgreSQL 函数，而非利用 PDO。您也可以构建一个 PDO 后端，使用传递给 `Logger::register` 的适当结构化连接字符串连接到任何有可用驱动程序的数据库，格式为 `pdo://user:pass@hostname/database?driver=[pdo driver name]`。

## 创建调试机制

虽然像您刚刚创建的这样强大的日志记录机制在灵活性和存储方面几乎有无限的可能性，但有时将调试消息打印到浏览器窗口要方便得多，而不必仔细查看大型日志文件；但就像 `Logger` 类旨在防止部署前必须手动删除的数十条 `print` 语句一样，调试机制使开发人员能够以这种方式将消息打印到屏幕上，以便在部署时可以轻松删除。

`Debugger` 类将调试消息存储在会话中，然后在页面请求结束时将它们打印在屏幕底部。这将调试输出集中到屏幕上的一个位置，使查找您要查找的特定输出变得更加容易。它还使您能够打印大量数据而不干扰用户界面的结构，并使禁用调试输出变得容易。

之所以将此信息存储在会话中，是因为并非每个页面请求都会生成输出。例如，当通过发布表单将信息保存到数据库时，通常应发出 302 重定向，以防止用户在浏览器上按下重新加载按钮时修改数据。302 重定向是指浏览器发出的 HTTP 响应代码，当您发出诸如 header('Location: [url]') 之类的代码时。

Debugger 有两个主要功能：

- DEBUG 函数将带有可选键和调试级别的条目写入会话中的调试数组。调试级别的工作方式与 Logger 类中的日志级别相同。日志级别值越低，优先级越高。
- debug_print 函数应在每个生成输出的页面底部调用。它从会话中获取数组并生成包含数组内容的 HTML 表。打印完成后，它会从会话中删除该信息。这样，不生成输出的页面请求仍会保留其调试信息。

此类的代码如下。将此类命名为 Debugger.php：

```php
<?php

define('DEBUG_INFO', 100);
define('DEBUG_SQL', 75);
define('DEBUG_WARNING', 50);
define('DEBUG_ERROR', 25);
define('DEBUG_CRITICAL', 10);

session_start();

class Debugger {

    public static function debug($data, $key = null, $debugLevel = DEBUG_INFO) {

        if(! isset($_SESSION['debugData'])) {
            $_SESSION['debugData'] = array();
        }

        if($debugLevel <= Config::getConfig('DEBUG_LEVEL') ) {
            $_SESSION['debugData'][$key] = $data;
        }
    }

    public static function debugPrint() {
        $arDebugData = $_SESSION['debugData'];
        print Debugger::printArray($arDebugData);

        $_SESSION['debugData'] = array();
    }
}
```


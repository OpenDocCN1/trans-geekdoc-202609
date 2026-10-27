Exception class briefly before demonstrating how each method is used.

```
```php
<?php
class Exception
{
protected $message = 'Unknown exception'; // exception message
private $string; // __toString cache
protected $code = 0; // user defined exception code
protected $file; // source filename of exception
protected $line; // source line of exception
private $trace; // backtrace
private $previous; // previous exception if nested exception

public function __construct($message = null, $code = 0, Exception $previous = null);

final private function __clone(); // Inhibits cloning of exceptions.

final public function getMessage(); // Gets the message string that was passed to the constructor
final public function getCode(); // Gets the error code that was passed to the constructor
final public function getFile(); // Gets the source filename
final public function getLine(); // Gets the source line
final public function getTrace(); // Gets a multidimensional array of the backtrace()
final public function getPrevious(); // Gets previous exception
final public function getTraceAsString(); // Gets a formatted string of the data returned by trace

/* Overrideable */
public function __toString(); // formatted string for display
}
?>
```
```

Let’s get started by referencing the Database class that we generated in our restaurant carte app to interact with the database. We utilize the Exception class to create a custom message when a database connection attempt fails, either because the database specified in the configuration file cannot be located or because some other connection credential specified in the configuration file was incorrect.

# Throwing an Exception

```
```php
<?PHP
require_once('configuration.PHP');

class DB
{
public $m_conn;
private function DB()
{

$m_DB_Name = $GLOBALS['config']['DB'];
$m_DB_Server_Name = $GLOBALS['config']['DB_Host'];
$m_DB_Customer = $GLOBALS['config']['customer'];
$m_DB_Password = $GLOBALS['config']['password'];
$m_DB_Port = $GLOBALS['config']['port'];

$this->m_conn = mysql_connect ($m_DB_Server_Name. ":".$m_DB_Port, $m_DB_Customer, $m_DB_Password);
mysql_set_charset('latin1',$this->m_conn);
if ($this->m_conn)
{
if (!mysql_select_db ($m_DB_Name))
{
throw new Exception('can’t find database “'.$m_DB_Name.'”.
```
```
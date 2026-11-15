

```php
<?php
// Read the XML document into a SimpleXMLElement object
$rss = simplexml_load_file( "./rss_feed.xml", "SimpleXMLElement", LIBXML_NOCDATA );

// Display the feed details
echo "<h2>" . $rss->channel->title . "</h2>\n";
echo "<p>" . $rss->channel->description . "</p>\n";
echo "<p><em>Last updated: " . $rss->channel->lastBuildDate . "</em></p><hr />\n";

// Display each news item in turn
echo "<ul>\n";

foreach ( $rss->channel->item as $item )
{
    echo "<li>\n";
    echo "<h3 style=\"margin: 0;\">\n";
    echo "<h4 style=\"margin: 0;\">\n";
    echo "<p>$item->description <a href=\"$item->link\">Read more...</a></p>\n";
    echo "</li>\n";
}

echo "</ul>\n";

?>
</body>
</html>
```

该脚本相当自解释。显示XHTML页面页眉后，脚本使用simplexml_load_file()将RSS feed读入SimpleXMLElement对象。接着，它显示channel元素内的相关feed信息，并遍历channel元素内的每个item元素，在遍历过程中显示相关字段。

图A-4显示了针对练习中示例feed运行该脚本时的输出。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_753_0.png)

图A-4

## 第20章

### 练习1答案

这个错误处理程序只需检查传入的$errno参数，以确定错误级别是E_WARNING还是E_USER_WARNING，然后使用error_log()根据需要通过电子邮件发送或记录错误。出于方便，其他信息（如错误类型和当前变量）也会通过电子邮件发送或记录。（请注意，$levels数组仅包含自定义错误处理程序可以捕获的错误类型。）然后使用trigger_error()来测试错误处理程序：

```php
function myErrorHandler( $errno, $errstr, $errfile, $errline, $errcontext ) {
    $levels = array (
        E_WARNING => "Warning",
        E_NOTICE => "Notice",
        E_USER_ERROR => "Error",
        E_USER_WARNING => "Warning",
        E_USER_NOTICE => "Notice",
        E_STRICT => "Strict warning",
        E_RECOVERABLE_ERROR => "Recoverable error",
        E_DEPRECATED => "Deprecated feature",
        E_USER_DEPRECATED => "Deprecated feature"
    );
    $message = date( "Y-m-d H:i:s - " );
    $message .= $levels[$errno] . ": $errstr in $errfile, line $errline\n\n";
    $message .= "Variables:\n";
    $message .= print_r( $errcontext, true ) . "\n\n";
    if ( $errno == E_WARNING or $errno == E_USER_WARNING ) {
    error_log( $message, 1, "joe@example.com" );
    } else {
    error_log( $message, 3, "/home/joe/non_serious_errors.log" );
    }
}
set_error_handler( "myErrorHandler" );
trigger_error( "Simulated warning", E_USER_WARNING );
trigger_error( "Simulated notice", E_USER_NOTICE );
?>
```

### 练习2答案

Circle类有五个方面需要测试：存储颜色的能力、填充状态、非填充状态、半径，以及正确计算面积的能力。以下脚本对该类进行了全面测试：

```php
<?php
require_once( "inheritance.php" );
require_once( "PHPUnit/Framework.php" );
require_once( "PHPUnit/TextUI/TestRunner.php" );
class CircleTest extends PHPUnit_Framework_TestCase
{
public function testColor()
{
$circle = new Circle();
$circle->setColor( "red" );
$this->assertEquals( "red", $circle->getColor() );
}
public function testFill()
{
$circle = new Circle();
$circle->fill();
$this->assertTrue( $circle->isFilled() );
}
public function testHollow()
{
$circle = new Circle();
$circle->makeHollow();
$this->assertFalse( $circle->isFilled() );
}
public function testRadius()
{
    $circle = new Circle();
    $circle->setRadius( 10 );
    $this->assertEquals( 10, $circle->getRadius() );
}
public function testArea()
{
    $circle = new Circle();
    $circle->setRadius( 10 );
    $this->assertEquals( M_PI * pow( 10, 2 ), $circle->getArea() );
}
}

$testSuite = new PHPUnit_Framework_TestSuite();
$testSuite->addTest( new CircleTest( "testColor" ) );
$testSuite->addTest( new CircleTest( "testFill" ) );
$testSuite->addTest( new CircleTest( "testHollow" ) );
$testSuite->addTest( new CircleTest( "testRadius" ) );
$testSuite->addTest( new CircleTest( "testArea" ) );

PHPUnit_TextUI_TestRunner::run( $testSuite );
?>
```

## 配置PHP

PHP引擎拥有大量可调整的配置指令，用于改变引擎的行为。大多数指令可以通过以下任一方法设置：

- 在PHP配置文件php.ini中设置指令：PHP引擎启动时会读取该文件。所有指令都可以以这种方式设置。通常您需要root（管理员）权限才能编辑此文件。

- 通过编辑Apache .htaccess文件：如果您将PHP引擎作为Apache模块运行，可以在网站文档根目录中创建.htaccess文件并将指令放在其中。（如果您希望设置仅应用于该子文件夹中的文件和文件夹，也可以将.htaccess文件放在子文件夹中。）使用php_value Apache指令设置非布尔值的PHP指令，使用php_flag Apache指令设置布尔值的指令。例如：

  ```
  php_value upload_max_filesize 8M
  php_flag display_errors Off
  ```

- 在Apache httpd.conf配置文件中设置Apache指令：这与.htaccess文件的格式大致相同，但允许使用两个额外指令：php_admin_value和php_admin_flag。这些指令用于设置只能在php.ini或httpd.conf文件中设置的PHP指令（例如extension_dir或file_uploads）。有关在Apache httpd.conf和.htaccess文件中设置指令的更多信息，请参阅http://www.php.net/configuration.changes。

- 通过编辑.user.ini文件：与.htaccess类似，这基于每个目录工作。它设计用于PHP作为CGI或FastCGI应用程序运行时的情况（在这些情况下无法使用.htaccess）。它为指令使用php.ini格式，而不是.htaccess格式：

  ```
  upload_max_filesize = 8M
  display_errors = Off
  ```

尽管.user.ini是按目录配置文件的默认文件名，但您可以在php.ini中使用user_ini.filename指令选择不同的文件名。请参见本附录后面的“php.ini选项”部分。

- 在脚本文件中使用ini_set()：这使您的应用程序更具可移植性，因为设置存储在应用程序的脚本文件中，而不是存储在服务器范围的配置文件中。例如：

  ```
  ini_set( "display_errors", 1 )
  ```

虽然可以在php.ini文件中更改所有指令，但只有部分指令可以在.htaccess文件中或使用ini_set()更改。要了解可以在哪里更改指令，请参阅http://www.php.net/manual/en/ini.list.php表格中的Changeable列。

由于php.ini文件将所有指令集中在一个位置，因此值得浏览它，看看可以进行哪些配置更改。本附录将引导您了解php.ini文件中的每个部分。

您可以通过在PHP脚本中调用phpinfo()并查看结果，了解当前的所有配置设置。

当前PHP发行版中提供两个版本的php.ini文件：php.ini-development和php.ini-production。php.ini-development文件适用于开发环境，而php.ini-production文件适用于生产环境（即实时网站）。

本附录列出并描述了PHP 5.3.0版本随附的php.ini-development文件中的大部分内容，这很可能与您安装的文件非常接近。

php.ini-development中的所有设置都是内置默认设置。换句话说，如果PHP引擎找不到任何配置文件，它将使用与php.ini-development中相同的设置。

## 关于php.ini

php.ini-development文件的第一部分描述了php.ini文件的用途，并解释了PHP引擎如何定位要使用的php.ini文件。它还描述了文件中指令的基本语法，基本形式如下：

```
directive_name = directive_value
```

某些指令值可以使用按位运算符OR（|）、AND（&）和NOT（~或!）来构建。标志可以使用任意值1、On、True或Yes打开（使用0、Off、False或No关闭）。注释行以分号（;）开头。

```
;;;;;;;;;;;;;;;;;;;;;;;
; About php.ini ;
;;;;;;;;;;;;;;;;;;;;;;;
; PHP's initialization file, generally called php.ini, is responsible for
; configuring many of the aspects of PHP's behavior.
;
; PHP attempts to find and load this configuration from a number of locations.
```

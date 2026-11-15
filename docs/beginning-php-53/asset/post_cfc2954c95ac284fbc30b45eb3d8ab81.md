
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

The script should be fairly self-explanatory. After displaying an XHTML page header, the script reads the RSS feed into a SimpleXMLElement object using simplexml_load_file(). It then displays the relevant feed information (inside the channel element), and loops through each item element inside the channel element, displaying the relevant fields as it goes.

Figure A-4 shows the output from the script when run against the example feed from the exercise.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_753_0.png)

Figure A-4

## Chapter 20

### Exercise 1 Solution

All this error handler has to do is inspect the passed $errno parameter to determine if the error level was E_WARNING or E_USER_WARNING, and then use error_log() to email or log the error as appropriate. Other information such as the error type and current variables is also emailed or logged, for convenience. (Notice that the $levels array only contains error types that can be trapped by a custom error handler.) trigger_error() is then used to test the error handler:

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

### Exercise 2 Solution

The Circle class has five aspects to test: its ability to store its color, its filled status, its not-filled status, its radius, and its ability to calculate its area correctly. The following script puts the class through its paces:

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

## Configuring PHP

The PHP engine features a large number of configuration directives that can be tweaked to alter how the engine behaves. Most directives can be set using any of the following methods:

- By setting the directive in the PHP configuration file php.ini: This file is read by the PHP engine when it starts. All directives can be set this way. Usually you need root (administrator) access to edit this file.

- By editing an Apache .htaccess file: If you're running your PHP engine as an Apache module, you can create an .htaccess file in the document root of your Web site and place directives in there. (You can also place the .htaccess file in a subfolder if you only want the settings to apply to files and folders in that subfolder.) Use the php_value Apache directive to set PHP directives that have non-Boolean values, and the php_flag Apache directive to set directives that have Boolean values. For example:

  ```
  php_value upload_max_filesize 8M
  php_flag display_errors Off
  ```

- By setting an Apache directive in an httpd.conf Apache configuration file: This takes much the same format as an .htaccess file, with two additional directives allowed: php_admin_value and php_admin_flag. These are used for setting PHP directives that can only be set in php.ini or httpd.conf files (such as extension_dir or file_uploads). For more on setting directives within Apache httpd.conf and .htaccess files, see http://www.php.net/configuration.changes.

- By editing a .user.ini file: Like .htaccess, this works on a per-directory basis. It's designed for use when PHP is running as a CGI or FastCGI application (.htaccess isn't available in these situations). It uses the php.ini-style format for directives, rather than the .htaccess format:

  ```
  upload_max_filesize = 8M
  display_errors = Off
  ```

Although .user.ini is the default filename for per-directory configuration files, you can choose a different filename with the user_ini.filename directive in php.ini. See the "php.ini Options" section later in this appendix.

- From within your script files using ini_set(): This makes your application more portable because the settings are stored in the application's script files, rather than in server-wide configuration files. For example:

  ```
  ini_set( "display_errors", 1 )
  ```

Whereas all directives can be changed in a php.ini file, only some directives can be changed in an .htaccess file or using ini_set(). To find out where a directive can be changed, see the Changeable column in the table at http://www.php.net/manual/en/ini.list.php.

Because the php.ini file contains all the directives in one place, it's worth browsing through it to see what sort of configuration changes you can make. This appendix guides you through each of the sections in the php.ini file.

You can find out all your current configuration settings by calling phpinfo() from within a PHP script and viewing the results.

Two versions of the php.ini file are delivered with the current distribution of PHP: php.ini-development and php.ini-production. The php.ini-development file is suitable for a development environment, whereas the php.ini-production file is suitable for production (that is, a live Web site).

This appendix lists and describes most of the contents of the php.ini-development file supplied with PHP version 5.3.0, which is likely to be very close to the one you have installed.

All of the settings in php.ini-development are the built-in default settings. In other words, if the PHP engine can't find any configuration files, it will use the same settings that are used in php.ini-development.

## About php.ini

The first section of the php.ini-development file describes the purpose of php.ini files and explains how the PHP engine locates a php.ini file to use. It also describes the basic syntax of directives in the file, which is essentially:

```
directive_name = directive_value
```

Some directive values can be constructed using the bitwise operators OR ( | ), AND ( & ), and NOT ( ~ or ! ). Flags can be turned on using any of the values 1, On, True, or Yes (and turned off with 0, Off, False, or No). Comment lines begin with a semicolon ( ; ).

```
;;;;;;;;;;;;;;;;;;;;;;;
; About php.ini ;
;;;;;;;;;;;;;;;;;;;;;;;
; PHP's initialization file, generally called php.ini, is responsible for
; configuring many of the aspects of PHP's behavior.
;
; PHP attempts to find and load this configuration from a number of locations.
```

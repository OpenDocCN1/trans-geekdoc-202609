You should see the following output:

```
ed@ed: ~/Desktop/Repos/php7_recipes/source/chapter13$
edged: ~/Desktop/Repos/php7_recipes/source/chapter13$ phpunit tests
PHPUnit 5.4.3 by Sebastian Bergmann and contributors.

............................ 12 / 12 (100%)

Time: 53 ms, Memory: 4.00MB

OK (12 tests, 32 assertions)
ed@ed: ~/Desktop/Repos/php7_recipes/source/chapter13$
```

To demonstrate the use of autoloading via a bootstrap file, create a new `tests_with_autoload` directory. In this folder, define a `bootstrap.php` file with the code shown in step 5. Create two directories in `tests_with_autoload`: `Demo` and `Simple`.

From the directory containing the source code for this chapter, copy the file (discussed in step 12 of the previous recipe) into `tests_with_autoload/Demo/Demo.php`. After the opening `<?php` tag, add this line:

```
namespace Demo;
```

Next, copy the `SimpleTest.php` file to `tests_with_autoload/Simple/ClassTest.php`. (Notice the filename change!). You will need to change the first few lines to the following:

```
<?php
namespace Simple;
use Demo\Demo;
use PHPUnit\Framework\TestCase;

class ClassTest extends TestCase
{
    protected $demo;
    public function setUp()
    {
        $this->demo = new Demo();
    }
    // etc.
```

After that, create a `tests_with_autoload/phpunit.xml` file that pulls everything together:

```
<phpunit bootstrap="bootstrap.php">
    <testsuites>
        <testsuite name="visitor">
            <directory>Simple</directory>
        </testsuite>
```
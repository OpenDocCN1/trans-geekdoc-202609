offers another helper method for this: expectException(). This can then look like the following:

```
$this->expectException(InvalidArgumentException::class);
UrlFinder::find('no URL');
```

Listing 36.2 shows an overview of the complete test class.

```
<?php
use PHPUnit\Framework\TestCase;
require "UrlFinder.php";

class UrlFinderTest extends TestCase
{
    public function testNoUrl()
    {
        $this->expectException(InvalidArgumentException::class);
        UrlFinder::find('no URL');
    }

    public function testFindInbetween()
    {
        $this->assertEquals(
            'http://php.net/',
            UrlFinder::find('http://php.net/ is the homepage of the PHP project'));
    }
}
```

# Listing 36.2 PHPUnit Tests ("UrlParserTest.php")

The code to be tested is ready, as are the tests. Only one thing is missing: the piece of software that performs the tests. Incidentally, this is precisely the point that needs to be automated!

If you use PHPUnit in the form of a PHAR archive, this is the necessary call:

```
php phpunit.phar UrlFinderTest.php
```

When using Composer, it looks quite similar. PHPUnit was automatically installed in vendor/bin and can be called directly (Windows users, simply replace the slashes with backslashes):

```
vendor/bin/phpunit UrlFinderTest.php
```

Figure 36.3 shows the result: Two tests with two assertions were tested, and both passed!
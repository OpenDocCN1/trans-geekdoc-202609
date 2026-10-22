Now create a passing test case so you can see the difference:

```
```php
1. <?php
2.
3. declare(strict_types=1);
4.
5. class BasicTestCase extends PHPUnit\Framework\TestCase
6. {
7.     public function testCase()
8.     {
9.         $this->assertTrue(true);
10.     }
11. }
```
```

Then, use the test runner and run this test.

```
```
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

.                                   1 / 1
(100%)

Time: 97 ms, Memory: 12.00 MB

OK (1 test, 1 assertion)
```
```

The test runner now shows you less information but informs you that the one assertion in your one test passed. What happens if you add another assertion?

```
```php
1. <?php
2.
3. declare(strict_types=1);
4.
5. class BasicTestCase extends PHPUnit\Framework\TestCase
6. {
7.     public function testCase()
8.     {
9.         $this->assertTrue(true);
10.         $this->assertFalse(false);
11.     }
12. }
```
```
# 8. REFACTORING HELPERS

Everything passes. Here's what the helper looks like now:

```
```php
/**
 * @param array $properties
 * @return Model\User
 */
private function createUserMock(array $properties = []): Model\User
{
    $user = new class extends Model\User {
        public $properties;

        public function __get($property)
        {
            if (\array_key_exists($property, $this->properties)) {
                return $this->properties[$property];
            }
        }

        public function __set($property, $value)
        {
            $this->properties[$property] = $value;
            return;
        }
    };
    $user->properties = $properties;

    return $user;
}
```
```

Re-run the tests and make sure this refactor did not break anything.

```
```
/usr/local/bin/php -dxdebug.remote_mode=jit \
/Users/chartjes/Sites/opencfp/vendor/phpunit/phpunit/phpunit \
--no-configuration OpenCFP\Test\Unit\Domain\Speaker\SpeakerProfileTest \
/Users/chartjes/Sites/opencfp/tests/Unit/Domain/Speaker/SpeakerProfileTest.php \
--teamcity
PHPUnit 7.5.8 by Sebastian Bergmann and contributors.

Time: 301 ms, Memory: 10.00 MB

OK (45 tests, 45 assertions)

Process finished with exit code 0
```
```

Excellent! The test suite still passes, and I have fixed the deprecated method.
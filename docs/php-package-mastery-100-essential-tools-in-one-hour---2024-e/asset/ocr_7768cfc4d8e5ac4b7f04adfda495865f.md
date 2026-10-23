# 74. PHPStan

PHPStan is a static analysis tool for PHP that focuses on finding errors in your code without actually running it. It can detect potential bugs and inconsistencies, adhering to modern development practices to ensure code reliability and maintainability. It supports various levels of analysis, from basic to strict, allowing developers to gradually improve their code base.

Ex:PHPStan

```
```php
// PHPStan is typically run from the command line, analyzing your
PHP files for potential issues. Here's an example command:
// $ vendor/bin/phpstan analyse src——level=max
// The command tells PHPStan to analyze the "src" directory of your
project at the maximum strictness level.
// Since PHPStan runs from the command line, here's a simplified PHP
example that might raise an error when analyzed by PHPStan:
function addNumbers(int $a, int $b): int {
    return $a + $b;
}
echo addNumbers('5', 10);
```
```
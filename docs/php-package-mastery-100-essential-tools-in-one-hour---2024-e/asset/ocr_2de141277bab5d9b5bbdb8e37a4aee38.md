# 49. Symfony Validator

The Symfony Validator component is a library that provides tools to validate data against a set of rules. It supports validating objects, arrays, and more using constraints. It's widely used to ensure data integrity and to validate user inputs or data objects in PHP applications.

```
Ex:Symfony Validator

```php
use Symfony\Component\Validator\Validation;
use Symfony\Component\Validator\Constraints\Length;
use Symfony\Component\Validator\Constraints\NotBlank;
$validator = Validation::createValidator();
$violations = $validator->validate('Hello World', [
    new Length(['min' => 10]),
    new NotBlank(),
]);
if (0 !== count($violations)) {
    // there are errors, let's get them.
    foreach ($violations as $violation) {
        echo $violation->getMessage()."\n";
    }
} else {
    echo "Validation passed!\n";
}
```
```
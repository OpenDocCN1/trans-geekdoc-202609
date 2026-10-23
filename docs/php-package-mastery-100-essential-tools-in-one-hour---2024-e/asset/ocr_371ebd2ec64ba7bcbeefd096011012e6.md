# 60. Respect\Validation

Respect\Validation is a powerful validation library designed for validating data in PHP applications. It supports a wide range of validators, making it easier to ensure data integrity and conform to business rules without extensive manual checks.

```
Ex:Respect\Validation
use Respect\Validation\Validator as v;
$usernameValidator = v::alnum()->noWhitespace()->length(1, 15);
try {
$usernameValidator->assert('ValidUsername123');
echo "Username is valid!";
} catch (\Respect\Validation\Exceptions\ValidationException $e) {
echo $e->getMessage();
}
```

Username is valid!

In this example, we start by importing the Validator class from the Respect\Validation library with an alias v to make it more concise. Then, we create a $usernameValidator which is an instance of a validator chain that checks if a value is alphanumeric (alnum()), has no whitespace
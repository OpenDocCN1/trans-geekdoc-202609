EOT;

?>

The above example will output:

My name is “MyName”. I am printing some Foo.

Now, I am printing some Bar2.

This should print a capital ‘A’: A

It is also possible to use the Heredoc syntax to pass data to function arguments:

# Example #4. Heredoc in arguments example

```
<?php
var_dump(array(<<<EOD
foobar!
EOD
));
?>
```

As of PHP 5.3.0, it’s possible to initialize static variables and class properties/constants using the Heredoc syntax:

# Example #5. Using Heredoc to initialize static values

```
<?php
// Static variables
function foo() {
  static $bar = <<<LABEL
Nothing in here...
LABEL;
}

// Class properties/constants
class foo {
  const BAR = <<<FOOBAR
Constant example
}
```
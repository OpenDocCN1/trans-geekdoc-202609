# Basic Computer Coding: PHP

```
public $john = "John Smith";
public $jane = "Jane Smith";
public $robert = "Robert Paulsen";

public $smith = "Smith";
}
```

$people = new people();

```
echo "\$people->john drank \$some[0] juice".PHP_EOL;
echo "\$people->john said hello to \$people->jane".PHP_EOL;
echo "\$people->s wife greeted \$people->robert".PHP_EOL;
echo "\$people->robert greeted the two \$people->smiths"; // Won't work
?
```

The above example will output:
He drank some apple juice.
He drank some orange juice.
He drank some purple juice.
John Smith drank apple juice.
John Smith said hello to Jane Smith.
John Smith's wife greeted Robert Paulsen.
Robert Paulsen 7.1.0 greeted the two.
As of PHP 7.1.0 also negative numeric indices are supported.

Example #10. Negative numeric indices

```
<?php
$string = 'string';
echo "The character at index -2 is \$string[-2].",PHP_EOL;
\$string[-3] = 'o';
echo "Changing the character at index -3 to o gives \$string", PHP_EOL;
?>
```
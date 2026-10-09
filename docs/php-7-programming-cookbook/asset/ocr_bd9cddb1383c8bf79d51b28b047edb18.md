+   2.  AST allows us to issue the `echo ${a() [1] () [2] (100)}` command. This is parsed
left-to-right, which executes as follows:

    -   `${a()}` interprets as `test()`, which returns an array
    -   `[1]` references array element 1, which returns a callback
    -   `()` executes this callback, which returns an array of two elements
    -   `[2]` references array element 2, which returns a callback
    -   `(100)` executes this callback, supplying a value of 100, which returns Level 1/2:101

![](bbox=[0.24, 0.31, 0.76, 0.38])

+   3.  The following is a more substantive example that takes advantage of AST syntax to define a data filtering and validating class. First of all, we define the `Application\\Web\\SecurityClass`. In the constructor, we build and define two arrays. The first array consists of filter callbacks. The second array has validation callbacks:

```
public function __construct()
{
    $this->filter = [
        'striptags'  => function ($a) { return strip_tags($a); },
        'digits'     => function ($a) { return preg_replace(
                       '/[^0-9]/', '', $a); },
        'alpha'      => function ($a) { return preg_replace(
                       '/[^A-Z]/i', '', $a); }
    ];
    $this->validate = [
        'alnum'      => function ($a) { return ctype_alnum($a); },
        'digits'     => function ($a) { return ctype_digit($a); },
        'alpha'      => function ($a) { return ctype_alpha($a); }
    ];
}
```

+   4.  We want to be able to call this functionality in a *developer-friendly* manner. Thus, if we want to filter digits, then it would be ideal to run a command such as this:

    $security->filterDigits($item);

+   5.  To accomplish this we define the magic method `__call()`, which gives us access to non-existent methods:

```
public function __call($method, $params)
{
```
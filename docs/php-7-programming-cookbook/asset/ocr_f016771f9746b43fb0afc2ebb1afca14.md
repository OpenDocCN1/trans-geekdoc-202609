# See also

For more information on AST, please consult the RFC that addresses the **Abstract Syntax Tree**, which can be viewed at <https://wiki.php.net/rfc/abstract_syntax_tree>.

# Understanding differences in parsing

In PHP 5, expressions on the right side of an assignment operation were parsed *right-to-left*. In PHP 7, parsing is consistently *left-to-right*.

# How to do it...

+   1. A variable-variable is a way of indirectly referencing a value. In the following example, first `$foo` is interpreted as `${$bar}`. The final return value is thus the value of `$bar` instead of the direct value of `$foo` (which would be `bar`):

```
$foo = 'bar';
$bar = 'baz';
echo $$foo; // returns   'baz';
```

+   2. In the next example we have a variable-variable `$foo`, which references a multi-dimensional array with a `bar` key and a `baz` sub-key:

```
$foo = 'bar';
$bar = ['bar' => ['baz' => 'bat']];
// returns   'bat'
echo $$foo['bar']['baz'];
```

+   3. In PHP 5, parsing occurs right-to-left, which means the PHP engine would be looking for an `$foo` array, with a `bar` key and a `baz` sub-key The return value of the element would then be interpreted to obtain the final value `${$foo['bar'] ['baz']}`.

+   4. In PHP 7, however, parsing is consistently left-to-right, which means that `$foo` is interpreted first (`$$foo` → `['bar']['baz']`).

+   5. In the next example you can see that `$foo->$bar['bada']` is interpreted quite differently in PHP 5, compared with PHP 7. In the following example, PHP 5 would first interpret `$bar['bada']`, and reference this return value against a `$foo` object instance. In PHP 7, on the other hand, parsing is consistently left-to-right, which means that `$foo->$bar` is interpreted first, and expects an array with a `bada` element. You will also note, incidentally, that this example uses the PHP 7 *anonymous class* feature:

```
// PHP 5:  $foo->{$bar['bada']}
// PHP 7:  ($foo->$bar)['bada']
$bar = 'baz';
// $foo = new class
```
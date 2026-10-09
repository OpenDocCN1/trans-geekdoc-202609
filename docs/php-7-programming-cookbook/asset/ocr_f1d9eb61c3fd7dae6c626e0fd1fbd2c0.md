# Best Practices, Testing, and Debugging

```
foreach ($a as $row) {
    $table .= '<tr><td>';
    $table .= implode('</td><td>', $row);
    $table .= '</td></tr>';
}
$table .= '</table>';
return $table;
```

+   6. We can construct a simple test that confirms that the output contains `<table>`, one or more characters, followed by `</table>`. Further, we wish to confirm that a `<td>B</td>` element exists. When writing the test, we build a test array that consists of three sub-arrays containing the letters A–C, D–F, and G–I. We then pass the test array to the function, and run assertions against the result:

```php
public function testTable()
{
    $a = [range('A', 'C'),range('D', 'F'),range('G','I')];
    $table = table($a);
    $this->assertRegExp('!^<table>.+</table>$!', $table);
    $this->assertRegExp('!<td>B</td>!', $table);
}
```

+   7. To test a class, instead of including a library of functions, simply include the file that defines the class to be tested. For the sake of illustration, let’s take the library of functions shown previously and move them into a Demo class:

```php
<?php
class Demo
{
    public function add($a, $b)
    {
        return $a + $b;
    }

    public function sub($a, $b)
    {
        return $a - $b;
    }
    // etc.
}
```
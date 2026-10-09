# Working with PHP Functional Programming

```
```
$g = someBooleanHint(0,0);   
$$s = someBooleanHint('');
var_dump($b, $i, $f, $s);
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

```

If you now try the same function call, but pass in a non-scalar data type, a TypeError is thrown:

```
```
try {
    $a = someBoolHint([1,2,3]);
    var_dump($a);
} catch (TypeError $e) {
    echo $e->getMessage();
}
try {
    $o = someBoolHint(new stdClass());
    var_dump($o);
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

```

Here is the overall output:

![](bbox=[0.24, 0.52, 0.74, 0.81])
# Part II: Learning the Language

```
echo "<p>My car's manufacturer is " . $myCar->manufacturer . "</p>;"
echo "<p>My car's engine size is " . $myCar->engineSize . "</p>;"
echo "<p>My car's fuel type is " . $myCar->fuelType . "</p>;"
echo "<h2>The $myCar Object:</h2><pre>
print_r($myCar);
echo "</pre>";
```

?

<body>
</html>

![](bbox=[0.115, 0.305, 0.815, 0.705])

# Using_get() and __set()

Some properties:

My car's manufacturer is Volkswagen.
My car's engine size is 1.8.
My car's fuel type is.

The $MyCar Object:

```
(
    [manufacturer] => Volkswagen
    [model] => Beetle
    [color] => red
    [_extraData:private] => Array (
        [engineSize] => 1.8
        [otherColors] => Array (
            [0] => green
            [1] => blue
            [2] => purple
        )
    )
)

```

Done

8-3

# It Works

This script creates the familiar Car class containing some fixed properties - $manufacturer, $model, and $ also adds a private array, $_extraData. The Car class also contains a __get() method that looks up the requested property name in the keys of the $_extraData array, returning the corresponding value in the array (if found). The corresponding __set() method takes the supplied property name and value, and stores the value in the $_extraData array, keyed by the property name.

186
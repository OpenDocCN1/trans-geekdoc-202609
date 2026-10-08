Whether you can access an attribute from outside the class is determined by access modifiers, discussed later in this chapter. This example does not restrict access to the attributes, so you can access them from outside the class as follows:

```
class className
{
    public $attribute;
    $a = new className();
    $a->attribute = "value";
    echo $a->attribute;
```

# Calling Class Operations

You can call class operations in the same way that you access class attributes. Say you have the class

```
class className
{
    function operation1()
{
    function operation2($param1, $param2)
{}
}
```

and create an object of type className called $a as follows:

```
$a = new className();
```

You then call operations the same way that you call other functions: by using their name and placing any parameters that they need in brackets. Because these operations belong to an object rather than normal function, you need to specify which object they belong. The object name used in the same way as you would use it to access an object’s attributes, as follows:

```
$a->operation1();
$a->operation2(12, "test");
```

If the operations return something, you can capture return data as follows:

```
$x = $a->operation1();
$y = $a->operation2(12, "test");
```
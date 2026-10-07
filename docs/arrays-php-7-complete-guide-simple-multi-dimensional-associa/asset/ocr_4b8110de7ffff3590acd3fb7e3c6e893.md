```
function subtract($value, $number)
{
  $value -= $number;
  return $value;
}
```

```
function multiply($value, $number)
{
  $value *= $number;
  return $value;
}
```

```
function divide($value, $number)
{
  $value /= $number;
  return $value;
}
```

print array_reduce($numerical_values, "add"). "<br>";
print array_reduce($numerical_values, "subtract"). "<br>";
print array_reduce($numerical_values, "multiply", -5). "<br>";; // start with a $value of -5
print array_reduce($numerical_values, "divide", 5). "<br>"; //start with a $value of 5

Output:

55
-55
-18144000
1.3778659611993E-6

* array_reduce allows you to create your own function to traverse through an array, pick each item, and do something with the item. In these examples, functions are shown to add, subtract, multiple, and divide the items in the array.
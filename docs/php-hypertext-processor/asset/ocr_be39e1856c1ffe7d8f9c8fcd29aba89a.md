```
}
if( !$b ){
    echo "TEST8 : b is true <br/>";
}else{
    echo "TEST8 : b is false<br/>";
}
?>
</body>
</html>
```

This will produce the following result:

```
TEST1 : Either a or b is false
TEST2 : Either a or b is false
TEST3 : Either a or b is true
TEST4 : Either a or b is true
TEST5 : a is true
TEST6 : b is true
TEST7 : a is false
TEST8 : b is false
```

# Assignment Operators

PHP supports the following assignment operators:

| Operator | Description | Example |
| :--- | :--- | :--- |
| = | Simple assignment operator, Assigns values from right side operands to left side operand | C = A + B will assign the value of A + B into C |
| += | Add AND assignment operator, It adds right operand to the left operand and assign the result to left operand | C += A is equivalent to C = C + A |
| -= | Subtract AND assignment operator, It subtracts right operand from the left operand and assign the result to left operand | C -= A is equivalent to C = C - A |
consistent with the logic used in other programming languages.

PHP also provides the method `array_fill` which will accomplish the same task as the previous example.

```
$customer_record = array_fill(0, 3, array_fill(0, 5, "default"));
```

The statement will create and fill each position in a $customer_record two-dimensional array with the value "default".

The array_fill syntax is:

Array name = array_fill(first subscript in array, last subscript in array, value used to fill array);

In the example, four rows are created (0, 1, 2, 3) as indicated by 0, 3. Each row contains an array (shown by the third position creating another array) with six columns (0, 1, 2, 3, 4, 5) as indicated by 0, 5. The limitation of using this method is that we need to know the initial size of the array. Of course, we can always add more rows and columns as needed.

```
$customer_record = array_fill(0, 5, "default");
```

For one dimensional array, we include the starting subscript (0), the ending subscript (5), and the value we want to place in each position ("default").

The same logic shown in this chapter can be used for arrays that have more than two dimensions. The number of subscripts is determined by the number of dimensions, as is the number of foreach loops.

```
$square_array[$height][$length][$width] = 123;
foreach($square_array as $height => $height_array)
{
    foreach($height_array as $length => $length_array)
    {
        foreach($length_array as $width => $width_value)
        {
            print $width_value;
            $square_array[$height][$length][$width] = 345;
        }
    }
}
```
```
If($subscript != -1)
{ $customer_record[$subscript] = $value;
else
{ array_push($customer_record, $value);
}
update_array_value("770-777-7777", 6);
update_array_value("770-777-7777");
update_array_value("Peter", 0);
```

This update method allows us to insert individual values values or actually replace values. If a subscript is passed, then the value passed into the location requested. If a subscript is not provided, the array_push function is called to place the value at the end of the array.

update_array_value("770-777-7777", 6);

Using the statement above, the phone number would be placed in position six. Even though there is not a position six in this example, PHP will create a position six, as we have seen from other examples. Thus, this is actually inserting the phone number.

update_array_value("770-777-7777", 6);

Using this format, causes the $subscript to be set to -1 since a default value was provided in the function declaration statement.

```
function update_array_value($value, int $subscript = -1)
```

This will cause the else part of the if statement to execute.

If($subscript != -1)

The array_push function will then be used to insert the phone number at the end of the array. This also places the phone number is position six.

update_array_value("Peter", 0);

This final statement passes both an exiting subscript and a value. This would cause the top of the if statement to execute. The value (Peter) would replace the current value in position 1.

As you will see frequently, once you get to using arrays, you will find the amount of code needed to process the information is much less. Example 1-7 has only four executable statements. Example 1-3 (and Example 1-4) has seven executable statements. This demonstrates that using arrays is more efficient than using individual properties. Arrays provide us the ability to
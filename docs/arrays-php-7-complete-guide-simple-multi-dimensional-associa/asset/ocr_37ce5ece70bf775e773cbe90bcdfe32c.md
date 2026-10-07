```
<input type='submit'
value="Click to submit your information" />
</form>
</body>
</html>
```

In Example 1-5, each html name element has been replaced by a position in the customer_record array. This html array is dynamically created, just like PHP arrays. The value in the first textbox (which will be the customers first name) is now placed into customer_record[0].

The html form can now pass this array to the PHP program via the post method without any other changes.

Example 1-7 – process_customer_array.php

```
<?php
$customer = filter_input_array(INPUT_POST);
$customer_record = validate_array($customer["customer_record"]);
print "Your name is $customer_record[0] $customer_record[1].";
You live at $customer_record[2], $customer_record[3],
$customer_record[4], $customer_record[5];";
?
```

As you can see from Example 1-7, we actually can use less coding to pull the html array into the program. The program includes a PHP filter_input_array method which pulls in the complete array created by the html form. It also filters out any harmful data, as html symbols <>.

Note: The filter_input_array method would not verify that the fields have the correct information, such as 15 or less alphabetic characters in the first_name field (now called customer_record[0]). A validate_array method can be created to accept the array and pass individual values to the correct validation.

```
function validate_array($input_array);
{
$value = validate_first_name($input_array[0]);
$value = validate_last_name($input_array[1]);
$value = validate_address($input_array[2]);
```
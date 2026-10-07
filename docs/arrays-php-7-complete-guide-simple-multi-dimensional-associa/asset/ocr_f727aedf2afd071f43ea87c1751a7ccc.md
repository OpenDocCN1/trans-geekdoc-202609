created.

print_r($customer_record);

Array (
[0] =>

Array ( [0] => Pete [1] => Smith [2] => 123 Main Street [3] => Atlanta [4] => GA [5]
=> 30001 )

[1] =>

Array ( [0] => Sally [1] => Parisi [2] => 101 South Street [3] => Atlanta [4] => GA
[5] => 30001 )

Note: The print_r method will display the information about without the line breaks that have been added.

The outside array (Array ( ) controls the rows, which are actually their own arrays. In this example, there are two rows indicated by [0]=> and [1]=> on the lines by themselves. Inside of each row is an Array that controls the columns for row. The first Array contains information about Pete Smith. The second Array contains information about Sally Parisi. You should notice that these arrays are exactly the same format as the one dimensional array that we discussed in chapter 1. In PHP, two-dimensional arrays are actually individual one-dimensional arrays held together by an array that surrounds them.

We can create this two dimensional array without specifying the subscript numbers (as shown with one dimensional arrays)?

When using the dynamic approach of creating the positions when needed, we have to tell PHP when to start a new array or row (when to switch to which array contains the Pete information to the array that contains the Sally information). One way we can do this by using a counting variable.

Example 2-1 process_customer_twodim.php

```
<?php
$I = -1;
$customer_record[+$I][][] = 'Pete';
$customer_record[$I][] = 'Smith';
$customer_record[$I][][] = '123 Main Street';
$customer_record[$I][][] = 'Atlanta';
```
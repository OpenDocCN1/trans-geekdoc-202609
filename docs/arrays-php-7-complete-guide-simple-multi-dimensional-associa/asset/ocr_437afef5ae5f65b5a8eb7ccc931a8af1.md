produces the same results as Example 2-1. You need to be careful to include all the required commas as shown above. Also note that the semicolon is still needed at the end of the complete statement.

We can still change and add additional values in the array using the approach we have seen before.

```
$customer_record[0][0] = 'Peter';
```

```
$customer_record[0][6] = '770-770-7777';
```

```
$customer_record[2] = array('Jake', 'Boukari',
```

```
‘111 Peachtree Street', 'Atlanta', 'GA', 30011);
```

Array (

```
[1] => Array ([0] => Sally [1] => Parisi [2] => 101 South Street [3] => Atlanta [4] => GA [5] => 30001
```

```
[2] => Array ([0] => Jake [1] => Boukari [2] => Peachtree Street [3] => Atlanta [4] => GA [5] => 30001
```

)

PHP arrays allow a lot of flexibility. We are able to change a value in the original array (replacing Pete with Peter). The array now contains his phone number. We were also able to add a complete new array inside the customer_record array (There is now a Jake array). To accomplish these tasks in other programming languages would take a lot more code.

However, we are not dynamically creating the array as we have seen previously. Soon we will see an example showing how to dynamically create an array and add rows without knowing the size of the current array.
When using this method to walk through an array, you need an assignment statement and an echo statement for every value in the array — for each of the 50 states. The output is a list of all the state capitals.

This method gives you flexibility. You can move through the array in any manner — not just one value at a time. You can move backwards, go directly to the end, skip every other value by using two next statements in a row, or whatever method is useful. However, if you want to go through the array from beginning to end, one value at a time, PHP provides foreach, which does exactly what you need much more efficiently. foreach is described in the next section.

# Using foreach to walk through an array

foreach walks through the array one value at a time and executes the block of statements by using each value in the array. The general format is

```
foreach( $arrayname as $keyname => $valuename )
{
    block of statements;
}
```

Fill in the following information:

+   ✓ *arrayname*: The name of the array that you’re walking through.
+   ✓ *keyname*: The name of the variable where you want to store the key. *keyname* is optional. If you leave out `$keyname =>`, the value is put into `$valuename`.
+   ✓ *valuename*: The name of the variable where you want to store the value.

For instance, the following foreach statement walks through the sample array of state capitals and echoes a list:

```
$capitals = array ( "CA" => "Sacramento", "TX" => "Austin",
    "OR" => "Salem" );
ksort ($capitals);
foreach ( $capitals as $state => $city )
{
    echo "$city, $state<br>";
}
```

The preceding statements give the following Web page output:

```
Sacramento, CA
Salem, OR
Austin, TX
```

You can use the following line in place of the foreach line in the previous statements.
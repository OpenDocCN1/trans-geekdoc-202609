# Reversing an Array

Sometimes you may want to reverse the order of an array. The simplest way to do this is with the function array_reverse(), which takes an array and creates a new one with the same contents in reverse order.

Using the range() function usually creates an ascending sequence, as follows:

```
$numbers = range(1,10);
```

You can then use the array_reverse() function to reverse the array created by range():

```
$numbers = range(1,10);
$numbers = array_reverse($numbers);
```

Note that array_reverse() returns a modified copy of the array. If you do not want the original array, as in this example, you can simply store the new copy over the original.

Alternatively, you could create the array in descending order in the first place, one element at a time, by writing a for loop:

```
$numbers = array();
for($i=10; $i>0; $i--) {
    array_push($numbers, $i);
}
```

A loop can operate in descending order like this: Use the starting high value and the end of each loop use the -- operator to decrease the counter by one.

Here, we create an empty array and use array_push() for each element to add one new element to the end of an array. As a side note, the opposite of array_push() is array_pop(). This function removes and returns one element from the end of the array.

Note that the desired order is just a range of descending integers, you can also create it in reverse order by passing -1 as the optional step parameter to range():

```
$numbers = range(10, 1, -1);
```

# Loading Arrays from Files

In Chapter 2, "Storing and Retrieval Data," you learned how to store customer orders in a file. Each line in the file looked like this:

```
01:34, 14th September 2015    1 tires 2 oil    3 spark plugs    $145.2    123 Main
Street, Sometown, CA 95128
```

To process or fulfill this order, you could load it back into an array. Listing 3.2 displays the current order file.
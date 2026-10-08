# Chapter 3 Using Arrays

By default, zero is the first element in the array. The same numbering scheme is used in C, C++, Java, and a number of other languages, it might take some getting used to if you are not familiar with it.

As with other variables, you change array elements' contents using the = operator. The following line replaces the first element in the array, 'Tires', with 'Fuses':

```
$products[0] = 'Fuses';
```

You can use the following line to add a new element—'Fuses'—to the end of the array, increasing a total of four elements:

```
$products[3] = 'Fuses';
```

To display the contents, you could use this line:

```
echo $products[0] $products[1] $products[2] $products[3];
```

Note although PHP's string parsing is clever, it can confuse you. If you are having trouble with any array or element not being interpreted correctly when embedded in a double-quoted string, you can either them outside quotes or use complex syntax, which we discuss in Chapter 4, "String Manipulation and Regular Expressions." The preceding echo statement works correctly, but in many of the more complex examples later in this chapter, you will notice that the arrays are outside the quotes.

Like other PHP variables, arrays do not need to be initialized or created in advance. They are automatically created the first time you use.

The following code creates the same $products array created previously with the array() statement:

```
$products[0] = 'Tires'
$products[1] = 'Oil'
$products[2] = 'Spark Plugs'
```

If $products does not already exist, the first line will create a new array with one element. The subsequent lines add values to the array. The array resizing capability capability is not present in many other programming languages.

# Using Loops to Access the Array

Because the array is indexed by a sequence of numbers, you can use a for loop to easily display its contents:

```
for ($i = 0; $i<3; $i++) {
    echo $products[$i]."";
}
```

This loop provides similar output to the preceding code but requires manually writing code to access each element in a large array. The ability to use a simple loop to access each element is a nice feature of arrays. You can also use the foreach loop, specially designed for use with arrays. In this example, you could use it as follows:
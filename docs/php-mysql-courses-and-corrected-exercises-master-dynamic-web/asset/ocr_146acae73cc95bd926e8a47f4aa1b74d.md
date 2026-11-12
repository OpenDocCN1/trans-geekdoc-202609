```
for ($i = 0; $i < $length; $i++) {
   echo $numbers[$i] . "<br>";
}
?>
```

In this example, we have an indexed array called $numbers containing five elements: 10, 20, 30, 40 and 50. The count() function is used to obtain the total number of elements in the array, which is stored in the $length variable.

Next, a for loop is used to iterate through each element of the array using an index. The variable $i is initialized to 0, and the loop continues as long as the value of $i is less than $length. At each iteration, the value of the array element at index $i is displayed with echo, followed by a <br> tag to create a line break in the HTML rendering. Execution of this code displays the following result:
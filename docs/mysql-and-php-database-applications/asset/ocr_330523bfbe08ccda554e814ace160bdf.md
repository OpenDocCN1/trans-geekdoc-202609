# do ...while

The do...while loop is nearly identical to the loop discussed above. The only difference is that the condition is tested after the code in question has been run once.

```
do
{
// code to be used here.
} while (condition);
```

This structure may be useful to you. It may even be vital to scripts you need to write. But in the course of writing seven applications for this book, we didn't need to use it once.

# for

The for loop takes three expressions. The first is evaluated only the first time through the loop. The second argument is a condition that is evaluated every time through the loop; if the condition in the second argument tests false, the loop will end. The third expression will be executed every loop after the first.
As an example, the following would iterate every value in an array and print the value for each element.

```
$myarray = array(jay, bray, john, kristin);
for ($i = 0; $i < count($myarray); $i++))
{
  echo $myarray[$i] . "<br>\n";
}
```

The first time, $i is assigned the value of 0, so the first element in the array will be printed. The next time and each subsequent time, $i will be incremented by one. The loop will end as soon as $i is equal to the length of the array (which would be 4). Remember that the elements in the array start at 0, so the last element in the above array is $myarray[3].
You can also leave the expressions in the loop empty. If you leave the second expression empty, the if condition will evaluate to true, and you will need to make sure that your loop will eventually hit a break statement (break will be discussed soon). The following would be very bad; it would run indefinitely, using your memory and CPU. You'd have to kill the Web server to get this script to stop. It could bring your entire machine down.

```
for ($i = 0; $i++)
{
  echo "$i<br>\n";
}
```
# Core PHP Programming

matching the type of the argument being fetched. The func_num_args function returns the number of arguments available.

Chapter 4, "Functions," discusses functions, including writing functions that accept an unlimited number of arguments.

```
/*
** Function concat
** Input: any number of strings
** Output: string
** Description: input strings are put together in
** order and returned as a single string.
*/
function concat() {
  //start with empty string
  $returnValue = "";

  //loop over each argument
  for($i=0; $i < func_num_args(); $i++) {
    //add current argument to return value
    $returnValue .= func_get_arg($i);
  }

  return ($returnValue);
}

//prints "OneTwoThree"
print(concat("One","Two", "Three") . "<BR\n";
?>
```

# array func_get_args()

Use func_get_args to get an array containing all the arguments passed as arguments to the function. The elements of the array are indexed by winintegers, starting with zero. This provides an alternative to using func_get_arg and func_num_args.

```
/*
** Function gcd
** Input: any number of integers
** Output: integer
** Description: Returns the greatest common
** denominator from the input.
*/
function gcd() {
  /*
```

IT-SC book 179
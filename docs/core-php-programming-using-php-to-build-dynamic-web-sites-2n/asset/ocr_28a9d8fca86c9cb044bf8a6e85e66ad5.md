# Core PHP Programming

array to the function, which in turn would pull the items out of the array. Alternatively, you could write a function that accepted a variable number of arguments, as I have in Listing 4.6.

# Listing 4.6 Function with Variable Number Arguments

```
<?php
function makeList()
{
    print("<OL\n");

    for($i=0; $i<$func_num_args(); $i++) {
        print("<li>" . func_get_arg($i) . "</li>\n");
    }
    print("</OL\n");
}

makeList("PHP", "MySQL", "Apache");
?>
```

# Recursion

Your functions may make calls to other functions, and they may also make calls to themselves. The process of a function calling itself is recursion. This circular definition leads to elegant algorithms. The problem is broken down into a small task that's repeated many times.

Recursive definitions are common in mathematics. Consider this definition of an integer: the sum or difference between one and any other integer is an integer. Is three an integer? Yes, because one plus one must be an integer, with one being two. And the sum of one and two must also be an integer.

Recursion is a difficult concept to understand, but it usually takes clearcode. Take a look at Listing 4.7. The function checkInteger takes a number as input. We know that the difference between integer and one is an integer. If the function gets a number bigger than one, it checks the number minus one. If we start with a number less than zero, we multiply it by negative one check it. Eventually we will reach a number between zero and one, unless we are passed zero, which is an integer.

# Listing 4.7 Using Recursion
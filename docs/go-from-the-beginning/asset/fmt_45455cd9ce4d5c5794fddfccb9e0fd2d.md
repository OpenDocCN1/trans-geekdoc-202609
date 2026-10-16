
`if` and `else` take you far. Sometimes, it’s not enough. You might need to grade a course at different levels depending on the points achieved on the exam. For this situation, you need an `else if` construct, a construct that will be evaluated if the `if` construct evaluates to false. It differs from `else` in that it also takes an expression. Here’s an example where it’s used:

```
1 if testScore >= testScoreGrade5 {
2   fmt.Println("Top mark")
3  } else if testScore >= testScoreGrade4 {
4   fmt.Println("Pass with distinction")
5  } else if testScore >= testScoreGrade3 {
6   fmt.Println("Pass with distinction")
7  } else {
8   fmt.Println("Failed")
9  }
```

## Multiple expressions

Your expression can examine more than one variable or condition. There are Boolean operators you can use to help you. Here are some operators you are likely to encounter:

*   `&&`, evaluates to true if values on the left and right side are both true. Here’s an example of this operator in use:

    ```
    1   hasGas := true
    2   hasKeyInIgnition := true
    3   if hasGas && hasKeyInIgnition {
    4     fmt.Println("Can drive car")
    5    }
    ```

    In the preceding code, the expression will evaluate to true as both `hasGas` and `hasKeyInIgnition` is true.

*   `||` , evaluates to true if either left or right value is true. Here’s an example of this operator in use:

    ```
    1 hasBurger := true
    2 hasSandwich := false
    3 
    4 if hasBurger || hasSandwich {
    5   fmt.Println("Can eat")
    6 }
    ```

    In the preceding code, `hasBurger` is true and that’s enough for this expression to become true.

*   `!`, also known as NOT, it will negate the expression. Here’s an example:

    ```
    1  hasSandwich := false
    2 
    3  if !hasSandwich {
    4   mt.Println("No sandwiches, then I will starve, I only eat sandwiches")
    5  }
    ```

    Above, the expression will evaluate to true, thanks to the negation with `!`.

## Assignment - create a program that tests your Boolean logic

In this assignment, you are creating a program that tests out various Boolean logic.

1.  Create a file *main.go* and give it the following content: 

    ```
     1  package main
     2 
     3  import "fmt"
     4  
     5  func main() {
     6   testScoreGrade5 := 80
     7   testScoreGrade4 := 60
     8   testScoreGrade3 := 50
     9   testScore := 49
    10  
    11   hasGas := true
    12   hasKeyInIgnition := true
    13  
    14   hasBurger := true
    15   hasSandwich := false
    16  
    17   printMessage := true
    18   if printMessage {
    19    fmt.Println("Message")
    20   }
    21  
    22   if testScore >= testScoreGrade5 {
    23    fmt.Println("Top mark")
    24   } else if testScore >= testScoreGrade4 {
    25    fmt.Println("Pass with distinction")
    26   } else if testScore >= testScoreGrade3 {
    27    fmt.Println("Pass with distinction")
    28   } else {
    29    fmt.Println("Failed")
    30   }
    31  
    32   if hasGas && hasKeyInIgnition {
    33    fmt.Println("Can drive car")
    34   }
    35  
    36   if hasBurger || hasSandwich {
    37    fmt.Println("Can eat")
    38   }
    39  
    40   if !hasSandwich {
    41    fmt.Println("No sandwiches, then I will starve, I only eat sandwiches")
    42   }
    43  }
    ```

2.  Run the command `go run main.go`, to run the program

    ```
    1 goo run main.go
    ```

    You should see the following output:

    ```
    1  Message
    2  Failed
    3  Can drive car
    4  Can eat
    5  No sandwiches, then I will starve, I only eat sandwiches
    ```

3.  Try playing around with the code, how does the output change if you change `testScore` value to 51, 62, 3 or 90?

## 🚀 Challenge

A test score shouldn’t be negative, how can you add a check for that?

## Solution

```
 1 package main
 2 
 3 import "fmt"
 4 
 5 func main() {
 6 	testScoreGrade5 := 80
 7 	testScoreGrade4 := 60
 8 	testScoreGrade3 := 50
 9 	testScore := 49
10 
11 	hasGas := true
12 	hasKeyInIgnition := true
13 
14 	hasBurger := true
15 	hasSandwich := false
16 
17 	printMessage := true
18 	if printMessage {
19 		fmt.Println("Message")
20 	}
21 
22 	if testScore >= testScoreGrade5 {
23 		fmt.Println("Top mark")
24 	} else if testScore >= testScoreGrade4 {
25 		fmt.Println("Pass with distinction")
26 	} else if testScore >= testScoreGrade3 {
27 		fmt.Println("Pass with distinction")
28 	} else {
29 		fmt.Println("Failed")
30 	}
31 
32 	if hasGas && hasKeyInIgnition {
33 		fmt.Println("Can drive car")
34 	}
35 
36 	if hasBurger || hasSandwich {
37 		fmt.Println("Can eat")
38 	}
39 
40 	if !hasSandwich {
41 		fmt.Println("No sandwiches, then I will starve, I only eat sandwiches")
42 	}
43 }
```

## Review & Self Study

Have a look at this [official tutorial on flow control](https://go.dev/tour/flowcontrol/6) using a Go sandbox.

# Converting between types

This chapter covers how to convert between strings and numbers.

## Introduction

This chapter will:

*   Introduce uses cases where data conversion makes sense.

*   Showcase how to use `strconv` library.

## Why convert between types

There are different data types and a need to convert between them. For example, we often need to convert between text and numbers for presentational and other reasons. We also need to convert between numbers and decimals without losing information in the process.

The main package for dealing with conversions in Go is `strconv`.

## Use case - command-line arguments

Let’s show a common case where you start off with strings and you need to make it into numbers, command-line arguments. To use command-line arguments in a program, you need the `os` package.

`os.Args` points to an array representing your command line arguments. To access a specific argument, you would use the index operator `[]` like so:

```
1 arg := os.Args[1]
```

You can then start your program like so:

```
1 go run main.go 1
```

The 1 would then be stored in `arg`.

### Finding the type

What type is `arg` in our code above? There are some ways to find out:

*   **IDE**, if you use for example Visual Studio Code and the Go plugin, hovering over the code, it will tell you that `os.Args` is a string array, `string[]`.

*   **PrintF() and %T**. One of the easiest ways to find the type is typing like so:

```
1    Printf("%T", os.Args[1])
2    Printf("%T", 1)
```

You would get an output like so:

```
1    string
2    int
```

*   **Type coercion**, you could try to modify that code and coerce it to be an integer like so, now what?

    ```
    1   var no int = os.Args[1]
    ```

    You get an error:

    ```
    1   cannot use os.Args[1] (type string) as type int in assignment
    ```

*   **Use reflection**. Another way to find the above is by using the `reflect` package like so:

    ```
     1   package main
     2   
     3   import (
     4     "reflect"
     5     "fmt"
     6     "os"
     7   )
     8   
     9   func main () {
    10     arg := os.Args[1]
    11     fmt.Println(reflect.TypeOf(arg))
    12   }
    ```

    Now, the program will print “string” as the type.

### Addressing the problem with `strconv`

Ok, so we know what type something is, what if we need to use these command-line arguments, which are of type `string`, and feed them into let’s say a calculator program?

Consider the below code, that at present WOULDN’T compile:

```
 1 package main
 2 
 3 import (
 4   "fmt"
 5   "os"
 6 )
 7 
 8 func add(first int second) int {
 9   return first + second
10 }
 11 
 12 func main() {
13   add(os.Args[1], os.Args[2]) // this would NOT compile
14 }
```

The reason is that the values on `os.Args[1]` and `os.Args[2]` are `string` not `int`. To fix this issue, we need to use the conversion package `strconv`.

## Convert from string to int with `strconv`

To convert strings to integers, we need to use `strconv` and call the `Atoi()` (stands for Ascii to integer) function like so:

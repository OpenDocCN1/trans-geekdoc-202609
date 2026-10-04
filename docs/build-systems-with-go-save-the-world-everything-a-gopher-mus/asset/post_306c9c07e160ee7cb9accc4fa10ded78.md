A function receives none or several parameters and returns none or several values. Functions are defined by keyword `func`, the arguments with their types, and the types of the returned values.

In example 2.6, the sum function returns the sum of two int arguments a and b.

## Example 2.6: Function with two arguments.

```go
package main
import "fmt"

func sum(a int, b int) int {
	return a + b
}

func main() {
	result := sum(2,2)
	fmt.Println(result)
}
```

It is possible to return multiple values like shown in example 2.7.

## Example 2.7: Function returning several values.

```go
package main
import "fmt"

func sum(ops ...int) (int, int) {
	return a + b, a - b
}

func main() {
	sum, subs := ops(2,2)
	fmt.Println("2+2=", sum, "2-2=", subs)
	b, _ := ops(10,2)
	fmt.Println("10+2=", b)
}
```

Functions can receive an undetermined number of arguments. These are called variadic functions. 2.8 declares a function to compute the sum of several numbers. Variadic arguments are identified with `...` before the type. These arguments must have the same type and can be treated as an array. How to iterate arrays is explained in more detail in section 3.2.2.

## Example 2.8: Variadic function

```go
package main
import "fmt"

func sum(nums ...int) int {
    total := 0
    for _, a := range(nums) {
        total := total + a
    }
    return total
}

func main() {
    total := sum(1,2,3,4,5)
    fmt.Println("The first five numbers sum is", total)
}
```

Functions can receive other functions as arguments. In Example 2.9, the function doit expects a function and two parameters. Notice how the operator argument is a function where we specify the type of its arguments and returned values. When the doit can modify its behavior changing the operator argument. In this case, we can sum function and multiply numbers using the corresponding functions.

## Example 2.9: Functions as arguments.

```go
package main

import "fmt"

func doit(operator func(int,int) int, a, b int) int {
    return operator(a,b)
}

func sum(a int, b int) int {
    return a + b
}

func multiply(a int, b int) int {
    return a * b
}

func main() {
    t := doit(sum, 2, 3)
    d := doit(multiply, 2, 3)
    fmt.Println("2+3=", t)
    fmt.Println("2*3=", d)
}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_24_0.png)

Go permits anonymous functions, and these functions can be closures. A closure is a function that can refer to variables outside its body. This can be particularly useful to define inline functions or solve complex problems that require recursion.

In Example 2.10, the function accumulator defines a closure that is bounded to variable i. Statements a := accumulator(1) and b := accumulator(2) create two functions with different starting i variables. For this reason, for the same number of iterations outputs for a and b differ.

## Example 2.10: Functions closure.

```go
1 package main
2
3 import "fmt"
4
5 func accumulator(increment int) func() int {
6	i := 0
7	return func() int {
8		i := i + increment
9		return i
10	}
11}
12
13 func main() {
14
15
16	a := accumulator(1)
17	b := accumulator(2)
18
19	for i:=0;i<5;i++ {
20		fmt.Printf("%d,%d\n", a(),b())
21	}
22}
```

## 2.4 POINTERS

Go works with arguments as values or references. When working with references we talk about pointers. A pointer addresses a memory location instead of a value. In Go pointers are identified following the C notation with a star. For example, * indicates a pointer to a value of type τ.

Example 2.11 has two functions a and b that set incoming argument to zero. The code in the main function declares a variable x and call these functions. Notice that a does not change x because it receives values as arguments. However, b sets x to zero because it receives a pointer to the value. See how this operator returns the memory address of variable.

## Example 2.11: Passing values and references to a function.

```go
1 package main
2
3 import "fmt"
4
5 func a (i int) {
6	i = 0
7}
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_25_0.png)

```go
8
 func b (i *int) {
10   *i = 0
11 }
12
13 func main() {
14   x := 0
15
16   a(x)
17   fmt.Println(x)
18   b(&x)
19
20   fmt.Println(x)
21 }
22
```

How to decide when to use a pointer or a value depends on use case. If a value is intended to be modified in different parts of the code, passing pointers seems reasonable.

## 2.5 NIL AND ZERO VALUES

A really important concept in Go is the value. When a variable is created and not initialized, the compiler automatically assigns a default value. This value depends on the variable. The keyword nil specifies a particular value for every non-initialized type. Notice that nil is not an undefined value like in any programming languages, nil is a value itself.

The output from Example 2.12 shows the zero value for various types. In general zero will be the value for numeric types such as int or float. In the case of string the empty string ("") is the zero value, not the numeric value (0). For pointers, functions and other types nil is the default value.

> **Example 2.12:** Zero values during initialization.

```go
1 package main
2
3 import "fmt"
4
5 func main() {
6   var a int
7   fmt.Println(a)
8
9   var b *int
10  fmt.Println(b)
11
12  var c bool
13  fmt.Println(c)
14
15  var d func()
16  fmt.Println(d)
17
18  var e string
19 fmt.Printf("%s",e)
20 
21 }
```

## 2.6 LOOPS AND BRANCHES

No program is complete without control flow. In any other programming language, Go offers a set of constructions to define loops and branches.

### 2.6.1 If/else

The if statement permits the definition of branch executions using boolean expressions with the following construction.

```go
if condition {
  // -
} else {
  // -
} else {
  // -
}
```

Compared with other verbose programming languages Go does not require parenthesis around the defined condition, only the braces.

Example 2.13 entails tossing a coin and tell us if we get head or tail.

**Example 2.13:** if/else example.

```go
1 package main
2 import (
3   "fmt"
4   "math/rand"
5   "time"
6 )
7
8 func main() {
9   rand.Seed(time.Now().UnixNano())
10  x := rand.Float32()
11
12  if x < 0.5 {
13    fmt.Println("head")
14  } else {
15    fmt.Println("tail")
16  }
17 }
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_27_0.png)

In the example, we generate a random number using the `rand.Float32()` function. The `x` variable goes from 0 to 1 then, when x is less than 0.5 we get, otherwise tail. The code in line 10 is just an initialization of the random generator. We set the initial random seed with the CPU time to get a different x value in every execution.

> If you are familiar with other programming languages you may be wondering how the ternary operator is. Something like the one you can find in C: condition ? statement : statement. There is no such thing in Go. Those operators do not follow the simplicity concepts from.

## 2.6.2 Switch

The switch operator is particularly useful when you want to take action for several values of the same variable.

For example, the program described in Example 2.14 takes a number and prints the name of the corresponding finger. This is by enumerating the values we want to control and adding the corresponding statement before we define the next value that requires a different statement. Finally, we set the special case default that is reached when the value is not controlled by any case.

## Example 2.14: switch example.

```go
1 package main
2
3 import "fmt"
4
5 func main() {
6 var finger int = 1
7
8 switch finger {
9 case 0:
10 fmt.Println("Thumb")
11 case 1:
12 fmt.Println("Index")
13
14 case 2:
15 fmt.Println("Middle")
16 case 3:
17 fmt.Println("Ring")
18 case 4:
19 fmt.Println("Pinkie")
20 default:
21 fmt.Println("Humans usually have no more than five fingers")
22 }
23
```

Branching with switch is very versatile. You do not need to define the variable you want to check. You can simply start checking your cases and even you can use conditionals instead of constants.

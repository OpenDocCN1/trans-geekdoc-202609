# 5.6. Custom Functions

takes one string argument (e.g., a filename), and returns a string which is the filename with the captured suffix.

```
addZip := MakeAddSuffix(".zip")
addTgz := MakeAddSuffix(".tar.gz")
fmt.Println(addTgz("filename"), addZip("filename"), addZip("gobook.zip"))

filename.tar.gz filename gobook.zip
```

This snippet shows the creation of two closures, addZip() and addTgz(), and some calls to them.

# 5.6.4. Recursive Functions

A recursive function is a function that calls itself, and mutually recursive functions are functions that call each other. Go fully supports recursive functions.

Recursive functions generally have the same structure: an "outcase" and a "body". The outcase is usually a conditional statement such as an if statement that is used to stop the recursion based on one of the arguments passed. The body is where the function does some processing and includes at least one to itself (or to its mutually recursive partner)—this must pass an argument that is changed from one it received and will be checked in the outcase to ensure that the recursion will ultimately finish.

Recursive functions make it easy to work with recursive data structures (such as binary trees), but they can be inefficient for, say, numerical computations.

We will start with a very simple (and inefficient) example, just to show how recursion is done. First we will see a call to a recursive function and its output, then we will see the recursive function itself.

```
for n := 0; n < 20; n++ {
    fmt.Print(Fibonacci(n), " ")
}
fmt.Println()
0 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181
```

The Fibonacci() function returns the n-th Fibonacci number.

```
func Fibonacci(n int) int {
    if n < 2 {
        return n
    }
    return Fibonacci(n-1) + Fibonacci(n-2)
}
```
# 3.2.3.1 Break statements

A break statement is used to terminate the loop or statement in which it presents. The break statement is used to terminate the execution of the current loop.

The example given below gives the output numbers starting from 1 and at break is encountered and it goes out of the loop:

# Program 3.7

// Go program to explain break statements

```
```go
package main

import "fmt"

// Main function
func main() {
for x := 1; x <= 5; x++ {

fmt.Println("Number:", x)

// For loop breaks when the value of x = 4
if x == 4 {
break
}
}
```
```
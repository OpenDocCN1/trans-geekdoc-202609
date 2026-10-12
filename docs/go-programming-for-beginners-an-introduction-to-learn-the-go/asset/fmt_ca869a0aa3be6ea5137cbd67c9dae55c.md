
# 4. Syntax

Now that we know how to compile and execute a program, let us begin learning the actual programming concepts of Go language. Go is a case sensitive language. We may say that the words “programming”, “Programming” and “PROGRAMMING” are the same but Go compiler treats all of them differently.

## 4.1 Statements

A statement is used to perform a task or a combination of tasks. It can be made up of anything such as operators, function calls, variable assignments, etc. In simple terms, a statement is a line of code that executes one or more instructions such as printing something on the screen, performing arithmetic operations, reading from a file, etc. In Go, one statement is placed on one line. Here are a few examples of statements:

```
fmt.Printf (“Hello”)
var x int = 51
msg = “Go book”
```

## 4.2 Comments

Comments are used to mark or explain a piece of code. These are ignored by the compiler and have no outcome on the execution of a program. Hence, comments are only relevant to us humans. A comment begins with `/*` character sequence and ends with `*/` character sequence. Here are a few examples:

```
/*This is a comment*/
/* You can have any text within this character sequences */
```

This book contains several programming examples. Each program contains comments which explain what a particular section of code does. Whenever you stumble upon programs in this book, make sure you read the comments well.

## 4.3 Identifiers

An identifier is a name given to a variable, class, object, function or anything else that is identifiable. Identifier names can contain alphanumeric characters but the first character has to be an alphabet. The only permitted special character is underscore (`_`).

## 4.4 Keywords

Keywords are reserved words that cannot be used as identifier names. Here is a list of keywords in Go:

| break | default | func | interface | select |
| :--- | :--- | :--- | :--- | :--- |
| case | defer | go | map | struct |
| chan | else | goto | package | switch |
| const | fallthrough | if | range | type |
| continue | for | import | return | var |

## 4.5 Tokens

A token is any meaningful item in a program. Keywords, identifiers, constants, symbols, string literals, etc. can all be called as tokens.

## 4.6 Basic Program Constituents

A very basic Go program should have the following constituents:

### Package Declaration

Go organizes source files inside the system as packages. A Go program can be used to build a library and also a standalone application. A standalone application is the one which executes on its own while a library cannot execute on its own, it has to be used in some other application. In this book, we will mostly be building standalone applications. The package name for standalone applications should be `main`. This tells the compiler that the Go program it is dealing with is supposed to be built as a standalone application and not a library. This is how you would write a package statement:

```
package <package name>
```

Example:

```
package main
```

### Import Packages

Packages are pre-built libraries which can perform various tasks. Go offers a rich set of packages for different things. Here is general syntax to import packages:

```
import (
    <package 1>
    <package 2>
    <package 3>
    ...
    <package n>
)
```

For handling formatted I/O operations, `fmt` package is used. If you want to write a program to print something on the console, it is considered as a formatted output operation. You would be importing `fmt` package as follows:

```
import ("fmt")
```

### Main Function

A main function serves as an entry point of a program. A program will start executing from the first statement inside the main function. Here is how you would write a main function:

```
func main() {
    /*Statements Here*/
}
```

Let us combine these program constituents and write a Go program that builds but does not do anything. It will have a package declaration statement and an empty main function. We will not be including import `fmt` statement because we are not going to perform any I/O operations:

```
/*Package Declaration Statement*/
package main

/*Mandatory main function*/
func main() {
}
```

**Compile and Execute:**

![](Image00016.jpg)

As seen, the program is built and run successfully. Nothing significant happens on the console as we are not doing anything inside the program. The program starts executing from the empty main function.

# 5. Hello World! Go Program

In the previous chapter, we saw what are the basic constituents of a standalone Go program. We also saw how to write a basic Go program that builds and executes but does not do anything. In this chapter, we will write a program to print something on the console. Printing something on the console is considered as an Output operation. We will be using a function called `Printf` from the `fmt` package. It can be accessed as `fmt.Printf`. General syntax of using this function is:

```
fmt.Printf(<string>)
```

The `Printf` function should be given a string to print. A string is a sequence of characters. While giving a string to this function, the sequence of characters should be enclosed within double quotes. This function actually accepts a formatted string but for simplicity sake, let us only focus on a normal string and worry about formatted string later. If you want to print something on the console, the `fmt.Printf` statement will look something like:

```
fmt.Printf(“Let us print something”)
```

Let us combine whatever we have learnt and write a program to print “Hello World!” on the console:

```
/*Package Declaration Statement*/
package main

/*Import statement, import fmt package*/
import "fmt"

/*Mandatory main function*/
func main() {
    /*Print Hello World! using fmt.Printf function*/
    fmt.Printf("Hello World!")
}
```

**Output:**

![](Image00017.jpg)

Let us try the same program in Go Playground:

![](Image00018.jpg)

You can alternatively use the `Println` function from the same `fmt` package. This function inserts a new line at the end of the printed screen. General Syntax:

```
fmt.Println(<string>)
```

Example:

```
fmt.Println(“Just another string…”)
```

Here is the modified Hello World! program using `Println` function:

```
/*Package Declaration Statement*/
package main

/*Import statement, import fmt package*/
import "fmt"

/*Mandatory main function*/
func main() {
    /*Print Hello World! using fmt.Println function*/
    fmt.Println("Hello World!")
}
```

**Output:**

![](Image00019.jpg)

As seen, there is an extra line of space left after printing Hello World. If you want to insert a new line anywhere in the string, you can use the escape character sequence `\n` inside the string. This will work with `Printf` as well as `Println` functions. Here is an example:

```
/*Package Declaration Statement*/
package main

/*Import statement, import fmt package*/
import "fmt"

/*Mandatory main function*/
func main() {
    /*Print Hello World! using fmt.Printf function*/
    fmt.Printf("\nHello \nWorld!\n")
}
```

**Output:**

![](Image00020.jpg)

There are many more escape character sequences. Another useful one is `\t` which will insert one tab-space in the output string. This will again work with `Printf` and `Println` functions. Here is an example:

```
/*Package Declaration Statement*/
package main

/*Import statement, import fmt package*/
import "fmt"

/*Mandatory main function*/
func main() {
    /*Print Hello World! using fmt.Println function*/
    fmt.Println("\nHello\tWorld!")
}
```

**Output:**

![](Image00021.jpg)

This is the chapter where we learned to build a meaningful console application which prints text on the screen. In almost every subsequent program, we will be printing something or the other on the console and hence you should know your way around `Printf` and `Println` functions really well. It is a good idea to play around with these functions and try to display different strings.


# CHAPTER 2
THE BASICS

This Chapter introduces the basics of Go. Like any programming language, Go uses variables, control loops, and data structures to create programs. You may find this Chapter not long enough to cover all the basics of a programming language. This is one of the greatest advantages of Go, its simplicity. The content of this Chapter reviews all the concepts a Go adopter must know to dive into the language.

## 2.1 PACKAGES AND IMPORTS

If you already read Chapter 1, you will have noticed that every piece of code starts with a package statement. Go programs are organized into packages. A package is a group of one or more source files which is accessible from the same package. Additionally, a package can be exported and used in other packages.

The package main is a special case that informs the compiler to consider that package the entry point for an executable file. Actually, the package main is expected to have a main function in order to be compiled.

A package can be imported into other packages using the keyword import. The line import "fmt" makes the fmt package available to the source file. When importing a package, Go checks the GOPATH and GORO environment variables. The GOPATH points to your workspace and is defined by the installation. GORO points to a custom installation. This variable should not be required unless a custom installation is done. The Go compiler will first check GORO and then the GOPATH when importing a package.

### 2.1.1 Import third-party packages

Programs may require additional packages that are developed by third-parties. For example, the implementation of a database driver. Go is dramatically different importing third-party code compared to other languages. Go forces code transparency by only compiling source code. This means that in order to import third-party packages, the source code must be locally available. Before importing any third-party package you can use the Go command-line to download the code.

For example, the Mongo driver which is available at http://go.mongodb.org/mongo-go-driver we execute:

# Example 2.1: Third-party package download using get.

```
>>> go get go.mongodb.org/mongo-driver
get "go.mongodb.org/mongo-driver" found meta tag get.metadata(Prefix:"go.mongodb.org/mongo-driver",
VCS:"git", RepoRoot:"https://github.com/mongodb/mongo-go-driver.git" at //go.mongodb.org/mongo-driver-go-1
go.mongodb.org/mongo-driver (download)
package go.mongodb.org/mongo-driver: no Go files in /XXXX/src/go.mongodb.org/mongo-driver
```

This downloads the source code from the external repository into ours. Afterwards, we can import the code using import "go.mongodb.org/mongo-driver/mongo". In some cases, the package name may not be very convenient. If required we can use an alias like shown below:

package main

```
import (
    myalias "go.mongodb.org/mongo-driver/mongo"
)
//-
client, err := myalias.NewClient(..)
//..
```

![](img/c7dcb4df7215ed1d3fb76d25373be6c7_18_0.png)

Using get to download third-party code is not a scalable solution. Fortunately, Go modules facilitate the acquisition of packages and their versioning for any project. Go modules are explained in Chapter 12.

## 2.2 VARIABLES, CONSTANTS, AND ENUMS

Variables are the cornerstone of any programming language. This Section explores Go variables and special cases such as constants and enums.

### 2.2.1 Variables

Go is a strong statically typed language. This means that the type of the variable must be fixed at compilation time. Go syntax permits different alternatives when declaring variables as shown in Example 2.2.

> Example 2.2: Declaration of variables.

```go
package main

import "fmt"

func main() {
    var a int
    a = 42

    var aa int = 100

    b := -42

    c := "this is a string"

    var d, e string
    d, e = "var d", "var e"

    f, g := true, false

    fmt.Println(a)
    fmt.Println(aa)
    fmt.Println(b)
    fmt.Println(c)
```

```go
fmt.Println(d)
fmt.Println(e)
fmt.Println(f)
fmt.Println(g)
```

The basic construction of a variable is formed by the reserved word var followed by the variable name and its type. For example, var a declares variable a of type int. Notice that this declares a variable with no value. The type and the value can be set in one line as shown in the example with var a := 10. Similarly using := we can declare and assign a value to the variable; the type will be inferred by the compiler. In our example, b := -42 has type int while c := "this is string".

### 2.2.2 Types

Go comes with basic types described in Table 2.1.

| Type | Description |
| :--- | :--- |
| bool | Boolean |
| string | String |
| int | Signed integers |
| uint | Unsigned integers |
| float32 | Floating numbers |
| float64 | Floating numbers |
| complex64 | Complex numbers |
| rune | Unicode point |
| byte | Byte |

Table 2.1: Basic types

### 2.2.3 Constants

A constant is a value that cannot be changed. Like variables, the type of a constant can be inferred. In our example, we defined Pi without type.

# Example 2.4: Constants declaration

```go
package main

import "fmt"

const (
    PI = 3.14
    Message = "Hello"
)

func main() {
    fmt.Println(PI)
    fmt.Println(Message)
}
```

### 2.2.4 Enums

Enums (enumerates) is a data type consisting of constant values. Classic examples are the days of the week, the months of the year, the states of a system, etc. Enums are intrinsically related to the iota keyword.

# Example 2.5: Enums declaration

```go
package main

import "fmt"

type DayOfTheWeek uint8

const(
	Monday DayOfTheWeek = iota
	Tuesday
	Wednesday
	Thursday
	Friday
	Saturday
	Sunday
)

func main() {
	fmt.Printf("Monday is %d\n", Monday)
	fmt.Printf("Wednesday is %d\n", Wednesday)
	fmt.Printf("Friday is %d\n", Friday)
}
```

## 2.3 FUNCTIONS

Functions are a basic concept in Go. A function encapsulates a piece of code that performs certain operations or logic that is going to be required by other sections of the code. A function is the most basic solution to reuse code.

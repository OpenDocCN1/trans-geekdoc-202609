![](Image00002.jpg)

# Go for Beginners

## A Genius Guide to Go Programming

## Edward Thornton

© Copyright 2021 - All rights reserved.

It is not legal to reproduce, duplicate, or transmit any part of this document in either electronic means or in printed format. Recording of this publication is strictly prohibited and any storage of this document is not allowed unless with written permission from the publisher except for the use of brief quotations in a book review.

# Contents

[Introduction](#text00003.html#introduction)

1. [Why Go?](#text00004.html#chapter-1)

[Designed for Modern Conditions](#text00004.html#subhead-1)

[Advantages of Go](#text00004.html#subhead-2)

[Disadvantages of Go](#text00004.html#subhead-3)

[Who Should Use Go?](#text00004.html#subhead-4)

[Chapter Summary](#text00004.html#subhead-5)

2. [Foundations of Golang](#text00005.html#chapter-2)

[Identifiers, Filenames, and Keywords](#text00005.html#subhead-1)

[Functions](#text00005.html#subhead-2)

[Data Types](#text00005.html#subhead-3)

[Constants](#text00005.html#subhead-4)

[Variables](#text00005.html#subhead-5)

[Operators](#text00005.html#subhead-6)

[Strings](#text00005.html#subhead-7)

[Times and Dates](#text00005.html#subhead-8)

[Chapter Summary](#text00005.html#subhead-9)

3. [You’ve Got It Under Control (Structures)](#text00006.html#chapter-3)

[If-Else](#text00006.html#subhead-1)

[Switch-Case](#text00006.html#subhead-2)

[For](#text00006.html#subhead-3)

[For Range](#text00006.html#subhead-4)

[Break and Continue](#text00006.html#subhead-5)

[Labels: Goto](#text00006.html#subhead-6)

[Chapter Summary](#text00006.html#subhead-7)

4. [Go Functions, What’s Your Function?](#text00007.html#chapter-4)

[Basics of Functions](#text00007.html#subhead-1)

[Return Values and Parameters](#text00007.html#subhead-2)

[Defer, Panic, and Tracing](#text00007.html#subhead-3)

[Built-in Functions](#text00007.html#subhead-4)

[Recursion](#text00007.html#subhead-5)

[Higher-Order Functions](#text00007.html#subhead-6)

[Closures](#text00007.html#subhead-7)

[Chapter Summary](#text00007.html#subhead-8)

5. [Slices and Arrays](#text00008.html#chapter-5)

[Arrays](#text00008.html#subhead-1)

[Slices](#text00008.html#subhead-2)

[Declaration](#text00008.html#subhead-3)

[Initialization](#text00008.html#subhead-4)

[Modifying Slices](#text00008.html#subhead-5)

[For and For Range with Slices](#text00008.html#subhead-6)

[Multidimensional](#text00008.html#subhead-7)

[Reslicing, Copying, and Appending](#text00008.html#subhead-8)

[Strings, Arrays, and Slices](#text00008.html#subhead-9)

[Sorting and Inverting](#text00008.html#subhead-10)

[Chapter Summary](#text00008.html#subhead-11)

6. [Map Your Way to Success](#text00009.html#chapter-6)

[Declaration and Initialization](#text00009.html#subhead-1)

[Key Value Item](#text00009.html#subhead-2)

[For Range](#text00009.html#subhead-3)

[Slices and Maps](#text00009.html#subhead-4)

[Modifying your Maps](#text00009.html#subhead-5)

[Sorting](#text00009.html#subhead-6)

[Chapter Summary](#text00009.html#subhead-7)

7. [Structs](#text00010.html#chapter-7)

[Introduction to Structs](#text00010.html#subhead-1)

[Anonymous Structs](#text00010.html#subhead-2)

[Metadata and Tags](#text00010.html#subhead-3)

[Chapter Summary](#text00010.html#subhead-4)

8. [Packages—Not Just For Delivery](#text00011.html#chapter-8)

[Standard Library Overview](#text00011.html#subhead-1)

[Regexp](#text00011.html#subhead-2)

[Sync](#text00011.html#subhead-3)

[Accurate Computations](#text00011.html#subhead-4)

[Custom Packages](#text00011.html#subhead-5)

[Documenting your Package](#text00011.html#subhead-6)

[Package Distribution with Git](#text00011.html#subhead-7)

[External Packages, Libraries, and Projects](#text00011.html#subhead-8)

[Chapter Summary](#text00011.html#subhead-9)

9. [Methods to the Golang Madness](#text00012.html#chapter-9)

[Differences between Functions and Methods](#text00012.html#subhead-1)

[Receivers and Methods as Pointers and Values](#text00012.html#subhead-2)

[Accepting Both Pointer and Value Types](#text00012.html#subhead-3)

[Embedded Types](#text00012.html#subhead-4)

[Inheritance and Multiple Inheritance](#text00012.html#subhead-5)

[Chapter Summary](#text00012.html#subhead-6)

10. [Interfaces and Reflection](#text00013.html#chapter-10)

[Embedded Interface](#text00013.html#subhead-1)

[Type Assertions](#text00013.html#subhead-2)

[Type Switches](#text00013.html#subhead-3)

[Implementing an Interface](#text00013.html#subhead-4)

[Sorter Interface](#text00013.html#subhead-5)

[Reading and Writing](#text00013.html#subhead-6)

[Empty](#text00013.html#subhead-7)

[Reflect Package](#text00013.html#subhead-8)

[Printf, Value, and Dynamic Interface](#text00013.html#subhead-9)

[Structs, Collections, and Higher-Order Functions](#text00013.html#subhead-10)

[Best Practices for Interfaces](#text00013.html#subhead-11)

[Chapter Summary](#text00013.html#subhead-12)

11. [Reading and Writing With the Simple Power of Go](#text00014.html#chapter-11)

[Read: User Input](#text00014.html#subhead-1)

[Read and Write: Files](#text00014.html#subhead-2)

[Read: Files with a Buffer](#text00014.html#subhead-3)

[Read: Arguments from Command Line](#text00014.html#subhead-4)

[Read with Slices](#text00014.html#subhead-5)

[JSON Data Format](#text00014.html#subhead-6)

[XML Data Format](#text00014.html#subhead-7)

[Chapter Summary](#text00014.html#subhead-8)

12. [Goroutines and Channels for Speedy Code](#text00015.html#chapter-12)

[About Concurrency and Parallelism](#text00015.html#subhead-1)

[Goroutines](#text00015.html#subhead-2)

[Synchronizing and Switching between Goroutines](#text00015.html#subhead-3)

[Channels](#text00015.html#subhead-4)

[Semaphore Pattern](#text00015.html#subhead-5)

[Channel Factory and Directionality](#text00015.html#subhead-6)

[Channels, Tickers, and Timeouts](#text00015.html#subhead-7)

[Chapter Summary](#text00015.html#subhead-8)

13. [Testing and Handling Errors](#text00016.html#chapter-13)

[Run-Time Exceptions and Panic](#text00016.html#subhead-1)

[Panics and Recover](#text00016.html#subhead-2)

[Error Handling with Closures](#text00016.html#subhead-3)

[Testing and Benchmarking](#text00016.html#subhead-4)

[Assessing Code Performance](#text00016.html#subhead-5)

[Chapter Summary](#text00016.html#subhead-6)

14. [Common Pitfalls and Patterns](#text00017.html#chapter-14)

[Pattern: Comma, OK](#text00017.html#subhead-1)

[Pattern: Visibility and Operator](#text00017.html#subhead-2)

[Pattern: Defer](#text00017.html#subhead-3)

[Common Pitfalls](#text00017.html#subhead-4)

[Chapter Summary](#text00017.html#subhead-5)

[Final Words](#text00018.html#uncategorized)

[About the Author](#text00019.html#about-the-author)

[Other Titles by Edward Thornton](#text00020.html#also-by)

[References](#text00021.html#uncategorized-2)

What’s the programming language that professional software developers most want to learn? Would it surprise you to find out that it’s not Python or JavaScript? Nearly a third of developers chose Go as their top language to learn (Combs, 2020) after Google engineers created it to address problems with existing languages, such as slow speeds. It’s also associated with top pay rates in the industry. If you’re looking to learn a powerful language that manages to be relatively lightweight and still has the features that developers are looking for, you’ve come to the right place. Although the tech sector is currently getting the most use out of it, other companies, including American Express, Target, and IBM, have begun using the programming language as well.

You may have picked up this book because you’ve already heard a lot about Go and want to add it to your programming arsenal. Or maybe you don’t have a lot of programming experience, so a lightweight language seems like it could be right up your alley. Perhaps your company is looking into adding Go to speed up the performance of its apps, or you’d like to get a job at a company like SoundCloud, Uber, BBC, or Dropbox. If you’re familiar with other languages, you can probably pick up Go in a few hours. With less programming experience, you’ll need to spend a bit longer to learn it. However, it’s very clear and doesn’t have the excess baggage that software development languages tend to add on over time since it’s a relatively youthful one.

In this book, before we dive into the basics of the language itself, you’ll discover why it’s so popular and why more and more programmers are adopting it. Go is more readable than many other languages, which makes using it for open-source programming a natural fit. You’ll learn about the foundations, including elementary types and strings, as well as control structures such as if-else and for range. You’ll find out about functions in Go and slices and arrays too. Maps and packages are important components of Go programming, and we’ve provided details about both in the book. In addition, you’ll learn about methods (and how they differ from functions), interfaces, and reflection. There’s information about reading the language, not to mention goroutines and channels. Finally, and maybe most importantly, we’ve included a chapter on testing and handling errors as well as a chapter on common pitfalls and patterns. Find out what mistakes many developers make, so you can avoid them yourself! Once you’ve learned the foundations of the language in this book, you’ll be ready to start programming in Golang.

As a Go programmer myself, I’ve written this book to help others learn the language. I know what the pitfalls are, and I’ve helped other software developers like you get up to speed on Go pretty quickly. I think as many developers as possible should start learning it so they can build code that executes faster, is cleaner, and helps spread the popularity of open-source applications.

The sooner you start reading the book, the sooner you’ll be able to start programming—it really is that simple! Go was designed to be learned fast, and to execute fast. So dive in and get started on your Golang; why wait any longer to add this powerful tool to your kit?

One 

In 2009, a team of Google employees introduced Go to the world. (It’s sometimes referred to as Golang to differentiate it from the well-known game of Go.) Supposedly, they started creating it while waiting for a program in another language to compile. The employees were frustrated by the limitations of the languages available at that time and decided to rethink programming from the very beginning, working from the ground up.

Over time, computer languages (just like spoken ones) tend to accumulate extra baggage that gets in the way and slows down the speed of the code. Starting from scratch meant that they could build something lean, yet powerful enough to handle massive code. They also designed it to be open-source, so it’s easy to create new applications and use them in a variety of industries for many different purposes.

First, a quick refresher on programs: they’re simply a set of instructions. Both compilers and interpreters take human code and translate it into machine-readable code. Compiled languages, like Go, are developed so that the target machine can read the code directly. Interpreter languages such as Python and Ruby don’t have the translation inside the source code and require a separate program to read and execute the code.

## Designed for Modern Conditions

Go was intentionally created to run on multiple cores, which allows programmers to scale when adding more cores. It also helps them create concurrency since goroutines execute in the background while other jobs are running. If you’re building a web app that requires data input from the user, for example, the goroutine can supply pre-populated text as the user is inputting. The program continues to run no matter how long it takes the concurrent processes to operate.

The language uses goroutines instead of threads, which requires much less use of the machine’s RAM. That makes an app running on Go less likely to crash from running out of memory. Goroutines are functions that execute simultaneously with concurrent goroutines and work on any hardware. By contrast, threads execute the code under the logic of the program and are dependent on the specific hardware being used.

Goroutines communicate with one another easily and without taking up a lot of power through channels. Threads don’t have an easy way to talk to one another, which results in communication between threads taking more time and power. As a result, goroutines are faster and cheaper than threads.

Unlike some previous languages, Go is designed for cloud-based servers that most web developers use these days. It’s compilable on almost any machine and works on a variety of platforms as well. If you’ve been using Perl to watch a log, Python to deliver tweets, or Java to manage thousands of concurrent users, you’ll find that Go can accomplish all of these little tasks and more.

Like Java, Go is compiled and needs no interpreter. That frees up a lot of power for the code itself, making it run much faster. Having lower system requirements also means that users will be able to use your app on older devices, which expands the potential market for your app and may land more money in your pocket.

## Advantages of Go

*   Flexibility

This language can solve a lot of problems for developers. It can be used for network and system programming as well as audio/visual apps, such as YouTube. More modern developments, such as big data and machine learning, are possible with this language.

*   Automatic documentation

GoDoc will automatically generate the technical documentation for the code. It provides cross-references, examples of the code, and links to the repository for version control. This is especially key for open-source developers and makes it much easier to build apps based on another’s code.

*   Embedded testing

The language comes with an API for use in testing and profiling, as well as your own examples. In addition to basic testing, you can also run skip tests and parallel tests, among others.

*   Static code analysis

Using the metatool GoMetaLinter, you can debug your source code before running it by analyzing it against the code rules. Using automated static code analysis is not only faster than debugging manually, but it also avoids the usual human error in manual analysis.

*   Detecting race condition

When multiple threads compete, they may end up being completed in an unexpected order which results in errors that are hard to track down (this is known as race condition). The Go engineers decided to create an automatic detector to eliminate the problem, which also ensures backward compatibility.

## Disadvantages of Go

*   Lack of GUI library

The lack of a GUI library is fine for single-page apps, but businesses that need both speed and GUI for their users typically choose Ruby instead. Otherwise, it’s a time-consuming job to try to connect libraries instead of using a native solution as you would with Python or Java.

*   No generics

Because of the way Go is designed, you may need to write more code to handle certain functions than you would for other languages. In languages that use generics, you can write algorithms with terms-to-be-specified-later that will then run when needed with the specific types as parameters. It helps reduce code repetition; you can write one function instead of two.

Without this capability, you need to write more lines of code for each function instead.

*   Error handling

Although handling errors is pretty simple in Go, it may require a lot more code than other languages.

*   Dependency management

You can install different libraries with Go, but if the maintainer of the library uploads a version that's not backward-compatible, then anyone running your app will get an error. If the library isn’t installed, the program won’t compile.

While there *is* a tool to help you manage this (Dep), it either forces you to load all the dependencies on the repository or store the package list. If you store on the repository, your code becomes *much* bigger because you’re also storing lines of dependency code. However, if you only store the package list, you may run into backward incompatibility issues which will cause your program to crash.

## Who Should Use Go?

This language is great for the underlying code on apps that require speed. It’s also good for high-performance apps that require scalability.

Google uses it for its cloud services infrastructure; companies like YouTube, Netflix, and Soundcloud use Go for high loads on their platforms; Uber used it to improve map processing speeds so it takes less time to match a rider with a driver; data science organizations are using it more and more to process big data and make sense of it.

Go is a great solution for fintech developers because it allows for a smooth connection between users and their financial institutions. Paypal has used it for scaling, AmEx for payments, and Salesforce for their “Einstein Analytics”. It’s also become the language of choice for programming on the blockchain, especially the Ethereum network.

As you can see, Go is a good tool to have for almost any modern programmer. Whether it’s for system programming, network programming, web applications, or DevOps, the language is easy to use and read. And most importantly for the users of today, it’s much faster than many of the other available options.

## Chapter Summary

Go was designed by Google engineers who wanted a faster computer language that could take advantage of multiple cores.

*   Because it is a younger language, it works well for modern applications that are located on the cloud instead of specific hardware and can run operations concurrently.
*   Go is flexible and uses goroutines that run simultaneously without slowing down the speed, among other advantages.
*   Golang’s GUI library is nonexistent, so it’s not preferred for apps that rely on GUI in addition to speed, among other disadvantages.
*   Go is applicable in many different types of applications and industries, especially for those with high user loads or other big data needs.

In the next chapter, you'll learn about the foundations of Go.

Two 

In this chapter, we’ll delve into the foundations of Golang, which you can think of as the basic vocabulary for the language. Some of these you’ll be familiar with if you’ve done programming with similar languages such as C and C++.

## Identifiers, Filenames, and Keywords

If you’re relatively new to programming, *identifiers* are the names of the program’s components as defined by the users. Identifiers in Go may be names of functions, constants, variables, statement labels, types, or package names.

Go identifiers must be written in a specific way to be recognized by the program. It must start with a letter or underscore, not a number. The identifier itself can contain letters, numbers, and underscores. It’s case-sensitive, so while Go\_lang and go\_lang are different, they’re both valid names. Golang1 is OK, but 1Golang is not. You can’t use keywords such as “if” or “default”.

Programmers find it best to keep the identifiers between 4 and 15 characters, though there’s technically no limit to the length. The underscore is a blank identifier and is used as an anonymous placeholder with a special meaning in certain parts of the program.

Go also has some identifiers that have been predeclared and can be used for constants, functions, and types.

*   Constants: true, false, iota, nil
*   Functions: make, copy, append, close, delete, plus others
*   Types: int, uint, string, bool, error, plus others

*Filenames* , which are used to identify each file uniquely, are typically written in lowercase and multiple words are separated with an underscore.

*Keywords* , sometimes known as reserve words, already have a meaning in the language and therefore, as noted above, can’t be used for identifiers. There are 25 keywords in Go, including map, struct, goto, switch, import, and return.

## Functions

In general, *functions* are blocks of code that perform a specific task. They’re also known as methods, subroutines, or procedures. Many functions follow the format of taking in data, processing it, and then returning the result. Functions can be “called” from within other functions. Once the function is called, the program leaves the code at that line, executes the function instructions line by line, then returns to the program, replacing the function with the result that it returned. Instead of continually rewriting code or copying and pasting for common tasks, functions can be reused over and over. Languages normally have several built-in functions that would otherwise require multiple lines of code, and programmers can also write their own to satisfy the need of their program. The variables inside the function are only live while the function is being executed, so you can use *i* to mean one thing in function\_1 and something else in function\_2, and the program will continue to run.

In Go, every program has at least one function: main(). This is a function declaration, which tells the program the name of the function, the return type, parameters, and the *definition.* The definition is the set of instructions or the function body.

There are other standard functions in Go such as len(), which will give you the length of the argument, string, or array, depending on what was called.

This is the syntax of a function in Go, or how it’s written in code:

> func function\_name ( \[parameter list\] ) \[return\_types\]
> 
> }
> 
> body of the function
> 
> {

where

*   func starts the *declaration,* telling the program that a function is coming up
*   function\_name names the function being used
*   parameter is similar to a placeholder, and gives the type, order, and number of parameters; there may be no parameters for a function
*   return\_types is the list of data types for the values the function returns; this isn’t always required
*   body defines what the function does

For example, suppose you wanted a function to show the maximum of two numbers, num1 and num2:

> func max (num 1, num2 int) int {
> 
> result int //The program ignores anything after //, so you can type notes here. Note that this is a local variable declaration.
> 
> if (num1 > num2) {
> 
> result = num1
> 
> } else {
> 
> result = num2
> 
> }
> 
> return result
> 
> }

## Data Types

The type of a variable specifies how much space it occupies and how the bit pattern should be interpreted. In Go, you can classify into four categories:

1\. Boolean

There are only two of these: true and false. *Bool* is one of the four elementary types.

2\. Numeric

These can be either integers or floating-point values. Examples of numeric types include uint8 (unsigned 8-bit integers from 0 to 255), int16 (signed 16-bit integers), and the like for integers.

Floating points can be float32 (IEEE 32-bit floating-point), float64 (IEEE 64-bit floating-point, complex62 (float32 with real and imaginary parts), or complex128 (float64 with real and imaginary.)

Both *int* and *float* are also elementary types.

3\. Strings

These represent the value of the string, which is a sequence of bytes. Once created, the string cannot be changed. Strings can be alphanumeric, such as in the iconic “helloworld”. A string is also an elementary type.

4\. Derived types

These include pointer types, array types, structure types, map types, etc., and will be discussed further in later chapters.

## Constants

Like other statistically typed programs, the compiler either already knows or can figure out the type of every variable when it comes time to compile. Unlike other languages, however, Go doesn’t allow you to mix numeric types. C, C++, or Java will convert smaller types (like “int”) into a larger one (like “float”) when the types are mixed.

The Golang engineers thought that allowing these automatic conversions not only potentially makes them hard to read, but creates inconsistencies across different platforms. Since Go is designed to work on a variety of architectures, the language was designed to ask for explicit types instead.

Unless you explicitly give a constant a type, it’s considered untyped, even if you give it a name. An untyped constant that’s an integer can only be used where integers are allowed. For example, you can’t assign an integer constant to a string or boolean variable. An untyped floating-point constant can be used wherever a floating point is permitted.

All untyped constants in Go have default types. Constants that are integers default to “int”, floats default to “float64”, characters to “rune”, etc. When you declare a type, the constant becomes typed. Again, constants must be declared as their correct type, or else the program will return an error.

Declare constants without a type unless you absolutely need them; declaring a type makes you lose the flexibility of being able to mix types in an operation.

There are a few rules for constant expressions in Go.

*   Comparison between two untyped constants results in an untyped boolean constant (“true”/”false”).
*   Operands of the same type result in the same type. In other words, if they’re two untyped integer constants, the yield is an untyped integer constant. The expression “11/2” results in “5” rather than “5.5” because it’s truncated to an integer.
*   If they’re not the same type, the result is the broader of the two according to this logic: integer<rune<floating-point<complex

## Variables

In all languages, the *variable* is the name given to a particular storage area used by the program. Names of variables can use letters, digits, and underscores. Golang variables have a specific size, memory layout, range of values for the memory layout, and possible operations. The variable definition tells the compiler how much storage to create for the variable and where to put it.

*Lvalues* are used to refer to a memory location and can appear on either the left or the right side of an assignment. *RValues* refer to data values that are stored in memory. Variables are lvalues and appear on the left side of the assignment.

When you declare a variable, you’ll use the keyword *var* .

## Operators

Most programming languages have *operators* , which are built-in symbols that perform a variety of mathematical or logical operations. Go has three types: bitwise, arithmetic, and logical.

*   Bitwise

These operators work on variables of the same bit length (that are integers).

*   AND: &
*   OR: ⎸
*   XOR and COMPLEMENT: ⌃
*   CLEAR: &⌃
*   Arithmetic

You’re probably familiar with these operations from math class. They include “+” for addition, “\*” for multiplication, “/” for division, and “%” for percentage.

*   Logical

While these operators are similar to the ones in other languages, Golang is strict about the values that can be compared to each other.

*   Equal: =
*   Not equal: !=
*   Less than: <
*   Less than or equal to: <=
*   Greater than: >
*   Greater than or equal to: >=

## Strings

In this language, strings are a bit different from the way they work in C++, Python, Java, etc. They’re immutable, or read-only. If you try to change a string, you’ll get an error. The characters represent bytes that are UTF-8 encoded.

Why does the UTF-8 encoding matter? When computers were first designed, they used bytes of 8 bits in binary code, and every letter of the English alphabet had its byte. (This is known as the ASCII format.) There are 256 ways to use binary for coding, and the English alphabet plus symbols only required 128.

However, once speakers of other languages wanted to program, having only 128 unique bytes left became a problem. Enter Unicode, which gives each character a code point. It’s able to generate about a million code points, which is enough for the planet—for now, anyway!

UTF-8, or Unicode Transformation Format, translates code points into binary and vice versa. Due to the utility of UTF-8, you can use any language in your strings.

Typically, strings are set off with double quotes (“) at the beginning and end of the string. Check out this example:

> package main
> 
> import “fmt”
> 
> func main (){
> 
> var my\_words string //using the keyword *var* here
> 
> my\_words = “Hello world”
> 
> //displaying the string
> 
> fmt.println(“String: “, my\_words)
> 
> }
> 
> Output: Hello world

Sometimes, instead of using the double quotes, strings use backticks (\`). This is common when writing in HTML, when writing a message that takes multiple lines, and when writing regular expressions.

## Times and Dates

In Go, times include a location that determines the date and time associated with that location. If it’s not specified, the time defaults to UTC or Coordinated Universal Time, which is used across the world.

If you want a timestamp, Time.Now, the signature is:

> func Now() time

For the date and time, Time.Date, the signature is in the format yyyy-mm-dd hh-mm-ss + nanoseconds:

> func Date (year int, month, day, hour, min, sec, nsec int, loc\*Location)

In Go, the duration is what’s elapsed in nanoseconds between two instants, written in int64nanosecond count. Remember that 1 second is equal to 1,000,000,000 nanoseconds. The function for the duration is:

> func Since(t Time) duration.

If you want to know how long until time t, the function is:

> func Until(t Time) duration.

Unlike other languages like Ruby, Golang formats the date and time placeholders to look like date and time, so it’s not as difficult to remember and you don’t have to look them up.

## Chapter Summary

Golang is similar to other languages, but if you program in Java, C++, or Python, it’s important to remember what Go does differently.

*   The “vocabulary” of Go is designed to be easily readable and clear.
*   Syntax rules for filenames, identifiers, variables, constants, and keywords may share similarities with other programs.
*   Go contains a variety of data types, and constants don’t have to have their types specified—in fact, it’s often better to leave them untyped.

In the next chapter, you'll learn about control structures.

Three 

It’s a useful habit to break large projects down into smaller steps, be they in school, work, or your day-to-day life. This remains true while learning a new programming language, whether or not it’s your first.

In the last chapter, you learned Go’s vocabulary and the syntax that it uses. The building blocks of a program are its control structures. The computer starts reading line by line, but in some places may need to jump to a different function or repeat one. Control structures allow the program to determine where to go next or which path to follow. They analyze the variables and figure out where to go based on the given parameters.

There are two main variations of control structures in programming: conditionals (AKA selection) and loops (AKA iterations). *Conditionals* tell the program what to do if a certain condition is met, while *loops* are instructions to repeat the statement a specified number of times, or until a condition is met.

## If-Else

A simple *if statement* will execute if the condition is true. If it’s false, nothing happens. If statements are written like so:

> If condition {
> 
> //code that will be executed if the condition is true
> 
> }

As an example, the output below is A (if true).

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func main () {
> 
> var grade = A
> 
> x=: true
> 
> If x {
> 
> fmt.println (grade)
> 
> }
> 
> }

However, if you want the program to do one thing if the condition is true and another if it’s false, you’ll need an *if-else statement.* As you’ve probably guessed, these statements take this form:

> If condition {
> 
> //code that will be executed if the condition is true
> 
> } else {
> 
> //code that will be executed if the condition is false
> 
> }

In this example, the output is Pass if x>= 60:

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func main () {
> 
> x : =75
> 
> If x >= 60 {
> 
> fmt.println(“Pass”)
> 
> } else {
> 
> fmt.println(“Fail”)
> 
> }
> 
> }

The else section is only executed when necessary; if the condition is true, the rest of it is ignored.

If-else statements can have multiple else or alternative statements. In Go, they’re known as if-else if-else statements. They’re written like so:

> If condition-1 {
> 
> //code that will be executed if condition-1 is true
> 
> } else if condition-2 {
> 
> //code that will be executed if condition-2 is true
> 
> { else {
> 
> //code that will be executed if both conditions are false
> 
> }

In this example, grades are on a high-pass, pass, or fail basis. If x>= 90, then the output is high-pass. 60 is the cutoff between pass and fail.

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func main () {
> 
> x := 95
> 
> If x >= 90 {
> 
> fmt.println(“High-pass”)
> 
> } else if x>= 60 {
> 
> fmt.println(“Pass”)
> 
> } else {
> 
> fmt.println(“Fail”)
> 
> }
> 
> }

## Switch-Case

Looking for an easier way to write multiple if-else statements? *Switch* is a shorter way to write the sequence. It’s similar to the switch you might have used in C, C++, or Java. However, in Go, the control switch runs the first case where the condition is true and ignores the remainder. Switch cases don’t need to be constants, and the values don’t have to be integers, either. You can use commas to separate expressions in the *case* if there is more than one. Here’s an example of a switch case to tell you whether it’s a weekday or a weekend.

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func main () {
> 
> switch time.Now() . Weekday (){
> 
> case time.Saturday, time.Sunday:
> 
> fmt.Println(“It’s the weekend”)
> 
> default:
> 
> fmt.Println(“It’s a weekday”)
> 
> }

## For

A *for loop* is the only looping construct in Go. It’s used to repeat statements until the condition is met. If there was no condition to be met, or the program can’t meet it, it would be in an infinite loop.

Take a simple example, like listing numbers from one to ten. Without a loop construct, you’d have to write ten statements:

> fmt.Println(1)
> 
> fmt.Println(2)
> 
> fmt.Println(3)
> 
> fmt.Pri
> 
> ntln(4)
> 
> fmt.Println(5)

… until you got to fmt.Println(10).

With a for loop, you only need to write it once.

> x :=1
> 
> for x <= 10 {
> 
> fmt.Println (x)
> 
> x += 1
> 
> }

Here, you’re telling the program to check if x is less than or equal to 10. If so, x is printed to the console or screen. Next is x+1, and if that is less than or equal to 10, it also gets printed. Note that if you don’t add the +1 element, x is always 1, and that gets printed in an infinite loop.

You can also shorten the language for the for loop. In this case, you would write:

> for x :=1; x <= 10; x++ {
> 
> fmt.Println(x)
> 
> }

The first line assigns x to 1, checks if x is less than or equal to 10, and adds 1 in case the previous condition (that x <=10) is true. The second line is the statement to be executed.

## For Range

The for loop is used to repeat for a variety of elements in data structures, such as arrays, slices, maps, strings, and channels. You’ll learn more about those in later chapters. The *for range* statement uses the keyword *range* to repeat an expression that evaluates an array, slice, map, etc.

For the sake of this example, let’s suppose you had a slice (don’t worry about what that is yet) and wanted to add the numbers in it:

> nums := \[\]int{2,3,4}
> 
> sum :=0
> 
> for\_, num := range nums {
> 
> sum += num
> 
> }
> 
> fmt.Println(“Sum:”,sum) //which would result in the output of sum: 9

## Break and Continue

These controls help you add logic into your Go program to control the operations. The *break statement* ends the current loop and is usually paired with an “if” statement.

The following program shows how the break and a conditional if statement work together.

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func main () {
> 
> for x :=0; x < 10; x++ { // check to see if x is less than 10; if so, add 1
> 
> if x == 5 {
> 
> fmt.Println(“Breaking out of loop”)
> 
> break // here’s the command to break when x reaches 5
> 
> }
> 
> fmt.Println (“The value of x is”, x) // if there’s no break
> 
> }
> 
> fmt.Println(“Exiting program”)
> 
> }

The output from this program reads like this:

> *The value of x is 0*
> 
> *The value of x is 1*
> 
> *The value of x is 2*
> 
> *The value of x is 3*
> 
> *The value of x is 4*
> 
> *Breaking out of loop*
> 
> *Exiting program*

If you nest loops inside each other, a break in an inner loop won’t necessarily mean a break in the outer loop.

Instead of breaking a loop, maybe you want to skip the rest of the loop and return to the top of it and repeat. That’s what the *continue statement* in Golang is for.

For example, we could change the program above not to stop and exit when x = 5, but to skip 5 and keep going until the number 10 is reached:

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func main () {
> 
> for x :=0; x < 10; x++ {
> 
> if x == 5 {
> 
> fmt.Println(“Continuing loop”)
> 
> continue // instead of break when x is 5
> 
> }
> 
> fmt.Println (“The value of x is”, x)
> 
> }
> 
> fmt.Println(“Exiting program”)
> 
> }

Now you’ll get a different result, which continues the loop at 5 instead of ending it.

> *The value of x is 0*
> 
> *The value of x is 1*
> 
> *The value of x is 2*
> 
> *The value of x is 3*
> 
> *The value of x is 4*
> 
> *Continuing loop*
> 
> *The value of x is 6*
> 
> *The value of x is 7*
> 
> *The value of x is 8*
> 
> *The value of x is 9*
> 
> *Exiting program*

The continue statement is often used where you need a loop, but want to eliminate common cases that you don’t want in the program. Using continue also helps you avoid multiple nests of conditions.

## Labels: Goto

Like the break and continue statements, *goto* alters the execution of a program and instructs the computer to *go to* a labeled statement and run the program from there. The label is an identifier written in plain text, and it can be anywhere in the program above or below the goto statement. Like continue and break, goto is often used with if and if-else controls.

In this example, you get different answers depending on what age you input.

> package main
> 
> import “fmt”
> 
> func main () {
> 
> var age int
> 
> election: //this is the label
> 
> fmt.Println(“Enter your age ”)
> 
> fmt.Scanln(&age) //user enters age
> 
> if (age <= 17) {
> 
> fmt.Println(“You are not eligible to vote.”)
> 
> goto election
> 
> } else {
> 
> fmt.Println(“You are eligible to vote.”)
> 
> }
> 
> }

The output might look something like this:

> *Enter your age 16*
> 
> *You are not eligible to vote.*
> 
> *Enter your age 17*
> 
> *You are not eligible to vote.*
> 
> *Enter your age 20*
> 
> *You are eligible to vote.*

Now that you understand how to use goto, try to avoid using it in your programming. Not only in Go but other languages as well. Most of the time, there’s another way to construct it which makes it easier for users who want to read the program. Using goto makes it a lot harder to trace the flow of controls in a program, making it more difficult to understand and modify. Since Go is designed to work on open-source platforms, your code should also be designed to be easy for others to use and modify.

## Chapter Summary

Control structures are the building blocks of a program. You can use either conditional statements or loops for your controls in Go.

*   Conditional statements include if, if-else, and if-else if-else statements; they direct the program to execute when certain conditions are met.
*   Switch case is a much shorter (and easier) way to write multiple alternatives instead of a long if-else if-else statement with many lines.
*   Loops repeat instructions rather than writing all the lines down in the code.
*   For is the only loop control that Go recognizes, and for range adds repetition over ranges.
*   Break and continue are different ways of skipping parts of a loop.
*   Goto is another method of controlling loops by sending the program back to a specific label, but goto statements make programs harder to understand and use and therefore are not recommended.

In the next chapter, you'll learn about functions.

Four 

In previous chapters, you learned a bit about functions in Golang. Here, we’ll take a deeper dive into some of the more commonly used functions in the language. As a refresher, functions are groups of statements that complete a task. Essentially, a function takes an input and produces an output of some kind.

Function names that start with an uppercase letter will be exported to other packages, while those that start with lowercase will only be used within the same package. (A *package* is a group of source files that are compiled together.) Names of functions can’t start with a digit and can’t contain spaces. If the name has multiple words in it, each word after the first should be capitalized, such as simpleFunction.

## Basics of Functions

SimpleFunction is a function that doesn’t have any parameters and doesn’t return any values. It’s used to print a message.

> package main
> 
> import “fmt”
> 
> func SimpleFunction (){
> 
> fmt.Println(“Hello World”)
> 
> }
> 
> func main () {
> 
> SimpleFunction ()
> 
> }

The output here is simply

> *Hello World*

If you want to pass information to a function, you can use *arguments* , which are just like variables. They’re specified inside parentheses and separated by commas. There’s no limit to the number of arguments that can be passed.

Here’s an example with two int-type arguments. Once the function *add* is called, you can pass two integers.

> package main
> 
> import “fmt”
> 
> func add(x int, y int) {
> 
> total : = 0
> 
> total: = x + y
> 
> fmt.Println (total)
> 
> } // this part of the code accepts the arguments
> 
> func main () {
> 
> add (10, 20)
> 
> } //this is where the argument is passed

The output, in this case, is 30.

## Return Values and Parameters

If you declare a return value, then you’ll also need a return statement. The *return value* is what retains the function’s output after running the instructions. In Go, unlike some other languages, there’s a variety of values. You as the coder can decide whether you want to name it or not.

For example, you can have a naked return where you use the return keyword, but without specifying the return value in the body. That’ll work as long as you declare the return value in the function header and the variable has the same name as what you’ve stated in the header.

Here’s an example of a naked return.

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func greeting (name string) (message string) {
> 
> message = “Hello, “ + name //variable has to be the same as in the header, e.g. message
> 
> return // Note that since *message* has been specified above, no need to declare here
> 
> }
> 
> func main () { //greeting return value
> 
> // the function stores the variable
> 
> msg := greeting(“world”)
> 
> fmt.Println(msg)
> 
> }

Output is Hello, world.

You can also construct functions that have multiple return values and multiple parameters. However, the number of variables that the function holds on the return has to be the same as the number of variables in the function.

Suppose you wanted to run four basic arithmetic operations on two numbers that you’ve named x and y. Here’s what that would look like:

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func operations (x, y int) (sum, diff, prod, div int) {
> 
> //the function has 4 variables: x+y, x-y, x\*y, x/y
> 
> return
> 
> }
> 
> func main() {
> 
> x, y := 6, 3
> 
> //since there are 4 variables in the function, there must be 4 receiver variables
> 
> sum, diff, prod, div := operations (x, y)
> 
> fmt.Println(sum, diff, prod, div)
> 
> }

The output would look like this: 9 3 18 2

## Defer, Panic, and Tracing

As you might guess, a *defer statement* delays the execution until the surrounding function returns. There are a couple of ways that can happen: either through the normal performance of the function or through a *panic* .

As a quick example, here’s what a defer statement looks like through normal function.

> func main() {
> 
> defer fmt.Println(“world”) // deferring the statement
> 
> fmt.Println(“Hello,”)
> 
> }

The output is (you guessed it!)

> *Hello,*
> 
> *world*

*Panic* stops a goroutine and prints a stack trace to the console. That way you can “catch” a panic and take control back. A *stack trace* lists the calls that the program was working on when the exception occurred.

Even if the function panics, the *defer* statement will still be performed. Later in the book, you’ll learn more about catching a panic and recovering from one as well.

If you call several deferred functions, they’ll be performed in a “last in, first out” (LIFO) order. Check out an example of how that works:

> func main() {
> 
> fmt.Println(“Hello”)
> 
> for a :=1; a <=3; a++ {
> 
> defer fmt.Println(a)
> 
> }
> 
> fmt.Println(“world”)
> 
> }

You end up with output that looks like this:

> *Hello*
> 
> *world*
> 
> *3*
> 
> *2*
> 
> *1*

## Built-in Functions

Built-in functions are automatically defined by Golang and represent a variety of common functions that developers like to use. As a compiled language, Go embeds the processing into its compiler. Each built-in function has a corresponding operation, or *op* , inside the compiler.

You’ve already seen a couple of examples of built-ins in previous examples.

1.  *Print* and *println* are used for printing the output.
2.  *Panic* is used for error handling. Another built-in for errors is *recover* .

Other built-ins include:

*   *Len* and *cap* for length and capacity, respectively, for array, slice, channel, and string
*   *Delete* for deleting a certain key in a map
*   *Make* for allocating memory for reference types and returning the initialized value
*   *New* for allocating user-defined and value type
*   *Copy* and *append* for those operations on a slice

You’ve already seen some examples of a string. Later in the book, you’ll learn more about the others, but here are some quick definitions. *Arrays* are sequences of elements of a certain length; the number of elements has to be defined in the array. *Slices* are more flexible and therefore tend to be more common than arrays, as they’re sized dynamically instead of specified. *Channels* connect goroutines that are running at the same time to one another, and you can send values from one goroutine channel into another’s channel to receive them.

## Recursion

With *recursive functions* , the function calls itself repeatedly, getting smaller and smaller until it finally meets its *base case* (AKA base condition). At that point, it’s finally converged and stops further calls. There are two ways of recursion: directly, where no other function is called, or indirectly, which requires another function to assist.

There are three other types of recursions that you might run into or want to use as a programmer. If there are only two functions, it’s known as *mutual recursion* . Tail recursion involves a *tail call* , which is the last call of the function. If the last or tail call calls back to the function, it’s referred to as *tail-recursive* . Similarly, *head-recursive* refers to a function where the first statement is a recursive call.

1\. Direct example

Here’s a sample where the recursive function is used to calculate the factorial of a positive number. You may (or may not) recall from math class that a factorial is indicated by a number followed by an exclamation point (like 4!) and is equal to all the numbers leading up to it multiplied together. In other words, 4! = 4\*3\*2\*1 = 24.

Here, the base case is either 0 or 1 (where the result is 1). In this example, the function decreases by one integer until the base case is reached, at which point the function stops. Negative numbers return an error message.

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func factorial\_calc(number int) int {
> 
> if number == 0 ll number ==1 { // base case
> 
> return 1
> 
> }
> 
> if number < 0 { //if number is negative
> 
> fmt.Println(“Invalid Number”)
> 
> return -1
> 
> }
> 
> return number\*factorial\_calc(number-1) // recursive function until operation reaches the base case
> 
> }
> 
> func main() {
> 
> answer1 := factorial\_calc(0) //where 0 is the parameter to be passed
> 
> fmt.Println(answer1, “\\n”)
> 
> answer2 := factorial\_calc(4)
> 
> fmt.Println(answer2, “\\n”)
> 
> answer3 := factorial\_calc(-1)
> 
> fmt.Println(answer3, “\\n”)
> 
> answer4 := factorial\_calc(5)
> 
> fmt.Println(answer4, “\\n”)
> 
> }

The output for this example looks like this:

> *0*
> 
> *24*
> 
> *Invalid number*
> 
> *\-1*
> 
> *120*

2\. Indirect example

Here you’ll see what it looks like when you use another function for recursion. Suppose you wanted to print all the numbers in order, decreasing from n.

> package main
> 
> import (
> 
> “fmt”
> 
> )
> 
> func print\_one (n int){
> 
> if n > =0 {
> 
> fmt.Println(“In first function: ,” n)
> 
> print\_two(n-1) //prints n if n is a positive integer and calls the second function
> 
> }
> 
> }
> 
> func print\_two (n int){
> 
> if n > = 0 {
> 
> fmt.Println(“In second function: ,” n)
> 
> print\_one(n-1)
> 
> }
> 
> }
> 
> func main() {
> 
> print\_one(6) //prints all positive integers from 1 up to 6
> 
> print\_one(-10) //prints nothing because it doesn’t follow the base case n >= 0
> 
> }

The output you’ll see:

> *In first function: 6*
> 
> *In second function: 5*
> 
> *In first function: 4*
> 
> *In second function: 3*
> 
> *In first function: 2*
> 
> *In second function: 1*
> 
> *In first function: 0*

What you want to avoid is *infinite recursion* , where the function never converges. Normally, something like this will result in either a system crash or memory overload. If you don’t specify a base case and launch a recursive call, you’ll end up with infinite recursion.

Golang also lets you use *anonymous* functions, which don’t have a name. You can also use these for recursion. You’ll need to tell the program what the anonymous function is.

## Higher-Order Functions

These types of functions operate on other functions, either receiving one as an argument or returning one as output. Here are a couple of simple high-order functions to give you the idea.

1\. Passing as argument

The example uses the partialSum function to return the sum function.

> package main
> 
> import “fmt”
> 
> func sum(a, b int) int{
> 
> return a + b
> 
> }
> 
> func partialSum(a int) func (int) int {
> 
> return func(b int) int {
> 
> return (a, b)
> 
> }
> 
> }
> 
> func main () {
> 
> partial := partialSum(2)
> 
> fmt.Println(partial(5))
> 
> }

Output: 7

2\. Returning as output

In this example, the squareSum function returns two functions and an integer.

> package main
> 
> import “fmt”
> 
> func squareSum(a int) func (int) func (int) int {
> 
> return func(b int) func (int) int {
> 
> return func (c int) int {
> 
> return a\*a + b\*b + c\*c
> 
> }
> 
> }
> 
> }
> 
> func main () {
> 
> fmt.Println(squareSum(5)(6)(7)) // will equal 5\*5 + 6\*6 + 7\*7
> 
> }

Output: 110

## Closures

*Closures* are function values that reference variables from outside the function’s body; they’re used as anonymous functions. They’re useful for *data isolation* , where the variable may be referenced in the anonymous function but the data isn’t available for other code.

Closures allow developers to associate data with the functions that operate on that specific data.

## Chapter Summary

Golang includes a variety of functions that you can use for programming different operations.

*   Some functions are built-ins, but developers can customize them as well.
*   Go allows the creation of anonymous functions.
*   You can use recursive functions too, but make sure that there’s a base case for the function to eventually converge, or you could end up with memory overload and/or a system crash.

In the next chapter, you'll learn the details of slices and arrays.

Five 

In the last chapter, you got a very brief introduction to slices and arrays in Go. They can be very useful for developers and programmers, so let’s dive in and get to know them a bit better.

Arrays are frequently used to collect variables of the same type. They save memory, which can be allocated at runtime when necessary. Because the values are literally near each other, arrays speed up the code. They’re also relatively easy to debug since you can use indices instead of looking over the entire collection.

Developers can use arrays over and over again, so there’s less time spent repeating code. In other words, they help you code faster. Zero-length arrays act like pointers, so they don’t use up a lot of memory. Slices are an easy way in Go to work with these collections, so you’ll find more examples of slices than of the arrays themselves.

## Arrays

Slice types are built on top of arrays in Go, so it’s worth understanding how arrays work in this language before moving on to slices. The definition of an *array type* includes both a length and a type of element.

Suppose you have an array type of \[3\]int. That’s an array of 3 (length) and type int. The size is fixed so that the two arrays \[3\]int and 4\[int\] are different and incompatible with each other. You can index arrays just as in other languages; s\[n\] indexes the nth value of the array, starting with 0.

Arrays don’t have to be initialized because the zero value has elements already equal to zero. Go is different from C in that the pointer to an array points to the entire array itself, rather than to the first element (as is the case with C.)

There are a couple of different ways to specify array b as \[2\]string. You can be specific…

> b := \[2\]string{“Apples”, “Oranges”}

Or you can let the compiler figure it out:

> b := \[...\]string{“Apples”, “Oranges”}

Arrays aren’t used as often in Golang because they’re relatively inflexible. Instead, programmers use slices.

## Slices

Slices are used to create and manage data collections. They serve as the descriptor of an array segment and they contain a pointer to the array, its length, and capacity. The *capacity* is the maximum length of that segment.

You might recall that a slice is composed of multiple elements. Unlike arrays, they’re declared without the length in brackets. The zero value of a slice is *nil* . Both length and capacity are zero and it doesn’t have a reference array.

## Declaration

You can *declare* the type for a variable that will hold a slice with a set of square brackets *\[\]* , then follow it with the element type that your slice will hold. Here are two examples of declaring a variable type, one with numbers and one with string:

> var intSlice \[\]int
> 
> var strSlice \[\]string

You can also declare a slice using the built-in function make instead, which contains length. Capacity is optional. If you only specify the length, the capacity is assumed to be the same. If the capacity is different from the length, you need to declare the capacity value.

Make allocates an array and then returns a slice referring to that array.

> var intSlice make(int\[\], 10) // here length and capacity are the same, 10
> 
> var strSlice make (\[\]string, 10, 20) // length 10 and capacity 20

Or, you can declare a slice with a new keyword. Follow the keyword with the capacity, then the type of elements in the slice:

> var intSlice = new(\[50\]int)\[0:10\]) // keyword is new, with capacity 50 and length 10

Slices can be formed by slicing through an array, but also from another slice. It’s specified by a half-open range, which includes the first value but not the end value, of two indices that are separated by a colon. You can think of it as \[low: high\]. The default low is the 0th value, and high is the length of the slice.

As an example, the expression b\[1:4\] will create a slice of b containing elements 1–3.

Suppose you have a slice b := \[\]byte{‘q’, ‘j’, ‘x’, ‘z’, ‘q’}:

> b\[1:4\] == \[\]byte{‘j’, ‘x’, ‘z’} // remembering that the first element is 0, not 1 and that the first element in the range is included but not the last one

Let’s look at another example with array a and a variety of slices:

> package main
> 
> import “fmt”
> 
> func main () {
> 
> a :=\[5\]{“Britain”, “Canada”, “Australia”, “India”, “New Zealand”\] //array a has 5 elements
> 
> //now let’s start slicing
> 
> slice 1 := a\[1:4\]
> 
> slice 2 := a\[ :3\] //remember default low is 0th
> 
> slice 3 := a\[2: \] //default high is last
> 
> slice 4 := a\[:\]
> 
> fmt.Println(“Array a = “, “a”)
> 
> fmt.Println(“slice 1 = “, slice1)
> 
> fmt.Println(“slice 2 = “, slice2)
> 
> fmt.Println(“slice 3 = “, slice3)
> 
> fmt.Println(“slice 4 = “, slice4)
> 
> }

You’ll get the following output:

> *Array a = \[Britain Canada Australia India New Zealand\]*
> 
> *slice1 = \[Canada Australia India\]*
> 
> *slice2 = \[Britain Canada Australia\]*
> 
> *slice3 = \[Australia India New Zealand\]*
> 
> *slice4 = \[Britain Canada Australia India New Zealand\]*

Note that slices can’t be grown past their capacity and they can’t be resliced below zero. You’ll end up with a runtime panic instead.

## Initialization

Listing the initial values of the slice is known as *initialization* . Use a slice literal with the empty brackets (as above) followed by the type, and then list the initial values in curly brackets *{}* .

> var intSlice = \[\]int{10, 20, 30, 40}
> 
> var strSlice = \[\]string{“Britain”, “Canada”, “Australia”}

## Modifying Slices

Since a slice is a segment of an array, any changes you make to the slice will also change the array it’s based on. Any other slices that reference the same array will also be changed.

Here’s an example based on days of the week that illustrates how modification works.

> package main
> 
> import “fmt”
> 
> func main () {
> 
> a :=\[7\]string{“Mon”, “Tues”, “Weds”, “Thurs”, “Fri”, “Sat”, “Sun”}
> 
> slice1 := a\[1:\]
> 
> slice 2 := a\[3:\]
> 
> fmt.Println(“-----Before Modification-----”)
> 
> fmt.Println(“a = “, a)
> 
> fmt.Println(“slice1 =”, slice1)
> 
> fmt.Println(“slice2 =”, slice2)
> 
> slice1\[0\] = “TUES”
> 
> slice1\[1\] = “WEDS”
> 
> slice1\[2\] = “THURS”
> 
> slice2\[1\] = “FRI”
> 
> fmt.Println(“-----After Modification-----”)
> 
> fmt.Println(“a = “, a)
> 
> fmt.Println(“slice1 =”, slice1)
> 
> fmt.Println(“slice2 =”, slice2)
> 
> }

The output is as follows:

> *“-----Before Modification-----”*
> 
> *a = \[Mon Tues Weds Thurs Fri Sat Sun\]*
> 
> *slice1 = \[Tues Weds Thurs Fri Sat Sun\]*
> 
> *slice2 = \[Thurs Fri Sat Sun\]*
> 
> *\-----After Modification-----*
> 
> *a = \[Mon TUES WEDS THURS FRI Sat Sun\]*
> 
> *slice1 = \[TUES WEDS THURS FRI Sat Sun\]*
> 
> *slice2 = \[THURS FRI Sat Sun\]*

## For and For Range with Slices

Just as you can iterate over some of the other expressions we’ve discussed in Golang, you can also iterate over slices and arrays.

*For*

> package main
> 
> import “fmt”
> 
> func main () {
> 
> days :=\[\]string{“Thurs”, “Fri”, “Sat”, “Sun”}
> 
> for i := 0; i < len (days); i++ {
> 
> fmt.Println(days\[i\])
> 
> }
> 
> }
> 
> The output would look like this:
> 
> Thurs
> 
> Fri
> 
> Sat
> 
> Sun

*For range*

> package main
> 
> import “fmt”
> 
> func main () {
> 
> primenumbers :=\[\]int{2, 3, 5, 7, 11}
> 
> for index, number := range primenumbers {
> 
> fmt.Printf(“Primenumber (%d) = %d\\n”, index +1, number)
> 
> }
> 
> }

You’ll get results that look like this:

> *Primenumber(1) = 2*
> 
> *Primenumber(2) = 3*
> 
> *Primenumber(3) = 5*
> 
> *Primenumber(4) = 7*
> 
> *Primenumber(5) = 9*

## Multidimensional

First, let’s take a look at multidimensional arrays. So far, we’ve used arrays with just one row. Consider a two-dimensional array, which has more than one row and more than one column. You could visualize this as a table with x rows and y columns. Although there’s technically no limit for the number of dimensions you could have, the most useful multidimensional arrays are two dimensions. The syntax for arrays is:

> var arrayName \[ x \] \[ y \]data\_type

For example, a \[2\] \[3\]int has two rows and three columns of numbers. Every element in a two-dimensional array a can be defined by its position: a\[i\]\[j\] where i is the row and j the column. Similarly, you can have two (or more) dimensions in your slices. These are suitable for applications for things like gaming, image processing, and matrix calculations.

## Reslicing, Copying, and Appending

When you *reslice* , you change the length of a given slice. If you want to copy a slice using the builtin function *copy* , you can take elements from the source slice and copy them to the destination. The copy will always have the minimum length of the two slices, and it returns the integer value of the number of elements copied. The syntax looks like this:

func copy (dst, src, \[\]type) where dst is the destination slice and source the original. Here’s an example of copying.

> package main
> 
> import “fmt”
> 
> func main() {
> 
> src := \[\]string{“Red”, “Orange”, “Yellow”, “Green”}
> 
> dest :=make(\[\]string, 2)
> 
> numCopied := copy(dest, src)
> 
> fmt.Println(“src = “, src)
> 
> fmt.Println(“dest = “, dest)
> 
> fmt.Println(“# elements copied from source to dest = “, numCopied)
> 
> }
> 
> }

The output looks appears like so:

> *src = \[Red Orange Yellow Green\]*
> 
> *dest = \[Red Orange\]*
> 
> *\# elements copied from source to dest = 2*

The built-in function *append* adds elements to the end of a slice. If the given slice doesn’t have the capacity for additional elements, then a new array with a higher cap is allocated. If it’s big enough for the appends, the existing array is used. In the case where the slice has enough capacity to accommodate the appendage, any changes to it will also appear in the appending slice, since they’re both referring to the same array.

> package main
> 
> import “fmt”
> 
> func main() {
> 
> slice1 := make(\[\]string, 3, 10)
> 
> copy(slice1, \[\]string{“Red”, “Orange”, “Yellow”})
> 
> slice2 := append(slice1, “Blue”, “Green”, “Violet”)
> 
> fmt.Printf(“slice1 = %v, len = %d, cap = %d\\n, slice1, len(slice1), cap(slice1))
> 
> fmt.Printf(“slice2 = %v, len = %d, cap = %d\\n, slice2, len(slice2), cap(slice2))
> 
> slice1\[0\] = “Pink” // will show in both slices because the underlying array is the same
> 
> fmt.Println(“\\nslice1 = “, slice1)
> 
> fmt.Println(“slice2 = “, slice2)
> 
> }

Your output would look like this:

> *slice1 = \[Red Orange Yellow\], len = 3, cap = 10*
> 
> *slice2 = \[Red Orange Yellow Blue Green Violet\], len = 6, cap = 10*
> 
> *slice1 = \[Pink Orange Yellow\]*
> 
> *slice2 = \[Pink Orange Yellow Blue Green Violet\]*

If the underlying array is different because the slice you’re appending to doesn’t have enough capacity, changes made in the first slice will not carry through to the appended one.

> package main
> 
> import “fmt”
> 
> func main() {
> 
> slice1 := \[\]string{“Red”, “Orange”, “Yellow”}
> 
> slice2 := append(slice1, “Blue”, “Green”, “Violet”)
> 
> fmt.Printf(“slice1 = %v, len = %d, cap = %d\\n, slice1, len(slice1), cap(slice1))
> 
> fmt.Printf(“slice2 = %v, len = %d, cap = %d\\n, slice2, len(slice2), cap(slice2))
> 
> slice1\[0\] = “Pink”
> 
> fmt.Println(“\\nslice1 = “, slice1)
> 
> fmt.Println(“slice2 = “, slice2)

In the output, you can see the difference between the case above and this one. Slice2 doesn’t change just because we changed slice1. We also didn’t specify the len and cap for the first slice, so the code returns what was used in the slice.

> *slice1 = \[Red Orange Yellow\], len = 3, cap = 3*
> 
> *slice2 = \[Red Orange Yellow Blue Green Violet\], len = 6, cap = 6*
> 
> *slice1 = \[Pink Orange Yellow\]*
> 
> *slice2 = \[Red Orange Yellow Blue Green Violet\]*

By using the operator …, you can also append one slice to another.

> package main
> 
> import “fmt”
> 
> func main() {
> 
> slice1 := \[\]string{“Red”, “Orange”, “Yellow”}
> 
> slice2 := \[\]string{“Green”, “Blue”, “Violet”}
> 
> slice3 := append(slice1, slice2, …)
> 
> fmt.Println(“slice1 = “, slice1)
> 
> fmt.Println(“slice2 = “, slice2)
> 
> fmt.Println(“slice3 = “, slice3)
> 
> }

As you probably expected, the output is as follows:

> *slice1 = \[Red Orange Yellow\]*
> 
> *slice2 = \[Green Blue Violet\]*
> 
> *slice3 = \[Red Orange Yellow Green Blue Violet\]*

## Strings, Arrays, and Slices

Since arrays are not very flexible, Go programmers tend to use slices more than arrays. Strings are just read-only slices; you can index them to return bytes and slice them to make a substring, which is very efficient. Golang allows you to create a string from a byte slice:

> str =: string(slice)
> 
> And reverse back to a byte slice:
> 
> slice =: \[\]byte()

## Sorting and Inverting

When it comes to slices in Go, there are three sorting functions. Which you use will depend on the type of data you’re sorting, but all of them will sort slices in ascending order.

1.  sort.Strings
2.  sort.Ints
3.  sort.Floats64

These will all sort the keys according to the type that you have. Here’s an example for sorting ints:

> package main
> 
> import “fmt”, “sort”
> 
> func main() {
> 
> primes := \[\]int{2, 11, 3, 19, 13, 7, 5, 17}
> 
> sort.Ints(primes)
> 
> fmt.Println(primes)
> 
> }

Here’s what the output looks like:

> *\[2 3 5 7 9 11 13 17 19\]*

There are functions that you can use to determine whether your strings, ints, or floats are sorted correctly. As you may have already guessed, there’s a separate function for each.

*   Strings: StringsAreSorted

func StringsAreSorted (a string\[\]) bool // returns true if they’re sorted, false otherwise

Let’s look at a sort check and sort with strings.

> package main
> 
> import “fmt”, “sort”
> 
> func main() {
> 
> animals := {“cow”, “bear”, “coyote”, “panther”, “wildebeest”}
> 
> sorted := StringsAreSorted(animals)
> 
> fmt.Println(sorted)
> 
> sort.Sort(sort.Stringslice(animals))
> 
> sorted = sort.StringsAreSorted(animals)
> 
> fmt.Println(sorted)
> 
> }

Your output is the following:

> *false*
> 
> *true*

*   Ints: IntsAreSorted

> *func IntsAreSorted (int\[\]) bool // returns true if they’re sorted, false otherwise*

*   Float64: Float64sAreSorted

> *In Float64 sorts, the NaN (not a number) items come first. Its function is also similar to ints and strings.*
> 
> *func (Float64sAreSorted)(x \[\]float64) bool*

Custom sorts are also available in Golang. One function to use is *sort.Slice* , which in turn uses the *less* function:

> less(i, j int) bool //shows whether element with index i comes before j

If you want to sort while keeping the same order for elements that are identical to each other, use *sort.Slicestable* instead, which also retains the less function above. Also, if you want j to come before i, you can use the swap function:

> swap(i, j int)

Now let’s see this in action:

> package main
> 
> import “fmt”, “sort”
> 
> func main() {
> 
> jonesFamily := struct { // don’t worry, we’ll get further into struct in a later chapter
> 
> Name string
> 
> Age int
> 
> }{
> 
> {“Caesaria”, 22},
> 
> {“Augustus”, 22},
> 
> {“Julius”, 3}
> 
> {“Octavia”, 4}
> 
> }
> 
> sort.Slicestable(jonesFamily, func (i, j int) bool {
> 
> return jonesFamily\[i\]. age < jonesFamily\[j\].age
> 
> })
> 
> fmt.printLn(jonesFamily)

The output as follows:

> *\[{Julius 3} {Octavia 4} {Caesaria 22} {Augustus 22}\]*

In general, you can use the custom sorts sort.Sort and sort.Stable to perform customized sorts. The syntax to use is:

> type Interface interface {
> 
> Len int // recall that len is the number of elements in the collection
> 
> Less(i, j int) bool
> 
> Swap(i, j int) // if you want to list in reverse order

This is how to swap the order of jonesFamily above:

> type Person struct {
> 
> Name string
> 
> Age int
> 
> }
> 
> type byAge \[\] Person // starting to implement sort.Interface by age
> 
> func(a ByAge) Len() int {return len(a)}
> 
> func(a ByAge) Less(i, j int) bool {return a\[i\].Age < a\[j\].Age}
> 
> func(a ByAge) Swap(i, j int){return a\[i\], a\[j\] = a\[j\], a\[i\]}
> 
> func (main) {
> 
> jonesFamily := Person\[\]{
> 
> {“Caesaria”, 22},
> 
> {“Augustus”, 22},
> 
> {“Julius”, 3}
> 
> {“Octavia”, 4}
> 
> }
> 
> sort.Stable(byAge(jonesFamily))
> 
> fmt.Println(jonesFamily) // \[{Julius 3} {Octavia 4} {Caesaria 22} {Augustus 22}\]

You can also sort in reverse order with the keys, using the reverse function for ints and strings. The syntax for that is as follows:

> func reverse (data Interface) Interface

Let’s see how this works by sorting ages in a company in descending order from highest to lowest.

> package main
> 
> import “fmt”
> 
> func main() {
> 
> num :=int{36, 45, 52, 29}
> 
> sort.Sort(sort.Reverse(sort.Intslice(num)))
> 
> fmt.Println(num)
> 
> }

The output using reverse sorts looks like this:

> *\[52, 45, 36, 29\]*

## Chapter Summary

Slices provide an easy way to work with arrays and strings in Golang.

*   Slices describe a segment of the array and contain a pointer, the length, and the max length (capacity).
*   Programmers can iterate with slices.
*   Additional operations such as reslicing, copying, and appending are also key ways of working with slices in Go.
*   You can sort and reverse sort to order your output.

In the next chapter, you'll learn about maps.

Six 

A *map* is a data type that’s a collection of \[key, value\] pairs; in other languages, they’re referred to as hashes or dicts (dictionaries). Possible keys appear once at most in the collection. Values can vary and may include other maps too.

The hash table, which you may be familiar with in other languages, is convenient for programmers because it provides fast lookups (in addition to adds and deletes). Go’s map implements a hash table. One thing to be aware of with Golang maps is that they can’t be run concurrently unless you mediate it with some code. Suppose you’ve launched a retail shop and you want to store the salaries for each employee; a map would be great for this because you can use the employee names as the key and their salaries as the value.

Although structs (discussed in the next chapter) often work better with JavaScript Object Notification (JSON) than maps do, there are times when you might want to use a map instead. JSON is a common language for transmitting web data from client to server. With a struct, you need to know the details for each JSON element.

When working with APIs and other configurations in which the data type and name are static, programming in the details is relatively easy. But if you don’t know the JSON structure in advance for code that needs to parse it, maps allow you to parse all of its fields without dropping any.

## Declaration and Initialization

Like pointers and slices, map types are references. That means a nil map doesn’t have any values and keys can’t be added to it. Go returns an error if you try to add an element to an uninitialized map and behaves like an empty map while reading. To create a map, you can use the make builtin or declare a map literal.

Using the *make* builtin allocates and initializes a hash structure. It returns a map value that points to the data structure. If you use make, the syntax is as follows:

> make(map\[type of key\]type of value)

Using the above example, you could write

> Salary =: make(map\[string\]int)

With no elements to it, the map is empty. Add the elements in to create an actual map.

> package main
> 
> import “fmt”
> 
> func main() {
> 
> Salary =: make(map\[string\]int)
> 
> Salary\[Jennifer\] = 50000
> 
> Salary\[Ben\] = 25000
> 
> Salary\[Matt\] = 20000
> 
> fmt.Println(“Salary map contents = ”, Salary)
> 
> }

Your output looks like this:

> *Salary map contents = map\[Jennifer:50000 Ben:25000 Matt:20000\]*

You can also declare a map literal that initializes the map with some data:

> package main
> 
> import “fmt”
> 
> func main() {
> 
> Salary =: map\[string\]int {
> 
> “Jennifer”: 50000,
> 
> “Ben”: 25000,
> 
> }
> 
> Salary\[Matt\] = 20000 //adding Matt in
> 
> fmt.Println(“Salary map contents = ”, Salary)
> 
> }

## Key Value Item

In Go, a key can be almost any type including boolean, string, int, and struct (we’ll cover these in detail in a later chapter). But because they can’t be compared using ==, slices, maps, and functions can’t be used as keys in your map. Consider the following statement:

> m\[“route”\]=66 //here the key is “route” and the value is 66.

To retrieve the value stored in “route” and assign it to new variable p:

> p =: m\[“route”\]

If the key doesn’t exist, then the zero value for that value type is returned. In this instance, the type is int, so the zero value is 0.

> q =: m\[“rute”\] // q == 0

You can test to see if the key exists on a particular map.

> p, ok := m\[“route”\]

If the key doesn’t exist, then the first value (here, p) is that type’s zero value. The second is boolean, which will be true if the key shows on the map and false if it doesn’t. You can also test that the key exists without returning the value by using underscore (\_) as the first value:

> \_, ok := m\[“route”\]

When the key isn’t present, the map returns zero. Programmers find zero values in maps useful for a variety of reasons. You could use it with boolean values, because the zero value in bool is *false* . You can test a map easily to find out if a condition is true or not. It’s also helpful when working with slices, because appending to a nil slice results in the allocation of a new slice. You wouldn’t have to test to see if a key is present because you can simply append a value to a map of slices.

Maps can also be used with strings. Note that the syntax shows each key-value pair connected by a colon (:). The pairs may not always return in the same order because maps in Go are unordered, but the pair relationships stay the same.

For example, you could have a map that describes a dog:

> map\[string\]string{“name”: “Powerpuff”, “breed”: “Jackaroodle”, “color”: “white/brown”, “owner”: “PetuniaJones”}
> 
> Here, the keys are “name”, “breed”, “color”, “owner” and the values are “Powerpuff”, “Jackaroodle”, “white/brown”, “PetuniaJones”.

If you wanted to print it out, you could store the map inside a variable.

> powerpuff := map\[string\]string{“name”: “Powerpuff”, “breed”: “Jackaroodle”, “color”: “white/brown”, “owner”: “PetuniaJones”}
> 
> fmt.Println(powerpuff)

Your output would print as follows:

> *map\[breed: Jackaroodle color: white/brown owner: PetuniaJones name: Powerpuff\]*

You might have already noticed the need to differentiate between a stored value of 0 and a zero value of 0 because the key isn’t found. When you look up a value, you have the option of returning a second value, which is a bool. Conventionally, this is known as the *ok idiom* (as you saw above). Use ok as the second value, because it will return “false” (instead of a misleading zero) if it doesn’t find the key.

For example, suppose you have a map called fluffythings, and you want to see if it contains the key “route”. If you simply wrote this:

> fluffythings := map\[string\]int{}
> 
> fmt.Println(fluffythings\[“route”\])

you’d end up with an output of 0, which is int type’s zero value. But if you didn’t already know that fluffythings didn’t contain “route”, you might assume that the actual value is 0. Instead, use the ok idiom:

> fluffythings, ok = fluffythings\[“route”\] // technically the second value can be anything, but the convention is to use ok

If “route” is contained in fluffythings, ok is true and otherwise is false. You can also try adding on if-else statements to tell the program what to do, as follows:

> if ok {
> 
> fmt.Println (“Fluffythings has route.”)
> 
> } else {
> 
> fmt.Println(“Route was not found.”)

Maps act like databases. If you want to get an index value, you call an integer. With a map, you call the key to get the value that’s related to it. Using the example above, you could isolate the name by calling the variable holding the map and its related key:

> powerpuff\[“name”\]

When printing it out using fmt.Println(powerpuff\[“name”\]), the output is Powerpuff. Similarly, you could call the other values in powerpuff:

> fmt.Println(powerpuff\[“breed”\]) // returns Jackaroodle
> 
> fmt.Println(powerpuff\[“color”\]) // returns white/brown
> 
> fmt.Println(powerpuff\[“owner”\]) // returns PetuniaJones

There are no convenience functions that allow you to list the keys and/or values in a map. However, you can get there using iterations.

## For Range

Using the *for range* function to iterate over maps will return two values, the first one being the key and the second being the value. The language uses the correct type for both. What iteration with maps does *not* automatically do in Go is retain the same order in every loop. If you want the loops to run in the same order every time, you’ll need to write a data structure that maintains the order you want.

In this iteration example, both key and value are strings, and the result will also be a string:

> for key, value := range powerpuff {
> 
> fmt.Printf(“%q is the key for the value %q\\n”, key, value)
> 
> }

Which results in the following output:

> “breed” is the key for the value “Jackaroodle”
> 
> “color” is the key for the value “white/brown”
> 
> “owner” is the key for the value “PetuniaJones”
> 
> “name” is the key for the value “Powerpuff”

## Slices and Maps

If you just want to get a list of the keys, you can use *range* for that as well. Declare a variable that only accesses the keys in your map, then append a slice to hold the keys:

> keysOnly :=\[\]string{}
> 
> for key := range powerpuff {
> 
> keysOnly := append(keysOnly, key)
> 
> }
> 
> fmt.Printf(“%q”, keysOnly)

This results in an output of

> *\[“breed” “color” “owner” “name”\]*

You can write similar code to provide a list of values without keys. That allows the program to run more efficiently (although there’s more code, as happens in Go). Here, you’ll preallocate the slice:

> powerpuff := map\[string\]string{“name”: “Powerpuff”, “breed”: “Jackaroodle”, “color”: “white/brown”, “owner”: “PetuniaJones”}
> 
> items := make(\[\]string, len(powerpuff)) //specifying the length of string to avoid potential memory allocations
> 
> var j int
> 
> for\_, v := range powerpuff { //using underscore because you don’t want the keys returned
> 
> items\[j\] = v
> 
> j++
> 
> }
> 
> fmt.Printf(“%q”, items)

You’ll get the output of the values.

> *\[“PetuniaJones” “white/brown” “Powerpuff” “Jackaroodle”\]*

## Modifying your Maps

In Golang, you’re not required to use a function or a method to make changes to your maps. You can add, change, and delete values.

*   Adding to maps

Here’s the syntax for adding to a map:

> map\[key\] = value, where map is the name of the map variable

For example, suppose that you need to keep a list of all the users and their usernames in your company.

> usernames := map\[string\]string{“Anna”: “axolotl”, “Mary”: “maxolotl”, “Suzanne”: “snaxolotl”} // this is your existing map
> 
> usernames\[“Tanya”\] = “taxolotl”

When you print it out...

> fmt.Println(usernames)

...you’ll see the new pair added to the existing map:

> \[Tanya: taxolotl Mary: maxolotl Suzanne: snaxolotl Anna: axolotl\]

*   Changing the values in a map

This type of operation is similar to adding to a map. All you need to do is provide the key with its new value; when you print it, you’ll be able to see the modifications.

Suppose you’re tracking the closed sales for everyone in your company. In real life, you’d probably just make sure that your CRM system is linked to the sales data, but let’s pretend you’re updating these in real-time. This morning, Tanya had $30,000, Mary had $35,000, Suzanne had $25,000, and Anna was at $25,000. Anna just closed a $15,000 deal, so you need to update her number to $40,000. You need to pass the new value to the key “Anna”:

> salesClosed :=map\[string\]int{ “Tanya”: 30000, “Mary”: 35000, “Suzanne” 25000, “Anna”: 25000}
> 
> salesClosed\[“Anna”\] = 40000
> 
> fmt.Println(salesClosed) //which shows you that the amount was updated.

Your output would then show:

> *map\[Mary: 35000 Anna: 40000 Suzanne: 25000 Tanya: 30000\]*

*   Deleting

You can delete a pair from a map, or all the values inside the map itself, which you can then use again in a different way.

To delete a pair, you can use the builtin function *delete* . The syntax is as follows:

> delete\[map, key\] where the map is the one you’re removing a pair from, and the key is the one you want to get rid of (which will also delete its value from the map).

Continuing with the above example, suppose Suzanne is fired for her relatively poor performance. Here’s how you’d remove her from the usernames map.

> usernames := map\[string\]string{“Anna”: “axolotl”, “Mary”: “maxolotl”, “Suzanne”: “snaxolotl”, “Tanya”: taxolotl }
> 
> delete\[usernames, “Suzanne”\]

To confirm that Suzanne is removed from the map you can print it out:

> fmt.Println(usernames)

And the output will read:

> *\[Tanya: taxolotl Mary: maxolotl Anna: axolotl\]*

## Sorting

As you’ve learned, maps are unordered in Go. However, you can arrange maps with the *sort* function. Let’s continue with the ages of the remaining users for our company to show how this works in maps.

> package main
> 
> import “fmt”
> 
> func main() {
> 
> m :=map\[string\]int{“Anna”:25, “Tanya”: 21, “Mary”: 37,}
> 
> keys := make(\[\]string, 0, len(m))
> 
> for k = range m {
> 
> keys = append(keys, k)
> 
> }
> 
> sort.Strings(keys)
> 
> for\_, k := range keys{
> 
> fmt.Println(k, m\[k\])
> 
> }

The result is the sorted output by key as follows:

> *Anna 25*
> 
> *Mary 37*
> 
> *Tanya 21*

## Chapter Summary

Maps are unordered collections of pairs of keys and their associated values. They’re based on hash tables and serve the same purpose as hashes or dicts in other computer languages.

*   Like pointers and slices, maps are reference types.
*   Keys can be almost any type, except maps (though maps can be value items), slices, and functions.
*   For range is most common for iterating over maps, but unless you sort it first, the result can be unordered (though later versions of Go sort by key automatically.)
*   Range can also provide a list of key values because those aren’t automatic as they are in some other languages.
*   You can add, change, or delete values from maps fairly easily.
*   Maps can be sorted, as long as you provide a data structure for it.

In the next chapter, you'll learn all about structs.

Seven 

In earlier chapters, we promised you’d learn more about structs; you’re finally there! *Structs* are collections of data fields with declared data types. In Golang, you can combine types, both built-in (like int) and custom, user-defined types.

The only way to create stable user-defined types is to use structs, which allow you to create and pass more complex data structures around your programs. It’s also common to use structs as a template for a data record, such as an employee record or a product for an e-commerce business.

Basically, anything that has a set of properties and/or fields is a great candidate for a struct. Since an address contains the street name and number, city, state/province, zip/postal code, and country name, collecting addresses into a struct makes sense. Structs are helpful when you need to organize information, particularly when you have a lot of it.

## Introduction to Structs

A really simple way to think about a struct is like a recipe. The field names are the ingredients, such as salt. The data types are the *kind* of ingredient, like sea salt.

Here’s what the declaration of a struct looks like:

> type identifier struct { //where the identifier is the name you’re giving the struct
> 
> field1 data\_type
> 
> field2 data\_type
> 
> field3 data\_type
> 
> }

The struct type is a blueprint for the kinds of data that the structure will hold. There are several ways to declare a struct. Suppose you’re declaring a struct named rectangle with three different fields and different types of data.

> type rectangle struct {
> 
> length float64
> 
> width float64
> 
> color string
> 
> }

You can also initialize one by adding data fields using the keyword *var* and dot notation. The latter tells the program to access data for a specific type.

> package main
> 
> import “fmt”
> 
> type rectangle struct {
> 
> length float64
> 
> width float64
> 
> color string
> 
> type geometry struct {
> 
> area int
> 
> perimeter int
> 
> }
> 
> }
> 
> func main () {
> 
> var rect rectangle //dot notation used here
> 
> rect.length = 5
> 
> rect.width = 10
> 
> rect.color = “violet”
> 
> rect.geometry.area = rect.length \* rect.width
> 
> rect. geometry.perimeter = 2 \* (rect. length + rect.width)
> 
> fmt.Println(“Area:/t”, rect.geometry.area)
> 
> fmt.Println(“Perimeter:”, rect.geometry.perimeter)
> 
> }

Another way is to create a struct literal with the fields initialized with their values.

> package main
> 
> import “fmt”
> 
> type Employee struct { //as a reminder, since this struct begins with a capital letter, it can be used in other packages
> 
> lastName, firstName string
> 
> salaryint
> 
> fullTimebool //allows the programmer to use true/false
> 
> func main() }
> 
> buffy := Employee { //using := here allows Go to infer the type for Employee automatically
> 
> firstName: “buffy”,
> 
> lastName : “Vampireslayer”,
> 
> fullTime: true,
> 
> salary: 10000,
> 
> }
> 
> fmt.Println(buffy)
> 
> }

The output on the screen is as follows:

> *{buffy Vampireslayer 10000 true}*

## Anonymous Structs

With no explicit definition for the struct type, you have an *anonymous struct* . Many developers use these when they don’t want to reuse a struct type. To create one, you’ll need to write a struct using the same syntax for the initial values and the inline struct type.

> package main
> 
> import “fmt”
> 
> func main () {// notice there’s no declaration of struct type before this statement
> 
> giles := struct {
> 
> firstName, lastName string
> 
> salaryint
> 
> fullTimebool
> 
> {}
> 
> firstName: “Giles”,
> 
> lastName: “Professor”,
> 
> salary: 20000,
> 
> }
> 
> fmt.Println(giles)
> 
> }

The output shows up as follows:

> *{Giles Professor 20000 false}*

When you only define the data types, Golang uses the data type declarations (keywords) as the field names. Since a struct field can be any data type, it can also be a struct. In other words, a struct can have a struct type as a data type. These are known as *nested* (or *embedded* ) *structs* .

You can access a field using dot notation that returns a struct, and similarly you can find or update a field in a nested struct. Suppose, using the example above, you wanted to access the salary field:

buffy.salary returns a struct, then

buffy.salary.bonus is involved in the nested struct shown below:

> package main
> 
> import “fmt”
> 
> type Compensation struct {
> 
> basic int // note these are fields inside the Compensation struct
> 
> healthins int
> 
> bonus int
> 
> }
> 
> type Employee struct {
> 
> lastName, firstName string
> 
> salaryCompensation // struct above, nested
> 
> bool//anonymous
> 
> }
> 
> func main() {
> 
> buffy := Employee{
> 
> firstName: Buffy,
> 
> lastName: Vampireslayer,
> 
> bool: true,
> 
> salary: Compensation{10000, 9999, 50000} //the nested struct returned
> 
> }
> 
> fmt.Println(“Buffy’s bonus compensation”, buffy.salary.bonus) //returns the bonus field
> 
> }

The output is

> *Buffy’s bonus compensation 50000*

When you use an anonymous struct where you’ve left out the field name, you can also create a nested anonymous struct. All the nested fields are available to the parent struct with *field promotion* .

Another field type that a struct can take is a function. Here’s an example where the struct has two fields, one a string and the other a function:

> package main
> 
> import “fmt”
> 
> type FullNameType func(string, string) string
> 
> type Employee struct {
> 
> FirstName, LastName string
> 
> FullNameFullNameType
> 
> }
> 
> func main() {
> 
> e := Employee{ //struct e needs to have the same syntax for the function type
> 
> FirstName: “Buffy”,
> 
> LastName: “Vampireslayer”,
> 
> FullName: func(firstName string, lastName string) string {
> 
> return firstName + “ “ + lastName
> 
> },
> 
> }
> 
> fmt.Println(e.FullName(e.FirstName, e.LastName)) // executing the function e.FullName
> 
> }

As a result, your output is simply

> *Buffy Vampireslayer*

## Metadata and Tags

Structs in Golang also give you the ability to add *metadata* to the fields. This is helpful when you want to provide information on how to encode or decode when you’re translating to or from a different format, or plan to store or retrieve it from another database. That being said, you can store whatever you want, whether it’s for yourself or a separate package. You define it through a string literal.

Suppose you’re storing metadata to use the struct for JSON encoding or decoding purposes. (JSON is a well-known data interchange format used for communication between many web applications.) We’ll use it here to show the metadata syntax:

> type Employee struct {
> 
> firstNamestring \`json: “firstName”\`
> 
> lastNamestring \`json: “lastName”\`
> 
> salary int \`json: “salary”\`
> 
> fullTimeint\`json: “fullTime”\`

This leads us to *struct tags,* which are short strings that are assigned some value and set off with backticks (\`). They don’t affect your Go code unless another code will examine them.

## Chapter Summary

Structs are collections of data fields that enable you to pass complex information in your code, similarly to classes in object-oriented programming.

*   Structs are like recipes for the data your structure will hold; there are several ways to declare and initialize them.
*   Without an explicit definition for the struct type, you have an anonymous struct that programmers like to use so they don’t have to reuse a struct type.
*   Struct fields can also be struct types, in which you have a nested or embedded struct.
*   Adding struct tags allows you to annotate the code with instructions that can be read by other packages (or formats) without affecting the Golang code you’ve written.

In the next chapter, you’ll learn about packages.

Eight 

As we’ve discussed, Go was developed by Google engineers who wanted better, faster code. A key principle in writing high-quality programs is DRY: Don’t Repeat Yourself. If you’re copying and pasting, you’re doing something wrong.

There are two major ways that Golang was engineered for DRY and reusability. The most basic is the use of functions, and the other is the concept of a package. A *package* is a directory that contains source files and/or other Go packages. Related source files are collected in a way that makes them modular and reusable in other code that you’re writing.

Every source file that you use must belong to a package. The first line of code for any source file must be the package declaration as follows:

> package packagename

All types, variables, and functions in your source file become part of that package. You can export something defined in one package to another package, or keep it for use inside that specific one. If you export them, other packages can import them and use whatever functions, variables, etc. are in the export.

## Standard Library Overview

You’ve seen the import of the *fmt* package in the examples shown in the book—it’s a core library package that includes functionalities related to formatting and printing output (to the screen), as well as reading certain types of input. When you import it into your program, you’re able to access items like Println() and Printf().

If you’re wondering why it’s so important to collect these functions together in a package or to have packages in general, consider how they help you as a programmer to follow the DRY principle.

*   Reduces naming conflicts

By having the same function names in different packages, you run into fewer issues with naming. It also improves your speed as a programmer by not trying to come up with a separate name every time you code that avoids conflicting with something else you wrote.

*   Organizes code that you want to reuse

This is key for DRY! Being able to quickly access functions and code that you’ve previously written means fewer repeats. You import the ones you want without writing more code, which speeds you up as a developer. Sure, you could go hunting for source files; maybe you had a Println() in one file and Printf() in a completely different one. Maybe you remember that you had it earlier (and maybe you don’t), but collecting similar files together means you don’t have to go hunting for the code you used before.

*   Speeds up the execution

Since Go makes use of a compiler, having to re-compile for a new program that uses a previous function would slow the program down quite a bit. Instead, only the parts that have changed must be re-compiled.

Another package that you’re already familiar with is *main* . It’s used with *commands* , or programs that are intended to be executable. Packages that aren’t executable are, well, packages. There are a couple of ways that you can import packages into your program. One is as follows:

> import “packagename”

You can import multiple packages for your program in this way:

> import “fmt”
> 
> import “math”
> 
> import “math/rand” // the package name is the last element of the import path, in this case *rand* . It’s a subdirectory inside the math package.

You might choose to use the factored method; either way, you’re importing a package for use with your code.

> import (
> 
> “fmt”
> 
> “math”
> 
> “math/rand”
> 
> )

Go comes with plenty of packages that have standard elements in the code, so before you create a custom package, check the standard library first. There are also additional sub-repositories that may be looser in terms of compatibility compared with the standard library.

As a refresher, the capitalization of a variable, type, or function to be exported starts with a capital letter. If it begins with lowercase, it will not be visible outside the package that you used it in and can’t be exported. When you’re importing a package, only the capitalized elements will be brought to your code. For example, if you define MaxInt64 in your code, it can then be exported out. If you name it maxInt64, it’s only visible inside that package.

## Regexp

Short for *regular expression* , *regexp* is a sequence of characters that are used to pattern-match and search and replace text. Many computer languages use it, and it’s also the standard package in Go for writing regular expressions. You can use regexp for filtering, parsing, validating, and extracting information from large amounts of text, such as logs or output generated from other programs. It can be used concurrently with goroutines. If your search query is complicated, compile a regular expression to create a regexp element.

You can use it to extract text from square brackets \[\], pull dates out of a string, extract a hostname or IP address, validate format for an email address, replace any non-alphanumeric characters (\*,&,@, ^, etc.) with a dash, split a string whenever a white space is found, and so on.

For example, the regular expression *a . b* matches any string that begins with *a* , ends with *b* , and contains any character in between (represented by the period.) The function *regexp.MatchString* will check to see if there’s a substring that matches *a . b* .

> matched, err := regexp.MatchString(\`a.b\`, “aaccbb”)
> 
> fmt.Println(matched) //true
> 
> fmt.Println(err) //nil, because regexp is valid

You can also check to see if a full string (as opposed to a substring) matches a . b. Here, you use ^ to signal the beginning of the text or line and $ to anchor the end of it. Likewise, you can check the start or the end anchor.

> matched, \_ := regexp.MatchString(\`^a.b$\`, “aaccbb”)
> 
> fmt.Println(matched) // false

When it comes to more complicated queries, it’s best to compile a regular expression to create a regexp object. You can do this in one of two ways:

> 1\. re1, err := regexp.Compile(\`regexp\`) // error if regexp invalid
> 
> 2\. re2 := regexp.MustCompile(\`regexp\`) //panic if invalid

You can use regexp *split* to slice a string into subslices. Here’s an example that shows the second way (re2) along with split. Here, the instructions are to split at the letter *a* into a substring according to the integer *n* . If n >0, then it can return n matches.

> a := regexp.MustCompile(\`a\`) // notice the backticks around a, which is what regexp must match to return a value
> 
> fmt.Printf(“%q\\n”, a.split(“pajama”, -1)) // returns \[ “p” “j” “m” “ “\]
> 
> fmt.Printf(“%q\\n”, a.split(“pajama”, 0)) // \[\] or nil slice
> 
> fmt.Printf(“%q\\n”, a.split(“pajama”, 1)) // \[“pajama”\] because we have requested one slice
> 
> fmt.Printf(“%q\\n”, a.split(“pajama”, 2)) // \[ “p” “jama”\] because we requested 2 slices, and the split occurs at the first letter *a* ; since n=2 at most it can return 2 matches

## Sync

As we’ve discussed, Go allows multiple goroutines to occur simultaneously. Without regulation, goroutines would end up competing for data. Channels (which we’ll discuss later) and sync packages are used to synchronize simultaneous operations to avoid the issue.

A task that can’t be subdivided by the computer is an *atomic operation* ; it’s something the computer executes directly from one instruction that can’t be interrupted. An operation is also considered atomic if it has multiple lines of code to execute but only one write element with data. Many operations are not atomic, and many goroutines execute faster or slower than one another, which leads to *data competition* or *data contention* . As a result, routines may not execute the same way every time because they may be preempted by a faster routine or have another data contention issue.

Of course, no programmer wants their code to come out differently every time. The point of coding is to get the right answer no matter what else may be running. *Thread-safe concurrency* is the goal, where concurrency doesn’t generate data competition. *Sync packages* help develop this kind of code.

*   sync.WaitGroup

This struct waits for a group of goroutines to finish executing and blocks control until they’re complete. Each value of sync.WaitGroup maintains an internal count with the initial default of zero. In this example, the main goroutine waits for 1000 to execute, then unblocks to run:

> import “sync”
> 
> import “sync/atomic” // provides support for atomic operations, which mostly involve int types and include add, subtract, swap, compare and swap, store, and load
> 
> func add (w \*sync.WaitGroup, num \*int32) {
> 
> defer w.Done()
> 
> atomic.AddInt32(num, 1) //replaces \*num = \*num +1, which is not an atomic operation and could vary in results when run concurrently with another routine
> 
> }
> 
> func main () {
> 
> var n int32 = 0
> 
> var wg \*sync.WaitGroup = new(sync.WaitGroup)
> 
> wg.Add(1000)
> 
> for i := 0; i < 1000; i = i + 1 { //you recognize this as a for loop iteration
> 
> go add(wg, &n) //creates 1000 new goroutines
> 
> }
> 
> wg.Wait()
> 
> Println (n) //guarantees that n is 1000
> 
> }

*   sync.Once

This operation is used for ensuring that the code isn’t used by simultaneous goroutines. Here’s an example, where doIt will only be run by one routine.

> var once \*sync.Once = new(sync.Once)
> 
> for i := 0; i < 10; i = i + 1 { //10 goroutines here
> 
> go func() {
> 
> printLn(i) //printLn must be executed before doIt can run
> 
> Once.do(doIt()) //only executed by one routine
> 
> } ()
> 
> }

*   sync.Mutex

If you want to make sure that a variable can only be accessed by one goroutine at a time while running concurrently, you need *mutual exclusion* to avoid any conflicts. The data structure for this is known as *Mutex* .

Go has two methods for this: *Lock* and *Unlock* . While the routine is in Lock, no other routine can access it. Unlock is used to allow other routines to use the variable once the goroutine is finished.

A Mutex value is commonly referred to as a mutex lock. A mutex lock that hasn’t been locked yet is a Mutex zero value. If the subroutine is not yet locked, calling m.Lock() will change it to locked and calling m.Unlock() results in an exception.

If the goroutine has been locked, m.Lock() is blocked until m.Unlock() is called to release the lock.

*   sync.RWMutex

While a goroutine is writing and RWMutex is involved, the concurrent ones can neither read nor write. In addition to Lock and Unlock, RMutex also includes RLock and RUnlock. As a general guide, here’s what each method does when locked and unlocked:

> • func(rw \*RWMutex)Lock() //get a write lock
> 
> • func(rw \*RWMutex)UnLock() //release a write lock
> 
> • func(rw \*RWMutex)RLock() //get a read lock
> 
> • func(rw \*RWMutex)RUnLock() //release a read lock

*   sync.Cond

The condition variable notifies blocked goroutines when the state of shared data changes. They’re always used in combination with Mutexes.

Sync.Cond examines a lock to determine whether it meets the processing conditions. If so, it unlocks and notifies the other goroutines, then blocks itself. When the goroutines finish executing, they alert the conditional, which unblocks itself and gets the lock.

‣ cond.L.Lock() and cond.L.Unlock() operate similarly to the mutex locks

‣ cond.Wait() tells the code to

1.  UnLock()
2.  blocking the waiting notification = waiting for Signal or Broadcast as below
3.  receives notification
4.  Lock()

‣ cond.Signal() notifies a Wait goroutine. The order of notifications is based on the original waitlist and runs FIFO (first in, first out). If there are no Wait routines, there’s no error report.

‣ cond.Broadcast alerts all Wait goroutines at once in contrast to cond.Signal, which operates in order. Like cond.Signal, if there are no Wait goroutines, there won’t be an error report.

‣ sync.Map

You need this to operate multiple maps at the same time to avoid the error you’d get by running them in parallel.

*   sync.Pool

sync.Pool is used to cache objects, which relieves pressure on the Garbage Collector (GC) and keeps Go running quickly. Initializing a pool requires you to set up the *New* function. When there’s a cached object and you call Get, it returns the object directly. If not, New is called to create it.

Pool is best for when you have a lot of memory and concurrency. If there isn’t much memory or concurrency, it’s counterproductive to use a pool. The best practice is also to empty the pool before you Put objects in it and after you Get the objects in it.

## Accurate Computations

Due to the way Go is written, there can be issues when dealing with large numbers. For example, the factorial of 100 contains 158 digits, so it can’t be stored in primitive data types like the ones in Go. It doesn’t have the implicit overflow checking that you might find in other languages, so trying to put a number over 64 bits into int64 may lead to unexpected results. You won’t get an error message, but you’ll get something that doesn’t look right.

To avoid the problem, use the package named *big* . Big is designed to allow programmers to work with large numbers using arbitrary-precision arithmetic, which typically stores in arrays instead of bits. This can be used when you need very accurate numbers and/or the arithmetic speed is not an issue.

The package supports Int, Rat (rational numbers), and Float. The zero values for all three are zero. Therefore, new values are easy to declare and don’t require initialization. The syntax can be as follows, with *x* , *r,* and *y* all zero values:

> var x Int
> 
> var R &Rat{}
> 
> y := new(Float)

It’s also an issue when it comes to type conversion since the input is commonly a primitive data type. An easy way to get around it is to use a JSON property as a string.

## Custom Packages

Once you’ve written code that you know you’ll reuse, it’s good practice to make it a package so you won’t need to copy and paste or try to remember where you used it last; all you’ll need to do is import the package in the future. When you’re ready to create your package, you need to be in your Go programming environment and workspace. In your directory, create the directory name that will hold the package—this is typically the same name as the package itself, for ease of import. It’s conventional to name the first file in the directory after the directory name.

Suppose you wanted to create a package called greeting. The name of the directory would be greeting, and the file would be greeting.go. To write the program, open the file.

When you’re writing packages, the first line should be the name of the package you’re creating. Then import whatever packages you need, like *fmt* . For this custom package example, we’ll be using the iconic Hello, World! in the code. Once you’ve written this package, anytime you want to use it, you just need to import the package.

> package greeting //everything in this file will be included in the package
> 
> import “fmt”
> 
> func() Hello {
> 
> fmt.Println(“Hello, World!”)
> 
> }

You can bring this package into executable files or entry points, often named main.go. Here’s what it looks like when you call the package:

> package main
> 
> import “greeting”
> 
> func main() {
> 
> greeting.Hello() //use dot notation to call the function (Hello) in the imported package
> 
> }

You can also add variables and types to your package; the syntax should look familiar from previous examples. First, add what you need to your package. The following code shows a modification to *greeting* :

> package greeting
> 
> import “fmt”
> 
> var Pet = “Powerpuff” //adding the variable
> 
> type Unicorn struct { //creating Unicorn type with name and color fields
> 
> Name string
> 
> Color string
> 
> }
> 
> func (Unicorn) String() string {
> 
> return fmt.Printf(“The unicorn’s name is q% and is the color %s.”, Name, Color)
> 
> }
> 
> func() Hello {
> 
> fmt.Println(“Hello, World!”)
> 
> }

To call the package with the new variable and type, your code would look something like this:

> package main
> 
> import “fmt”
> 
> import “greeting”
> 
> func main() {
> 
> greeting.Hello
> 
> fmt.Println(greet.Pet) //using the variable Pet defined in *greeting*
> 
> uni := greet.Unicorn{
> 
> Name: “Petunia”,
> 
> Color: “Fuschia”,
> 
> }
> 
> fmt.Println(uni.String())
> 
> }

Your output will look like this:

> *Hello, World!*
> 
> *Powerpuff*
> 
> *The unicorn’s name is Petunia and is the color fuchsia.*

Putting your custom package in its own directory makes it easier for you to find and add to other codes.

## Documenting your Package

You’ve seen C++-style line comments in many of the examples so far, which are set off with “//”. The language also allows for C-style block comments: “/\* \* /”. Block comments typically precede the package clause and are used for comments about specific packages.

Comments are plain text, so don’t use HTML tags or syntax in your descriptions. Your package comment introduces the package and explains how it should be used. It should give the reader a brief idea of what’s happening. If your package has more than one file, you can insert the package comments in any file. It appears first on the godoc page.

Go is designed to make it easy for all users to understand the purpose of the code that a programmer has written. The program and server *godoc* pulls out documentation about a given package (or type, variable, etc.) from source files.

## Package Distribution with Git

Since Go doesn’t have a central package repository, you’ll often be pulling third-party packages. What you’ll find on the web are known as VCS (version control systems), such as Git (*.git* ) and Subversion (*.svn* ). Others include Bazaar (*.bzr* ), Fossil (*.fossil* ), and Mercurial(*.hg* ). GitHub is one of the Go repositories that use Git. Others include bitbucket.org (which also handles Mercurial) and IBM Dev Ops at hub.jazz.net.

First, you need to go get the package you want. Go can pull packages from anywhere on the Internet and install them. For that, the syntax looks like this (very much like a URL):

> go get repository.com/username/packagename

There are no quotation marks because it’s not using the import command, but rather *go get* . Note that there is no http protocol included because go get takes care of all that. Here, we’re using repository.com for a general form of bizbucket.org or github.com.

Once you go get it, Go installs it under $GOPATH/src as repository.com/username/packagename. Now you’ve got the package sitting locally, but you still need to import it into your program. Use the usual import function:

> import “repository.com/username/packagename”

## External Packages, Libraries, and Projects

In the previous section, you learned that Go can pull packages from anywhere on the web that supports the language and uses a compatible VCS. There are also standard libraries (stdlib) that live inside your $GOROOT directory, and these you don’t need to go get or install.

If you’re importing a package that you’ve already defined in your program, use a relative path (which doesn’t contain any references to outside URLs). Name the directory that your program is in and the directory inside that with the package you want.

> import “myprogram/mostexcellentpackage”

But suppose you want to use a package that you saved to a third-party repository like GitHub. You’ll need to go get it and import it as described above, the same way that you’d import someone else’s package.

Projects are a great way to learn code. Tutorials that show you how to take steps are the building blocks, but taking on projects helps you implement what you’ve learned. Projects can be building a website, creating an app, redesigning a website template, or anything else you come up with.

When you’re thinking about your packages, consider the following ideas to guide you in structuring everything. Since Go is intended to be open-source, simplicity and ease of use are two key principles to follow in your projects.

*   Consistency

Your code should have a consistent look and feel to it, using the same conventions in all your packages and projects.

*   Simplicity

It should be simple enough to be easy to read and use, but not so simple that steps or important information are left out.

*   Ease of navigation

Make it clear how to move around the structures you have in place. This will help both you and other users. Use obvious naming conventions so you won’t have to try to figure out what’s in any folder or directory.

For small projects, it’s enough to keep all your code in one folder, but as you develop larger ones this often becomes problematic. Additional conventional folders include:

*   /cmd

Contains the entrypoint files (executables).

*   /internal

Holds private library code and is specific to the service without being shared with any others.

*   /pkg

Contains files that you’re OK to share with other users.

## Chapter Summary

Packages in Go allow programmers to reuse code easily without copying and pasting or remembering where a piece of code is. Importing a package brings all of the information in that file to the current program.

*   The standard library is extensive and comes with many commonly used items.
*   Writing regular expressions with the regexp package saves time.
*   Sync package helps concurrent goroutines avoid data competition, which creates undesired problems and results.
*   You’ll need a package to ensure that the program runs accurate computations since there are times when 64 bits is not long enough to hold the data.
*   Although there are many standard packages to choose from, you can also create your own when necessary.
*   In the interests of open-source, developers should document their packages so other users understand the purpose.
*   Since Golang doesn’t have a central repository, you may need to import packages from third-party version control systems such as Git and Bazaar.
*   External libraries, packages, and projects have conventions to follow.

In the next chapter, you'll learn about methods.

Nine 

By now, you’ve worked with plenty of functions, but you might need to use multiple functions on the same piece of data. No need to copy and paste; instead, you can use a *method* that operates on a specific type, known as the *receiver* . With methods, you can explain what the data type is and how it should be used. In other languages, the receiver is a keyword, but Go considers the receiver a variable so you can name it whatever you like. The convention is to use lowercase letters for the receiver type.

Methods are the only way to implement interfaces, which are in chapter ten. When you embed a type, you get access to the relevant method. If you’re using an editor that features autocomplete in Go, you can get method suggestions from autocomplete rather than referring to your documentation every time. While this isn’t a major reason to use methods, it speeds up your process.

## Differences between Functions and Methods

The syntax for a method is very similar to that of a function, with an additional parameter to specify the receiver. Calling methods is similar to calling functions, using the additional receiver variable.

There are also significant differences. Methods accept a pointer *and* a value, while functions can’t. In one program you can have methods with the same name and different types, but in a function, you can’t. Methods are linked to the type they’re attached to, so they depend on the state, while functions provide the same output every time. If your code doesn’t rely on the state, you should use a function instead of a method.

Let’s illustrate the differences. In the example below, we’re creating a struct called Creature, with string fields for Name and Greeting. Here, the method (rather than the function) is Greet; note that the variable c is used with the receiver Creature type.

> package main
> 
> import “fmt”
> 
> type Creature struct {
> 
> NameString
> 
> GreetingString
> 
> }
> 
> func (c Creature) (Greet) () {
> 
> fmt.Printf(“%s says %s”, c,Name, c.Greeting)
> 
> }
> 
> func main () {
> 
> sarah := Creature{
> 
> Name: “Sarah”,
> 
> Greeting:“Hello!”,
> 
> }
> 
> sarah.Greet()
> 
> }

Your output then looks like this:

> *Sarah says Hello!*

## Receivers and Methods as Pointers and Values

Defining methods on types, as opposed to functions on values, has other benefits. In the interfaces chapter, you’ll see why methods are helpful when using interfaces in code.

You can also define methods on a pointer receiver. As a developer, you can force users of a package to use a specific method by using capitals to begin the method and lowercase if it’ll only work in that particular spot. Defining the method on a pointer receiver ensures that modification of that type will persist. The pointer acts as a reference to the specific type, not to a copy of it. The declaration of a pointer receiver is similar to that of the value receiver, but an asterisk (\*) is used as a prefix to denote the pointer:

> package main
> 
> import “fmt”
> 
> type Boat struct {
> 
> Name string
> 
> occupants \[\] string
> 
> }
> 
> func (b \*Boat) AddOccupant( name string) \*Boat {
> 
> b.occupants = append(b.occupants, name)
> 
> return b
> 
> }
> 
> func (b Boat) Manifest() {
> 
> fmt.Println(“The”, b.Name, “has the following occupants:”)
> 
> for \_, n := range b.occupants {
> 
> fmt.Println(“\\t”, n)
> 
> }
> 
> }
> 
> func main() {
> 
> b := &Boat{
> 
> Name: “S.S. Powerpuff”,
> 
> }
> 
> b.AddOccupant(“Sarah the stingray”)
> 
> b.AddOccupant(“Mary the mussel”)
> 
> b.Manifest()
> 
> }

When you run it, you’ll get the following:

> *The S.S. Powerpuff has the following occupants:*
> 
> *Sarah the stingray*
> 
> *Mary the mussel*

Pointer receivers help allow the method to change the value that the receiver points to. They also allow you to avoid copying the value every time you call the method, which is great when the receiver is a large struct. They help speed up the code and the process.

## Accepting Both Pointer and Value Types

As a reminder, when you have a Go function that has a value argument, only the parameter values can be passed to it. Trying to pass a pointer to a value function will give you an error. However, that’s not the case with a method. Here’s an example of using both pointer and value in a method:

> package main
> 
> import “fmt”
> 
> //author structure
> 
> type author struct {
> 
> name string
> 
> section string
> 
> }
> 
> //method using pointer with receiver author type
> 
> func(a \*author) show\_1(asection string) {
> 
> (\*a).section = asection
> 
> }
> 
> //method with a value receiver for author type
> 
> func(a author) show\_2() {
> 
> a.name = “Johnson”
> 
> fmt.Println(“Author’s name (Before) : “, a.name)
> 
> }
> 
> func main () {
> 
> res := author{
> 
> name : “Smith”,
> 
> section:“RQY”
> 
> }
> 
> fmt.Println(“Section name (Before) : “, res.section)
> 
> //call the pointer method of show\_1 with the value
> 
> res.show\_1(“XJU”)
> 
> fmt.Println(“Section name (After) : “, res.section)
> 
> //call the value method show\_2 with pointer
> 
> (&res).show\_2()
> 
> fmt.Println(“Author’s name (After) : “, res.name)
> 
> }

Here’s the output:

> *Section name (Before): RQY*
> 
> *Section name (After): XJU*
> 
> *Author’s name (Before): Johnson*
> 
> *Author’s name (After): Smith*

## Embedded Types

The embedded type in a struct can be specified with the name of the type. It can be a value type or a pointer to a value type. In Golang, a field or method can be promoted or become available in the outer/embedding type.

There are some rules for this, of course. The method set of a type determines the interfaces that the type implements, as well as the methods that can be called using a receiver of that type. In a set, each method must have a unique non-blank name. The method set of a type T (any type other than an interface) includes all methods declared with receiver type T, EXCEPT those declared with a pointer receiver \*T. However, the method set of a pointer receiver \*T includes both \*T and T receivers.

## Inheritance and Multiple Inheritance

If you’re familiar with object-oriented programming (OOP), then you know inheritance means inheriting one class into another. However, since Go is not an OOP and doesn’t use classes, there is no inheritance in Go. However, the basic concept of inheritance can be achieved with structs instead. In Go, this is known as *composition* . Base structs can be embedded into a child struct, and then the methods of the base can be called on the child struct. Let’s take a look at a simple base/child composition:

> package main
> 
> import “fmt”
> 
> type Movie struct{
> 
> //declare struct variable
> 
> Universe string
> 
> }
> 
> //function to return the universe of the movie
> 
> func (movie Movie) MovieUniverse () string {
> 
> return movie.Universe
> 
> }
> 
> type Quentin struct{
> 
> //anonymous field, composition for embedding struct
> 
> Movie
> 
> }
> 
> type Nancy struct{
> 
> Movie
> 
> }
> 
> func main()
> 
> //creating an instance
> 
> m1 := Quentin{
> 
> //child struct directly accesses base struct variables
> 
> Movie{
> 
> Universe : “QU”,
> 
> },
> 
> }
> 
> // child struct directly accesses base struct methods
> 
> // print base method using child
> 
> fmt. Println(“Universe is “, m1.MovieUniverse())
> 
> m2 := Nancy{
> 
> Movie{
> 
> Universe : “NU”,
> 
> },
> 
> }
> 
> fmt. Println(“Universe is “, m2.MovieUniverse())

Your output will be:

> *Universe is: QU*
> 
> *Universe is: NU*

Multiple inheritances occur when the child struct can access all the fields, methods, and properties of the base struct. Here’s an example of how that could work:

> package main
> 
> import “fmt”
> 
> //declare 1st base struct
> 
> type first struct{
> 
> //declare 1st struct variable
> 
> base\_one string
> 
> }
> 
> //declare 2nd base struct
> 
> type second struct{
> 
> //declare 2nd struct variable
> 
> base\_two string
> 
> }
> 
> //function that will return the first struct variable
> 
> func (f first) printBase\_1() string{
> 
> return f.base\_one
> 
> //function that will return the 2nd struct variable
> 
> func (f first) printBase\_2() string{
> 
> return f.base\_two
> 
> //child struct to embed both the base structs
> 
> type child struct{
> 
> //anonymous fields and struct embedding of the two structs
> 
> first
> 
> second
> 
> }
> 
> func main()
> 
> //declare instance of child struct
> 
> c1 := child{
> 
> first{
> 
> base\_one(“In base struct 1.”),
> 
> },
> 
> second{
> 
> base\_two(“In base struct 2.”),
> 
> },
> 
> }
> 
> //print base method using child struct instance
> 
> fmt.println(c1.PrintBase1())
> 
> fmt.println(c1.PrintBase2())
> 
> }

The output is:

> *In base struct 1.*
> 
> *In base struct 2.*

## Chapter Summary

Methods are similar to functions, but with a specified receiver.

*   Pointers *and* values are accepted in methods, but not in functions.
*   Using a pointer receiver ensures that modifications to the type persist through the program.
*   Embedded types have rules for the way they’re accepted in method sets.
*   Since Go doesn’t have classes it doesn’t have inheritance, but you can use base and child structs for composition.
*   You can use multiple base structs and fields with a child struct.

In the next chapter, you'll learn about interfaces.

Ten 

Now that you have a grasp of methods in Go, you can add interfaces, a necessary tool for abstraction. An *interface* consists of three parts: a value, a method set, and the type for the stored value. Reflection allows you to examine the type and value at runtime and make changes to the value if you need to. When you use an interface as a parameter for a function, passing a value to the function adds the type, method set, and value into the interface parameter. They’re good tools for making code clearer, more readable, and shorter. You can think of interfaces as collections of methods, in addition to being a custom type.

They’re a little different in Go compared to other languages. You need to implement all the methods in the interface to implement the interface itself, though they’re implemented implicitly with no keyword necessary.

Interfaces deliver the concept of polymorphism to Go. This is writing code that takes on different behavior depending on the type that’s implemented. An interface with zero value is nil, and if there are no methods, it’s an empty interface. An interface itself is a static type that points to the dynamic values and type. The syntax to create the interface is similar to that used for a struct, as shown in the example below:

> package main
> 
> import “fmt”
> 
> //create the interface
> 
> type container interface {
> 
> //specify the methods
> 
> Carea() float64
> 
> Volume()float64
> 
> }
> 
> type somevalue struct {
> 
> radiusfloat64
> 
> heightfloat64
> 
> }
> 
> //implement the container interface methods
> 
> func (s somevalue) Carea() float64{
> 
> return 2\*s.radius\*s.height + 2\*3.14\*s.radius\*s.radius
> 
> {
> 
> func (s somevalue) Volume() float64{
> 
> return 3.14\*s.radius\*s.radius\*s.height
> 
> }
> 
> func main () {
> 
> //accessing the elements of the container interface
> 
> var c container
> 
> c = somevalue{10, 14}
> 
> fmt.Println(“Area of container :”, c.Carea())
> 
> fmt.Println(“Volume of container :”, c.Volume())
> 
> }

As a result, your output would be the area and volume using a radius of 10 and a height of 14.

> *Area of container : 908*
> 
> *Volume of container : 4396*

## Embedded Interface

An interface can embed another interface, as well as another interface’s method set. You can embed as many interfaces as you want into your interface. If you make any changes to those, you’ll change the embedded interface as well.

Let’s take a look at how that could manifest in practice:

> package main
> 
> import “fmt”
> 
> //interface 1
> 
> type WriterDetails interface {
> 
> details()
> 
> }
> 
> //interface 2
> 
> type WriterArticles interface {
> 
> articles()
> 
> picked()
> 
> }
> 
> //interface 3
> 
> //interface 3 is embedded with 1’s method, interface 2, and its own method
> 
> type SummaryDetails interface {
> 
> details()
> 
> WriterArticles
> 
> wdeets()
> 
> }
> 
> type writer struct {
> 
> w\_namestring
> 
> sectionstring
> 
> collegestring
> 
> yearint
> 
> incomeint
> 
> particlesint
> 
> tarticlesint
> 
> widint
> 
> poststring
> 
> pickint
> 
> }
> 
> //implement method of interface 1
> 
> func (w writer) details () {
> 
> fmt.Printf(“Writer name :%b”, w.w\_name)
> 
> fmt.Printf(“\\nsection :%b and passing year :%d”, w.section, w.year)
> 
> fmt.Printf(”\\ncollege name :%b, w.college)
> 
> fmt.Printf(“\\nincome :%d”, w.income)
> 
> fmt.Printf(“\\nPublished Articles :%d”, w.particles)
> 
> }
> 
> //implement interface 2 methods
> 
> func (w writer) articles() {
> 
> pendingarticles = w.tarticles - w.particles
> 
> fmt.Printf(“\\nPending articles :%d”, w.pendingarticles
> 
> }
> 
> func (w writer) picked() {
> 
> fmt.Printf(\\nTotal number of picked articles :%d”, w.pick)
> 
> }
> 
> //implementing methods of embedded interface 3
> 
> func (w writer) wdeets() {
> 
> fmt.Printf (“\\nWriter ID : %d”, w.wid)
> 
> fmt.Printf(“\\nPost :%b, w.post)
> 
> }
> 
> func main() {
> 
> //assign values to the structure
> 
> values := writer{
> 
> w\_name: “Agatha”,
> 
> section: “Computer coding”,
> 
> college:“BestSchoolEver”,
> 
> year: 2020,
> 
> income:60000,
> 
> particles:300,
> 
> tarticles:400,
> 
> wid:666,
> 
> post:“Technical Code Writer”,
> 
> pick:66,
> 
> }
> 
> //access methods from interfaces 1 and 2 using SummaryDetails interface
> 
> var s SummaryDetails = values
> 
> s.details()
> 
> s.articles()
> 
> s.picked()
> 
> s.wdeets()
> 
> }

From here, you know what the output looks like, so I’ll keep it short. This example shows how the embedded interface (3) uses elements from the embedding interfaces 1 and 2.

## Type Assertions

*Type assertion* is how you pull the values out of the interface to check whether the dynamic type matches the asserted type. If it does, the type assertion returns the dynamic value. If it doesn’t, you get a panic. Type assertion helps you remove any ambiguity from the variables of the interface itself. The syntax for this is:

> t := value.(typeName)

In this, *value* is a variable of interface type, *typeName* is the concrete (AKA dynamic) type to check, and *t* is the variable with the underlying typeName value.

If you want to check whether the interface value holds a specific type, use type assertion to return two values. One is the boolean true/false, the other is the variable with typeName value. Here’s an example showing type assertion with error checking:

> package main
> 
> import “fmt”
> 
> func main()
> 
> //interface with int value
> 
> var value interface{} 30035
> 
> //retrieve a type int value and assign to the variable value1
> 
> var value1 int = value.(int)
> 
> //print the concrete value
> 
> fmt.Println(value1)
> 
> //test if interface has string type
> 
> //if so, then true and if not then false
> 
> value2, test := value.(string)
> 
> if test {
> 
> fmt.Println(“String found!”)
> 
> fmt.Println(value2)
> 
> } else {
> 
> fmt.Println(“String not found!”)
> 
> }
> 
> }

Since the typeName is int and not string, you’d see the following output:

> *30035*
> 
> *String not found!*

Assertions of any kind in Go help programmers check their code, allow the compiler to compile it, and find any code defects.

## Type Switches

When you’re not sure what type the interface could be, a type switch runs multiple type assertions to find the variable type. Rather than coding multiple if-else statements, a type switch allows you to shorten the code so you can develop it quickly. It’ll run the first switch case that matches the specified type. Here’s an illustration of this:

> package main
> 
> import “fmt”
> 
> func main() {
> 
> //this interface is a string type
> 
> var value interface {} = “All your code are belong to us”
> 
> //use type switch to find out what type it is (as if you didn't already know)
> 
> switch t := value.(type){
> 
> case int64:
> 
> //prints if type of interface is int64
> 
> fmt.Println(“Type is an integer:”, t)
> 
> case float64:
> 
> fmt.Println(“Type is a float:”, t)
> 
> case nil:
> 
> fmt.Println(“Type is nil.”)
> 
> case string:
> 
> fmt.Println(“Type is a string:”, t)
> 
> case bool:
> 
> fmt.Println(“Type is a bool:”, t)
> 
> case default:
> 
> //if type is none of the above
> 
> fmt.Println(“Type is unknown!”)
> 
> }

Output includes the string element:

> *Type is a string: All your code are belong to us*

## Implementing an Interface

The interface defines (but doesn’t declare) the behavior of the element. Suppose you have *Cat* that can *meow* and *zoom* . An interface that defines the method sets for zoom and meow while Cat implements the methods for zoom and meow results in cat implementing that interface.

Now, let’s say you have a variable of interface type that holds a value of a type that implements the interface. The value of that type becomes the dynamic (or concrete) value of the interface, and the type becomes the dynamic type of the interface.

In this example, we’ll create an interface Shape with Area and Perimeter methods. The program creates the struct Shape, which will implement the Shape interface by implementing its methods:

> package main
> 
> import “fmt”
> 
> type Shape interface {
> 
> Area() Float64
> 
> Perimeter() Float 64
> 
> }
> 
> type Rectangle struct {
> 
> width float64
> 
> heightfloat64
> 
> }
> 
> //Area belongs to Rectangle struct type, so Rectangle implements the method
> 
> func (r Rectangle) Area() float64{
> 
> return r.width\*r.height
> 
> }
> 
> //although we are not forcing Rectangle to implement Shape interface, it’s doing so by implementing the method
> 
> func (r Rectangle) Perimeter() float64{
> 
> return 2 \* (r.width + r.height)
> 
> }
> 
> func main () {
> 
> var s Shape
> 
> s = Rectangle{1.0, 2.0}
> 
> r := Rectangle{1.0, 2.0}
> 
> fmt.Printf(“Type of s is %T\\n”, s)
> 
> fmt.Printf(“Value of s is %v\\n”, s)
> 
> fmt.Println(“Area of rectangle s is”, s.area)
> 
> }

The output would be:

> *Type of s is main.Rectangle*
> 
> *Value of s is {1, 2}*
> 
> *Area of rectangle s is 2*

The dynamic type (s) of the interface is now (struct) type Rectangle. The dynamic value of Shape is now the value of (struct) Rectangle of {1, 2}.

You can also change the dynamic type and value within the program from one to another, as shown below:

> package main
> 
> import (
> 
> “fmt”
> 
> “math”
> 
> )
> 
> //using the same Shape interface as above
> 
> type Shape interface {
> 
> Area() Float64
> 
> Perimeter() Float 64
> 
> }
> 
> //also the same Rectangle struct
> 
> type Rectangle struct {
> 
> width float64
> 
> heightfloat64
> 
> }
> 
> //adding another struct
> 
> type Circle struct {
> 
> radius float64
> 
> }
> 
> //as seen above
> 
> func (r Rectangle) Area() float64{
> 
> return r.width\*r.height
> 
> }
> 
> func (r Rectangle) Perimeter() float64{
> 
> return 2 \* (r.width + r.height)
> 
> }
> 
> //now adding the Shape methods for Circle
> 
> //using math package for value of pi instead of rounding to 3.14
> 
> func (c Circle) Area() float64{
> 
> return math.pi \* c.radius \* c.radius
> 
> }
> 
> func (c Circle) Perimeter() float64{
> 
> 2\* math.pi\* c.radius
> 
> }
> 
> func main() {
> 
> var s Shape = Rectangle{2, 3}
> 
> fmt.Printf(“Type of s is %T\\n”, s)
> 
> fmt.Printf(“Value of s is %v\\n”, s)
> 
> fmt.Printf(“Value of s is %0.2f\\n\\n”, s.area())
> 
> s = Circle{10}
> 
> fmt.Printf(“Type of s is %T\\n”, s)
> 
> fmt.Printf(“Value of s is %v\\n”, s)
> 
> fmt.Printf(“Value of s is %0.2f\\n\\n”, s.area())

The output appears like so:

> *Type of s is main.Rectangle*
> 
> *Value of s is {2, 3}*
> 
> *Value of s is 6*
> 
> *Type of s is main.Circle*
> 
> *Value of s is {2}*
> 
> *Value of s is 314.16*

You might have noticed that although Perimeter was a method for Shape and we included a function for it, the method wasn’t used for the output. But had we left Perimeter out, the program would’ve thrown an error. Since Shape has two methods, Rectangle implementing Shape must also have two methods to avoid the error.

## Sorter Interface

In previous chapters, you discovered how to sort with basic types using Golang. *sort.Interface* is used to sort more complex data types. This interface comes with three specific functions:

1.  Len: returns the length of the collection
2.  Less: receives two integers that act as indices from the collection
3.  Swap: performs the necessary change from calling the Less method

The syntax is the following:

> Type Interface interface
> 
> Len() int
> 
> Less (i, j) bool
> 
> Swap(i, j int)

Using sort.interface allows you to use any logic you like in sorting. Instead of enforcing *what* the algorithm should do, it knows *how* to do it.

Suppose you wanted to sort a list of strings according to the length of the strings:

> package main
> 
> import (
> 
> “fmt”
> 
> “sort”
> 
> )
> 
> //assign a type byLength that’s basically an alias for string = Interface interface
> 
> type byLength \[\]string
> 
> //implement sort.Interface
> 
> func (s byLength) Len() int {
> 
> return len(s)
> 
> }
> 
> func (s byLength) Swap(i, j int) {
> 
> s\[i\], s\[j\] = s\[j\], s\[i\]
> 
> }
> 
> //typically Less holds the custom sorting logic
> 
> //since sorting shortest to longest string length, using len(s\[i\]) and len(s\[j\])
> 
> func (s byLength) Less(i, j int) bool {
> 
> return len(s\[i\]) < len(s\[j\])
> 
> }
> 
> func main() {
> 
> breeds := \[\]string{“Labradoodle”, “Chiweenie”, “Shiapso”}
> 
> sort.sort (byLength(breeds))
> 
> fmt.Println(breeds)
> 
> }

The output looks like this:

> *\[Shiapso Chiweenie Labradoodle\]*

## Reading and Writing

What you might not have realized until now is that many of the Go standard library components are interfaces. Error, for example, is simply an interface with a method error that consumes nothing and returns a string. Similarly, *io* is a package that contains interfaces for use with a variety of operations and use cases around both input and output. It’s used to wrap input/output primitives (such as in package os) into shared public interfaces.

In the io.Writer interface, there’s just one method—Write—which allows developers to write a byte slice into a stream of data or write data into code that implements the io.Writer interface. It takes the byte slice p, writes it into the underlying data, and then returns n number of bytes written, and if an error exists, *err* . The syntax is:

> type Writer interface {
> 
> Write (p \[\]byte) (n int, err error)
> 
> }

This is flexible enough to be used in a variety of different applications. For example, you could create a writer that encodes the byte string into .jpeg and write to a specific file, or encodes to mp3 and writes to an audio device. Interfaces are the primary tool for abstraction in Golang, and io.Write provides a lot of flexibility for this type of tool.

For the read version of a stream of data, the standard library contains io.Reader. There are a variety of ways to implement it that are also included in the stlib, including compressors, ciphers, and network connections. Similar to the io.Writer syntax, io.Reader populates the byte slice b with data. It returns n number of bytes populated, as well as an error function err. When the stream ends, you’ll get an io.EOF error. The interface appears like so:

> func T Read(b \[\]byte) (n int, err error)

Users of Go are well-served when coders include io.Reader whenever possible for data sources. Because there are so many types that it can work with, your code now works for many more users.

For example, suppose you’re thinking about the reverse function on a string:

> func Reverse(s string) (string, error)

Or, instead, of using the single-method io.Reader:

> func Reverse(r io.Reader) io.Reader

Now, others can use that with strings, files, web requests, etc., without having to write extra code as long as io.Reader implements the type you’re using.

## Empty

As mentioned earlier, the type interface{} is the empty interface, and it can accept values of any type. Because it’s empty, there are no methods required to satisfy it. As a result, every type can satisfy it.

In the following example, the variable (manytype) is declared to be an empty interface. Therefore, you can assign it values of different types. Since the function printType() accepts the interface{}parameter, it likewise takes any valid type.

> package main
> 
> import “fmt”
> 
> func printType(i interface{}) {
> 
> fmt.Println(i)
> 
> }
> 
> func main() {
> 
> var manytype interface{}
> 
> manytype = 10
> 
> fmt.Println(manytype)
> 
> manytype = 50
> 
> fmt.Println(manytype)
> 
> manytype = “cat”
> 
> fmt.Println(manytype)
> 
> printType(“Go language”)
> 
> var states = \[\]string{“California”, “Hawaii”, “New York”, “Virginia”, “Illinois”}
> 
> printType(states)
> 
> var staff = map\[string\] int{“Meg”: 27, “Jenny”: 31}
> 
> printType(staff)
> 
> state := \[2\]string{“Hawaii”, “Massachusetts”}
> 
> }

Your output reads as follows:

> *10*
> 
> *50*
> 
> *cat*
> 
> *Go language*
> 
> *\[California Hawaii New York Virginia Illinois\]*
> 
> *map\[Meg: 27 Jenny: 31\]*
> 
> *\[Hawaii Massachusetts\]*

Empty interfaces are valuable for handling values with unknown types. If you’re creating an output library, you’d need a function that receives values and then passes them to the usual output.

Rather than trying to write code for every value you come up with, the empty interface allows Go to convert at runtime. If you’re sending them to a printout, it doesn’t matter what type it is. As long as the code can handle it, your program will work.

## Reflect Package

Not all languages provide the ability to examine their structure, but Go does through *reflection* . It’s based on types. At compile time, every variable has a static type that can only be changed through conversion. Interface types represent a fixed set of methods, and an interface variable can implement any dynamic (non-interface) value as long as that value implements the interface’s methods.

You now know that io.Reader is an interface and a variable that has the type io.Reader can hold any value that has a Read method in it. All the following are acceptable because they have Read methods (don’t worry if they are not familiar to you yet):

*   var r io.Reader
*   r = os.Stdin
*   r = bufio.NewReader(r)
*   r = new(bytes.Buffer)
*   //and plenty more!

However, the key here is that no matter what concrete value r holds, its type is always io.Reader.

The variable of interface type stores a pair, which consists of the concrete value assigned to that variable and the value’s type descriptor. Here the value is the concrete piece of data that implements the interface.

Reflection is the mechanism that examines the value and type pair stored inside the interface variable. It’s particularly helpful when you’re doing things like querying a database or creating one that has data of unknown types in it. The reflect package helps you determine the type as well as the number of fields.

The package *reflect* includes two types, which are simply Type and Value. It has two functions, reflect.Typeof and reflect.Valueof, which return reflect.Type and reflect.Value from the interface. Here’s a quick example:

> package main
> 
> import (
> 
> “fmt”
> 
> “reflect”
> 
> )
> 
> func main() {
> 
> var y float 3.14
> 
> fmt.Println(“Type”, reflect.Typeof(y))
> 
> }

As a result, you see

> *Type float64*

At first glance, you might think that the float64 variable y is what’s being passed, not the interface. However, reflect.Typeof contains an empty interface. When you call the function reflect.Typeof(y), an empty interface stores y. That’s passed as the argument, then the function unpacks the empty interface to find the type information. Similarly, reflect.Valueof retrieves the value information of the pair.

There are three pillars to the Reflect package: type, kind, and value. You’ve seen type and value above. Kind refers to the representation of a type and can be obtained using type.Kind().

In Go, reflection goes from the interface value to the object of reflection. This is known as the first law of reflection. The second law is that reflection goes from the reflection object to the interface value. In other words, reflection has its own inverse. If you’re given a reflect.Value, the interface value can be recovered from it. The third law involves a characteristic known as *settability* , which not all values have. It is the property that a reflection object can change the storage used to create that object. In other words, a reflection value is settable if it holds the original item. You’ll get an error trying to call a Set method on a non-settable value.

Here’s a snippet of code that generates a panic, even though you might think it appears valid:

> var y float64 = 3.14
> 
> v := reflect.Valueof(y)
> 
> v.SetFloat(6.28)

In the above code, a copy of y is passed to reflect.Valueof, not y itself. Therefore, rather than changing variable y to 6.28, you would be changing the copy of y to 6.28, which doesn’t make any sense. Settability prevents you from doing so.

You can find out if a value is settable using the CanSet method:

> var y float64 = 3.14
> 
> v := reflect.Valueof(y)
> 
> fmt.Println(“settability of v:”, v.Canset())
> 
> //which in this case would print settability of v: false

It’s very similar to using a “plain” function f(x). Here, since a copy of x is passed to the function, you wouldn’t expect f to be able to change x. If you want to modify x directly, you’d need to pass a pointer to x, which would look like f (&x).

Similarly, if you want to pass y through reflection, first you need a pointer to the y value that you want to change. Here’s what that would look like in the previous example:

> var y float64 = 3.14
> 
> //take y’s address
> 
> z := reflectValueof(&y)
> 
> //reflection object z isn’t settable, so we need to get what z points to
> 
> //call Elem method on value to get there
> 
> //then save in a reflection value
> 
> v := z.Elem()
> 
> //now that finally represents y, so we can modify it
> 
> v.SetFloat = 6.28
> 
> fmt.Println(v.interface())
> 
> fmt.Println(y)
> 
> // yields the result 6.28 for both

## Printf, Value, and Dynamic Interface

To be as easy to understand as possible, Go includes concepts that make it easier to log and debug code. Printing the dynamic type of an interface value makes those operations easier. Fortunately, our old friend *fmt.Printf* provides a short version using reflect.Typeof, which is %T.

An interface value has a concrete value and a dynamic type. Just as %T gives you the dynamic type of the interface, you can use %v to print the concrete value using printf. The dynamic and concrete also help you determine equality. Two interfaces are equal if the concrete values are equal and the dynamic type is the same, or if both are nil. An interface value t of interface type T and the value s of non-interface value type S are equal if t’s concrete value = s *and* t’s dynamic type = S.

When you’re using reflect.Value, you can hold arbitrary values, just like an empty interface does. What’s the difference between the two? Values have a variety of ways that you can peek under the hood and determine its contents. By contrast, an empty interface hides all its methods and representations. You need to know what type it contains so that you can use type assertion to pop the hood if you want to make any modifications to it.

## Structs, Collections, and Higher-Order Functions

Reflection can be very useful when it comes to structs. In addition to some other methods included in the package, reflect also provides the following for use with structs only:

*   NumField(), which counts the number of fields available in a struct
*   Field(), which provides access to the fields themselves using an index variable

In this example, you’ll see the difference between type and kind, and how they’re used in programming:

> package main
> 
> import (
> 
> “fmt”
> 
> “reflect”
> 
> )
> 
> type info struct {
> 
> fname string
> 
> name string
> 
> age int
> 
> balance float64
> 
> }
> 
> type meType string
> 
> //function showInfo takes empty interfaces as parameters
> 
> func showInfo(i, j interface {}) {
> 
> t1 := reflect.Typeof(i)
> 
> k1 := reflect.Kind()
> 
> t2 := reflect.Typeof(j)
> 
> k2 := reflect.Kind()
> 
> fmt.Println(“Type of 1st interface is”, t1)
> 
> fmt.Println(“Kind of 1st interface is”, k1)
> 
> fmt.Println(“Type of 2nd interface is”, t2)
> 
> fmt.Println(“Kind of 2nd interface is”, k2)
> 
> fmt.Println(“The values in the first argument are:”)
> 
> if reflect.Valueof(i).Kind == reflect.Struct {
> 
> value := reflect.Value(i)
> 
> numberofFields := value.NumField()
> 
> for i :=0; i < NumberofFields; i++
> 
> fmt.Printf(“%d.Type:%t || Value:%#v\\n”,
> 
> (i + 1), value.Field(i), value.Field(i))
> 
> fmt.Println(“Kind is “, value.Field(i).Kind())
> 
> }
> 
> }
> 
> value := reflect.Valueof(j)
> 
> fmt.Printf(“The value passed in “ + “2nd parameter is %#v”, value)
> 
> }
> 
> func main () {
> 
> id := meType(“9876”)
> 
> person := info{
> 
> fname = “Cassie”
> 
> lname = “Coder”
> 
> age = 27
> 
> balance = 5987.65
> 
> }
> 
> //passing two arguments to showInfo
> 
> //person is a struct, id is a string
> 
> showInfo(person, id)
> 
> }

The output here shows you the difference between type and kind.

> *Type of 1st interface is main.info*
> 
> *Kind of 1st interface is struct*
> 
> *Type of 2nd interface is main.meType*
> 
> *Kind of 2nd interface is string*
> 
> *1\. Type:reflect.Value || Value: “Cassie”*
> 
> *Kind is string*
> 
> *2\. Type:reflect.Value || Value: “Coder”*
> 
> *Kind is string*
> 
> *3\. Type:reflect.Value || Value: 27*
> 
> *Kind is int*
> 
> *4\. Type:reflect.Value || Value: 5987.65*
> 
> *Kind is float64*

The value passed in 2nd parameter is “9876”

You can see that the struct person is type main.Info and kind struct, where the variable id is type main.meType and kind string.

## Best Practices for Interfaces

Keep the interfaces small. Only define the minimum behavior to accurately explain the concept. In keeping with clean, small interfaces, you don’t need to specify the types that will satisfy it; the interface only needs to define what other types will classify as an element of it. For example, suppose you’re writing an interface that will describe what’s necessary to define a car:

> type car interface {
> 
> color() string
> 
> speed() int
> 
> //the next field doesn’t work
> 
> IsFiretruck() bool
> 
> }

It doesn’t make sense for all cars to declare they’re not firetrucks, because then you’d need to specify IsSedan(), IsAmbulance(), IsConvertible(), etc. There are a lot of possible types you’d need to include if you mistakenly added isFiretruck. Type assertion will provide the underlying type when given an interface instance. If you feel it’s necessary, you could add in a sub-interface which “inherits” the methods from car interface and adds a method to be a firetruck:

> type firetruck interface {
> 
> car
> 
> Hoselength()

If you’ve dealt with classes in other programs, just remember that class is *not* the same as an interface in Golang.

## Chapter Summary

Interfaces introduce more flexibility and polymorphism into your coding in Golang. They also provide the ability through reflection to add abstraction, especially when you don’t know what types will pass into your function.

*   Interfaces can be thought of as a collection of methods.
*   An interface will accept an interface as a type, which means they can be embedded or nested inside one another.
*   Type assertions allow you to check what types are included in any interface.
*   Type switches allow you to change the type when necessary.
*   You can use the sorter interface to sort anything more complex than the earlier sorting methods in the book.
*   Reading and writing both involve interfaces and can make code easier to write and implement.
*   Empty interfaces can be very useful and are necessary for reflection. They’re included in the printf format from the fmt package.
*   The reflect package allows you to delve into what’s inside the interface.
*   Structs and interfaces are key players in your Go code.
*   The best practice is to keep interfaces small; only use the minimum amount of definition necessary.

In the next chapter, you'll learn about reading and writing in Golang.

Eleven 

In the last chapter, you learned that reading and writing are based on interfaces. Now, we’ll go into more detail about *how* to read and write. There are many potential applications where you’ll be using user input in your code, so knowing how to read that input is critical for any developer.

## Read: User Input

There are several packages you’ll find helpful when you’re working on code that requires user input. They include *fmt* , *bufio* , and *os* .

The primary function you’ll use from fmt when it comes to reading user input is *scanf* . The syntax is similar to what you’ve seen in earlier examples with printf. It scans what the user enters, separating based on spaces into arguments that are specified by the format, and returns the number of items successfully scanned.

For example, here’s a simple request for user name and age.

> package main
> 
> import “fmt”
> 
> func main() {
> 
> var name string
> 
> var age int
> 
> fmt.Print(“Enter your name and age, separated by a space: “)
> 
> //reading two values
> 
> //using & to create and return a pointer to a new value
> 
> fmt.scanf(“%s %d”, &name, &age)
> 
> fmt.Printf(“%s is %d years old\\n”, name, age)
> 
> }

If the user entered Sarah 33, you’d get the result Sarah is 33 years old.

Bufio is the package that implements buffered I/O, which creates better performance than non-buffered. It’s a way to accumulate the results of an IO operation before transmitting it, which reduces the number of system calls. Since those calls can be slow, buffering helps speed up the program.

When reading, the program reads in batches. The type *Reader* buffers an io.Reader object and the function NewReader returns a—you guessed it—new Reader (with default buffer size.)

The os package provides an interface that’s standard across all operating systems. Standard input, which is often abbreviated as stdin, is the stream where the program reads the input information.

Here’s an example that uses both the bufio and os packages to read user input:

> package main
> 
> import (
> 
> “fmt”
> 
> “bufio”
> 
> “os”
> 
> )
> 
> func main() {
> 
> //reading a name from the input
> 
> reader := bufio.NewReader(os.Stdin)
> 
> fmt.Print(“Enter your name: ”)
> 
> //pass the input to the bufio.NewReader
> 
> name, \_ := reader.ReadString(‘\\n’)
> 
> fmt.Printf(“Hello %s\\n”, name)
> 
> }

## Read and Write: Files

*Some* of what you learned about user input will come back for files, but there are some additional tools as well. To read and/or write files to your local system, you’ll use the *io/ioutil* package. You'll also find the log package handy, especially the type Logger that provides methods for formatting output. Here are some of the elements that you’ll find very useful for files.

*   os.Create()

Create a file with the desired name with this tool. If that file has already been created, os.Create() truncates it.

*   io/ioutil.ReadFile() and io/ioutil.WriteFile()

The ReadFile method has only one parameter, which is the path to the file you want to read. It will either return the data in that file or return an error.

By contrast, the WriteFile has three parameters to write data to the specified file. The first is the path to the file, the second is the data object, and the third is the FileMode, which provides the file’s mode and permission bits.

*   FileMode and permission bits

Files have associated access permissions. The permission indicator has a group of bits associated with it that tell you who has read-write-execute (rwx) permissions for the file.

If a user type can’t access the permissions, there’s a dash for the letter they’re not permitted. For example, the user might be able to read and run the file, but not make changes to it. Their permission would look like r-x. The first bit of the permission indicator specifies whether it’s a file or a directory.

The next group (3 bits) is for the file owner, who needs to be logged in under the proper username to access all their permissions. The next bit trio is for the user group that owns the file, and the third is for the rest of the system users.

These three permission groups are known as the *mode* for the file.

*   log.Fatalf

This will terminate the program after the log message is printed. It’s the equivalent of Printf followed by a call to os.Exit(1).

*   log.Panicf

This is an exception at runtime. When the program terminates, the argument passed to Panic() is printed. It’s the same as Println() followed by a call to panic().

*   inputReader.ReadString(\`\\n\`)

This was used in a previous example. You use it to read user input from stdin until the first delimiter appears in the stream. It returns a string that consists of the data up to and including the delimiter. If the program finds an error before it reaches the first delimiter, you’ll get the data it read up to the error as well as the error itself.

This example demonstrates how you might accept user input to read/write to a file:

> package main
> 
> import (
> 
> “fmt”
> 
> “os”
> 
> “bufio”
> 
> “log”
> 
> “io/ioutil”
> 
> )
> 
> func CreateFile(filename, text string) {
> 
> fmt.Printf(“Writing to a file in Go\\n”)
> 
> //using Create method with user input for filename and err variable if error thrown
> 
> file, err := os.Create(filename)
> 
> if err ! = nil {
> 
> log.Fatalf(“Failed to create file %s”, err)
> 
> }
> 
> //use defer to close the file that’s running after main is executed and writing to file complete
> 
> defer file.Close()
> 
> //write data to file using WriteString method, with string length stored in len variable
> 
> len, err := file.Writestring(text)
> 
> if err ! = nil {
> 
> log.Fatalf(“Failed to create file %s”, err)
> 
> }
> 
> fmt.Printf(“\\nFileName: %s”, file.Name())
> 
> fmt.Printf(“\\nLength: %d bytes”, len)
> 
> }
> 
> func ReadFile(filename string) {
> 
> fmt.Printf(“\\n\\nRead a file in Go\\n”)
> 
> data, err := ReadFile(filename)
> 
> //if error thrown, then error printed and program stopped
> 
> if err ! = nil {
> 
> log.Panicf(“Failed to read data from file %s”, err)
> 
> }
> 
> fmt.Printf(“\\nFile Name: %s”, filename)
> 
> fmt.Printf(“\\nFile Size: %d bytes”, len(data))
> 
> fmt.Printf(“\\nData: %s”, data)
> 
> }
> 
> func main () {
> 
> //get user input for the name of the file
> 
> fmt.Println(“Enter filename: “)
> 
> var filename string
> 
> fmt.Scanln(&filename)
> 
> //get user input for file content
> 
> fmt.Println(“Enter text: “)
> 
> inputReader := bufio.NewReader(os.Stdin)
> 
> input, \_ :=inputReader.ReadString(\`\\n\`)
> 
> //creates and reads file
> 
> CreateFile(filename, input)
> 
> ReadFile(filename)
> 
> }

If the user enters “Hello.txt” as the filename and “Hello World, it’s reading and writing in Golang!” at the prompts, then your output would look like this:

> *Writing to a file in Go*
> 
> *Filename: Hello.txt*
> 
> *Length: 101 bytes*
> 
> *Read a file in Go*
> 
> *File Name: Hello.txt*
> 
> *Size: 101 bytes*

Data: Hello World, it’s reading and writing in Golang!

## Read: Files with a Buffer

Earlier in this chapter, we discussed that buffers reduce the time necessary to execute a program. A buffer is an area of space in memory that can be either variable or fixed. You can use the bytes package to provide the Buffer structure type if you need a variable size.

The function bytes.NewBuffer initializes a variable buffer size with an initial value. The syntax for this function is as follows:

> func NewBuffer(buf \[\]byte) \*bytes.buffer

Similarly, using bytes.NewBufferString initializes a variable buffer with bytes of a string for its initial value. Here’s the syntax:

> func NewBufferString(s string) \*bytes.buffer

In addition to ReadFrom and WriteTo and other Read and Write methods you’re familiar with, the Buffer package includes other methods you’ll likely find very useful, including WriteString (which writes data from a string), Reset (which empties the buffer), and Grow (which increases buffer size).

## Read: Arguments from Command Line

Arguments from the command line are a quick way to add additional information to the start of a program. You can separate the argument values by spaces on the command line with the following syntax:

> $./program Arg1 Arg2 Arg3

The os package contains the Args array; this string array holds all the arguments passed. For example, maybe you want the program to greet your colleagues:

> package main
> 
> import (
> 
> “fmt”
> 
> “os”
> 
> )
> 
> func main() {
> 
> names := os.Args\[1:\]
> 
> for \_, name : range names {
> 
> fmt.Printf(“Hello, %s\\n!”, name)
> 
> }
> 
> }

Your command line and output would look like this:

> *$ go build hello-team.go*
> 
> *$./hello-team Nancy Bob Sylvia*
> 
> *Hello Nancy!*
> 
> *Hello Bob!*
> 
> *Hello Sylvia!*

## Read with Slices

The bufio package also gives coders the ability to use slices with buffers when reading data.

*   ReadSlice

ReadSlice returns a slice of a string, including the delimiter. The syntax for this is :

> func (b \*Reader) ReadSlice(delim byte) (line \[\]byte, err error)

If the end of the function has been reached and no delimiter found, then it returns io.EOF. If the delimiter hasn’t been found before the buffer runs out of room, it returns io.ErrBufferFull.

*   ReadLine

Similar to ReadSlice, ReadLine removes new line characters (such as \\n) from the slice. The syntax for this is:

> ReadLine() (line byte\[\], isPrefix bool, err error)

In addition, it contains the *isPrefix* flag, which returns true when the buffer capacity is reached and the delimiter isn’t found. It can’t handle lines longer than the buffer, but it can be called repeatedly until the data is read.

*   ReadByte

ReadByte works on top of ReadSlice and can call ReadSlice multiple times to accumulate the read data, which is a workaround for buffer size limitations. It returns a new slice of byte, which also makes it safer since you’re not overwriting any data from your reading operations. The syntax for this is:

> func(b \*Reader) ReadBytes(delim byte) (\[\]byte, error)

The bufio package also includes the embedded struct ReadWriter, which combines both Reader and Writer as follows:

> type ReadWriter struct {
> 
> \*Reader
> 
> \*Writer
> 
> }

Here’s an example of how these could come together, leaving out the main and import instructions:

> s := strings.NewReader(“wxyz”)
> 
> br := bufio.NewReader(s)
> 
> k := new(bytes.Buffer)
> 
> bk := bufio.NewWriter(k)
> 
> rk := bufio.NewReadWriter(br, bk)
> 
> buf := make(\[\]byte, 2)
> 
> \_, err := rk.Read(buf)
> 
> if err ! = nil {
> 
> panic(err)
> 
> }
> 
> fmt.Printf(“%q\\n”, buf)
> 
> buf = \[\]byte(“fghi”)
> 
> \_, err = rk.Write(buf)
> 
> if err ! = nil {
> 
> panic(err)
> 
> }
> 
> //flush is used to empty buffer
> 
> err = rk.Flush
> 
> if err ! = nil {
> 
> panic(err)
> 
> }
> 
> fmt.Println(k.String())

Your results would look like so:

> *“wx”*
> 
> *fghi*

## JSON Data Format

Using JSON is an easy way to interchange data between formats. It doesn’t require much processing power and your computer can easily parse and generate it. Humans can easily read and write it, which makes it an excellent partner for your Golang code. It’s a text format that’s independent of other computer languages, and if you’ve programmed in Python, Perl, C, or C++, you’ve probably used it quite a bit.

The basis for JSON rests on two foundations: one is the collection of name/value pairs, and the other is an ordered list of values. ITo parse JSON or encode Go programs to it, you’ll need the *encode/JSON* package. The *Marshal* and *Unmarshal* functions will allow you to marshal your data into JSON or out of it, respectively.

Here’s an example of transforming a struct and slices from Go to JSON.

> package main
> 
> import (
> 
> “fmt”
> 
> “encoding/json”
> 
> “log”
> 
> )
> 
> //declare the user struct, as you’ve seen before
> 
> type user struct {
> 
> IDint
> 
> Namestring
> 
> Titlestring
> 
> }
> 
> func main() {
> 
> //create the struct instance, as you’ve seen
> 
> u1 := user{10, “Bob Builder”, “Foreman”}
> 
> //use Marshal to encode u1 struct to JSON
> 
> json\_data, err := json.Marshal(u1)
> 
> if err ! = nil {
> 
> log.Fatal(err)
> 
> }
> 
> //convert json\_data array to string
> 
> fmt.Println(string(json\_data))
> 
> //now a slice of users
> 
> users := \[\]User{
> 
> {ID: 20, Name: “Dora Explorer”, Title: “Explorer”},
> 
> {ID: 30, Name: “JJ Schmidt”, Title: “Lyricist”},
> 
> {ID: 40, Name: “Cruella DeVil”, Title: “Designer”},
> 
> }
> 
> //encode the slice with Marshal
> 
> json\_data2, err := json.Marshal(users)
> 
> if err ! = nil {
> 
> log.Fatal(err)
> 
> }
> 
> fmt.Println(string(json\_data2))
> 
> }

Here’s what the output looks like:

> *{“ID”:10, “Name”:“Bob Builder”, “Title”:“Foreman”}*
> 
> *\[{“ID”: 20, “Name”: “Dora Explorer”, “Title”: “Explorer”}, {“ID”: 30, “Name”: “JJ Schmidt”, “Title”: “Lyricist”}, {“ID”: 40, “Name”: “Cruella DeVil”, “Title”: “Designer”}\]*

Now let’s see an example of decoding from JSON into Go:

> package main
> 
> import (
> 
> “fmt”
> 
> “encoding/json”
> 
> “log”
> 
> )
> 
> type user struct {
> 
> IDint
> 
> Namestring
> 
> Titlestring
> 
> }
> 
> func main() {
> 
> var u1 user
> 
> //transform JSON object into bytes
> 
> data := \[\]byte(\`{
> 
> “ID”: 10,
> 
> “Name”: “Bob Builder”,
> 
> “Title”: “Foreman”,
> 
> }\`)
> 
> //decode u1 struct from JSON to Go with Unmarshal
> 
> err := json.Unmarshal(data, &u1)
> 
> if err ! = nil {
> 
> log.Fatal(err)
> 
> }
> 
> fmt.Println(“Struct is:”, u1)
> 
> fmt.Printf(“%s is a %s.\\n”, u1.Name, u1.Title)
> 
> //declare a slice of User structs
> 
> var 2 \[\]User
> 
> //this is the JSON array to be decoded into a slice
> 
> data2 := \[\]byte(\`
> 
> \[
> 
> {“ID”: 20, “Name”: “Dora Explorer”, “Title”: “Explorer”},
> 
> {“ID”: 30, “Name”: “JJ Schmidt”, “Title”: “Lyricist”},
> 
> {“ID”: 40, “Name”: “Cruella DeVil”, “Title”: “Designer”},
> 
> \]\`)
> 
> //encode Go slice from JSON with Unmarshal
> 
> err2 := json.Unmarshal(data2, &u2)
> 
> if err ! = nil {
> 
> log.Fatal(err)
> 
> }
> 
> //print the decoded array user by user
> 
> for i := range u2 {
> 
> fmt.Println(u2\[i\])
> 
> }

Your output would look like this:

> *Struct is {10 Bob Builder Foreman}*
> 
> *Bob Builder is a Foreman.*
> 
> *{20 Dora Explorer Explorer}*
> 
> *{30 JJ Schmidt Lyricist}*
> 
> *{40 Cruella DeVil Designer}*

## XML Data Format

This is another popular data format that coders often use with Go. It’s very similar to working with JSON data, except that you use the encode/XML package instead. You’ll still make use of Marshal and Unmarshal when moving back and forth between Golang and XML.

Here, we’ll encode from Go to XML:

> package main
> 
> import (
> 
> “encoding/xml”
> 
> “fmt”
> 
> )
> 
> type Person struct {
> 
> Namestring
> 
> Titlestring
> 
> }
> 
> func main() {
> 
> p := &person{“Cruella”, “Designer”}
> 
> // use Marshal and the “pretty printing” indent
> 
> s, \_ :=XML.MarshalIndent(p, “ ”, “ ”)
> 
> fmt.Println(string(s))
> 
> }

The output looks like this:

> *<Person>*
> 
> *<Name>Cruella</Name>*
> 
> *<Title>Designer</Title>*
> 
> *</Person>*

Likewise, we can Unmarshal from XML to Go:

> package main
> 
> import (
> 
> “encoding/xml”
> 
> “fmt”
> 
> )
> 
> //note backticks for the struct
> 
> type Book struct {
> 
> Namestring \`xml:“Name”\`
> 
> Authorstring \`xml:“Author”\`
> 
> }
> 
> func main() {
> 
> v := \`
> 
> <Book>
> 
> <Name>The Last Hack</Name>
> 
> <Author>Christopher Brookmyre</Author>
> 
> </Book>
> 
> \`
> 
> b := &Book{}
> 
> xml.Unmarshal(\[\]byte(v), b)
> 
> fmt.Println(b)
> 
> }

## Chapter Summary

In this chapter, we discussed the functionality of reading from files—even those not in Go!—and writing to Go files. When reading and writing, the bufio package comes in handy with buffering that speeds up the execution of the code.

*   Reading user input primarily uses the scanf function, which scans elements separated by spaces.
*   You can also read and write to files, and the os and log packages assist with this by providing ways to log any errors that occur.
*   The os package also contains Arg methods that you use to read right from the command line.
*   You can also read with slices, which makes it easier to deal with information from JSON and XML languages.

In the next chapter, you'll learn about goroutines and channels.

Twelve 

Throughout the book, you’ve discovered many ways that Golang allows you to execute programs faster. Another way to juice up your programs is to allow for independent execution of your processes.

The first question that might have come to mind is how you can prevent concurrent routines from becoming entangled with each other. We introduced the subject earlier, but now that you’re more familiar with Golang, we can take a deeper dive into concurrency.

## About Concurrency and Parallelism

If you have experience coding in other languages, you might be familiar with the concept of parallelism. Sometimes, concurrency is mistaken for parallelism, but the two are not the same. *Parallelism* refers to executing processes that may or may not be related to one another. You can think of it as doing lots of things at once. *Concurrency* , on the other hand, is the composition of processes that run independently of each other or dealing with multiple items at once.

Consider what happens when you’re out running. You realize your shoelace is untied, so what do you do? You stop running, tie your shoelace, then start running again. That’s concurrency. Parallelism is jogging along while listening to the music in your earbuds because you’re doing two things at the same time.

When it comes to programming, concurrency occurs when two (or more) tasks are in progress at the same time. Parallelism is a run-time property where two or more tasks are executed simultaneously. It’s not the ultimate goal of concurrency, though the latter can use parallelism to get the job done.

## Goroutines

These are the tools Go uses for concurrency. They’re methods or functions that can run concurrently with other methods and functions. Simply using the prefix go- before the method or function will enable it to run concurrently.

Goroutines are similar to Java threads, but they’re lightweight and not as costly to use. They also start up faster than threads and have built-in primitives (called channels) to communicate with each other. Their size can grow or shrink according to the needs of the code, unlike Java threads which require a specified size.

Here’s an example of multiple concurrent routines:

> package main
> 
> import (
> 
> “fmt”
> 
> “time”
> 
> )
> 
> //goroutine 1
> 
> func printnumbers () {
> 
> for i := 1; i < = 5; i++ {
> 
> //using Sleep to synchronize all 3 goroutines to show more clearly, though normally you would use channels
> 
> //this routine runs every 250 milliseconds
> 
> time.Sleep(250\* time.Millisecond)
> 
> fmt.Printf(“%d ”, i)
> 
> }
> 
> }
> 
> //goroutine 2
> 
> func printletters() {
> 
> for i := ‘a’; i <= ‘e’; i++
> 
> //this routine runs every 400 milliseconds
> 
> time.Sleep(400\* time.Millisecond)
> 
> fmt.Printf(“%s ”, i)
> 
> }
> 
> }
> 
> //goroutine 3
> 
> func main() {
> 
> go printnumbers()
> 
> go printletters()
> 
> time.Sleep(5000\* time.Millisecond)
> 
> fmt.Println(“Print from main”)
> 
> }

As a result, the output looks like this:

> *1 a 2 3 b 4 c 5 d e Print from main*

## Synchronizing and Switching between Goroutines

Go provides more than one way to synchronize concurrent routines to avoid errors and ensure the computations are done correctly. Now that you’re familiar with the methods we discussed in chapter eight, let’s go into a little more detail.

*   Waitgroup

This is most often used when you have one goroutine that will wait until the others are all finished to run. You might recall that the Waitgroup value maintains its internal counter, and the default for that counter is zero. Waitgroup has 3 methods: Add(delta int), Done(), and Wait().

Some of these Waitgroup values can be addressable. An *addressable* value is a pointer indirection, a variable, a slice index operation (though the slice itself need not be addressable), a field that addresses a struct, an indexed operation for an array (which must be addressable), or a composite literal type.

For any of these addressable Waitgroup values wg, call wg.Add(delta int) to change the counter value that wg maintains, and note that calling wg. Done() is the same as wg.Add(-1). If a call of wg.Add(delta int) or wg.Done results in a negative counter value for wg, it results in a panic. When you call wg.Wait() and the counter is already zero, it’s the same as a no-op. Otherwise, when the counter is positive, calling wg.Wait() means the goroutine enters its blocking state, and runs again when another goroutine modifies the counter to zero, normally by calling wg.Done(). Make sure that you call Add method with a positive delta when the counter is zero before calling Wait, otherwise you end up with a data race.

*   Once

Use this function to make sure that the piece of code runs only once during the program. As a reminder, the \*sync.Once value has a Do(f func()) which takes one parameter with the func() type.

An addressable Once value o contains the method call o.Do(), which can be executed concurrently in multiple routines. The arguments in the calls are best used with the same function value, although that’s not a code requirement.

Just one argument function results from the o.Do() method, and it will always exit before any o.Do() method returns.

*   Cond

Use sync.Cond to make notifications among goroutines. It’s often used when you have a goroutine that waits for changes of a condition, and other goroutines make the change and send notifications.

*   Mutex/RWMutex

Both of these use Lock and Unlock to prevent more than one user from accessing the same piece of data at the same time. Locks are not bound to goroutines, so a lock can be locked in one goroutine and unlocked in a different goroutine at a different time.

RWMutex comes in handy when you want to slice a write program into several. Both Mutex and RWMutex can also be used to notify routines, although they’re not the best tool for the job (sync.Cond is preferred).

For an addressable RWMutex value rwm, keep in mind that the write lock can be held by only one writer at a time, and the read lock and the write lock can’t be held at the same time. However, the read lock can be held by more than one reader at a time. When its lock count returns to zero, it unlocks.

## Channels

One way to visualize channels is to think of them as pipes that connect concurrent goroutines. It enables you to send values into the channel of one goroutine and receive them into another. Each channel can send only one type of data. A nil channel is useless because you can’t read to or send from it, so you’ll need to use the function *make* to create a channel.

By default, a channel is a pointer. Usually, you pass the channel as an argument to the function or method. When a channel receives the argument, there’s no need to dereference it to use the data.

When creating channel c, the syntax is simple. The arrow points from data to channel c, so you’re pushing the data to the channel:

> c <- data

When you want to read data from channel c, you just reverse the location of c as shown:

> <- c

If you want to use variable data to hold what’s coming from the channel, you could use the following syntax:

> var data int
> 
> data = <- c

Or you can use its equivalent:

> data := <- c

Either way, channel operations block by nature. When data is written to channel c, a goroutine is blocked until another goroutine reads it. However, a channel won’t block forever, because the channel operations tell the scheduler to schedule another goroutine.

Here’s a quick example of a channel:

> package main
> 
> import “fmt”
> 
> //declare salute function which accepts the channel c string data
> 
> func salute(c chan string) {
> 
> fmt.Println(“Hello” + <-c + “!”)
> 
> }
> 
> func main() {
> 
> //main function first goroutine
> 
> fmt.Println(“Main() started”)
> 
> //using make to create channel c of string type
> 
> c := make(chan string)
> 
> //use keyword go to create goroutine for passing channel c to the salute function
> 
> go salute(c)
> 
> //pushing string value “Jane” to channel c
> 
> c<- “Jane”
> 
> //goroutine is blocked until another goroutine reads it
> 
> //activate main goroutine
> 
> fmt.Println(“Main() stopped”)
> 
> }

You’d end up with results that look like this:

> *Main() started*
> 
> *Hello Jane!*
> 
> *Main() stopped*

When a channel is read or written to, that goroutine is blocked and control gets passed to other available goroutines. If, however, there are no other goroutines available, you get *deadlock* and a program crash.

Suppose you’re trying to read data from a channel that doesn’t have a value in it. The current goroutine is blocked and another will be unlocked in case it can push a value to the channel. That read operation is blocking. Similarly, when you send data to a channel, the goroutine blocks it and unblocks others until the data is read, where the write operation is blocking.

When you want to close the channel so no more data can be transported through it, use the built-in *close* function. Closing the channel will not block the goroutine. The syntax here is pretty simple:

> close(channel)

You don’t need to check if the channel is closed if you use the for range loop, which will automatically close when the channel closes.

> package main
> 
> import “fmt”
> 
> func squares(c chan int) {
> 
> for i:= 0; i <=9; i++ {
> 
> c <- i\*i
> 
> }
> 
> //close channel
> 
> close(c)
> 
> }
> 
> func main() {
> 
> fmt.Println(“Main() started”)
> 
> c := make(chan int)
> 
> //start goroutine
> 
> go squares(c)
> 
> //blocks and unlocks main goroutine until channel closes
> 
> //for range reads the values one at a time until closed
> 
> for val:= range c {
> 
> fmt.Println(val)
> 
> }
> 
> fmt.Println(“Main() stopped”)
> 
> }

Your results would look like this:

> *Main() started*
> 
> *0*
> 
> *1*
> 
> *4*
> 
> *9*
> 
> *16*
> 
> *25*
> 
> *36*
> 
> *49*
> 
> *64*
> 
> *81*
> 
> *Main() stopped*

## Semaphore Pattern

In addition to channels, goroutines, and mutexes, there’s yet another way that you can synchronize in Go to make sure that the program is fast and everything’s done at the right time. Semaphores are a construct that allows control over access to a shared resource when multiple goroutines are in use.

You’ve seen them in use in the real world. When you go to the grocery store, there are lines for the cashiers. Otherwise, if the mob of shoppers after work on Friday descended on the cash registers, the result would be messy and incorrect, since some shoppers would end up with items they hadn’t bought and missing ones they had due to the chaos. A supermarket could easily have 10 open lanes with 10 cashiers ready to ring up the next shopper. (For our purposes, ignore the bagger and self-checkout lanes.)

You can think of this system, with 10 lines feeding 10 cash registers, like a semaphore that allows 10 shoppers to be accommodated in parallel. Also note that whatever the behavior in line—if people try to jump in front of another, or leave their cart in place while they run to the bathroom—only 10 shoppers can be cashed out at once. If there are 10 cash registers in the store, then the system only allows for 10 purchases to run in parallel.

In the programming world, you’ve probably run across a shared resource such as a remote server. If it were to be bombarded with 10,000 jobs at once, it wouldn’t work as well (and potentially not at all.) When you use a mutex to constrain access to a goroutine, it only allows one goroutine to access the shared resource, which avoids the problem of data races.

Similarly, a *semaphore* (which is found in the *sync* package) allows no more than a certain number N of goroutines to access the resource. You’re able to constrain access to protect the resource from overuse. Of course, this only works if all the goroutines play by the semaphore rules. That’s why many coders put an API in front of the semaphore to ensure that it’s the only conduit in. If you want to allow open access and set N equal to a million, there’s no reason to use a semaphore. It’s not always obvious what N is for a given resource, and you might have to bombard it to discover the optimal N value.

As an example, suppose you have a function that deletes an employee over the company’s network, and you use a simple for-range to use it on the variable named employeeList. If your company’s got 15 or 50 employees, that’s probably fine.

But what if you’re writing code for a global company that employs hundreds of thousands of people? Or what if you wrote the code when there were 50 people, and years later it’s grown rapidly? Tens of thousands of calls could potentially hit the server concurrently. Instead, you could use a *bounded channel* with the semaphore as shown below.

> //remoteDeleteEmployee is the function you’re using to delete employees
> 
> func remoteDeleteEmployee() {
> 
> …
> 
> }
> 
> //the channel sem allows up to 10 concurrent operations
> 
> var sem = make(chan int, 10)
> 
> func main() {
> 
> for\_, employee := range employeeList {
> 
> //if there’s room in the sem channel for 1 integer, the goroutine kicks off
> 
> sem <- 1
> 
> go func(){
> 
> //once the remoteDeleteEmployee call returns, channel sem is drained of the integer and the goroutine continues
> 
> remoteDeleteEmployee(employee.ID)
> 
> <- sem
> 
> } ()
> 
> }
> 
> }

If sem is full, that means at least 10 are in progress. If an 11th comes along, it’s blocked until one of the previous calls returns. Here, we’re using a buffered channel.

However, there’s another option that’s a bit more sophisticated than a bounded channel, which is known as a *weighted semaphore* . This technique will not block the code when it finds the sem variable full. It also lets you specify how many units of the concurrency that you want to limit.

You might want to limit concurrency, but not all the calls come at the same cost. The *context* package makes it easier to pass request-scoped calls, deadlines, and cancellation signals through an API to all the goroutines that are involved in a specific request. A weighted semaphore requires ctx.

Weighted semaphore also gives you the ability to return error states, which is a best practice when it comes to code with network calls, along with context. You need to be able to instantiate it with a defined limit, be able to Acquire() when access to the shared resource is requested, and Release() when the access is complete. The weighted semaphore has three functions: Acquire (sem.Acquire(ctx, 1) where ctx is context, discussed below in more detail. It is the same as sem <-1, which you saw for the bounded channel), Release (sem.Release(1) which is the same as <-sem), and TryAcquire (This attempts to acquire the room for an operation, but doesn’t block the code if there isn’t any room).

Here’s an example of a weighted semaphore with the remoteEmployeeDelete function seen earlier.

> func remote.DeleteEmployee() {
> 
> …
> 
> }
> 
> //sem here is a weighted semaphore that allows up to 10 concurrent goroutines
> 
> var sem = semaphore.NewWeighted(int64(10))
> 
> func main() {
> 
> //context here
> 
> ctx := ctx.Background()
> 
> for\_, employee := employeeList {
> 
> //handle the error, potentially with a break
> 
> if err := sem.Acquire(ctx, 1); err ! = nil {
> 
> }
> 
> go func() {
> 
> remoteDeleteEmployee(employee.ID)
> 
> sem.Release(1)
> 
> } ()
> 
> }
> 
> }

Limiting your code’s concurrent goroutines through semaphores avoids bringing down your system or anyone else’s.

## Channel Factory and Directionality

Another concept you might have come across in other computer languages is the factory pattern. The *factory* pattern is a design pattern intended to define an interface at runtime to create an object. This pattern can create a variety of objects, even when it doesn’t know what it’s creating or how to do it, which is where the name factory comes in. It allows the program to choose the objects at run-time, which means that just small changes in the code can grow the family of objects. There are four aspects to a factory method: Product (which defines the interface of the objects created), ConcreteProduct (which implements the Product interface), Creator (which declares the factory method, which returns an object of type Product), and ConcreteCreator (which overrides the factory method to return an instance of the ConcreteProduct).

Good code that implements the factory pattern involves careful consideration of the arguments of your factory. In addition, it’s best if the created objects can be cached and reused instead of creating them from scratch every time. With channels, the factory method generates a channel inside a function and returns it, rather than passing the channel as a parameter.

You can also specify whether your channel will send only or receive only, known as *directionality* . The syntax is as follows:

> var send-only chan<- int //will only send data
> 
> var recv-only <-chan int //will only receive it, and only receiving data isn’t very helpful because a closed channel is used to indicate it’s no longer sent

## Channels, Tickers, and Timeouts

Timers and tickers allow you to run code in the future, either once or repeatedly, depending on the demands of your program. Using them with channels makes the code easier to write. They’re included, as you’d probably expect, inside the *time* package.

The first is Timer (Timeout). Use this when you want to wait for a specific duration, then send the current time through the channel. Here’s the syntax:

> time.After

And here’s an example:

> select {
> 
> case news := AFJ:
> 
> fmt.Println(news)
> 
> case <-time.After(time.Hour):
> 
> fmt.Println(“No news in an hour”)
> 
> }

The time.Timer underlying this operation won’t be recovered by the garbage collector until the timer fires. If you want to avoid this, you can use time.newTimer instead and call Stop when you don’t need the timer anymore, as seen below:

> for exist := true; exist; {
> 
> timer := time.NewTimer(time.Hour)
> 
> select {
> 
> case news := AFJ:
> 
> timer.Stop(news)
> 
> fmt.Println(news)
> 
> case <-timer.C:
> 
> exists = false
> 
> fmt.Println(“No news in an hour, service terminating”)
> 
> }
> 
> }

After Timer, we have Ticker (Repeat). The ticker returns a channel that delivers clock ticks at specified intervals. Here’s the syntax:

> time.Ticker

Similar to Timer, it will not be recovered by the garbage collector, so you can use time.NewTicker and call the Stop method when it’s no longer needed.

After the Ticker, we have Wait, Act, Cancel. This waits for the specified interval and then calls the function in its goroutine. It returns a time.Timer that you can use to cancel the call. Here’s the syntax:

> time.AfterFunc

## Chapter Summary

Goroutines are the key to providing concurrency in Golang. Channels are the communication pipelines between concurrent goroutines.

*   Concurrency is not the same as parallelism, but can help speed up code execution.
*   There are several ways to synchronize goroutines, including Mutex and RWMutex that lock and unlock portions of the code to avoid data competition.
*   Channels are an elegant way to communicate between goroutines.
*   The semaphore pattern allows you to constrain more than a specified number of channels from accessing a shared resource.
*   Channels can be used inside channels in a channel factory, and you can also specify whether the channel is send-only with directionality.
*   You can also schedule channels in the future using timers and tickers.

In the next chapter, you'll learn about handling errors and testing your code.

Thirteen 

As great as it would be to write flawless code every time, that’s not a reasonable expectation. Like all other computer languages, Go will let you know when there’s a problem. Testing code is an important part of handling errors and shipping programs that are less likely to cause problems and system crashes for end-users. In Go, errors are values; since values can be programmed, errors can be programmed too.

## Run-Time Exceptions and Panic

Go has a built-in error type and uses error values to tell you when the code isn’t working. The error type is an interface, and an error variable is usually described as a string. Unlike other languages, you’re encouraged by design to check for errors explicitly rather than waiting for an exception to get thrown on execution.

*Panic* is a built-in function that stops the program’s ordinary control of flow. When the function P calls panic, the execution of P stops, any deferred functions inside P execute as they normally would, and then P returns to its caller. You can invoke panic directly, but it occurs with some run-time errors. The syntax for panic looks like this, and can take any argument:

> func panic(p interface{})

## Panics and Recover

Golang allows you to handle a panic and recover from it while providing some helpful info and potentially some output to the end-user.

Earlier in the book, we discussed the defer statement, which adds a function call to a list. That saved call list will execute once the surrounding function has returned. In other words, the deferred function is guaranteed to run at the end.

When a function panics, its current execution stops, any deferred functions run, and the function returns to its collar. This goes on up the stack until all functions have either returned or panicked.

The function *recover* , which can only be used with a deferred function, gives Go control over a panicking goroutine. If you try to use recover() with normal flow, you’ll just get nil, but it will capture the panic value if called in a panicking goroutine.

As an example, suppose you had a function PrintAllOps that took two integers, x and y, and added them together, subtracted them, multiplied, and divided them. If you gave y the value of zero, the function would panic because dividing by zero is illegal, but this can be handled with *recover* :

> func PrintAllOps(x int, y int) {
> 
> defer func() {
> 
> if r := recover(); r ! = nil {
> 
> fmt.Printf(“Recovering from panic in PrintAllOps error is: %v \\n”, r)
> 
> }
> 
> } ()
> 
> sum, subtract, multiply, divide := x+y, x-y, x\*y, x/y
> 
> fmt.Printf(“sum= %v, subtract=%v, multiply=%v, divide=%v \\n”, sum, subtract, multiply, divide)
> 
> }

When you run the main function with x:=20 and y:=0, the resulting output appears like so:

> *Recovering from panic in printAllOps error is: runtime error:*
> 
> *integer divide by zero*
> 
> *Exiting main without any issues*

## Error Handling with Closures

In programming, *closures* are records that store a function with its environment. Closures let the function access captured variables (ones that are used locally and defined in an enclosed scope) through the closure’s copies of the references and values, even if the function is called outside their scope.

Closures help when you want to check for errors and report them in the same function. Here’s an example of wrapping error handling in a closure. Notice that the error checking, error reporting, and then normal function are separate in the code.

> func onlineReqHandler( r http.ResponseWriter, req \*http.Request) {
> 
> err := func () os.Error {
> 
> if req.Method ! = “GET” {
> 
> return os.NewError(“expected GET”)
> 
> }
> 
> if input := parseInput(req); input ! = “command” {
> 
> return os.Error(“malformed command”)
> 
> }
> 
> } ()
> 
> if err ! = nil {
> 
> r.WriteHeader(400)
> 
> io.WriteString(r, err)
> 
> return
> 
> }
> 
> do something()...

## Testing and Benchmarking

Part of developing a code that’s easy for others to read and use involves making testing simple. Add your tests to the same folder where you put the rest of your code. The file is named “\_test.go”. If as an example you have a code file called monsters.go, then your test for that file should be saved in the same folder and named monsters\_test.go.

There’s a *testing* package in Golang, as you might expect. The test method always has the following signature:

> TestXxx(t \*testing.T)

For example, suppose you wanted to test your salutation function. Here’s a quick sample:

> package main
> 
> import “testing”
> 
> func TestSayHello(t \*testing.T) {
> 
> goodRun := “Hi Cerberus”
> 
> salutation := sayhello(“Cerberus”)
> 
> if salutation != goodRun, {
> 
> t.Errorf(“Salutation was incorrect, got: %s wanted: %s” salutation, goodRun)
> 
> }
> 
> }

An additional part of the testing package is *benchmarking* . Testing is necessary, but being able to benchmark how your code performs and identify any bottlenecks is valuable as well.

However, you don’t need to benchmark every single piece of code you create. Use benchmarking when you’re having performance issues or when you have time to indulge your curiosity about your code’s performance.

The syntax for benchmarking is similar to that of testing:

> BenchmarkXxx(b \*testing.B)

If you want to run all the benchmarks inside a program, you can run them from the command line with the following signature:

> go test -bench=.

Suppose you have a function that takes an integer and adds 3 to it. This part of the code would look like so:

> func Calculate(x int) (result int) {
> 
> result = x + 3
> 
> return result
> 
> }

To benchmark its performance, import testing and add to the code:

> package main
> 
> import “testing”
> 
> func BenchmarkCalculate(b \*testing.B) {
> 
> for i := 0; i < b.N; i++ {
> 
> Calculate (3)
> 
> }
> 
> }

The result provides you with three values: the name of the benchmark, how many times the program ran the code, and the time it took in nanoseconds per operation in ns/op. It’s run multiple times so the program can take the average instead of basing the benchmark on one observation.

As you add on benchmarks and/or increase the complexity of the code, expect them to take longer. Trying different inputs can also give you a view into how your program might operate in a real-world environment and point to any potential bottlenecks.

For example, in this scenario you might add the following benchmark calculations:

> func BenchmarkCalculate100(b \*testing.B) {benchmarkCalculate(100, b)}
> 
> func BenchmarkCalculateNeg1(b \*testing.B) {benchmarkCalculate(-1, b)}
> 
> func BenchmarkCalculateNeg100(b \*testing.B) {benchmarkCalculate(-100, b)}

## Assessing Code Performance

You may be used to using time complexity analysis to see which program or code snippet runs faster. But Go gives you built-in tools to go deeper than that with benchmarking. Bottlenecks in code aren’t always the result of running the wrong algorithm; sometimes, they’re due to a poor selection or inefficient use of system calls.

Benchmarks allow you to see whether one version of the code performs better than another. Run one version of the code, benchmark it, run a new version with modifications and benchmark it, then compare the results. This could get tedious, but Go has the command *benchstat* (older versions may use benchcmp) to compare the statistics, including mean, minimum, and maximum run time between benchmarks. When run for a single file, the results summarize the file.

If it’s invoked for two input files with multiple benchmarks, you’ll see a column showing the percent change in the mean between the two. It’ll also show the p-value and sample sizes from the tests. Remember, a low p-value (<= 0.05) means the results are statistically significant.

## Chapter Summary

Golang makes it easy for developers to handle errors before end-users find them, and to test and benchmark code to ensure good performance and speedy execution.

*   Panic allows you to override control of the program flow.
*   You can use recover to deal with a panic so portions of the code may still run.
*   Check for errors and report them using closures.
*   The testing package allows you to write tests and benchmark your programs.
*   Go makes it easy for you to compare benchmarks so you can assess the performance of what you’ve written.

In the next chapter, you'll learn about more patterns as well as common Go coding pitfalls.

Fourteen 

Two more ways that speed up your code development and code performance are learning from the mistakes of others and deploying patterns where they make sense. When you learn to avoid common pitfalls, you can make your own mistakes much faster. (That’s kind of a joke, but not really!)

Using patterns and recognizing where they fit in the development of your program will help you skip tedious repetition. You might’ve heard of idiomatic programming, which means to follow language conventions. Even though Go is still relatively new, it still has conventions. These may change over time, but here are a few you’ll probably see.

## Pattern: Comma, OK

One of the idioms often used is “, ok”. It’s useful when you need to clarify the difference between the integer zero and the zero value returned for some functions. For example, if you want to map the high scores for a game, you need to know the difference between a high score of zero and the zero value returned for a player who doesn’t exist.

> highScores := make(map\[string\]int)
> 
> highScores\[“Bert”\] = 317
> 
> highScores\[“Ernie”\] = 433
> 
> log.Println(highScores\[“Ernie”\]) // returns 433, but if you asked for (highScores\[“Oscar”\]) the log results in 0. Does that mean Oscar’s high score was zero, or that Oscar doesn’t exist on the map?
> 
> //so add , ok to avoid this problem.
> 
> if val, OK := highScores\[“Ernie\]; ok {
> 
> log.Println(val) // logs 433
> 
> }

## Pattern: Visibility and Operator

One of the concepts that are different in Golang is public or private visibility. If you’ve programmed in Java, you don’t see protected, public, etc. modifiers. In C++, you don’t see the friend class. Golang gives you capitalization (sometimes called exported/not exported): public identifiers that can be accessed by any Go user begin with a capital letter, while “private” or not exported ones begin with a lowercase. Given this limitation, the general advice is to prefer larger and fewer packages to avoid overly complex package hierarchies.

You might find Go a bit limiting when it comes to operators, which are functions that return a new object and don’t change their parameters. Languages like C++ support overloading operators so you can use math-like syntax, but Go does not. Using an operator as a function helps you get around the limitation as long as you implement them inside a package that contains the objects the code is operating on. You might need to use several variations to make it work. Alternatively, using an operator as a method allows you to chain methods together. Each method returns a receiver, which then becomes the object of the next method call.

Using interfaces is a good practice when you feel an operator is necessary. If you can’t do a generic implementation based on the methods in the interface, you probably have items that aren’t the same type and shouldn’t use the operator pattern.

## Pattern: Defer

*Defer* lets you execute a function just before the surrounding function returns, whether or not there’s a panic. There are a few common mistakes that developers make with defer that you should be aware of. Remember that recover() should *only* be used inside a deferred function. Otherwise, when a panic occurs, recover() won’t catch it and will return nil. When using defer, check for errors to ensure you don’t miss anything. Using the errors package will help you wrap multiple errors, and the information will be in your log so it’s easier to see and understand.

## Common Pitfalls

Now you’re ready to learn from others’ mistakes! If you find something in your programming that you’re not sure about, bear in mind the key principles of Go programming: make the code quick to compile, quick to run, and easy to read and use.

*   Assignment operator :=

This useful operator allows the developer to avoid declaring a variable before assignment. However, because the curly brackets {} define scope, when used with := Golang treats the variables as entirely new within the scope, so you may not get the results you were expecting. It’s easiest to avoid using := as shorthand and beware when you’re switching scope.

*   Incorrect basics

You can’t use the opening brace { on a line by itself; that’s why you’ve always seen

> *func main () {*

Unused variables inside functions will fail to compile, though it’s OK to have global variables that you don’t use. Similarly, if you import a package and don’t use anything from it, you’ll get a compiler error.

*   Nil “gotchas”

You can’t use nil to initialize a variable unless you also declare an explicit type. You can add items to a nil slice, but adding them to a nil map creates a panic. In Go, you can’t use nil with strings. With nonexistent map keys, the returned value is nil if the zero value for the data type is nil, but you’ll get something else with different data types.

*   Array “gotchas”

Like nil, arrays are different in Golang. Instead of pointers, they’re values. When you pass an array to a function, the function receives a copy of the data and not the data itself. That’s a problem when you need to update the array. Use array pointer types or slices if you need to update the data. Unlike other languages, arrays (and slices) are not multidimensional; however, you can create arrays of arrays and slices of slices to help solve coding issues.

*   Logs

Calling log.Fatal() and log.Panic() logs *and also* ends your program. The Golang logging library doesn’t have different log levels.

*   Apps with active goroutines

The app doesn’t wait for all the goroutines to complete. The most common workaround is a WaitGroup variable, which lets all worker goroutines finish before the main one starts. You can also close the channel that’s sending information to the worker goroutines, which will complete them.

*   Channels

If you receive from a closed channel, you’ll get an indication that no data was received. However, if you *send* to a closed channel, it starts a panic. Send and receive operations on a nil channel will block forever.

*   Slices

Reslicing a slice references the array of the original slice, which may lead to more memory usage than you expect, especially if you’re using large, temporary slices to refer to small sections of the original. Copy the data you need from the temporary slice instead of reslicing it.

Beware of “stale” slices; you may reach the point where adding data to a slice creates a new array allocation because the original can’t handle any more data. At that stage, other slices will point to the original array with the old data instead.

## Chapter Summary

There are common patterns frequently used in Golang, and they may be different from similar ones in other languages. Beginners in Golang, especially those who’ve programmed in other languages, have a variety of “gotchas” that are often made by new developers in the language.

*   The comma, ok idiom ( , ok) helps distinguish between a zero value and the integer zero.
*   Go uses capitalization to show whether an identifier is public or private.
*   You might find operators more limited than in other languages, but using interfaces with them is a best practice for coders.
*   Common pitfalls can occur due to the differences in otherwise similar languages.

Whether you’re an experienced developer or this is your first programming language, you now have the basics for beginning your journey in the fast and easy Go programming language. It’s prized for speeding up not only the execution of the program, but also the development of the code.

You’ve learned why developers use it and why it’s preferred in some programming environments, as well as the foundational “vocabulary” which provides a solid introduction to the language.

If you’re an experienced developer, you’ve seen where Golang is similar to and different from other languages you’ve programmed in. If you’re not, you have a solid introduction to programming and understand many of the shared features of other computer languages.

We’ve covered the essentials for Golang, including slices and arrays. While in other languages arrays are a primary component, here slices (based on underlying arrays) are used more often and provide the flexibility that you need.

One of the main features of Go is concurrency, or the ability to run multiple goroutines. There are many techniques for doing so without running into data competition, where multiple aspects of code try to access a shared resource at the same time. These range from timing functions to channels, which act as communication pipelines between multiple goroutines. Concurrency helps to increase the speed of code.

Go helps programmers find and debug errors more easily. Other languages might try to catch errors at run-time, but Go treats them as values that can be programmed. The language also includes the nifty little function *defer* , which can execute deferred routines even if the main routine panics.

Another performance bonus for Golang that you don’t find in many programming languages is the *testing* package, which contains the functions and methods you need to test the code and assess its performance. Benchmarking is built into this, which makes it faster and easier to compare snippets of code and determine which provides better performance.

As you’ve seen, Go is designed to be learned quickly, speed up code development, and execute quickly. It’s also modular so you can import packages that have the functions you want if they aren’t in the main package.

It’s intended to be easy to read so that you can quickly understand what someone else’s code does. Writing code is faster when you don’t have to continually reinvent the wheel; you can reuse your own or import someone else’s. Saving your packages makes it much faster for you to grab a snippet that you’ve used before instead of trying to hunt through directories to find it.

If you haven’t already, now is the time to head to the Go playground and try some coding on your own! Although it’s a relatively young language, you’ll be able to find plenty of other users and communities that can help you with any issues you have.

If you liked this book and found it helpful, please write a review! We want to spread the word about Go and how it can help programmers in a variety of industries and from a variety of coding backgrounds.

My journey into software development started when I was a kid, which gave me ample opportunity to learn about the basics of computer programming and software development in my early years. I never stopped studying computer programming, spending my youth picking apart games to learn how their programs worked. After high school, I went to the University of Missouri where I joined the I.S. Programming Club and studied Information Systems and Computer Science. In 2016, I graduated and started my company as an independent software developer; I’ve used Google programming languages to develop many apps for clients *and* for myself, including *Loop* , a social media app designed to help communities better police themselves. I’ve trained and consulted with Fortune 500 companies all over the world. To keep up with me, find me on Twitter at @Streetgenius\_.

If you liked this book and found it helpful, consider expanding your coding toolkit by reading my other books:

Flutter for Beginners: A Genius Guide to Flutter App Development

Python for Beginners: A Genius Guide to Python Programming

Combs, Veronica. “Google’s Go Scores as the Top Language Developers Want to Learn.” *TechRepublic* , 12 May 2020, [www.techrepublic.com/article/developers-put-learning-googles-go-at-the-top-of-their-to-do-list](http://www.techrepublic.com/article/developers-put-learning-googles-go-at-the-top-of-their-to-do-list) .

**Additional Sources**

Bellairs, R. “What Is Static Analysis? Static Code Analysis Overview.” *Perforce Software* , 10 Feb. 2020, www.perforce.com/blog/sca/what-static-analysis.

Biggs, John, and Ben Popper. “What’s so Great about Go?” *Stack Overflow Blog* , 6 Nov. 2020, stackoverflow.blog/2020/11/02/go-golang-learn-fast-programming-languages.

Caraveo, Ralph, III. “Go’s Extended Concurrency: Semaphores (Part 1) - Ralph Caraveo III.” *Medium* , 4 Sept. 2018, medium.com/@deckarep/gos-extended-concurrency-semaphores-part-1-5eeabfa351ce.

Chng, Peter. “Golang: Promoted Methods, Method Sets and Embedded Types » Unitstep.Net.” *Unitstep* , 16 Sept. 2015, unitstep.net/blog/2015/09/16/golang-promoted-methods-method-sets-and-embedded-types.

Chu, Zion. “Use of Synchronization Techniques in Golang - Zion Chu.” *Medium* , 29 Mar. 2021, lebum.medium.com/use-of-synchronization-techniques-in-golang-53d75bc0a646.

Damilola, Kassim. “Sort.Sort() Interface in GoLang - Kassim Damilola.” *Medium* , 15 June 2020, medium.com/@kdnotes/sort-sort-interface-in-golang-1d263d96956d.

Develop Paper. “Built in Functions in Golang.” *Develop Paper* , 14 Sept. 2020, developpaper.com/built-in-functions-in-golang.

Dice. “Dice Tech Salary Report.” *CourseHero* , www.coursehero.com/file/55824776/Dice-TechSalaryReport-2019pdf.

Franssen, Marco. “Test and Benchmark Your Code in Go - Marco Franssen.” *Marco Franssen* , 3 Feb. 2019, marcofranssen.nl/test-and-benchmark-your-code-in-go.

freeCodeCamp.org. “Interpreted vs Compiled Programming Languages: What's the Difference?” *FreeCodeCamp.Org* , 28 Apr. 2021, www.freecodecamp.org/news/compiled-versus-interpreted-languages.

*Fullstack Go* . www.fullstackgo.io.

GeeksforGeeks. “Different Types of Recursion in Golang.” *GeeksforGeeks* , 11 July 2020, [www.geeksforgeeks.org/different-types-of-recursion-in-golang](http://www.geeksforgeeks.org/different-types-of-recursion-in-golang) .

Gitlab. “Go Standards and Style Guidelines | GitLab.” *Gitlab* , docs.gitlab.com/ee/development/go\_guide.

*Go 101* . go101.org.

*Go Googlesource* . go.googlesource.com.

*Golang* . Callicoder, www.callicoder.com/golang.

*Golang By Example* . golangbyexample.com.

*Golang Cafe* . golang.cafe.

*Golang Docs* . golangdocs.com.

*Golang Patterns* . www.golangpatterns.info.

*Golang Programs* . www.golangprograms.com.

*Golang Spec* . Medium, medium.com/golangspec.

*Golang Tour* . tour.golang.org.

*Golang Tutorial* . Educative, www.educative.io/blog/golang-tutorial.

*Gopher Academy* . blog.gopheracademy.com.

*Gopher Guides.* “Defining Methods in Go.” *DigitalOcean* , 6 Feb. 2021, www.digitalocean.com/community/tutorials/defining-methods-in-go.

\---. “How to Read and Write the Files in Golang?” *GeeksforGeeks* , 24 June 2021, www.geeksforgeeks.org/how-to-read-and-write-the-files-in-golang.

\---. “How to Use Array Reverse Sort Functions for Integer and Strings in Golang?” *GeeksforGeeks* , 17 May 2020, [www.geeksforgeeks.org/how-to-use-array-reverse-sort-functions-for-integer-and-strings-in-golang](http://www.geeksforgeeks.org/how-to-use-array-reverse-sort-functions-for-integer-and-strings-in-golang) .

\---. “How To Use Struct Tags in Go.” *DigitalOcean* , 1 Apr. 2021, www.digitalocean.com/community/tutorials/how-to-use-struct-tags-in-go.

\---. “How To Write Packages in Go.” *DigitalOcean* , 12 Jan. 2021, www.digitalocean.com/community/tutorials/how-to-write-packages-in-go.

\---. “Identifiers in Go Language.” *GeeksforGeeks* , 18 Nov. 2019, www.geeksforgeeks.org/identifiers-in-go-language.

\---. “Inheritance in GoLang.” *GeeksforGeeks* , 22 June 2020, [www.geeksforgeeks.org/inheritance-in-golang](http://www.geeksforgeeks.org/inheritance-in-golang) .

Interfaces, Demystifying Golang’S Io. Reader And Io. Writer. “Demystifying Golang’s Io.Reader and Io.Writer Interfaces | I Care, I Share, I’m Nathan LeClaire.” *Nathan LeClaire* , 19 July 2014, nathanleclaire.com/blog/2014/07/19/demystifying-golangs-io-dot-reader-and-io-dot-writer-interfaces.

\---. “Interfaces in Golang.” *GeeksforGeeks* , 20 Nov. 2019, [www.geeksforgeeks.org/interfaces-in-golang](http://www.geeksforgeeks.org/interfaces-in-golang) .

*Learn Go Programming* . blog.learngoprogramming.com.

Lodha, Tilak. “Concurrency and Parallelism in Golang - Tilak Lodha.” *Medium* , 15 June 2018, medium.com/@tilaklodha/concurrency-and-parallelism-in-golang-5333e9a4ba64.

\---. “Methods in Golang.” *GeeksforGeeks* , 20 Nov. 2019, www.geeksforgeeks.org/methods-in-golang.

\---. “Naming the Return Values of a Function in Golang.” *GeeksforGeeks* , 10 May 2020, [www.geeksforgeeks.org/naming-the-return-values-of-a-function-in-golang](http://www.geeksforgeeks.org/naming-the-return-values-of-a-function-in-golang) .

Osadchiy, Victor. “Why Use the Go Language for Your Project?” *Yalantis* , yalantis.com/blog/why-use-go. Accessed 1 July 2021.

Peshkov, Sergei. “4 Go Language Criticisms.” *Toptal Engineering Blog* , 4 Apr. 2018, www.toptal.com/go/4-go-language-criticisms.

Programmersought. “Golang - Goroutine and Channel - Programmer Sought.” *Programmersought* , www.programmersought.com/article/8644637992. Accessed 1 July 2021.

Quest, Kyle. “50 Shades of Go: Traps, Gotchas, and Common Mistakes for New Golang Devs.” *Devs ♥ Security* , 17 Dec. 2015, devs.cloudimmunity.com/gotchas-and-common-mistakes-in-go-golang.

*QVault* . qvault.io/golang.

Ralch, S. “Desing Patterns in Golang: Factory Method : Blog.Ralch.Com.” *Ralch* , 31 Jan. 2016, blog.ralch.com/tutorial/design-patterns/golang-factory-method.

Rao, Karthic. “Analyzing Benchmarks with Ease Using Benchcmp and Benchviz Golang.” *Medium* , 5 Apr. 2018, medium.com/@hackintoshrao/analyzing-benchmarks-with-ease-using-benchcmp-and-benchviz-golang-add607fc46d6#.8x32zrjpo.

\---. “Reflection in Golang.” *GeeksforGeeks* , 21 Apr. 2020, [www.geeksforgeeks.org/reflection-in-golang](http://www.geeksforgeeks.org/reflection-in-golang) .

Roy, Arindam. “Simple Guide to Panic Handling and Recovery in Golang.” *Medium* , 15 Sept. 2019, medium.com/swlh/simple-guide-to-panic-handling-and-recovery-in-golang-72d6181ae3e8.

*Run Go* . Medium.com, medium.com/rungo.

\---. “Strings in Golang.” *GeeksforGeeks* , 9 Aug. 2019, [www.geeksforgeeks.org/strings-in-golang](http://www.geeksforgeeks.org/strings-in-golang) .

Shichao. “Chapter 12. Reflection - Shichao’s Notes.” *Shichao* , notes.shichao.io/gopl/ch12. Accessed 1 July 2021.

Shirsath, Reemi. “Golang In Fintech - Reemi Shirsath.” *Medium* , 22 Oct. 2020, reemishirsath.medium.com/golang-in-fintech-e27193a7b603.

Sophie. “Go Goto Statement.” *W3Adda* , 17 Dec. 2017, www.w3adda.com/golang-tutorial/go-goto-statement.

*Tutorial Edge* . tutorialedge.net/golang.

*Tutorials Point* . www.tutorialspoint.com/go.

\---. “Type Assertions in Golang.” *GeeksforGeeks* , 22 June 2020, www.geeksforgeeks.org/type-assertions-in-golang.

\---. “Understanding Maps in Go.” *DigitalOcean* , 14 June 2021, www.digitalocean.com/community/tutorials/understanding-maps-in-go.

\---. “Using Break and Continue Statements When Working with Loops in Go.” *DigitalOcean* , 14 June 2021, [www.digitalocean.com/community/tutorials/using-break-and-continue-statements-when-working-with-loops-in-go](http://www.digitalocean.com/community/tutorials/using-break-and-continue-statements-when-working-with-loops-in-go) .

Wolfe, Mark. “How Do I Structure My Go Project?” *Wolfe* , 9 Mar. 2020, www.wolfe.id.au/2020/03/10/how-do-i-structure-my-go-project.

*Your Basic* . yourbasic.org/golang.

Yse, Diego Lopez. “Essential Programming | Control Structures - Towards Data Science.” *Medium* , 22 Jan. 2020, towardsdatascience.com/essential-programming-control-structures-2e5e73285df4.

*Zetcode* . zetcode.com/golang.
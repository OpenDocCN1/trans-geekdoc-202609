
# Reading user input

You will learn how to read user input, both a simpler technique and a more advanced one using formatters.

## Introduction

This chapter will cover:

*   The `Scan()` method to read user input.

*   Reading one input.

*   Reading multiple inputs.

*   Working with formattters.

## User input

It’s an important thing to be able to read user input from the console. It gives the user a chance to interact with the program. Things to consider are how you are asking the user to input, is it one word, several inputs. Will the user separate input by space or newline? Regardless of what approach you go with, try to communicate the chosen approach to the user.

## Managing user input with `fmt`

So far, you’ve seen how the `fmt` package can be used to print to the console. It can also be used to read user input.

The `fmt` library has a built-in `Scan()` method that we will use to capture the user input.

## Reading one input

You might start out wanting to read one input from the user. That’s what the `Scan()` method does by default.

Here’s some code showing how to collect user input:

```
1 package main
2 
3 import "fmt"
4 
5 func main() {
6     var response string
7     fmt.Scan(&response)
8     fmt.Println("User typed: ", response)
9 }
```

Note how you send in the string `response` as a reference, using the `&` operator. It’s done this way as the `Scan()` method will modify the variable you send in.

When you run this code, you will see the below output:

```
1 hello
2 User typed: hello
```

## Reading multiple inputs

You can provide several arguments to the `Scan()` method. By providing several arguments, you can collect more than one user input and separate each input, in the `Scan()` function, with a comma. Here’s how to apply this technique:

```
1 var a1, a2 string
2 // multiple input
3 fmt.Scan(&a1, &a2)
4 
5 // formatted string to print out the user input
6 str := fmt.Sprintf("a1: %s a2: %s", a1, a2)
```

Note how `a1` and `a2` is sent into `Scan()` and they are comma-separated. So how will those codes run?

When you run this code, there are two ways for the user to input. The user can either separate the values by space like so:

```
1 hi you
2 a1: hi a2: you
```

or by newline:

```
1 hi 
2 you
3 a1: hi a2: you
```

## `Scanf()`, scan the input with formatters

So far, you’ve seen how you can collect input with spaces and endlines as separators. You can also be specific in how you collect input. Imagine that the user wants to type in an invoice number like so “INV200” or “INV114” and what you are interested in is the number part, or you are interested in the prefix as well?

The answer to solving this is in the `Scanf()` function. It takes formatters. With formatters, you’re able to pick the part of the user input you are interested in and place that into the variable you want.

In the above-mentioned case, you can construct code looking like so:

```
1 var prefix string
2 var no int
3 // in110
4 fmt.Scanf("%3s%d", &prefix, &no)
5 fmt.Printf("prefix: %s, invoice no: %d", prefix, no)
```

The interesting part lies in the first argument of `Scanf()`, namely `3s%d`. What this means is, take the first 3 characters, `%3s` and interpret them as a string. Then interpret and place the remaining as a number, `%d`.

Running this program, you will get an output like so:

```
1 inv200
2 prefix: inv, invoice no: 200
```

“inv” is placed in `prefix` and 200 in `no` variable.

## Learn more

To learn more about this area, check out this link [https://pkg.go.dev/fmt#Scanf](https://pkg.go.dev/fmt#Scanf)

## Assignment - read user input

In this assignment, you will read user input for a card game. The objective is to capture the names of the players.

1.  Create a file *main.go* with the following content: 

    ```
    1 package main
    2 
    3 import "fmt"
    4 
    5 func main() {
    6 
    7 }
    ```

2.  Add the following code to the `main()` method: 

    ```
    1 fmt.Println("Enter player names (separated by space or newline):")
    2 var player1, player2 string
    3 fmt.Scan(&player1, &player2)
    4 fmt.Println("Players are: ", player1, player2)
    ```

3.  Run the program using `go run main.go`:

    ```
    1 go run main.go
    ```

    You should see the following output:

    ```
    1 Enter player names (separated by space or newline):
    2 Alice Bob
    3 Players are:  Alice Bob
    ```

## 🚀 Challenge

Try modifying the program so it takes several players first and then ensures all players get a name. Here’s an example output of such a program:

```
1 Enter number of players: 
2 3
3 Enter Player 1 name: 
4 Alice
5 Enter Player 2 name:
6 Bob
7 Enter Player 3 name:
8 Jean
9 Players are: Alice Bob Jean
```

## Solution

```
 1 package main
 2 
 3 import "fmt"
 4 
 5 func main() {
 6  fmt.Println("Enter player names (separated by space):")
 7  var player1, player2 string
 8  fmt.Scan(&player1, &player2)
 9  fmt.Println("Players are: ", player1, player2)
10 }
```

# Using functions

In this chapter, we will discuss how you can define and use functions. Functions are great when you have the same type of code used in many places. By using functions, you thereby reduce repetition.

## Introduction

This chapter will cover:

*   What a function is and why use it.

*   How to define and call a function.

*   Returning multiple values.

## Why functions

As soon as you have a set of statements you repeat in many places, it’s a good use case for creating a function. Typical things you put in functions are logging to a file, performing a calculation or talking to a data source.

## Your first function `main()`

So far, you’ve seen the function `main()`, define like so:

```
1 func main(){
2 }
```

There’s only one such function, it’s called an entry point and represents the start of the program. You can however define other functions.

## The anatomy of a function

A function consists of various parts. By incorporating all these parts, you ensure you have a reusable piece of code you can use in many places.

Here are the parts you need to care about:

*   `func`, the keyword `func`.


![](resources/go-from-the-beginning-generated.png)

![Go, from the beginning](resources/go-from-the-beginning-generated.png)

## Go, from the beginning

### from o to hero

#### Chris Noring

This book is for sale at [http://leanpub.com/go-from-the-beginning](http://leanpub.com/go-from-the-beginning)

This version was published on 2022-05-06

![publisher's logo](resources/leanpub-logo.png)

\*   \*   \*   \*   \*

This is a [Leanpub](https://leanpub.com) book. Leanpub empowers authors and publishers with the Lean Publishing process. [Lean Publishing](https://leanpub.com/manifesto) is the act of publishing an in-progress ebook using lightweight tools and many iterations to get reader feedback, pivot until you have the right book and build traction once you do.

\*   \*   \*   \*   \*

© 2022 Chris Noring 

To the brave people of Ukraine for which I’m writing this book

## Table of Contents

1.  [Your first program](#chap00.xhtml#leanpub-auto-your-first-program) 

    1.  [Introduction](#chap00.xhtml#leanpub-auto-introduction)

    2.  [A history of Go](#chap00.xhtml#leanpub-auto-a-history-of-go)

    3.  [What is it used for though?](#chap00.xhtml#leanpub-auto-what-is-it-used-for-though)

    4.  [References](#chap00.xhtml#leanpub-auto-references)

    5.  [Features](#chap00.xhtml#leanpub-auto-features)

    6.  [Install Go](#chap00.xhtml#leanpub-auto-install-go)

    7.  [A Go program](#chap00.xhtml#leanpub-auto-a-go-program)

    8.  [Commands](#chap00.xhtml#leanpub-auto-commands)

    9.  [Summary](#chap00.xhtml#leanpub-auto-summary)

    10.  [🚀 Challenge](#chap00.xhtml#leanpub-auto-challenge)

    11.  [Review & Self Study](#chap00.xhtml#leanpub-auto-review--self-study)

    12.  [Assignment](#chap00.xhtml#leanpub-auto-assignment)

    13.  [Solution](#chap00.xhtml#leanpub-auto-solution)

2.  [Using variables](#chap01.xhtml#leanpub-auto-using-variables) 

    1.  [Introduction](#chap01.xhtml#leanpub-auto-introduction-1)

    2.  [Declare variables](#chap01.xhtml#leanpub-auto-declare-variables)

    3.  [Assign variables](#chap01.xhtml#leanpub-auto-assign-variables)

    4.  [Data types](#chap01.xhtml#leanpub-auto-data-types)

    5.  [String interpolation](#chap01.xhtml#leanpub-auto-string-interpolation)

    6.  [Assignment - define some variables and print them out](#chap01.xhtml#leanpub-auto-assignment---define-some-variables-and-print-them-out)

    7.  [🚀 Challenge](#chap01.xhtml#leanpub_auto-challenge-1)

    8.  [Review & Self Study](#chap01.xhtml#leanpub_auto-review--self-study-1)

    9.  [Solution](#chap01.xhtml#leanpub_auto-solution-1)

3.  [Flow control](#chap02.xhtml#leanpub-auto-flow-control) 

    1.  [Introduction](#chap02.xhtml#leanpub_auto-introduction-2)

    2.  [Flow control](#chap02.xhtml#leanpub_auto-flow-control-1)

    3.  [The `if` construct](#chap02.xhtml#leanpub_auto-the-if-construct)

    4.  [Using `else if`](#chap02.xhtml#leanpub_auto-using-else-if)

    5.  [Multiple expressions](#chap02.xhtml#leanpub_auto-multiple-expressions)

    6.  [Assignment - create a program that tests your Boolean logic](#chap02.xhtml#leanpub_auto-assignment---create-a-program-that-tests-your-boolean-logic)

    7.  [🚀 Challenge](#chap02.xhtml#leanpub_auto-challenge-2)

    8.  [Solution](#chap02.xhtml#leanpub_auto-solution-2)

    9.  [Review & Self Study](#chap02.xhtml#leanpub_auto-review--self-study-2)

4.  [Converting between types](#chap03.xhtml#leanpub_auto-converting-between-types) 

    1.  [Introduction](#chap03.xhtml#leanpub_auto-introduction-3)

    2.  [Why convert between types](#chap03.xhtml#leanpub_auto-why-convert-between-types)

    3.  [Use case - command-line arguments](#chap03.xhtml#leanpub_auto-use-case---command-line-arguments)

    4.  [Convert from string to int with `strconv`](#chap03.xhtml#leanpub_auto-convert-from-string-to-int-with-strconv)

    5.  [Parse string to int](#chap03.xhtml#leanpub_auto-parse-string-to-int)

    6.  [Integer to string](#chap03.xhtml#leanpub_auto-integer-to-string)

    7.  [Additional parsing](#chap03.xhtml#leanpub_auto-additional-parsing)

    8.  [Assignment](#chap03.xhtml#leanpub_auto-assignment-1)

    9.  [Solution](#chap03.xhtml#leanpub_auto-solution-3)

    10.  [🚀 Challenge](#chap03.xhtml#leanpub_auto-challenge-3)

5.  [Working with loops](#chap04.xhtml#leanpub_auto-working-with-loops) 

    1.  [Introduction](#chap04.xhtml#leanpub_auto-introduction-4)

    2.  [The case for looping statements](#chap04.xhtml#leanpub_auto-the-case-for-looping-statements)

    3.  [The `for` loop](#chap04.xhtml#leanpub_auto-the-for-loop)

    4.  [Repeat until the condition is met with `while`](#chap04.xhtml#leanpub_auto-repeat-until-the-condition-is-met-with-while)

    5.  [Using for-each over a range](#chap04.xhtml#leanpub_auto-using-for-each-over-a-range)

    6.  [Controlling the loop with `continue` and `break`](#chap04.xhtml#leanpub_auto-controlling-the-loop-with-continue-and-break)

    7.  [Assignment - create a command line loop](#chap04.xhtml#leanpub_auto-assignment---create-a-command-line-loop)

    8.  [🚀 Challenge](#chap04.xhtml#leanpub_auto-challenge-4)

    9.  [Solution](#chap04.xhtml#leanpub_auto-solution-4)

6.  [Reading user input](#chap05.xhtml#leanpub_auto-reading-user-input) 

    1.  [Introduction](#chap05.xhtml#leanpub_auto-introduction-5)

    2.  [User input](#chap05.xhtml#leanpub_auto-user-input)

    3.  [Managing user input with `fmt`](#chap05.xhtml#leanpub_auto-managing-user-input-with-fmt)

    4.  [Reading one input](#chap05.xhtml#leanpub_auto-reading-one-input)

    5.  [Reading multiple inputs](#chap05.xhtml#leanpub_auto-reading-multiple-inputs)

    6.  [`Scanf()`, scan the input with formatters](#chap05.xhtml#leanpub_auto-scanf-scan-the-input-with-formatters)

    7.  [Learn more](#chap05.xhtml#leanpub_auto-learn-more)

    8.  [Assignment - read user input](#chap05.xhtml#leanpub_auto-assignment---read-user-input)

    9.  [🚀 Challenge](#chap05.xhtml#leanpub_auto-challenge-5)

    10.  [Solution](#chap05.xhtml#leanpub_auto-solution-5)

7.  [Using functions](#chap06.xhtml#leanpub_auto-using-functions) 

    1.  [Introduction](#chap06.xhtml#leanpub_auto-introduction-6)

    2.  [Why functions](#chap06.xhtml#leanpub_auto-why-functions)

    3.  [Your first function `main()`](#chap06.xhtml#leanpub_auto-your-first-function-main)

    4.  [The anatomy of a function](#chap06.xhtml#leanpub_auto-the-anatomy-of-a-function)

    5.  [Adding a return type](#chap06.xhtml#leanpub_auto-adding-a-return-type)

    6.  [Multiple returns](#chap06.xhtml#leanpub_auto-multiple-returns)

    7.  [Assignment - adding a function to a program](#chap06.xhtml#leanpub_auto-assignment---adding-a-function-to-a-program)

    8.  [Solution](#chap06.xhtml#leanpub_auto-solution-6)

8.  [Handling errors](#chap07.xhtml#leanpub_auto-handling-errors) 

    1.  [Introduction](#chap07.xhtml#leanpub_auto-introduction-7)

    2.  [Errors](#chap07.xhtml#leanpub_auto-errors)

    3.  [Crash the program with `panic()`](#chap07.xhtml#leanpub_auto-crash-the-program-with-panic)

    4.  [Improve the error handling](#chap07.xhtml#leanpub_auto-improve-the-error-handling)

    5.  [Use the error pattern with the `errors` package](#chap07.xhtml#leanpub_auto-use-the-error-pattern-with-the-errors-package)

    6.  [Assignment I - add error handling](#chap07.xhtml#leanpub_auto-assignment-i---add-error-handling)

    7.  [Solution I](#chap07.xhtml#leanpub_auto-solution-i)

    8.  [Assignment II - improve error logging](#chap07.xhtml#leanpub_auto-assignment-ii---improve-error-logging)

    9.  [Solution II](#chap07.xhtml#leanpub_auto-solution-ii)

9.  [Arrays and slices](#chap08.xhtml#leanpub_auto-arrays-and-slices) 

    1.  [Introduction](#chap08.xhtml#leanpub_auto-introduction-8)

    2.  [Arrays](#chap08.xhtml#leanpub_auto-arrays)

    3.  [Declare an array](#chap08.xhtml#leanpub_auto-declare-an-array)

    4.  [Accessing elements](#chap08.xhtml#leanpub_auto-accessing-elements)


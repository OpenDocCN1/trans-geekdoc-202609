```
**Python**

```
number = int(input("Enter a number: "))
try:
    result = 10/number
    print(result)
except:
    print("There was a problem!")
```
```

The exception handling construct can include only a `try/catch` block in Java, or just a `try/except` block in Python. There is no need to specifically indicate the type of error that might have caused the program to crash, but this is useful to help the programmer debug the code and fix issues that might be solved or to let the user understand the problem if the wrong input is provided.

> **Key information**
> 
> "Exception" refers to the event that interrupts the execution of a program, while "exception handling" refers to the actions taken to deal with an exception or how the system is prevented from halting unexpectedly. For example, a division by 0 is an exception; using a `try/catch` or `try/except` block is the exception handling technique.

+   **REVIEW QUESTIONS**
+   
+   1. Explain how exceptions differ from errors.
+   2. Explain why it is important to handle exceptions in your code.
+   3. Identify some common types of exceptions.
+   4. Explain a scenario when a runtime error could occur.
+   5. Explain the risks of showing detailed exception messages to end users.

# B2.1.4 Debugging techniques

Debugging refers to finding and fixing errors in code. Common debugging techniques include trace tables, breakpoint debugging, print statements and step-by-step code execution.

+   * Debugging: finding and fixing errors in a program.
+   * Trace table: a technique used to test an algorithm, and to predict how it will be run and how values of variables will change.
+   * Breakpoint: a marker to interrupt the execution of code for debugging purposes.

# Trace tables

Trace tables represent a technique usually used at design stage to test an algorithm and predict step by step how it will run. They can be used to demonstrate the outcome of an algorithm or to identify logic errors.

A trace table is a table in which the columns represent variables, conditions or an output in the algorithm. However, not all variables, conditions or outputs are always needed; this depends on the purpose of the trace table.

Its role is to identify how variables change, what conditions evaluate to and what are the produced outcomes. By producing a trace table, the purpose of the algorithm can be determined or any flaws in the algorithm can be detected.
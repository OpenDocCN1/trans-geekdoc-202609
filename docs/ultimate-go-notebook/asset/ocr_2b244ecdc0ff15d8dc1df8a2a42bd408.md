# Chapter 13: Stack Traces / Core Dumps

In this chapter, I will learn how to read stack traces and generate core dumps. Understanding the information in a stack trace can sometimes mean the difference between finding the bug or needing to add more logging, and waiting for it to happen again.

# 13.1 ABI Changes In 1.17

As of version 1.17, Go changed the ABI (application binary interface) to implement a new way of passing function input and output arguments using registers instead of memory on the stack. This is enabled for Linux, macOS, and Windows on the 64-x86 architectures. This means that function arguments won't be copied on the stack, but some may depend on the viability of using registers.

Because of this ABI change, stack trace output has changed in 1.17 and function input values that are placed in registers won't appear accurately in the stack trace anymore. The format of how input values are displayed has changed as well.

Accuracy is something the Go team is looking to improve on future releases of Go. For now, this chapter will focus on how to read a stack trace in version 1.16 or less. I have added a section to show the changes of the stack output and how they are no longer accurate.

# 13.2 Basic Example

I will start with stack traces and learn how to read all the information that is presented. Here is a program that uses the built-in function panic to cause a stack trace.

Listing 13.1

```
01 package main
02
03 func main() {
04     example(make([]string, 2, 4), "hello", 10)
05 }
06
07 //go:noinline
08 func example(slice []string, str string, i int) error {
09     panic("Want stack trace")
10 }
```

After running the program, the following stack trace is presented.
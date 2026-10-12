
In this figure, we can see the system’s cores. The OS scheduler manages a layer of thread; above it, we can see our Go program that executes the Goroutines thread, and the Go Scheduler manages all of that.

Let’s observe single-core system behavior.

![](OEBPS/images/2.4.jpg)

**Figure 2.4:** Single-core OS allocating a goroutine

This figure shows a single-core OS that executes some Goroutines called G1. Then another Goroutine is executed at the end, called G2.

But what happens when we have multi-cores? When a program starts in Go, the scheduler will initial a thread; if some goroutines are executed and the previous goroutines were not done, it allocates more threads until the maximum number of threads is reached. The maximum number of threads in a configuration is Go, which is set as an environment variable called `GOMAXPROCS`. The default and recommended value by a benchmark done by the Go team is the number of cores. For example, if a machine has 8 cores, the value of `GOMAXPROCS` is 8, and the scheduler won’t schedule more than 8 threads. We can configure the environment variable, but this isn’t recommended.

How does the scheduler work when more goroutines need to be executed rather than available threads?

![](OEBPS/images/2.5.jpg)

**Figure 2.5:** Multiple threads with queues managed by the scheduler

There is a dedicated queue for each thread that knows the next goroutines that are supposed to be scheduled on this thread. A new queue is created for each new thread being allocated. Each goroutine is allocated while running on some thread and directly goes to the same thread’s queue. To prevent an intense load on a single queue, the scheduler performs work, stealing between threads and balances the work between them.

This was an explanation in a nutshell of the Go scheduler. There are many other things that the scheduler is considering, like system locks, code locks, communication between threads, allocating of threads, idle threads, and so on.

# Maintainability of Go

Several reasons are why Go is easy to maintain:

*   Compatibility
*   Go simplicity
*   Error handling

# Compatibility

> “It is intended that programs written to the Go 1 specification will continue to compile and run correctly, unchanged, over the lifetime of that specification. At some indefinite point, a Go 2 specification may arise, but until that time, Go programs that work today should continue to work even as future “point” releases of Go 1 arise (Go 1.1, Go 1.2, etc.).”

It is a quote from the documentation of Go when the first version of Go was released. There is an attachment to this documentation in the references. Note that later in the documents, they set expectations and write that things can go wrong, like bugs, security issues, structs literals, and more.

When every version of Go is released, there is an intention for backward and forward compatibility. According to Russ Cox from GopherCon 2022, the Go team uses two main approaches to keep it compatible:

*   API Checking
*   Testing

## API Checking

In order to prevent the breakage of previous versions of Go, we can’t remove exported symbols, API methods, packages, and so on. Otherwise, the program will fail. Go can’t remove libraries, structs, methods, and so on.

The Go team uses a tool that contains all the exported API signatures for all Go versions. Then, the Go team runs tests that compare the package API to the exported API signatures and notify if something has changed. If something changes, they take action to either prevent it or at least minimize its impact.

## Testing

A colossal advantage that Google maintains in Go is that it can be tested within Google. The development version of Go is being tested against all of Google’s internal Go program tests. After all these tests pass, the Go development branch is used in the Google production environment and toolchain.

With every release of Go, they note if something got broken in the new version. Go also provides a powerful tool called `GODEBUG` that helps us upgrade our version and verify that our program doesn’t panic.

# Go Simplicity

As we have seen before, one of Go’s main goals is simplicity. This simplicity pays off when we examine the program’s maintainability. One significant advantage of the Go team is that they make all the rules. In the previous chapter, we talked about “*Effective Go*,” which has all the conventions, best practices, and documentation for how to do things. Unlike some other languages where conventions come from different places, in Go, the Go team decides everything.

# Error Handling

Go is different from other languages. In many other languages, we are expecting to see a `try-catch-finally` idiom.

This is not the case with Go. In Go, we will explicitly create an error and return it as a variable. Here is a quote from Go FAQ.

> “We believe that coupling exceptions to a control structure, as in the `try-catch-finally` idiom, results in convoluted code. It also tends to encourage programmers to label too many ordinary errors, such as failing to open a file, as exceptional.”

Sometimes it can be frustrating to see code like this:

```
if err != nil {
    return err
}
```

However, if we understand its motive, we can accept it. Additionally, to Go FAQ, the error handling in Go gives us a way to tell a story. Instead of just returning the error, we can add context to it and, by that, create the story of the error, for instance:

```
if err != nil {
    return fmt.Errorf("connecting to DB: %w", err)
}
```

Now we have the context that this error happened while trying to connect to the DB. It was just one example to understand the hidden power of error handling in Go.

# From Onboarding to Production

A programming language doesn’t consist only of language components like compiler, syntax, and so on. It also consists of several tools crucial to the toolchain, like a package manager, documentation, formatter, linter, test tools, and so on.

Go aims to give the Go developer a holistic experience by providing the tools in the toolchain. There are three reasons why the Go team wants to create the toolchain.

One is that they don’t need to depend on anonymous contributors to create a tool. The second and more important reason is that the Go team knows the best way to build such a tool. The third reason is to achieve standardization.

We don’t want to have two formatters that do very similar things but operate differently, and we can see these patterns in other languages. The formatter is just one example of standardization. It can be a linter, tests, time package, and so on.

What are the steps for the newcomer to the language until they deploy it to production?

1.  Getting Started
2.  Plan
3.  Package Management
4.  Writing code
5.  Troubleshoot
6.  Test
7.  Security
8.  Build
9.  Others

## Getting Started

A newcomer to the language doesn’t know how the language syntax looks alike. The Go team created a playground, so developers who read about the language can already be engaged and play with it. All the documentation and playground exist in `go.dev`.

## Plan

The newcomer fell in love with the language. Now, they want to start a project. But before jumping into the code, we want to plan. We want to understand how the project is going to look. To do so, we must understand and explore the packages we aim to use. There is a single artifact manager for all Go packages, and this manager, not surprisingly, exists in `go.dev`, specifically in `pkg.go.dev`.

## Package management

To interact with various tools from the Go toolchain, we need to have the Go CLI; that’s it. In the Go CLI, various tools help us to start the project. We finished planning our project, and now we want to start. We will run the following command to initial a project:

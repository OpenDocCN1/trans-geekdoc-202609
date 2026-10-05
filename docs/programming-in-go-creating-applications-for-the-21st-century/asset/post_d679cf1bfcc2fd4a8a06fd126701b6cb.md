
## 5.3. Looping with For Statements

```gofound := false
for row := range table {
  for column := range table[row] {
    if table[row][column] == x {
      found = true
      break
    }
  }
  if found {
    break
  }
}

found := false
FOUND:
for row := range table {
  for column := range table[row] {
    if table[row][column] == x {
      found = true
      break FOUND
    }
  }
}
```

A label is an identifier followed by a colon. Both code snippets achieve the same thing but the right-hand snippet is shorter and clearer as soon as the searched-value (x) is found, it breaks to the outer loop by using a break statement that specifies a label. The advantages of breaking to a label are even greater if we are in a deeply nested series of loops (e.g., iterating over three-dimensional data).

Labels can be applied to loops, switch statements, and select statements. Both break and continue statements specify labels and can be used inside loops. It is also possible to use break statements—either bare or specifying a label—inside switch and select statements.

Labels can also appear as statements in their right in which they may be the targets of goto statements (using the syntax goto label). If a goto statement jumps past any statement that creates a variable, the Go program's behavior is undefined—if we are lucky it will crash, but probably it will continue to run and produce spurious results. One use for goto statements is when automatically generating code, since in this circumstance goto can be convenient and the concerns about spaghetti code not necessarily apply. Although, at the time of this writing, more than 30 of Go's source files use goto statements, none of the book's examples use the goto statement, and we advocate avoiding it.*

## 5.4. Communication and Concurrency Statements

Go's communication and concurrency features are covered in Chapter 7, but for completeness of our coverage of procedural programming we will describe its basic syntax here.

> * goto statements have been generally despised since Edsger Dijkstra's famous 1968 letter titled “Go-to statement considered harmful” (www.cs.utexas.edu/users/Ewd/ew2xx.PDF).

A goroutine is a function or method invocation that executes independently and concurrently in relation to any other goroutines in a program. Every Go program has at least one goroutine, the main goroutine in which the main package's main function executes. Goroutines are like lightweight threads or coroutines, in that they can be created in large numbers (whereas even small numbers of threads can consume a huge amount of resources). Goroutines all share the same address space, and Go providing primitives to allow data to be safely shared across goroutines. However, the recommended approach to concurrent Go programming is to communicate data, rather than share it.

A Go channel is a bidirectional or unidirectional communication pipe that can be used to communicate (i.e., send and receive) data between two or more goroutines.

Between them, goroutines and channels provide a means of lightweight (i.e., scalable) concurrency that does not use shared memory and so does not require locking. Nonetheless, as with all approaches to concurrency, care must be exercised when creating concurrent programs and maintenance is usually more challenging than non programs. Most operating systems are excellent at running multiple programs at the same time, so exploiting this can reduce maintenance—instance, by running multiple programs (multiple copies of the same program) each operating on different data. Good programmers write concurrent programs only when the approach has clear advantages that outweigh the increased burden.

```go
go function(arguments)
go func(parameters) { block }(arguments)
```

We either call an existing function or call an anonymous function created on the spot. The function may have zero or more parameters just like any other function, and if it has parameters, corresponding arguments must be passed the same as with any other function call.

Execution of the called function begins immediately—but in a separate goroutine—execution of the current goroutine (i.e., the one that has the go statement) resumes immediately from the next statement. So, after a go statement, there are at least two goroutines running, the original one (initially the main goroutine), and the newly created one.

In rare cases it is sufficient to start a bunch of goroutines and wait for them all to finish, with no communication necessary. In most situations, though, goroutines need to work cooperatively together, and this can best be achieved by giving them the ability to communicate. Here are the syntaxes used for sending and receiving data:

```go
channel <- // Blocking send
<-channel // Receive and discard
x := <-channel // Receive and store
x, ok := <-channel // // As above & check for channel closed & empty
```

Nonblocking sends are possible using the select statement, and to some extent using buffered channels.

Channels are created with the built-in make() function with these syntaxes:

```go
make(chan Type)
make(chan Type, capacity)
```

If no buffer capacity is specified the channel is synchronous, so it will block until the sender is ready to send and the receiver is ready to receive. If a capacity is given the channel is asynchronous and communication will progress without blocking so long as there is unused capacity for sends and there is data in the channel to be received.

Channels are bidirectional by default, but we can make them unidirectional if we want to—for to express our semantics in a way the compiler can enforce.

In some situations we may have multiple goroutines executing, each with its own communication channel. We can monitor their communications using a select statement.

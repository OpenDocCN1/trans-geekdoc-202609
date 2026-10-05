# 5.4. Communication and Concurrency Statements 211

The function is given some data to work on, and two channels. The answer channel is used to send each result to the monitoring code and the done channel is used to notify the monitoring code that the computation has finished.

```
// setup ...
const allDone = 2
doneCount := 0
answer := make(chan int)
answerbeta := make(chan int)
defer func() {
	close(answer)
	close(answerbeta)
}()
done := make(chan bool)
defer func() { close(done) }
go expensiveComputation(data, answer, done)
go expensiveComputation(data2, answerbeta, done)
for doneCount != allDone {
	var result int
	select {
	case result = <-answer:
		which = 'alpha'
	case result = <-answerbeta:
		which = 'beta'
	case <-done:
		doneCount++
	}
	if result != 0 {
		fmt.Printf("%s-%d\n", which, result)
	}
}
fmt.Println()
fmt.Println()
```

α-3 β-3 α-0 β-9 α-0 β-2 β-3 α-9 α-6 β-1 α-0 β-8 α-8 β-5 α-0 β-3 β-0 α-3

This is the code that sets up the channels, starts the expensive computations, monitors progress, and cleans up the end—there isn't a lock in sight.

We begin creating two channels to accept results, answer and answerbeta, and a channel to keep track of when the computations are finished. We create anonymous functions in which the channels are closed and can we defer in statements so that they will be closed when they are no longer needed, that is, when the enclosing function returns. Next, we start off the expensive computations (in their own goroutines), giving each one its own unique data to work on, and for communications, its own unique answer channel, and the done channel that is shared.
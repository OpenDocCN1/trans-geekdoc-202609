# 330 Chapter 7. Concurrent Programming

Although both of the actual channels passed into the function are bidirectional, we have specified both to be unidirectional send-only channels that is how the jobs channel is used inside the function and how the Job.results channel is defined in the struct.

```
func doJobs(done <-chan struct{}, lineRx *regexp.Regexp, jobs <-chan Job) {
	for job := range jobs {
		job.Do(lineRx)
	}
	done <- struct{}{}
}
```

This function is called four times in four separate goroutines, so there are four invocations to share the work. Each invocation iterates over the same shared jobs channel (declared as a receive-only channel), and is blocked the channel it is executing in) until a job becomes available for it to receive. Each job that an invocation gets to, the function calls the job's Job.Do() method (which we will review further on). When an invocation runs out of jobs it signifies that it has finished by sending an empty struct to the done channel (which is declared as a send-only channel).

Incidentally, it is a Go convention that functions have channel parameters the destination channels, followed by the source channels.

```
func awaitCompletion(done <-chan struct{}, results chan Result) {
	for i := 0; i < workers; i++ {
		--
	}
	close(results)
}
```

This function (along with the processResults() function) ensures that the goroutine waits until all the processing is done before terminating, avoiding the pitfalls mentioned in the previous section (§7.1, 317 ◄). It is executed in its own goroutine and waits for as many receives on the channel as there are workers—blocking its goroutine while it waits. The loop terminates the results channel closed so that the receiver knows when it has received the last result. Note that we cannot pass the results channel as a receive-only channel (<-chan Result), since Go disallows closing such channels. We don't bother closing the done channel since we never use it in a context where it is checked for being closed.

```
func processResults(results <-chan Result) {
	for result := range results {
		fmt.Printf("%s:%d:%s\n", result.filename, result.lino, result.line)
}
```
# 7.2. Examples 333

This is a variation of cgrep2, the difference being that we pass in a timeout value. The After() function takes a time.Duration value (essentially a number of nanoseconds), and returns a channel on which it returns the current time at least time.Duration nanoseconds have passed. Here, we have assigned the returned channel to finish variable and include a receive case for for select. If we get a timeout (i.e., if the finish channel sends a value), we return from the function and the program finishes, even if work is still being done.

If all the results are gathered before the timeout occurs (i.e., all the workers are done), for first loop is terminated and the for loop is the same as for cgrep2 example. The only differences are that instead of breaking out of the second loop, we simply define a return from the select's default case; we have included a timeout case.

Now that we have seen how the concurrency is handled, we will finish our coverage of the grep examples by reviewing how each job is processed.

```
func (job Job) Do(lineX *regexp.Regexp) {
tfile, err := os.Open(job.filename)
	if err != nil {
	log.Printf("error: %s\n", err)
	return
	}
	defer file.Close(file)
	reader := bufio.NewReader(file)
	for line := 1; line++ {
	line, err := reader.ReadBytes('\n')
	line = bytes.TrimRight(line, "\n\r")
	if lineRegex.Match(line) {
		job.results <- Result{job.filename, line, string(line)}
	}
	if err != nil {
		if err != io.EOF {
			log.Printf("error: %s\n", line, err)
		}
		break
	}
}
```

This method is used to process each file. It is passed a *regexp.Regexp, a pointer—unusually for a pointer—is thread-safe, so it doesn't matter how many goroutines make use of it. Practically all of the function should be familiar by now: We open the file for reading, handle any error, and if there is no error we defer closing the file. We create a buffered reader to make it easy
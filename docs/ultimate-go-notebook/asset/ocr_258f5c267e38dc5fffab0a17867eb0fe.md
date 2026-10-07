Now I have a stack trace of every Goroutine and register information. I can get a larger core dump by using the GOTRACEBACK variable with the crash option when running the program.

# Listing 13.16

```
$ GOTRACEBACK=crash ./example3
```

This will provide stack traces for the runtime Goroutines, like the netpoller and scavenger.
```
// The background() helper accepts an arbitrary function as a parameter.
func (app *application) background(fn func()) {
    // Launch a background goroutine.
    go func() {
        // Recover any panic.
        defer func() {
            if err := recover(); err != nil {
                app.logger.PrintError(fmt.Errorf("%s", err), nil)
            }
        }()
        // Execute the arbitrary function that we passed as the parameter.
        fn()
    }()
}
```

This background() helper leverages the fact that Go has first-class functions, which means that functions can be *assigned to variables* and *passed as parameters* to other functions.

In this case, we’ve set up the background() helper so that accepts any function with the signature func() as a parameter and stores it in the variable fn. It then spins up a background goroutine, uses a deferred function to recover any panics and log the error, and then executes the function itself by calling fn().

Now that this is in place, let’s update our registerUserHandler to use it like so:

File: cmd/api/users.go
# 12.4. WRITING AND ORGANIZING VALIDATION CODE 373

```
type userValFn func(*User) error
```

Function types are similar to struct and interface types, except they define a function format. What we are saying with the code we just wrote is that a userValFn is any function that accepts a pointer to a User and returns an error.

That means that all of our validation functions are going to need to accept a User pointer, whatever work is necessary, and then return nil if no errors were encountered, or an error something went wrong during the validation.

# What's the point? Why do we want a single format for our validation functions?

The upside to using this standardized approach is that we can now define a function that runs all of our validations sequentially, stopping and returning any errors encountered along the way. Once we have written this, it will make it easier to start adding new validators to our code without needing to check one individually for others.

```
func runUserValFns (user *User, fns ...userValFn) error {
  for _, fn := range fns {
    if err := fn(user); err != nil {
      return err
    }
  }
  return nil
}
```

The runUserValFns accepts a pointer to a user and any number of validation functions as its arguments, and then it iterates over each validation function using a range. As it iterates over each function, it calls that validation function passing in the user as the argument, and capturing the error return value.

If the return value turns out to be nil, it means we didn't receive an error and we
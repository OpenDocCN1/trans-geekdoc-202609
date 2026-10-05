# CHAPTER 16. DEPLOYING TO PRODUCTION

Note: We will discuss the JSON tags on the Config type in an upcoming section, but have added them here so they are available.

Instead of passing a config filled with data options, functional options allow us to provide a series of functions that will help us build our services. For example, if we wanted to add a UserService to our Services object, we might write the following code:

```
// WithUser accepts pepper and hmacKey as arguments, then
// returns a function as its return value. The function that it
// returns is one that accepts a Services pointer as its
// only argument and returns an error.
func WithUser(pepper, hmacKey string) func(*Services) error {
	return func(s *Services) error {
		Our NewUserService doesn't match this definition yet
		s.User = NewUserService(s.db, pepper, hmacKey)
		return nil
	}
```

Note: We will eventually write this function and use it in our code, but it will be presented again at that time.

This is very similar to what we did when we built out our validation code; most notably when we created the idGreaterThan validation. We are creating a new function that uses some of the data passed into the first function. This is often referred to as a closure.

But what does this get us? Think back on when we wrote our runValFns function; by creating a function that accepted many functions, we were able to easily iterate over all of the functions and run them sequentially without caring about what each individual function did. All we knew that those functions were validating our data and returning an error if there was an issue.

When using functional options to build our Services object we can do something similar. We can write a NewServices function that accepts a list of functions intended to build the Services object, but we don't have to worry about how they are building. We just need to run each function in the order
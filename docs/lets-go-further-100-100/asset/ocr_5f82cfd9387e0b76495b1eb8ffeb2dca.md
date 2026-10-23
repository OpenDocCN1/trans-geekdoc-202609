# Additional Information

# Panicking vs returning errors

The decision to panic in the `readJSON()` helper if we get a `json.InvalidUnmarshalError` error isn’t taken lightly. As you’re probably aware, it’s generally considered best practice in Go to return your errors and handle them gracefully.

But — *in some specific circumstances* — it can be OK to panic. And you shouldn’t be too dogmatic about *not panicking* when it makes sense to.

It’s helpful here to distinguish between the two classes of error that your application might encounter.

The first class of errors are *expected errors* that may occur during normal operation. Some examples of expected errors are those caused by a database query timeout, a network resource being unavailable, or bad user input. These errors don’t necessarily mean there is a problem with your program itself — in fact they’re often caused by things outside the control of your program. Almost all of the time it’s good practice to return these kinds of errors and handle them gracefully.

The other class of errors are *unexpected errors*. These are errors which should not happen during normal operation, and if they do it is probably the result of a developer mistake or a logical error in your codebase. These errors are truly exceptional, and using panic in these circumstances is more widely accepted. In fact, the Go
If the type does satisfy the interface, then Go will call its `MarshalJSON()` method and use the `[]byte` slice that it returns as the encoded JSON value.

If the type doesn’t have a `MarshalJSON()` method, then Go will fall back to trying to encode it to JSON based on its own internal set of rules.

So, if we want to customize how something is encoded, all we need to do is implement a `MarshalJSON()` method on it which returns a *custom JSON representation of itself* in a `[]byte` slice.

> **Hint:** You can see this in action if you look at the source code for Go’s `time.Time` type. Behind the scenes `time.Time` is actually a `struct`, but it has a `MarshalJSON()` method which outputs a RFC 3339 format representation of itself. This is what gets called whenever a `time.Time` value is encoded to JSON.

# Customizing the Runtime field

To help illustrate this, let’s look at a concrete example in our application.

When our `Movie` struct is encoded to JSON, the `Runtime` field (which is an `int32` type) is currently formatted as a JSON number. Let’s change this so that it’s encoded as a string with the format `"<runtime> mins"` instead. Like so:
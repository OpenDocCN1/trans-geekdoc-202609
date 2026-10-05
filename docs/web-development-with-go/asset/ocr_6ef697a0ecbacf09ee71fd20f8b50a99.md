# 12.1. SEPARATING RESPONSIBILITIES

```
type Dog struct {}
func (d Dog) Speak() string {
	return "woof"
}
```

In order to chain this, we would simply need to create a second Speaker that is meant to wrap an existing speaker and create a chain.

```
type PrefixSpeaker struct {
	s Speaker
}
func (ps PrefixSpeaker) Speak() {
	return "prefix: " + ps.s.Speak()
}
```

With this we now create a chaining effect where we wrap a Dog with a PrefixSpeaker which would add a prefix to any strings returned by the Speak method.

```
speaker := PrefixSpeaker{
	s: Dog(),
}
// This prints out "prefix: woof"
fmt.Println(speaker.Speak())
```

What is happening that our initial call to the Speak method calls the PrefixSpeaker's method, but inside of this the Dog type's Speak method is called, causing a sort of chain of method calls.

While our example is trivial, method chaining can be very powerful in Go. It is used extensively in packages like io and net/http, and we will be using it later in this course to create middleware that verifies a user is logged in and has permission to access a gallery before calling the controller to render gallery.
To hear more about interface chaining, check out this talk by Francesc Campoy - https://www.youtube.com/watch?v=F4wUrj6pmSI&feature=youtu.be&t=1337

# **Box 12.3. Embedding interfaces**

Related to interface chaining is embedding. There are two types of embedding in Go - embedding interfaces embedding fields in a struct. You can read more about both of these in Effective Go - https://golang.org/doc/effective_go.html#embedding.

What we are going to discuss in this section revolves around embedding fields inside of a struct. Specifically, we are going to look at embedding an field with an interface type inside of a struct.

```
type Speaker interface {
  Speak() string
}
type DemoSpeaker struct {
  // Speaker is embedded in the DemoSpeaker
  Speaker
}
```

Embedding is occurring here because we didn't define a field name for the Speaker field. Instead, the field name is defaulted to the same name as the type. That means right now if we had a DemoSpeaker instance, the following two lines of code would effectively be the same.

```
demoSpeaker.Speak()
demoSpeaker.Speaker.Speak()
```
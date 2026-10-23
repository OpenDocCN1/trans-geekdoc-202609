# Advanced JSON Customization

By using struct tags, adding whitespace and enveloping the data, we’ve been able to add quite a lot of customization to our JSON responses already. But what happens when these things aren’t enough, and you need the freedom to customize your JSON even more?

To answer this question, we first need to talk some theory about how Go handles JSON encoding behind the scenes. The key thing to understand is this:

> *When Go is encoding a particular type to JSON, it looks to see if the type has a `MarshalJSON()` method implemented on it. If it has, then Go will call this method to determine how to encode it.*

That language is a bit fuzzy, so let’s be more exact.

Strictly speaking, when Go is encoding a particular type to JSON it looks to see if the type satisfies the `json.Marshaler` interface, which looks like this:

```
type Marshaler interface {
    MarshalJSON() ([]byte, error)
}
```
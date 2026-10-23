# Additional Information

# Supported destination types

It’s important to mention that certain JSON types can be only be successfully decoded to certain Go types. For example, if you have the JSON string `"foo"` it can be decoded into a Go `string`, but trying to decode it into a Go `int` or `bool` will result in an error at runtime (as we’ll demonstrate in the next chapter).

The following table shows the supported target decode destinations for the different JSON types:

| JSON type | ⇒ | Supported Go types |
|---|---|---|
| JSON boolean | ⇒ | bool |
| JSON string | ⇒ | string |
| JSON number | ⇒ | int*, uint*, float*, rune |
| JSON array | ⇒ | array, slice |
| JSON object | ⇒ | struct, map |

# Using the json.Unmarshal function

As we mentioned at the start of this chapter, it’s also possible to use the `json.Unmarshal()` function to decode a HTTP request body.

For example, you could use it in a handler like this:
The omitempty struct tag directive never considers a struct to be empty — even if all the struct fields have their zero value and you use omitempty on those fields too. It will always appear as an object in the encoded JSON. For example, the following struct:

```
```go
s := struct {
    Foo struct {
        Bar string `json:",omitempty"`
    } `json:",omitempty"`
}{}
```
```

Will encode to the JSON:

```
```json
{"Foo":{}}
```
```

There’s a long-standing proposal which discusses changing this behavior, but the Go 1 compatibility promise means that it’s unlikely to happen any time soon. Instead, you can get around this by making the field a pointer to a struct, which works because omitempty considers nil pointers to be empty. For example:

```
```go
s := struct {
    Foo *struct {
        Bar string `json:",omitempty"`
    } `json:",omitempty"`
}{}
```
```
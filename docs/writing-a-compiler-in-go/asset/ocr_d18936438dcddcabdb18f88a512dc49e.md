```
```go
args[0].Type()
    }
  },
  },
},
}

func newError(format string, a ...interface{}) *Error {
    return &Error{Message: fmt.Sprintf(format, a...)}
}
```
```

Builtins is a slice of structs, where each struct contains the name and the *Builtin function itself.

While we did copy the *Builtin with the name len, please note that this is not mindless copy and pasting: in the *Builtin itself we had to remove references to the object package. They’re redundant now that we’re in object.

The newError function we also had to copy over since it’s heavily used by most of the built-in functions.

With Builtins defined and containing its first definition, we can now add a function called GetBuiltinByName:

```
```go
// object/builtins.go

func GetBuiltinByName(name string) *Builtin {
    for _, def := range Builtins {
        if def.Name == name {
            return def.Builtin
        }
    }
    return nil
}
```
```

There’s not much to explain here. It’s a function that allows us to fetch a built-in function by name. But with this in place, we can get rid of the duplication in evaluator/builtins.go and replace the old definition of len with this:

```
```go
// evaluator/builtins.go

var builtins = map[string]*object.Builtin{
    "len": object.GetBuiltinByName("len"),
    // [...]
}
```
```

That’s our first built-in function moved. Congratulations! And, look at that, the tests of the evaluator package are still working:
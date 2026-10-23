And then we define push, which adds an element to an array. It doesn’t mutate the array, but instead leaves it untouched and allocates a new one, containing the elements of the original array and the addition:

```
// object/builtins.go

var Builtins = []struct {
    Name     string
    Builtin  *Builtin
}{}
    // [...]
    {
        "push",
        &Builtin{Fn: func(args ...Object) Object {
            if len(args) != 2 {
                return newError("wrong number of arguments. got=%d, want=2", len(args))
            }
            if args[0].Type() != ARRAY_OBJ {
                return newError("argument to `push` must be ARRAY, got %s", args[0].Type())
            }

            arr := args[0].(*Array)
            length := len(arr.Elements)

            newElements := make([]Object, length+1, length+1)
            copy(newElements, arr.Elements)
            newElements[length] = args[1]

            return &Array{Elements: newElements}
        },
    },
},
```

And that was the last of the built-in functions we set out to implement. All of them are now defined in object.Builtins, stripped free of redundant references to the object package and making no mention of evaluator.NULL.

Now we can go back to evaluator/builtins.go and replace all of the currently-duplicated definitions with calls to object.GetBuiltinByName:

```
// evaluator/builtins.go

import (
    "monkey/object"
)

var builtins = map[string]*object.Builtin{
    "len":   object.GetBuiltinByName("len"),
    "puts":  object.GetBuiltinByName("puts"),
    "first": object.GetBuiltinByName("first"),
```
```
freeSymbols := c.symbolTable.FreeSymbols
numLocals := c.symbolTable.numDefinitions
instructions := c.leaveScope()

for _, s := range freeSymbols {
    c.loadSymbol(s)
}

compiledFn := &object.CompiledFunction{
    Instructions: instructions,
    NumLocals:    numLocals,
    NumParameters: len(node.Parameters),
}

fnIndex := c.addConstant(compiledFn)
c.emit(code.OpClosure, fnIndex, len(freeSymbols))

// [...] 
}

// [...] 
}
```

A lot of this is just presented here to give you context for the changes, which are only five lines of code.

The first new line is the assignment of freeSymbols. It’s important that this happens before we call c.leaveScope(). Then, after we left the scope, we iterate through the freeSymbols in a loop and c.loadSymbol each.

The len(freeSymbols) is then used as the second operand to the OpClosure instruction. After the c.loadSymbol calls, the free variables sit on the stack waiting to be merged with an *object.CompiledFunction into an *object.Closure.

Five lines that give us a lot:

```
$ go test ./compiler
ok      monkey/compiler 0.008s
```

Would you look at that! We are successfully compiling closures! Compile time, check. Now we need to take care of the run time, which is when the magic of closures emerges.
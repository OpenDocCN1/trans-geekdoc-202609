```
c.enterScope()

err := c.Compile(node.Body)
if err != nil {
    return err
}

instructions := c.leaveScope()

compiledFn := &object.CompiledFunction{Instructions: instructions}
c.emit(code.OpConstant, c.addConstant(compiledFn))

// [...] 
}

// [...] 
}
```

This snippet of code revolves around one idea: change where emitted instructions are stored when compiling a function.

So, when we come across an *ast.FunctionLiteral the first thing we do is enter a new scope by calling c.enterScope. Then we compile the node.Body, the AST nodes making up the function’s body. After that, we take the just-filled slice of instructions off the stack of CompilationScopes by calling c.leaveScope, create a new *object.CompiledFunction that holds these instructions, and add that function to the constant pool.

# Done, function compiled:

```
$ go test ./compiler
--- FAIL: TestFunctions (0.00s)
compiler_test.go:654: testInstructions failed: wrong instruction at 2.
    want="0000 OpConstant 2\n0003 OpPop\n"
    got ="0000 OpConstant 0\n0003 OpPop\n"
FAIL
FAIL    monkey/compiler 0.008s
```

Oh, well. It turns out that we do know how to compile function literals, but we don’t know how to compile *ast.ReturnStatements. And since the body of the function in the test is nothing more than a single return statement, we do not compile anything of that function. We only create an *object.CompiledFunction constant with no instructions.

Our testing infrastructure is just not advanced enough to point us to the origin of the problem with a precise error message. You can trust me, though, I’ve done the digging for both of us.
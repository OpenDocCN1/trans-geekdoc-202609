is enough to advance it past both operands, we still put a symbolic and absolutely useless ReadUint8 in place, to show us where we will later decode the second operand. The _ is a little reminder that we still have work to do.

We then pass the first operand, constIndex, to the new pushClosure method, which in turn takes care of finding the specified function in the constants, turns it into an *object.Closure and puts it on the stack. There it can be passed around or called, just like *object.CompiledFunctions before, which is to say that it did the trick:

```
$ go test ./vm
ok      monkey/vm   0.051s
```

Now, everything’s a closure. Time to add closures.
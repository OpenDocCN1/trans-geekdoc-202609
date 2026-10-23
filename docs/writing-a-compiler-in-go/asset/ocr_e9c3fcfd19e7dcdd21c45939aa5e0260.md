```
$ go test ./vm
ok	monkey/vm	0.035s
```

The stack will hold, even if we call a function with the wrong number of arguments.

Now we can enjoy the fact that we’ve implement functions and function calls in a bytecode compiler and VM, including arguments and local bindings. That’s certainly no small feat and puts us, again, in another league:

```
$ go build -0 monkey . && ./monkey
Hello mrnugget! This is the Monkey programming language!
Feel free to type in commands
>> let one = fn() { 1; };
CompiledFunction[0xc42008a8d0]
>> let two = fn() { let result = one(); return result + result; };
CompiledFunction[0xc42008aba0]
>> let three = fn(two) { two() + 1; };
CompiledFunction[0xc42008ae40]
>> three(two);
3
```

Time to add another type of function.
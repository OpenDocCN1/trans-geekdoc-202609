If the value is truthy we do nothing and start another iteration of the main loop.
The result is that we’re executing the consequence of the conditional, which is
made up of the instructions right after the `OpJumpNotTruthy` instruction.

And now, open a `drumroll.wav` of your choice in your favorite audio player,
pour your preferred beverage, hit play and watch this:

```
~~~text
$ go test ./vm
ok      monkey/vm   0.009s
~~~
```

We did it. Yes, we did it! Our bytecode compiler and VM are now able to
compile and execute Monkey conditionals!

```
~~~text
$ go build -o monkey . && ./monkey
Hello mrnugget! This is the Monkey programming language!
Feel free to type in commands
>> if (10 > 5) { 10; } else { 12; }
10
>> if (5 > 10) { 10; } else { 12; }
12
>>
~~~
```

This is the point where we went from “well, this is toy, isn’t it?” to “oh wow,
we’re getting somewhere!”. Stack arithmetic is one thing, but jump instructions
are another. We’re in the big leagues now. Except…

```
~~~text
>> if (false) { 10; }
panic: runtime error: index out of range

goroutine 1 [running]:
monkey/vm.(*VM).pop(...)
    /Users/mrnugget/code/04/src/monkey/vm/vm.go:117
monkey/vm.(*VM).Run(0xc42005be48, 0x800, 0x800)
    /Users/mrnugget/code/04/src/monkey/vm/vm.go:60 +0x40e
monkey/repl.Start(0x10f1080, 0xc42000e010, 0x10f10a0, 0xc42000e018)
    /Users/mrnugget/code/04/src/monkey/repl/repl.go:43 +0x47a
main.main()
    /Users/mrnugget/code/04/src/monkey/main.go:18 +0x107
~~~
```

We forgot something.
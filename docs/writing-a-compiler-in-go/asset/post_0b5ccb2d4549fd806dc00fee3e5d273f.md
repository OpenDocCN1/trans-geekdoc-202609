
## Executing Jumps

Before we wrote the compiler tests for conditionals, we really had to think through what we want them to say and what we want the compiler to do. That’s not the case now, when writing the same tests for the VM. We already know how conditionals in Monkey are supposed to work and can cleanly express that in test cases and assertions:

```
// vm/vm_test.go
```

```
func TestConditionals(t *testing.T) {
	tests := []vmTestCase{
		{"if (true) { 10 }", 10},
		{"if (true) { 10 } else { 20 }", 10},
		{"if (false) { 10 } else { 20 }", 20},
		{"if (1) { 10 }", 10},
		{"if (1 < 2) { 10 }", 10},
		{"if (1 < 2) { 10 } else { 20 }", 10},
		{"if (1 > 2) { 10 } else { 20 }", 20},
	}

	runVmTests(t, tests)
}
```

Half of these test cases would’ve been enough. But they’re easy to write, expressive, neat and cost us basically nothing! It also doesn’t hurt us to be abundantly clear about what we want.

We test whether boolean expressions are correctly evaluated by the VM according to Monkey’s “truthy” standards and that the correct branch of the conditional is taken. Since conditionals are expressions that produce values, they allow us to infer which branch was executed by testing for the produced value of the whole conditional.

As neat as the tests are, the error message they produce is nasty:

```
$ go test ./vm
--- FAIL: TestConditionals (0.00s)
panic: runtime error: index out of range [recovered]
    panic: runtime error: index out of range

goroutine 20 [running]:
testing.tRunner.func1(0xc4200bc2d0)
/usr/local/go/src/testing/testing.go:742 +0x29d
panic(0x11190e0, 0x11f1fd0)
/usr/local/go/src/runtime/panic.go:502 +0x229
```

```
/monkey/vm.(*VM).Run(0xc420050e38, 0x800, 0x800)
/Users/mrnugget/code/04/src/monkey/vm/vm.go:46 +0x39c
monkey/vm.runVmTests(0xc4200bc2d0, 0xc420079e88, 0x7, 0x7)
/Users/mrnugget/code/04/src/monkey/vm/vm_test.go:101 +0x35a
monkey/vm.TestConditionals(0xc4200bc2d0)
/Users/mrnugget/code/04/src/monkey/vm/vm_test.go:80 +0x114
testing.tRunner(0xc4200bc2d0, 0x1149b40)
/usr/local/go/src/testing/testing.go:777 +0xd0
created by testing.(*T).Run
/usr/local/go/src/testing/testing.go:824 +0x2e0
FAIL monkey/vm 0.011s
```

Ugh. Not even an error, but a panic.

Before you dive into the code, though, and try to figure out where the error originates, let me explain: the VM is tripping over the bytecode because it contains opcodes it doesn’t know how to decode. That in itself shouldn’t be a problem, because unknown opcodes are skipped, but not necessarily their operands. Operands are just integers, remember, and might have the same value as an encoded opcode, which might lead the VM to treat them as such. That’s wrong, of course. It’s time we introduce our VM to our jump instructions.

We’ll start with OpJump, because it’s the most straightforward jump instruction we have. It has one 16 bit operand that’s the offset of the instruction the VM should jump to. That’s all we need to know to implement it:

```
```go
// vm/vm.go

func (vm *VM) Run() error {
  // [ ... ]
  switch op {
    // [ ... ]

case code.OpJump:
  pos := int(code.ReadInt16(vm.instructions[ip+1:]))
  ip = pos - 1

// [ ... ]
}
// [ ... ]
```
```

We use code.ReadInt16 to decode the operand located right after the opcode. That’s step 1. Step 2 is to set the instruction pointer, ip, to the target of our jump. Here’s where we come across one interesting implementation detail: since we’re in a loop that increments ip with each iteration we need to set ip to the offset right before the one we want. That lets the loop do its work and ip gets set to the value we want in the next cycle.

Solely implementing `OpJump` doesn’t buy us much though, since it’s `OpJumpNotTruthy` that’s integral to the implementation of conditionals. But while adding a case branch for `code.OpJumpNotTruthy` does take slightly more code, it’s not much more complicated:

```
```go
// vm/vm.go

func (vm *VM) Run() error {
    for ip := 0; ip < len(vm.instructions); ip++ {
        op := code.Opcode(vm.instructions[ip])

        switch op {
        // [...]

        case code.OpJumpNotTruthy:
            pos := int(code.ReadUint16(vm.instructions[ip+1:]))
            ip += 2

            condition := vm.pop()
            if !isTruthy(condition) {
                ip = pos - 1
            }

        // [...]
        }
    }
    // [...]
}

func isTruthy(obj object.Object) bool {
    switch obj := obj.(type) {

    case *object.Boolean:
        return obj.Value

    default:
        return true
    }
}
```
```

We again use `code.ReadUint16` to read in and decode the operand. After that we manually increase `ip` by two so we correctly skip over the two bytes of the operand in the next cycle. That’s not a new – we’ve already done that when executing `OpConstant` instructions.

What’s new is the rest. We pop off the topmost stack element and check if it’s truthy with the helper function `isTruthy`. If it’s *not* truthy, we jump, which means that we set `ip` to the index of the instruction right before the target, letting the for-loop do its work.

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

## Welcome Back, Null!

At the start of this chapter we looked back at our implementation of conditionals in *Writing An Interpreter In Go*, and now we have implemented the majority of its behaviour. But there’s one thing we’re still missing: what happens when the condition of a conditional is *not* truthy but the conditional itself has no alternative? In the previous book the answer to this question was `*object.Null`, Monkey’s null value.

That makes sense, because conditionals are expressions and expressions, by definition, produce values. So what does an expression that produced nothing evaluate to? Null. Wait, let me try that again, only this time imagine a *big organ sound* in the background, *crows flying overhead, screeching, thunder*: They… *lightning strikes…* evaluate to … *sirens* … null.

Look, null and I, we’re not the best of friends. I’m not really sure what to think of it, whether it’s good or bad. It’s the cause of many curses but I do understand that there are languages in which some things evaluate to nothing and that “nothing” has to be represented somehow. In Monkey, conditionals with a false condition and no alternative are one of these things, and “nothing” is represented by `*object.Null`. Long story short: it’s time we introduce `*object.Null` to our compiler and VM and make this type of conditional work properly.

The first thing we need is a definition of `*object.Null` in our VM. Since its value is constant, we can define it as a global variable, just like our previous global definitions of `vm.True` and `vm.False`:

```
// vm/vm.go

var Null = &object.Null{}
```

This is also similar to `vm.True` and `vm.False` in that it saves us a lot of work when comparing Monkey objects. We can simply check if an `object.Object` is `*object.Null` by checking whether it’s equal to `vm.Null`. We do not have to unwrap it and take a look at its value.

The reason why we first defined `vm.Null`, before writing any compiler tests — our usual course of action — is that this time we want do write a VM test first. And that’s because the VM tests allow us to express what we want so succinctly:

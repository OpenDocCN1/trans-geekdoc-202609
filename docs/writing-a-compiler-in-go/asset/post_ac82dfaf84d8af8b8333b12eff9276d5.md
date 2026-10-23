
}

This thing runs like clockwork:

```
$ go test ./vm
ok      monkey/vm   0.039s
```

We can even be meticulous and add a test for explicit return statements. We already know that these compile down to the same instructions we just successfully executed, but adding it will give us much better feedback should something go wrong in the future:

```
// vm/vm_test.go

func TestFunctionsWithReturnStatement(t *testing.T) {
    tests := []vmTestCase{
        {
            input: `
let earlyExit = fn() { return 99; 100; };
earlyExit();
`,
            expected: 99,
        },
        {
            input: `
let earlyExit = fn() { return 99; return 100; };
earlyExit();
`,
            expected: 99,
        }
    }

    runVmTests(t, tests)
}
```

Even that runs without any hiccups:

```
$ go test ./vm
ok      monkey/vm   0.032s
```

Holy opcode! We’re compiling function calls to bytecode and have our own call stack in our bytecode VM and it all works! It’s high time for a nice round of patting ourselves on the back and to sit back and take a deep breath.

But since we’re here…

## It’s Not Nothing, It’s Null

Before we move on, we need to take care of the OpReturn opcode. In the compiler we already made sure that empty functions compile to a single opcode: OpReturn. We also decided that calling these functions should put vm.Null on the VM’s stack and now is the time to implement that.

Thankfully, this last paragraph is a straightforward definition of the desired behaviour and can be rewritten as a test:

```
// vm/vm_test.go

func TestFunctionsWithoutReturnValue(t *testing.T) {
    tests := []vmTestCase{
        {
            input: `
let noReturn = fn() { };
noReturn();
`,
            expected: Null,
        },
        {
            input: `
let noReturn = fn() { };
let noReturnTwo = fn() { noReturn(); };
noReturn();
noReturnTwo();
`,
            expected: Null,
        },
    }

    runVmTests(t, tests)
}
```

Clueless as our VM is about OpReturn, it doesn’t put vm.Null on the stack:

```
$ go test ./vm
--- FAIL: TestFunctionsWithoutReturnValue (0.00s)
vm_test.go:546: object is not Null: <nil> (<nil>)
vm_test.go:546: object is not Null: <nil> (<nil>)
FAIL
FAIL    monkey/vm    0.037s
```

What do we have to do to fix these test cases? We already know how to return from a function and we even know how to return with a value. Now we have to do less:

```
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...]
case code.OpReturn:
    vm.popFrame()
    vm.pop()

    err := vm.push(Null)
    if err != nil {
        return err
    }

    // [...]
}
// [...]
}
```

Pop the frame, pop the called function, push Null. Done:

```
$ go test ./vm
ok      monkey/vm   0.038s
```

### A Little Bonus

Here’s a little treat. In this section, we did more than reach the milestone of compiling and executing the snippet we set out to get working. We also — without making it a goal or even thinking about it — managed to implement the best thing since REPLs and fast unit tests: first-class functions. Yes, the compiler and VM are already capable of compiling and executing the following piece of Monkey code:

```
let returnsOne = fn() { 1; };
let returnsOneReturner = fn() { returnsOne; };
returnsOneReturner()();
```

Don’t believe me? Well, no need, I’m willing to bet a test case on it:

```
// vm/vm_test.go

func TestFirstClassFunctions(t *testing.T) {
    tests := []vmTestCase{
        {
            input:
                `let returnsOne = fn() { 1; };
let returnsOneReturner = fn() { returnsOne; };
returnsOneReturner()();
`,
            expected: 1,
        },
    }

    runVmTests(t, tests)
}
```

Here’s what we achieved without even intending to:

```
$ go test ./vm
ok    monkey/vm    0.038s
```

If it wouldn’t be us patting ourselves shamelessly on our backs, I’d say that’s a note as high as you can end a section on.

## Local Bindings

Our current implementation of functions and function calls does not support local bindings. We do support bindings, but only global ones. Local bindings are different in a crucial detail, in that they are *local to a function*, meaning that they are only visible and accessible within the scope of a function. This detail is crucial because it ties the implementation of local bindings to the implementation of functions. And since we did a great job with the second one, we’re now ready to approach the first one.

At the end of this section we want to have this piece of Monkey code working:

```monkey
let globalSeed = 50;
let minusOne = fn() {
  let num = 1;
  globalSeed - num;
}
let minusTwo = fn() {
  let num = 2;
  globalSeed - num;
}
minusOne() + minusTwo()
```

What we have here is a mixture of global and local bindings. `globalSeed` is a global binding that can be accessed in nested scopes, like the `minusOne` and `minusTwo` functions. Then we also have the local binding `num`, showing up in both functions. Important about `num` is that it’s not accessible outside these functions and that both bindings of `num` in each function are unique and don’t overwrite each other.

In order to get this piece of code compiled and executed, we need to do a few different things.

First of all, we need to define opcodes that tell the VM to create local binding and to retrieve them. I bet you guessed as much.

Then we need to extend the compiler so it can output these new opcodes correctly. That means, it needs to distinguish between local bindings and global bindings, and also between local bindings with the same name in different functions.

The last step is to implement these new instructions and local bindings in the VM. We already know how to store and access global bindings and that knowledge won’t be wasted, since the main mechanism behind bindings won’t change. But for local bindings we need a new store.

As always, we’ll take small steps and start at the beginning.

### Opcodes for Local Bindings

We already have two opcodes for bindings in place: OpSetGlobal and OpGetGlobal. Now we need equivalents for local bindings. We don’t even need to be creative here, we’ll just create “local versions” of the global ones and call them OpSetLocal and OpGetLocal. They’ll also, just like the global ones, have one operand each, a unique index for the local binding in question.

The naming doesn’t play a huge role, as you know, because it’s just bytes underneath. The important bit is that these opcodes are distinct from the global ones. They should tell VM that the binding is local to the currently executing function and that it should have absolutely no effect on global bindings. The binding shouldn’t overwrite a global binding and it itself shouldn’t be overwritten by one.

And since defining opcodes is a rather dull task, we’ll treat ourselves to a little flourish: instead of giving these new opcodes the two-byte operand their global cousins have, we’ll use one byte, which we haven’t had before. And besides that, 256 local bindings per function should surely be enough for the average Monkey program, right?

Here are the definitions:

```
// code/code.go

const (
    // [...] 
    OpGetLocal
    OpSetLocal
)

var definitions = map[Opcode]*Definition{
    // [...] 
    OpGetLocal: {"OpGetLocal", []int{1}},
    OpSetLocal: {"OpSetLocal", []int{1}},
}
```

Nothing surprising here, only the one-byte operands are new. That means we need to make sure our existing tooling can handle them:

```
// code/code_test.go

func TestMake(t *testing.T) {
    tests := []struct {
        op         Opcode
        operands   []int
        expected   []byte
    }{
        // [...] 
        {OpGetLocal, []int{255}, []byte{byte(OpGetLocal), 255}},
    }

    // [...] 
}
```

Rightfully, Make is stumped by the one byte:

```
$ go test ./code
--- FAIL: TestMake (0.00s)
    code_test.go:26: wrong byte at pos 1. want=255, got=0
FAIL
FAIL    monkey/code 0.007s
```

Getting Make to work means extending its switch statement, which I promised you to do since it’s been introduced:

```
// code/code.go

func Make(op Opcode, operands ...int) []byte {
    // [...] 

    offset := 1
    for i, o := range operands {
        width := def.OperandWidths[i]
        switch width {
        case 2:
            binary.BigEndian.PutUint16(instruction[offset:], uint16(o))
        case 1:
            instruction[offset] = byte(o)
        }
        offset += width
    }

    return instruction
}
```

The added case 1 branch is enough to get it working, since there’s only one way to sort a single byte:

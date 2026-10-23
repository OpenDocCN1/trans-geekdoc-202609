
// compiler/compiler.go

func (c *Compiler) Compile(node ast.Node) error {
    switch node := node.(type) {
        // [...] 
        case *ast.Boolean:
            if node.Value {
                c.emit(code.OpTrue)
            } else {
                c.emit(code.OpFalse)
            }
        // [...] 
    }
    // [...] 
}
```

Yep, that did it, alright:

```
$ go test ./compiler
ok      monkey/compiler 0.008s
```

The next step is to tell the VM about true and false. And just like in the compiler package we now create a second test function:

```
// vm/vm_test.go

func TestBooleanExpressions(t *testing.T) {
    tests := []vmTestCase{
        {"true", true},
        {"false", false},
    }
    
    runVmTests(t, tests)
}
```

This test function is very similar to the first one, TestIntegerArithmetic. But since we now have a bool as our expectation here, we need to update the testExpectedObject function used by runVmTests and provide it with a new helper function called testBooleanObject:

```
// vm/vm_test.go

func testExpectedObject(
    t *testing.T,
    expected interface{},
    actual object.Object,
) {
    t.Helper()
```

```
switch expected := expected.(type) {
    // [...] 
    case bool:
        err := testBooleanObject(bool(expected), actual)
        if err != nil {
            t.Errorf("testBooleanObject failed: %s", err)
        }
    }
}
```

```
func testBooleanObject(expected bool, actual object.Object) error {
    result, ok := actual.(*object.Boolean)
    if !ok {
        return fmt.Errorf("object is not Boolean. got=%T (%v)",
            actual, actual)
    }

    if result.Value != expected {
        return fmt.Errorf("object has wrong value. got=%t, want=%t",
            result.Value, expected)
    }

    return nil
}
```

testBooleanObject is testIntegerObject’s counterpart and not the most fascinating of functions, but we’ll get a lot of use out of it, that’s for sure. What is noteworthy is that our VM tests now blow up:

```
$ go test ./vm
--- FAIL: TestBooleanExpressions (0.00s)
panic: runtime error: index out of range [recovered]
panic: runtime error: index out of range

goroutine 19 [running]:
testing.tRunner.func1(0xc4200ba1e0)
/usr/local/go/src/testing/testing.go:742 +0x29d
panic(0x1116f20, 0x11eefc0)
/usr/local/go/src/runtime/panic.go:502 +0x229
monkey/vm.(*VM).pop(...)
/Users/mrnugget/code/02/src/monkey/vm/vm.go:74
monkey/vm.(*VM).Run(0xc42050ed8, 0x800, 0x800)
/Users/mrnugget/code/02/src/monkey/vm/vm.go:49 +0x16f
monkey/vm.runVmTests(0xc4200ba1e0, 0xc420079f58, 0x2, 0x2)
/Users/mrnugget/code/02/src/monkey/vm/vm_test.go:60 +0x35a
monkey/vm.TestBooleanExpressions(0xc4200ba1e0)
/Users/mrnugget/code/02/src/monkey/vm/vm_test.go:39 +0xa0
testing.tRunner(0xc4200ba1e0, 0x11476d0)
/usr/local/go/src/testing/testing.go:777 +0xd0
created by testing.(*T).Run
/usr/local/go/src/testing/testing.go:824 +0x2e0
FAIL    monkey/vm  0.011s
```

It blows up because we’re so tidy and issue an OpPop after every expression

statement to keep the stack clean. And when we try to pop something off the stack without first putting something on it, we get an index out of range panic.

The first step towards fixing this is to tell our VM about true and false and defining global True and False instances of them:

```
// vm/vm.go

var True = &object.Boolean{Value: true}
var False = &object.Boolean{Value: false}
```

The reasons for reusing global instances of the *object.Booleans are the same as in our evaluator package. First, these are immutable, unique values. true will always be true and false will always be false. Treating them as such by defining them as global variables is an absolute no-brainer in terms of performance. Why create new *object.Booleans with the same value if we can just reference these two? The second reason is that this makes comparisons in Monkey, like true == true, easier to implement and perform, because we can just compare two pointers without having to unwrap the value they’re pointing at.

Of course, defining True and False does not magically make the tests pass. We also need to push them on to the stack when instructed to do so. For that we extend the main loop of our VM:

```
// vm/vm.go

func (vm *VM) Run() error {
    // [...] 
    switch op {
    // [...] 
    case code.OpTrue:
        err := vm.push(True)
        if err != nil {
            return err
        }

    case code.OpFalse:
        err := vm.push(False)
        if err != nil {
            return err
        }

    }
    // [...] 
}
```

Not much to explain here: we push the globals True and False on to the stack. That means that we *are* actually pushing something on to the stack before trying to clean it up again, which means our tests don’t blow up anymore:

```
$ go test ./vm
ok      monkey/vm    0.007s
```

Alright! Boolean literals work and our VM now knows about True and False. Now we can start to implement the comparison operators, because now we can put their results on to the stack.

## Comparison Operators

The four comparison operators in Monkey are: ==, !=, > and <. We will now add support for all four of them by adding three (!) new opcode definitions and supporting them in the compiler and the VM. Here they are:

```
// code/code.go

const (
    // [...] 
    
    OpEqual
    OpNotEqual
    OpGreaterThan
)

var definitions = map[Opcode]*Definition{
    // [...] 
    
    OpEqual:      {"OpEqual", []int{}},
    OpNotEqual:   {"OpNotEqual", []int{}},
    OpGreaterThan: {"OpGreaterThan", []int{}},
}
```

They do not have operands and instead do their work by comparing the two topmost elements on the stack. They tell the VM to pop them off and push the result back on. Just like the opcodes for arithmetic operations.

You might be wondering why there is no opcode for <. If we have OpGreaterThan, shouldn’t we have an OpLessThan, too? That’s a valid question, because we could add OpLessThan and that would be fine, but I want to show something that’s possible with compilation and not with interpretation: reordering of code.

The expression 3 < 5 can be reordered to 5 > 3 without changing its result. And because it can be reordered, that’s what our compiler is going to do. It will take every less-than expression and reorder it to emit the greater-than version instead. That way we keep the instruction set small, the loop of our VM tighter and learn about the things we can do with compilation.

Here are new test cases for the existing TestBooleanExpressions function that express this:

// compiler/compiler_test.go

```go
func TestBooleanExpressions(t *testing.T) {
	tests := []compilerTestCase{
		// [...]
		{
			input:              "1 > 2",
			expectedConstants:  []interface{}{1, 2},
			expectedInstructions: []code.Instructions{
				code.Make(code.OpConstant, 0),
				code.Make(code.OpConstant, 1),
				code.Make(code.OpGreaterThan),
				code.Make(code.OpPop),
			},
		},
		{
			input:              "1 < 2",
			expectedConstants:  []interface{}{2, 1},
			expectedInstructions: []code.Instructions{
				code.Make(code.OpConstant, 0),
				code.Make(code.OpConstant, 1),
				code.Make(code.OpGreaterThan),
				code.Make(code.OpPop),
			},
		},
		{
			input:              "1 == 2",
			expectedConstants:  []interface{}{1, 2},
			expectedInstructions: []code.Instructions{
				code.Make(code.OpConstant, 0),
				code.Make(code.OpConstant, 1),
				code.Make(code.OpEqual),
				code.Make(code.OpPop),
			},
		},
		{
			input:              "1 != 2",
			expectedConstants:  []interface{}{1, 2},
			expectedInstructions: []code.Instructions{
				code.Make(code.OpConstant, 0),
				code.Make(code.OpConstant, 1),
				code.Make(code.OpNotEqual),
				code.Make(code.OpPop),
			},
		},
		{
			input:              "true == false",
			expectedConstants:  []interface{}{},
			expectedInstructions: []code.Instructions{
				code.Make(code.OpTrue),
				code.Make(code.OpFalse),
				code.Make(code.OpEqual),
				code.Make(code.OpPop),
			},
		},
		{
			input:              "true != false",
			expectedConstants:  []interface{}{},
			expectedInstructions: []code.Instructions{
				code.Make(code.OpTrue),
```

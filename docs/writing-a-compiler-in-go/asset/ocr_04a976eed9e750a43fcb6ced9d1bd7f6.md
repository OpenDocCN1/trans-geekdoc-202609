lex and parse the input, take the AST, pass it to the compiler, check the compiler for errors and then hand the *compiler.Bytecode over to the New function.

The New function should return a new instance of the virtual machine, assigned to vm. This is where we get to the heart of each test case. We start the vm with a call to vm.Run and after making sure it ran without an error, we use a method called StackTop to get the object that’s left sitting on top of the VM’s stack. We then pass that to testExpectedObject to make sure that this object matches what we expected in the vmTestCase.expected field.

Whew! Quite a lot of preparation and setup. But, trust me, this is going to make it so easy to write VM tests in the future. I mean, take a look at this, our first test:

```
```go
// vm/vm_test.go
func TestIntegerArithmetic(t *testing.T) {
    tests := []vmTestCase{
        {"1", 1},
        {"2", 2},
        {"1 + 2", 2}, // FIXME
    }

    runVmTests(t, tests)
}
```
```

Isn’t that wonderful? No noise, no boilerplate. We just write down the Monkey code and what we expect to end up on the stack when the VM executes it.

Please note that we do not expect 3 but 2 to be sitting on top of the stack after compiling and executing 1 + 2. Sounds wrong, right? Well, it is wrong. At the end of this chapter executing 1 + 2 should, of course, result in 3. But right now we only have OpConstant defined, which makes the only thing we can test and implement the pushing of constants on the stack. And in this test case, the 2 is the second integer to be pushed, so that’s what we’re going to test.

The other two test cases, with only the integers 1 and 2 as their input, are sanity checks. They do not test separate functionality. Pushing a sole integer on to the stack is included in, well, pushing two of them. But these test cases do not have a huge cost and don’t take up a lot of space, so I added them to explicitly make sure that a single integer literal in an expression statement ends with an integer being pushed on to the stack.

Currently, though, nothing’s pushed because we haven’t defined VM yet. But we
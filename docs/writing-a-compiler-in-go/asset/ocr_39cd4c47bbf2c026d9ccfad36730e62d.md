```
// vm/vm_test.go

func TestConditionals(t *testing.T) {
    tests := []vmTestCase{
        // [...] 
        {"if (1 > 2) { 10 }", Null},
        {"if (false) { 10 }", Null},
    }

    runVmTests(t, tests)
}
```

```
func testExpectedObject(
    t *testing.T,
    expected interface{},
    actual object.Object,
) {
    t.Helper()

    switch expected := expected.(type) {
    // [...] 
    case *object.Null:
        if actual != Null {
            t.Errorf("object is not Null: %T (%v)", actual, actual)
        }
    }
}
```

Here we have two new test cases for our existing TestConditionals function in which the condition is not Monkey truthy to force the evaluation of the alternative. But since there is none, we expect Null to end up on the stack. To test that properly, we extend the testExpectedObject with a new case branch for *object.Null.

Neatly expressed, isn’t it? Well, the error message isn’t:

```
$ go test ./vm
--- FAIL: TestConditionals (0.00s)
panic: runtime error: index out of range [recovered]
panic: runtime error: index out of range

goroutine 7 [running]:
testing.tRunner.func1(0xc4200a82d0)
/usr/local/go/src/testing/testing.go:742 +0x29d
panic(0x11119420, 0x11f1fe0)
/usr/local/go/src/runtime/panic.go:502 +0x229
monkey/vm.(*VM).pop(...)
/Users/mrnugget/code/04/src/monkey/vm/vm.go:121
monkey/vm.(*VM).Run(0xc420054df8, 0x800, 0x800)
/Users/mrnugget/code/04/src/monkey/vm/vm.go:53 +0x418
monkey/vm.runVmTests(0xc4200a82d0, 0xc420073e78, 0x9, 0x9)
/Users/mrnugget/code/04/src/monkey/vm/vm_test.go:103 +0x35a
monkey/vm.TestConditionals(0xc4200a82d0)
/Users/mrnugget/code/04/src/monkey/vm/vm_test.go:82 +0x149
```
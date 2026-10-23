Before it’s too late, we move the main part of the OpCall implementation to a new method, called callFunction. Don’t be fooled, though, barely anything has changed in the implementation itself. The only difference is the second argument in the call to NewFrame. Instead of passing in vm.sp as the future basePointer for the frame, we first subtract numArgs. That gives us the basePointer as pictured in the diagram earlier.

Now look at that:

```
$ go test ./vm
ok      monkey/vm   0.047s
```

All of our tests are passing! Let’s roll the dice, go even further and throw some more tests at our VM:

```
// vm/vm_test.go

func TestCallingFunctionsWithArgumentsAndBindings(t *testing.T) {
    tests := []vmTestCase {
        // [...] 
        {
            input: `
let sum = fn(a, b) {
    let c = a + b;
    c;
};
sum(1, 2);
`,
            expected: 3,
        },
        {
            input: `
let sum = fn(a, b) {
    let c = a + b;
    c;
};
sum(1, 2) + sum(3, 4);`,
            expected: 10,
        },
        {
            input: `
let sum = fn(a, b) {
    let c = a + b;
    c;
};
let outer = fn() {
    sum(1, 2) + sum(3, 4);
};
outer();
`,
            expected: 10,
        },
    }
}
```
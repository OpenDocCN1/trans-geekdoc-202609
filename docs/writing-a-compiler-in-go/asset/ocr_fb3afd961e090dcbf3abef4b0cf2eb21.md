# Arguments in the VM

Remember that our goal is to compile and get this piece of Monkey code running in our VM:

```
let globalNum = 10;

let sum = fn(a, b) {
    let c = a + b;
    c + globalNum;
};

let outer = fn() {
    sum(1, 2) + sum(3, 4) + globalNum;
};

outer() + globalNum;
```

We’re nearly there. We can already extract bits of this snippet and turn them into a test for the VM:

```
// vm/vm_test.go

func TestCallingFunctionsWithArgumentsAndBindings(t *testing.T) {
    tests := []vmTestCase{
        {
            input: `
let identity = fn(a) { a; };
identity(4);
`,
            expected: 4,
        },
        {
            input: `
let sum = fn(a, b) { a + b; };
sum(1, 2);
`,
            expected: 3,
        }
    }

    runVmTests(t, tests)
}
```

That shows what we’re after in its most basic form. In the first test case we pass one argument to a function that only references its single argument and returns it. The second test case is the sanity check that makes sure we’re not hard-coding edge cases into our VM and can also handle multiple arguments. Both fail:

```
$ go test ./vm
--- FAIL: TestCallingFunctionsWithArgumentsAndBindings (0.00s)
```
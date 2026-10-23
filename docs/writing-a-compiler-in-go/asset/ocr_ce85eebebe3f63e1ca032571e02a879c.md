```
let a = 1;
let newAdderOuter = fn(b) {
    fn(c) {
        fn(d) { a + b + c + d };
    };
};
let newAdderInner = newAdderOuter(2)
let adder = newAdderInner(3);
adder(8);
`,
    expected: 14,
},
{
    input: `
let newClosure = fn(a, b) {
    let one = fn() { a; };
    let two = fn() { b; };
    fn() { one() + two(); };
};
let closure = newClosure(9, 90);
closure();
`,
    expected: 99,
},
}
runVmTests(t, tests)
}
```

Now we have closures that return other closures, global bindings, local bindings, multiple closures being called in other closures, all thrown together and this thing still runs:

```
$ go test ./vm
ok      monkey/vm   0.039s
```

This is as close as you can get to “certified working”. With great confidence we can now say: we’ve successfully implemented closures in a bytecode compiler and a bytecode VM! We’ve added the crown jewel to our shiniest Monkey implementation. Time to celebrate.
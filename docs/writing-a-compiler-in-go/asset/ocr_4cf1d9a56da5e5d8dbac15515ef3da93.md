```
```go
{
    input: `
let newAdder = fn(a, b) {
    fn(c) { a + b + c };
};
let adder = newAdder(1, 2);
adder(8);
`,
    expected: 11,
},
{
    input: `
let newAdder = fn(a, b) {
    let c = a + b;
    fn(d) { c + d };
};
let adder = newAdder(1, 2);
adder(8);
`,
    expected: 11,
}
runVmTests(t, tests)
}
```
```

Here we have closures that reference multiple free variables, some defined as parameters in the enclosing function, some as local variables. Cross your fingers:

```
```shell
$ go test ./vm
ok      monkey/vm   0.035s
```
```

Sweet! Let’s take it up a notch:

```
```go
// vm/vm_test.go

func TestClosures(t *testing.T) {
    tests := []vmTestCase{
        // [...]
        {
            input: `
let newAdderOuter = fn(a, b) {
    let c = a + b;
    fn(d) {
        let e = d + c;
        fn(f) { e + f; };
    };
};
let newAdderInner = newAdderOuter(1, 2)
let adder = newAdderInner(3);
adder(8);
`,
            expected: 14,
        },
        {
            input: `
```
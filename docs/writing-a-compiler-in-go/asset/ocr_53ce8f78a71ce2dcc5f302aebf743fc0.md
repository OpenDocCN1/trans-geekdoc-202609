To fix these tests we create a ReadUint8 function and use it in ReadOperands:

// code/code.go

```
```go
func ReadOperands(def *Definition, ins Instructions) ([]int, int) {
    operands := make([]int, len(def.OperandWidths))
    offset := 0

    for i, width := range def.OperandWidths {
        switch width {
        case 2:
            operands[i] = int(ReadUint16(ins[offset:]))
        case 1:
            operands[i] = int(ReadUint8(ins[offset:]))
        }

        offset += width
    }

    return operands, offset
}

func ReadUint8(ins Instructions) uint8 { return uint8(ins[0]) }
```
```

Yes, reading one byte and turning it into an uint8 means nothing more than telling the compiler that from now on it should treat it as such:

```
```bash
$ go test ./code
ok      monkey/code 0.008s
```
```

Alright, we now have two new opcodes, SetLocal and GetLocal, and both have a one-byte operand that’s supported by our infrastructure. Let’s move on to the compiler.

# Compiling Locals

We already know where and how to emit the correct instructions for bindings, because we already did that for global bindings. The “where” and “how” won’t change now, but the “scope” will. And that’s also the main challenge when it comes to compiling local bindings: deciding whether to emit an instruction for a global or for a local binding.

From the outside, though, it’s clear what we want and easy to express in a test case:

// compiler/compiler_test.go

```
```go
func TestLetStatementScopes(t *testing.T) {
```
```
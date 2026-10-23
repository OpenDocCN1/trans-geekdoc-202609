# Booleans

These four operators we added comprise only a subset of the operators available in Monkey. There are also has the comparison operators ==, !=, >, < and the two prefix operators ! and -. Our next goal is to implement all of them and that includes teaching our Monkey VM about another Monkey data type: booleans. Without booleans we couldn’t represent the results of these operators (well, except for the - prefix), but booleans also exist as literal expressions in Monkey:

```
true;
false;
```

We’re going to start by adding support for these two literals. That way we already have our boolean data type in place when we add the operators.

So what does a boolean literal do? Well, in our evaluator a boolean literal evaluates to the boolean value it designates: true or false. Now we’re working with a compiler and a VM, so we have to adjust our expectations a little bit. Instead of boolean literals evaluating to boolean values, we now want them to cause the VM to load the boolean values on to the stack.

That’s pretty close to what integer literals do and those are compiled to OpConstant instructions. We could treat true and false as constants too, but that would be a waste, not only of bytecode but also of compiler and VM resources. Instead, we’ll now define two new opcodes that directly tell the VM to push an *object.Boolean on to the stack:

```
// code/code.go

const (
    // [...] 
    
    OpTrue
    OpFalse
)

var definitions = map[Opcode]*Definition{
    // [...] 
    
    OpTrue:  {"OpTrue", []int{}},
    OpFalse: {"OpFalse", []int{}},
}
```
# # Adding the index operator

As we said at the beginning of the chapter, our goal is to make this piece of Monkey code work:

```
```monkey
[1, 2, 3][1]
{"one": 1, "two": 2, "three": 3}["o" + "ne"]
```
```

We’re nearly there: we already support array literals, hash literals, and also string concatenation. What we don’t have yet is the index operator, which allows us to retrieve a single element from an array or a hash.

What’s interesting about the index operator is that it’s quite generic. While we only want to use it with arrays and hashes, its syntactic form allows for much more:

```
```text
<expression>[<expression>]
```
```

The data structure being indexed and the index itself can be produced by any expression. And since a Monkey expression can produce any Monkey object that means, on a semantic level, that the index operator can work with any object.Object either as the index or as the indexed data structure.

That’s exactly how we’re going to implement it. Instead of treating the index operator in combination with a specific data structure as a special case, we’ll build a generic index operator into the compiler and VM. The first step, as so often, is to define a new opcode.

It’s called OpIndex and has no operands. Instead, for OpIndex to work, there need to be two values sitting on the top of the stack: the object to be indexed and, above that, the object serving as the index. When the VM executes OpIndex it should take both off the stack, perform the index operation, and put the result back on.

That’s generic enough to allow for arrays and hashes to be used as the indexed data structure, while also being easy to implement, due to its usage of the stack.

Here is the definition of OpIndex:

```
```go
// code/code.go
```
```
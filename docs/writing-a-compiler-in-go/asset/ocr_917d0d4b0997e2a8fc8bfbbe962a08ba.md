That really is a reason to celebrate: we turn function literals into `*object.CompiledFunction`, take care of implicit and explicit returns in the function’s body and also emit an `OpConstant` instruction to load the function on to the stack in the VM. Cheers to that!

We’ve reached the halfway point on the compilation side. The rest of the way is the compilation of function *calls*.

# Compiling Function Calls

Before we open `compiler_test.go` and start hammering out test cases, let’s take a step back and think this through. We want to implement function calls. In other words, we need to emit instructions that represent Monkey’s bytecode calling convention, since that’s how you call a function in Monkey bytecode.

At the beginning of this chapter we decided that the start of the calling convention is putting the function you want to call on to the stack. We already know how to do that. Either by using an `OpConstant` instruction in case it’s a function literal that’s being called, which looks like this:

```
fn() { 1 + 2 }()
```

Or with an `OpGetGlobal` instruction, if the function was previously bound to a name:

```
let onePlusTwo = fn() { 1 + 2 };
onePlusTwo();
```

Both options result in the `*object.CompiledFunction` we want to call to sit on the stack. In order to now execute its instructions, we need to issue an `OpCall` instruction.

The VM then executes the function’s instructions and when it’s done, it pops the function itself off the stack and replaces it with the return value. That’s if there is a return value. If not, it only pops the function off the stack, which is fine too.

This whole part of the calling convention — what the VM does with the function once it’s done executing it — is implicit: we do not need to issue an `OpPop` instruction to get the function off the stack. It’s part of the convention and we’ll build it straight into the VM.
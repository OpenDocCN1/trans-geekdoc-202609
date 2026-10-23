This is similar to the previous test case in TestConditionals, except that the input now contains not only the consequence of the conditional, but also the alternative: else { 20 }.

The expectedInstructions make clear what we want the bytecode to look like, with the first part being the same as in the previous test case: the condition is compiled to OpTrue and is followed by the OpJumpNotTruthy instruction that instructs the VM to *jump over* the compiled consequence.

Then, things start to differ. As the next opcode, we expect an OpJump, the opcode for an unconditional jump instruction. It has to be there because if condition is truthy the VM should only execute the consequence and *not* the alternative. To stop that from happening the OpJump instruction tells the VM to jump over the alternative.

The OpJump should then be followed by instructions that make up the alternative. In our test case, that’s the OpConstant instruction that loads 20 on to the stack.

Then we’re back on familiar ground. An OpPop is there to pop the value produced by the conditional off the stack and the loading of the bogus 3333 gives us guidance.

I know that it’s not easy to wrap ones head around these jumps, so I hope that this illustration makes it clearer which instruction belongs to which part of the conditional and how the jumps tie them all together:
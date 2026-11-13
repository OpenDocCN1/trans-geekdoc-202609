# Third cycle

Click step.

+   1 Fetch: The PC is currently 2, so the instruction at memory address 2 is fetched (305). The control bus sends a read signal to initiate this. 3 is stored in the instruction register, and 05 is stored in the address register.
+   The PC is incremented to 3 via the ALU.
+   
+   2 Decode: The instruction 3 decodes as “store accumulator to address” and the address register gives the location of where to store the data (05). The control unit uses the control bus to co-ordinate this.
+   
+   3 Execute: Memory address 5 is opened via the address bus, and the control bus sends the appropriate signals to send the accumulator contents down the data bus and store them at address 5 (overwriting the current data).

# Fourth cycle

Click step.

+   1 Fetch: The PC is currently 3, so the instruction at memory address 3 is fetched (000). The control bus sends a read signal to initiate this. 0 is stored in the instruction register, and 00 is stored in the address register.
+   The PC is incremented to 4 via the ALU.
+   
+   2 Decode: The instruction 0 decodes as “halt”. The control unit uses the control bus to signal this operation.
+   
+   3 Execute: The computer halts all operations and ends the program.

# Common mistake

A common mistake is assuming that the program counter (PC) gets updated after the execute stage of the fetch–decode–execute cycle. The PC is usually updated during or immediately after the fetch stage, so it points to the next instruction in memory before the current instruction is even decoded or executed. This ensures that the CPU always knows where to find the next instruction in the sequence.

# PROGRAMMING EXERCISES

Write an LMC program to:

+   1 input two numbers, add them, and output the result
+   2 input a number and output whether it is positive or zero
+   3 calculate the sum of the first five natural numbers
+   4 input two numbers and output the larger one
+   5 input three numbers and output them in ascending order.

# REVIEW QUESTIONS

+   1 What are the main steps in the fetch–decode–execute cycle, and why is this cycle fundamental to CPU operations?
+   2 How does the CPU use the address, data and control buses during the fetch–decode–execute cycle?
+   3 Why is the interaction between memory and registers crucial during the fetch phase of the CPU cycle?
that once you place something on a stack, you can't get to anything underneath until you take the top off the stack. You're always either adding one to the top of the stack or taking the top item off.

# FIGURE 12.6 Stack frame

![](bbox=[0.4, 0.21, 0.58, 0.36])

A buffer overflow works because of the local variables. Each variable is allocated space on the stack. In some cases, data will be copied into the space allocated for it, but if the data being copied into that space, called a buffer, is larger than the buffer, the data being copied in will overwrite anything else in the stack. This includes the return address.
Figure 12.7 shows what happens if too much data is sent into a buffer. Let’s say there is
a buffer named strName that has been allocated 10 bytes (characters) but the function is
copying 16 bytes (characters) into that variable. The 10 bytes (10 As in this case) fill up the
10 bytes allocated for that variable. The remaining 6 bytes write into the next addresses in
memory. In this case, the next memory address space is the return address. This gets popu-
lated when the function is called and retrieved when the function completes.

# FIGURE 12.7 Buffer overflow

![](bbox=[0.35, 0.61, 0.63, 0.77])

Here, the return address is loaded with As. In reality, the byte would be 0x41, which is
the hexadecimal for the ASCII value of A. The address the program would try to jump to
would include 0x41414141414141. An address like this likely falls outside of the address space
allocated for the program’s execution, which means the program would fail with a segmen-
tation fault. A segmentation fault happens when the program tries to jump to an address
outside of its memory segment.
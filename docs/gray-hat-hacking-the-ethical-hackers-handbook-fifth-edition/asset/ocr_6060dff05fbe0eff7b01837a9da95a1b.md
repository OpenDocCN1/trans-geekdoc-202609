overwriting the return pointer on the stack, execution never reaches the return instruction. This is commonly due to a read or write access violation happening prior to reaching the function epilog, caused by the large number of characters you sent into the buffer. In this case, further down the stack past the buffer is the location of the SEH chain for the thread. The read or write access violation will cause FS:[0] to get dereferenced, which is the thread's stack address where the first “Next SEH” (NSEH) value is stored. Directly below the NSEH position on the stack is the address of the first handler to be called. Overwriting this address with a custom address is often an easy way to gain control if you are unable to via the return pointer overwrite. SafeSEH aims to stop this technique from working, but as you will see, it is easily bypassed.

# Understanding and Bypassing Windows Memory Protections

As could be expected, over time, attackers learned how to take advantage of the lack of memory protections in previous versions of Windows. In response, around the time of Windows XP SP2 and Server 2003, Microsoft started to add memory protections, which were quite effective for some time. However, the attackers eventually learned ways around these protections too. This is the continuous evolution of exploitation techniques and protections for thwarting the success of those techniques.

# Safe Structured Exception Handling (SafeSEH)

The purpose of the SafeSEH protection is to prevent the overwriting and use of SEH structures stored on the stack. If a program is compiled and linked with the /SafeSEH linker option, the header of that binary will contain a table of all valid exception handlers; this table will be checked when an exception handler is called to ensure that it is in the list. The check is done as part of the RtlDispatchException routine in ntdll.dll, which performs the following tests:

+   - It ensures that the exception record is located on the stack of the current thread.
+   - It ensures that the handler pointer does not point back to the stack.
+   - It ensures that the handler is registered in the authorized list of handlers.
+   - It ensures that the handler is in an image of memory that is executable.

So, as you can see, the SafeSEH protection mechanism takes steps to protect exception handlers, but as you will see in a bit, it is not foolproof.

# Bypassing SafeSEH

As previously discussed, when an exception is triggered, the operating system places the except_handler function on the stack and calls it, as shown in Figure 13-3.
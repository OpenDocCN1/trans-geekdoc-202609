Process = address space + execution context (thread of control)

Process address space (segments):

+   - Code.
+   - Data (static/global).
+   - Heap (dynamic memory allocation).
+   - Stack.

Execution context:

+   - Data registers.
+   - Stack pointer (SP).
+   - Program counter (PC).
+   - Working Registers.

OS Scheduling of processes: context switching (ie. save/load Execution context)

# Pros/cons

+   - Context switching expensive.
+   - (potentially) complex data sharing (not necessary true).
+   - Cooperating processes - no need for memory protection (separate address spaces).
+   - Relevant for parrallel computation with memory allocation.

# Threads

+   - Threads share the same address space (Data registers): access to code, heap and (global) data.
+   - Separate execution stack, PC and Working Registers.

# Pros/cons

+   - Faster context switching only SP, PC and Working Registers.
+   - Can exploit fine-grain concurrency
+   - Simple data sharing through the shared address space.
+   - Precautions have to be taken or two threads will write to the same memory at the same time. This is what the global interpreter lock (GIL) is for.
+   - Relevant for GUI, I/O (Network, disk) concurrent operation

# In Python

+   - The threading module uses threads.
+   - The multiprocessing module uses processes.

# Multithreading

```
import time
import threading
```
of tickets and may be authorized to lend or give them to others. Because tickets may be dispersed around the system, they present a greater security problem than access-control lists. In particular, the ticket must be unforgeable. One way to accomplish this is to have the OS hold all tickets on behalf of users. These tickets would have to be held in a region of memory inaccessible to users.

Network considerations for data-oriented access control parallel those for user-oriented access control. If only certain users are permitted to access certain items of data, then encryption may be needed to protect those items during transmission to authorized users. Typically, data access control is decentralized, that is, controlled by host-based database management systems. If a network database server exists on a network, then data access control becomes a network function.

# 24.3.4 Protection Based on an Operating System Mode.

One technique used in all OSs to provide protection is based on the mode of processor execution. Most processors support at least two modes of execution: the mode normally associated with the OS and that normally associated with user programs. Certain instructions can be executed only in the more privileged mode. These would include reading or altering a control register, such as the program status word; primitive I/O instructions; and instructions that relate to memory management. In addition, certain regions of memory can be accessed only in the more privileged mode.

The less privileged mode often is referred to as the user mode, because user programs typically would execute in this mode. The more privileged mode is referred to as the system mode, control mode, or kernel mode. This last term refers to the kernel of the OS, which is that portion of the OS that encompasses the important system functions. Exhibit 24.3 lists the functions typically found in the kernel of an OS.

# EXHIBIT 24.3 Typical Kernel Mode Operating System Functions

+   **Process Management**
+   - Process creation and termination
+   - Process scheduling and dispatching
+   - Process switching
+   - Process synchronization and support for interprocess communication
+   - Management of process control blocks

+   **Memory Management**
+   - Allocation of address space to processes
+   - Swapping
+   - Page and segment management

+   **I/O Management**
+   - Buffer management
+   - Allocation of I/O channels and devices to processes

+   **Support functions**
+   - Interrupt handling
+   - Accounting
+   - Monitoring

The most common technique for user access control on a shared system or server is the user logon, which requires both a user identifier (ID) and some form of authentication, such as providing a password, a token, or biometric attributes. Authentication refers to the binding of a real-world identity (for example, a named employee or a named role in an organization) and the ID being presented. The system will allow a user to log on only if that user's ID is known to the system and if the user knows the password associated by the system with that ID.

Once a user has established a session, the operating system can then authorize different forms of access (e.g., read, write, append, lock, or execute) to different types of data (e.g., specific files, databases, devices, or communications).

User access control in a distributed environment can be either centralized or decentralized. In a centralized approach, the network provides a logon service, determining who is allowed to use the network and to whom the user is allowed to connect.

Decentralized user access control treats the network as a transparent communication link, and the destination host carries out the usual logon procedure. The security concerns for transmitting passwords over the network must still be addressed.

In many networks, two levels of access control may be used. Individual hosts may be provided with a logon facility to protect host-specific resources and application. In addition, the network as a whole may provide protection to restrict network access to authorized users. This two-level facility is desirable for the common case, currently, in which the network connects disparate hosts and simply provides a convenient means of terminal-host access. In a more uniform network of hosts, some centralized access policy could be enforced in a network control center.

Chapters 28 and 29 of this Handbook present more information about identification and authentication.

## 24.3.3 Data-Oriented Access Control.

Following successful logon, the user is granted access to one or a set of hosts and applications. This is generally not sufficient for a system that includes sensitive data in its database. Through the user access-control procedure, a user can be identified to the system. Associated with each user, there can be a profile that specifies permissible operations and file accesses. The OS can then enforce rules based on the user profile. The database-management system, however, must control access to specific records or even portions of records. For example, it may be permissible for anyone in administration to obtain a list of company personnel, but only selected individuals may have access to salary information. The issue is more than just one of level of detail. Whereas the OS may grant a user permission to access a file or use an application, following which there are no further security checks, the database management system must make a decision on each individual access attempt. That decision will depend not only on the user's identity but also on the specific parts of the data being accessed and even on the information already divulged to the user.

A general model of access control as exercised by a file or database management system is that of an access matrix (see Exhibit 24.2a). The basic elements of the model are:

- Subject. An entity capable of accessing objects. Generally, the concept of subject equates with that of process. Any user or application actually gains access to an object by means of a process that represents that user or application.
- Object. Anything to which access is controlled. Examples include files, portions of files, programs, and segments of memory.
- Access right. The way in which an object is accessed by a subject. Examples are read, write, and execute.

| User | File 1 | File 2 | File 3 | File 4 | Account 1 | Account 2 |
|---|---|---|---|---|---|---|
| User A | Own R W |  | Own R W |  | Inquiry Credit |  |
| User B | R | Own R W | W | R | Inquiry Debit | Inquiry Credit |
| User C | R W | R |  | Own R W |  | Inquiry Debit |

(a) Access matrix

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_755_0.png)

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_755_1.png)

(b) Access control lists for files of part (a)

(c) Capability lists for files of part (a)

## EXHIBIT 24.2 Example of Access-Control Structures

Source: Based on a figure in Sandhu (1996).

One dimension of the matrix consists of identified subjects that may attempt data access. Typically, this list will consist of individual users or user groups, although access could be controlled for terminals, hosts, or applications, instead of, or in addition to, users. The other dimension lists the objects that may be accessed. At the greatest level of detail, objects may be individual data fields. More aggregate groupings, such as records, files, or even the entire database, also may be objects in the matrix. Each entry in the matrix indicates the access rights of that subject for that object.

In practice, an access matrix usually is sparse and is implemented by decomposition in one of two ways. The matrix may be decomposed by columns, yielding access-control lists (see Exhibit 24.2b). Thus, for each object, an access-control list lists users and their permitted access rights. The access-control list may contain a default, or public, entry. This allows users who are not explicitly listed as having special rights to have a default set of rights. Elements of the list may include individual users as well as groups of users.

Decomposition by rows yields capability tickets (see Exhibit 24.2c). A capability ticket specifies authorized objects and operations for a user. Each user has a number of tickets and may be authorized to lend or give them to others. Because tickets may be dispersed around the system, they present a greater security problem than access-control lists. In particular, the ticket must be unforgeable. One way to accomplish this is to have the OS hold all tickets on behalf of users. These tickets would have to be held in a region of memory inaccessible to users.

Network considerations for data-oriented access control parallel those for user-oriented access control. If only certain users are permitted to access certain items of data, then encryption may be needed to protect those items during transmission to authorized users. Typically, data access control is decentralized, that is, controlled by host-based database management systems. If a network database server exists on a network, then data access control becomes a network function.

## 24.3.4 Protection Based on an Operating System Mode.

One technique used in all OSs to provide protection is based on the mode of processor execution. Most processors support at least two modes of execution: the mode normally associated with the OS and that normally associated with user programs. Certain instructions can be executed only in the more privileged mode. These would include reading or altering a control register, such as the program status word; primitive I/O instructions; and instructions that relate to memory management. In addition, certain regions of memory can be accessed only in the more privileged mode.

The less privileged mode often is referred to as the user mode, because user programs typically would execute in this mode. The more privileged mode is referred to as the system mode, control mode, or kernel mode. This last term refers to the kernel of the OS, which is that portion of the OS that encompasses the important system functions. Exhibit 24.3 lists the functions typically found in the kernel of an OS.

## EXHIBIT 24.3 Typical Kernel Mode Operating System Functions

### Process Management
- Process creation and termination
- Process scheduling and dispatching
- Process switching
- Process synchronization and support for interprocess communication
- Management of process control blocks

### Memory Management
- Allocation of address space to processes
- Swapping
- Page and segment management

### I/O Management
- Buffer management
- Allocation of I/O channels and devices to processes

### Support functions
- Interrupt handling
- Accounting
- Monitoring

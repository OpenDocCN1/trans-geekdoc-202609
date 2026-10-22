# 24·2 OPERATING SYSTEM SECURITY

+   2. **Sharing originals of program or data files.** With the use of reentrant code, a single physical realization of a program can appear in multiple virtual address spaces, as can read-only data files. Special locking mechanisms are required for the sharing of writable data files, to prevent simultaneous users from interfering with each other.
+   
+   3. **Confined, or memoryless, subsystems.** In this case, processes are grouped into subsystems to enforce a particular protection policy. For example, a “client” process calls a “server” process to perform some task on data. The server is to be protected against the client discovering the algorithm by which it performs the task, while the client is to be protected against the server’s retaining any information about the task being performed.
+   
+   4. **Controlled information dissemination.** In some systems, security classes are defined to enforce a particular dissemination policy. Users and applications are given security clearances of a certain level, while data and other resources (e.g., input/output [I/O] devices) are given security classifications. The security policy enforces restrictions concerning which users have access to which classifications. This model is useful not only in the military context but in commercial applications as well.¹

Much of the work in security and protection as it relates to OSs can be roughly grouped into three categories.

+   1. **Access control.** Concerned with regulating user access to the total system, subsystems, and data, and regulating process access to various resources and objects within the system.
+   
+   2. **Information flow control.** Regulates the flow of data within the system and its delivery to users.
+   
+   3. **Certification.** Relates to proving that access and flow control mechanisms perform according to their specifications and that they enforce desired protection and security policies.

This chapter looks at some of the key mechanisms for providing OS security and then examines Windows 2000 as a case study.

# 24.2 REQUIREMENTS FOR OPERATING SYSTEM SECURITY

# 24.2.1 Requirements.

Understanding the types of threats to OS security requires a definition of security requirements. OS security addresses four requirements:

+   1. **Confidentiality.** Requires that the information in a computer system be accessible only for reading by authorized parties. This type of access includes printing, displaying, and other forms of disclosure, including simply revealing the existence of an object.
+   
+   2. **Integrity.** Requires that only authorized parties be able to modify computer system assets. Modification includes writing, changing, changing status, deleting, and creating.
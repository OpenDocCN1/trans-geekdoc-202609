The most common technique for user access control on a shared system or server is the user logon, which requires both a user identifier (ID) and some form of authentication, such as providing a password, a token, or biometric attributes. Authentication refers to the binding of a real-world identity (for example, a named employee or a named role in an organization) and the ID being presented. The system will allow a user to log on only if that user's ID is known to the system and if the user knows the password associated by the system with that ID.

Once a user has established a session, the operating system can then authorize different forms of access (e.g., read, write, append, lock, or execute) to different types of data (e.g., specific files, databases, devices, or communications).

User access control in a distributed environment can be either centralized or decentralized. In a centralized approach, the network provides a logon service, determining who is allowed to use the network and to whom the user is allowed to connect.

Decentralized user access control treats the network as a transparent communication link, and the destination host carries out the usual logon procedure. The security concerns for transmitting passwords over the network must still be addressed.

In many networks, two levels of access control may be used. Individual hosts may be provided with a logon facility to protect host-specific resources and application. In addition, the network as a whole may provide protection to restrict network access to authorized users. This two-level facility is desirable for the common case, currently, in which the network connects disparate hosts and simply provides a convenient means of terminal-host access. In a more uniform network of hosts, some centralized access policy could be enforced in a network control center.

Chapters 28 and 29 of this Handbook present more information about identification and authentication.

# 24.3.3 Data-Oriented Access Control.

Following successful logon, the user is granted access to one or a set of hosts and applications. This is generally not sufficient for a system that includes sensitive data in its database. Through the user access-control procedure, a user can be identified to the system. Associated with each user, there can be a profile that specifies permissible operations and file accesses. The OS can then enforce rules based on the user profile. The database-management system, however, must control access to specific records or even portions of records. For example, it may be permissible for anyone in administration to obtain a list of company personnel, but only selected individuals may have access to salary information. The issue is more than just one of level of detail. Whereas the OS may grant a user permission to access a file or use an application, following which there are no further security checks, the database management system must make a decision on each individual access attempt. That decision will depend not only on the user's identity but also on the specific parts of the data being accessed and even on the information already divulged to the user.

A general model of access control as exercised by a file or database management system is that of an access matrix (see Exhibit 24.2a). The basic elements of the model are:

+   - Subject. An entity capable of accessing objects. Generally, the concept of subject equates with that of process. Any user or application actually gains access to an object by means of a process that represents that user or application.
+   - Object. Anything to which access is controlled. Examples include files, portions of files, programs, and segments of memory.
+   - Access right. The way in which an object is accessed by a subject. Examples are read, write, and execute.
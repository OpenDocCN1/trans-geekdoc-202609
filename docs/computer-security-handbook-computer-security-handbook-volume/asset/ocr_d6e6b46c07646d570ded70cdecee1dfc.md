![](bbox=[0.1, 0.12, 0.27, 0.33])

![](bbox=[0.33, 0.12, 0.5, 0.38])

![](bbox=[0.6, 0.12, 0.82, 0.42])

(a) Access token

(b) Security descriptor

(c) Access-control list

# Exhibit 24.6 Windows 2000 Security Structures

group has a unique group SID. Access to an object can be defined on the basis of group SIDs, individual SIDs, or a combination.

+   - **Privileges.** A list of security-sensitive system services that this user may call. An example is create token. Another example is the set backup privilege; users with this privilege are allowed to use a backup tool to back up files that they normally would not be able to read. Most users will have no privileges.
+   - **Default owner.** If this process creates another object, this field specifies who is the owner of the new object. Generally, the owner of the new process is the same as the owner of the spawning process. However, a user may specify that the default owner of any processes spawned by this process is a group SID to which this user belongs.
+   - **Default access control list (ACL).** This is an initial list of protections applied to the objects that the user creates. The user may subsequently alter the ACL for any object that it owns or that one of its groups owns.

# 24.6.3 Security Descriptors.

Exhibit 24.6b shows the general structure of a security descriptor, which includes these parameters:

+   - **Flags.** Defines the type and contents of a security descriptor. The flags indicate whether the system access-control list (SACL) and discretionary access control list (DACL) are present, whether they were placed on the object by a defaulting mechanism, and whether the pointers in the descriptor use absolute or relative addressing. Relative descriptors are required for objects that are transmitted over a network, such as information transmitted in an RPC.
+   - **Owner.** The owner of the object generally can perform any action on the security descriptor. The owner can be an individual or a group SID. The owner has the authority to change the contents of the DACL.
+   - **System access control list (SACL).** Specifies what kinds of operations on the object should generate audit messages. An application must have the corresponding
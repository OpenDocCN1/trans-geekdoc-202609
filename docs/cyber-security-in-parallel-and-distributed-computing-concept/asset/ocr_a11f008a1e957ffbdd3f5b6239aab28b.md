which it is assigned to. We will discuss authorization along with access control. Let us first discuss two things which need to be taken into account when considering the security in any distributed system:

+   - **Security Policy**: This determines what is secure for the system or organization or entity. It basically refers to the constraints on the characteristics of the members and restrictions imposed upon the adversaries by various techniques, viz. locks, keys, walls, doors, etc.
+   - **Security Mechanism**: A security mechanism is basically designed for preventing or recovering from a security attack. A security service basically uses one or more security mechanisms. Fundamentally, a security service is that which enhances the security of the data processing systems. The following four different types of security threats are commonly present:
+     - *Interception*: Refers to the situation where an unauthorized party has access to data or service. Such situation arises when the communication between two parties is overheard by another person.
+     - *Interruption*: When something is corrupted or lost, the interruption occurs. Basically, it is a situation in which services or data become unavailable, destroyed, unusable, etc. In denial-of-service attacks, someone maliciously tries to make a service inaccessible to another party.
+     - *Modification*: This is concerned with unauthorized change or tampering of data such that it cannot further adhere to its initial specifications; for example, frequently changing the transmitted data.
+     - *Fabrication*: Represents the circumstance where additional data or activity gets produced that does not normally exist. For example, an intruder may attempt to append an entry into the password file or the database.

Furthermore, the security mechanisms through which a policy can be enforced are as follows:

+   - Encryption
+   - Authentication
+   - Authorization
+   - Auditing

Encryption is fundamental to computer security. Encryption transforms data into something an attacker cannot understand. In other words, encryption provides a means to implement data confidentiality. In addition, encryption allows us to check whether data have been modified. Thus, it also provides support for integrity checks. Authentication is used to verify the claimed identity of a user, client, server, host, or other entity. In the case of clients, the basic premise is that before a service starts to perform any work on behalf of a client, it should be known [9].
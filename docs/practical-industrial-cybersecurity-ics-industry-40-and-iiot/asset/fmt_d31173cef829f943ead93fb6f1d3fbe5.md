
# Key Management System (KMS)

*Key Management System* (*KMS*) applications provide integrated management functions for creating, storing, and distributing keys for computing devices and applications. On the server side, these applications are responsible for generating, distributing, and replacing keys throughout the system. On the client side, they are responsible for storing and managing the keys. There are a wide variety of KMS systems available through both open source and proprietary outlets. These applications provide end-to-end protection for keys from generation to retirement and destruction.

## Hashing

As already discussed, in cybersecurity settings *hashing* is a cryptographic technique defined as the application of a mathematical algorithm to a set of data to produce a numeric value that represents the set. The value resulting from the application of the algorithm is known as the *hash value* or *hash*.

Hashing is different than encryption in that the algorithm is designed in such a way as to make the conversion infeasible to deconstruct. It is a one-way conversion.

Hashing is used to provide several security-related functions, including the following:

*   Integrity verification for transmitted files or messages
*   Password verification
*   File identification
*   Proof of work
*   eSignature security

The classical example of hashing is running an algorithm to generate a hash for a password that can then be regenerated each time the password is used to verify its authenticity. Placing the original hash in a *hash table* enables the creation of a system where the actual password never needs to be seen—only the new hash to compare to the old hash.

A hash table is simply a lookup table that maps keys to values using a *hash function* that converts the keys into hash values. Rather than sequentially searching a table of data looking for a particular value, a hash function can be performed on the lookup key that will return the index to the hash value being searched for. This can save a tremendous amount of time searching for data.

A *distributed hash table* *(DHT)* is a similar type of function, but the mapping from keys to values is distributed among the different nodes across the network. The node that stores this map can be found by hashing that key.

## Resource Constraints

A *resource constraint* is a limit on what a resource can accomplish with the tools that are available to it. The resource can include funding limits, personnel quantity or capability limitations, and device or physical infrastructure capability limits.

As you've seen, DoS attacks are based on constraining a targeted resource and can be conducted in a number of ways:

*   Flooding network connectivity devices to disrupt connections and prevent users from accessing them
*   Consuming the resources of a targeted computing device (disk space, memory, CPU processing capabilities or bandwidth)
*   Manipulating device configuration settings
*   Injecting data that a computing or network device cannot process

## Review Questions

The following questions test your knowledge of the material presented in this chapter.

1.  \_\_\_\_\_\_\_\_\_\_ creates a tracking list of events using logs or other tracking tools.
2.  \_\_\_\_\_\_\_\_\_\_ is applying approval of access to designated information after the individual is authenticated.
3.  \_\_\_\_\_\_\_\_\_\_ involves making sure that an individual is who they say they are.
4.  \_\_\_\_\_\_\_\_\_\_ is an assurance that data remains secret or private. It is established through sets of rules designed to limit data access to authorized people.
5.  \_\_\_\_\_\_\_\_ is an assurance that data is accurate and can be trusted.
6.  \_\_\_\_\_\_\_\_\_ is an assurance that data can reliably be accessed in a timely manner.
7.  What type of cyberattack involves impersonating a user or a system?
8.  Describe the objective of performing a DoS attack.
9.  How do the basic tenets of enterprise networks differ from those of OT networks?
10.  Which phase of a cyberattack is most time-consuming, and at what point in the process does it occur?
11.  What security feature can be used to make sure that if data is accessed at rest or intercepted in motion by an unauthorized third party, it cannot be read?
12.  Describe the two general categories of social engineering techniques.
13.  What cryptographic technique is used to provide integrity verification for transmitted files or messages?
14.  Describe three types of password attacks.
15.  \_\_\_\_\_\_\_\_\_\_\_\_\_ provides integrated management functions for creating, storing, and distributing keys for computing devices and applications.

## Exam Questions

1.  This principle refers to giving each user the least amount of access possible to accomplish their job role and only to the areas of the network they must have.

    1.  User rights principle
    2.  User access principle
    3.  Least privilege principle
    4.  Access control principle

2.  What term is used to refer to a service that proves the integrity and origin (authorship) of data?

    1.  Authorization
    2.  Authentication
    3.  Identification
    4.  Nonrepudiation

3.  Which threat agent represents the greatest threat to most networked organizations?

    1.  Denial of service
    2.  Insider threats
    3.  Man in the middle
    4.  Spammers

4.  What is the target of a distributed denial-of-service (DDoS) attack?

    1.  A single client is being attacked.
    2.  Multiple servers are being attacked.
    3.  A single server is being attacked.
    4.  Multiple clients are being attacked.

5.  Which of the following is associated with occurrences that create adverse effects within the network or computing environment that will require actions to mitigate, or with occurrences that violate organizational security policies, procedures, or acceptable use practices?

    1.  Cyber events
    2.  Cyber incidents
    3.  Cyber occurrences
    4.  Cyberattacks

6.  What does a SYN attack take advantage of?

    1.  The TCP/IP buffer space used during a handshake exchange
    2.  The IPX/SPX frame relay used during an initial connection
    3.  The UDP header frame used during a handshake exchange
    4.  The ICMP echo connection used during connectivity checks

7.  What security action involves applying a cipher to data to produce a scrambled message that cannot be understood without the knowledge of the secret code that was used to create it?

    1.  Hashing
    2.  Encryption
    3.  Steganography
    4.  Cryptology

8.  A close friend wants to know what your job at work is like, so you invite him over to see the operation and test your high-speed Internet connection. The following week, the network administrator tells you that your computer has a virus. What could be the cause?

    1.  Unauthorized access
    2.  DoS
    3.  Social engineering
    4.  Spoofing

9.  One of the significant features of using digital signatures is that it presents a reliable method to ensure data integrity. Which of the following is used to digitally sign a message?

    1.  The sender's public key
    2.  The sender's private key
    3.  The receiver's private key
    4.  The receiver's public key

10.  While searching the Web for a specific product, you log into the site using your credentials. The browser appears to be trying to authenticate you but eventually returns you to the login page without an error message. Assuming that you have misentered your credentials, you apply them again, and they are accepted. You were pretty sure your username and password were correct the first time, but they didn't get you into the site. What type of activity might you have been involved in?

     1.  Clickjacking
     2.  SQL injection
     3.  Smurfing
     4.  Man in the middle

# Chapter 6: Physical Security

## Introduction

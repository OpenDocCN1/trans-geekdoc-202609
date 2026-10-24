
are now considered obsolete. SHA-2, which produces a 256-bit string or a 512-bit string, is used commonly nowadays.

Digital signature is another very important cryptographic construct in building secure systems. A digital signature mimics a physical signature in legal documents, and it must possess the following properties:

- The receiver of a digitally signed document can verify the signer’s identity. This is to facilitate authentication of the signer. Unlike in real world, where an official could verify the signer identity by checking for government-issued identification document such as driver’s license or passport, the digital signature must be designed in a way that a remote receiver of the digital signature can authenticate the signer based on the digital signature alone.
- The signer of the digital signature cannot repudiate the signed document once it has been signed.
- No one other than the original signer of the signed document could possibly have fabricated the signature.

The first property is for authenticating the signer of a signed document. The second and the third properties are essentially the same because if another person could have fabricated the digital signature, then the original signer could in fact repudiate the signed document. In other words, if the original signer cannot repudiate the signed document, then it must be true that no one else could fabricate the digital signature. Digital signatures are typically produced by using public-key cryptography on the hash of a document. This hash of a document is typically called message digest. The message digest is used because public-key cryptography must use long-keys and it is computationally very expensive compared with symmetric cryptography. In this case, the no-collision requirement for secure hash functions is essential to protect the integrity of digital signatures.

Message authentication code (MAC) is based on secure hash function and symmetric key encryption. More specifically, the sender would concatenate the message to be sent and a security key together, then hash it to produce a MAC. It is used pervasively in message exchanges to both authenticate the sender and to protect the integrity of the message. The basis for authentication is that only the sender and the receiver would know the security key used to generate the MAC. Because of the characteristic of the secure hash function, if any bit in the message is altered during transmission, the transmitted MAC would differ from the one recomputed at the receiver. Hence, the MAC is also used as a form of checksum with much stronger protection than traditional checksum method such as CRC16.

In conventional systems, communication between a client and server is done over a session. Hence, security mechanisms were designed around this need. At the beginning of the session, the client and the server would mutually authenticate each other. Once the authentication step is done, a session key would be created and used to encrypt all messages exchanged within the session. For a prolonged session, the session key might be refreshed. For sessions conducted over the Web, the secure socket layer (SSL) (or transport layer security) protocol is typically used. The server authentication is done via a digital signature and public-key certificate protected by a public-key infrastructure. Client authentication is typically done via user-name and password. Some enterprise systems, such as directory services, adopt much more sophisticated authentication algorithms based on the challenge-response approach.

## REFERENCES

- 1. A. Avizienis and L. Chen. On the implementation of n-version programming for software fault tolerance during execution. In Proceedings of the IEEE International Computer Software and Applications Conference, pages 149–155, 1977.
- 2. A. Avizienis, J. C. Laprie, B. Randell, and C. Landwehr. Basic concepts and taxonomy of dependable and secure computing. IEEE Transactions on Dependable and Secure Computing, 1(1):11–33, 2004.
- 3. M. Y. Chen, E. Kiciman, E. Fratkin, A. Fox, and E. Brewer. Pinpoint: Problem determination in large, dynamic internet services. In Proceedings of the 2002 International Conference on Dependable Systems and Networks, DSN ’02, pages 595–604, Washington, DC, USA, 2002. IEEE Computer Society.
- 4. M. Franz. Understanding and countering insider threats in software development. In Proceedings of the International MCETECH Conference on e-Technologies, pages 81–90, January 2008.
- 5. L. Lamport, R. Shostak, and M. Pease. The byzantine generals problem. ACM Transactions on Programming Languages and Systems, 4:382–401, 1982.
- 6. P. M. Melliar-Smith and B. Randell. Software reliability: The role of programmed exception handling. In Proceedings of an ACM conference on Language design for reliable software, pages 95–100, New York, NY, USA, 1977. ACM.
- 7. C. P. Pfleeger, S. L. Pfleeger, and J. Margulies. Security in Computing (5th Ed.). Pearson, 2015.
- 8. B. Randell and J. Xu. The evolution of the recovery block concept. In Software Fault Tolerance, pages 1–22. John Wiley & Sons Ltd, 1994.
- 9. J. Shore. Fail fast. IEEE Software, pages 21–25, September/October 2004.
- 10. A. S. Tanenbaum and M. V. Steen. Distributed Systems: Principles and Paradigms. Prentice Hall, 2nd edition, 2006.
- 11. A. S. Tanenbaum and D. J. Wetherall. Computer Networks (5th Ed.). Pearson, 2010.
- 12. L. Tewksbury, L. Moser, and P. Melliar-Smith. Live upgrade techniques for corba applications. In New Developments in Distributed Applications and Interoperable Systems, volume 70 of IFIP International Federation for Information Processing, pages 257–271. Springer US, 2002.

## Logging and Checkpointing

Checkpointing and logging are the most essential techniques to achieve dependability in distributed systems [7]. By themselves, they provide a form of fault tolerance that is relatively easy to implement and incurs low runtime overhead. Although some information could be lost (if only checkpointing is used) when a fault occurs and the recovery time after a fault is typically larger than that of more sophisticated fault tolerance approaches, it may be sufficient for many applications. Furthermore, they are used in all levels of dependability mechanisms.

A checkpoint of a distributed system refers to a copy of the system state [7]. If the checkpoint is available after the system fails, it can be used to recover the system to the state when the checkpoint was taken. Checkpointing refers to the action of taking a copy of the system state (periodically) and saving the checkpoint to a stable storage that can survive the faults tolerated.

To recover the system to the point right before it fails, other recovery information must be logged in addition to periodical checkpointing. Typically all incoming messages to the system are logged. Other nondeterministic events may have to be logged as well to ensure proper recovery.

Checkpointing and logging provide a form of rollback recovery [7] because they can recover the system to a state prior to the failure. In contrast, there exist other approaches that accomplish roll-forward recovery, that is, a failed process can be recovered to the current state by incorporating process redundancy into the system. However, roll-forward recovery protocols typically incur significantly higher runtime overhead and demand more physical resources.

### 2.1 System Model

In this section, we define the system model used in the checkpointing and logging algorithms introduced in this chapter. The algorithms are executed in a distributed system that consists of N number of processes. Processes within the system interact with each other by sending and receiving messages. These processes may also interact with the outside world by message exchanges. The input message to the distributed system from the outside world is often a request message sent by the user of the system. The output message from the system is the corresponding response message. An example distributed system consisting of 4 processes is shown in Figure 2.1.

![](img/7320b1480d74f1d65f74659cab456782_53_0.png)

Figure 2.1 An example distributed system.

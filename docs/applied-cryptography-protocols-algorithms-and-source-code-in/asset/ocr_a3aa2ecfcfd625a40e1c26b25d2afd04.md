# 10.5 Hardware Encryption versus Software Encryption

and key management for banks; dedicated encryption boxes for communications links, and boards that plug into personal computers.

Some encryption boxes are designed for certain types of communications links, such as T-1 encryption boxes that are designed to encrypt synchronization bits. There are different boxes for synchronous and asynchronous communications lines. Newer boxes detect to accept higher rates and are more versatile.

Even so, many of these devices have some incompatibilities. Buyers should be aware of this and may be well-versed in their particular needs, lest they find themselves the owners of encryption equipment unable to perform the task at hand. Pay attention to restrictions in hardware type, operating system, applications software, network, and soft.

PC-board encoders usually encrypt everything written to the hard disk and can be configured to encrypt everything to the floppy disk and serial port as well. These boards are not shielded against electromagnetic radiation or physical interference, since there would be no benefit in protecting the boards if the computer remains unaffected.

More companies are starting to put encryption hardware into their communications. Secure telephones, facsimile machines, and modems are all available.

Internal key management for these devices is generally secure, although there are many different schemes as there are encryption vendors. Some schemes are more suited for one situation than another, and buyers should know what kind of key management is incorporated into the encryption box and what they expect to provide themselves.

# Software

Any encryption algorithm can be implemented in software. The disadvantages are in speed, cost, and ease of modification or [manipulation]. The advantages are in flexibility and portability, ease of use, and ease of upgrade. The algorithms written in C at the end of this book can be implemented, with little modification, on any computer. They can be inexpensively copied and installed on many machines. They can be incorporated into larger applications, such as communications programs or word processors.

Software encryption programs are popular and available for all major operating systems. These are made to protect individual files, the user generally has to manually encrypt and decrypt specific files. It is important that the key management be secure: The keys should not be stored on any disk (or even written to a place in memory where the processor swaps out to disk). Key unencrypted files should be erased after encryption. Many programs are sloppy in this regard, and a user has to choose carefully.

Of course, Mallory can always replace the software encryption algorithm with something lousy. For most users, that isn't a problem. If Mallory can break into our office and modify our encryption program, he can also put a hidden camera on the wall, a wiretap on the telephone, and a TEMPEST detector down the street. Mallory is that much more powerful than the user, the user has lost the game before it starts.
# CHAPTER 3 Basic Protocols

cannot decrypt it with his private key and re-encrypt it with Bob's public key. He must invent a totally new message and send half of it to Bob. When he intercepts half of Bob's message to Alice in step [4], he has the same problem. He cannot decrypt it with his private key and re-encrypt it with Alice's public key. He has to invent a totally new message and send half of it to Alice. By the time he intercepts the second halves of the real messages in step [5) and (6), it is too late for him to change the new messages he invented. The conversation between Alice and Bob will necessarily be different.

Mallory could easily get away with this scheme. If he knows Alice and Bob well enough to mimic both sides of a conversation between them, they might never realize that they are being duped. But surely this is much harder than sitting the two of them, intercepting and reading their messages.

# Key Exchange with Digital Signatures

Implementing digital signatures in a session-exchange protocol circumvents this man-in-the-middle attack well. Trent signs both Alice and Bob's public keys. The signed keys include a signed certification of ownership. When Alice and Bob receive the keys, each verify Trent's signature. Now they know that the public key belongs to that other person. The key exchange could then proceed.

Mallory has serious problems. He cannot impersonate Alice or Bob because he doesn't know either of their private keys. He cannot substitute public key for either of theirs, unless he has one signed by Trent, it is signed by Mallory. All he can do is listen to the encrypted traffic go back and forth or disrupt the lines of communication and prevent Alice and Bob from talking.

This protocol uses Trent, the risk of compromising the KDC is less than Trent's private key. It enables him only to sign new keys; it decrypt any session keys or any message traffic. To read the traffic, Mallory has to impersonate one of the users on the network and legitimate legitimate users into encrypting messages with his public key.

Mallory can launch that kind of attack. With Trent's private key, he can create phony signed keys to fool Alice and Bob. Then, he can exchange them in the database for real users' requests and reply with his phony keys. This enables him to launch a man-in-the-middle attack and read people's communications.

This attack will work, but remember that Mallory has to be able to intercept and modify messages. In some networks this is a lot more than passively sitting on a network reading messages as they go. On a broadcast channel, it is almost impossible to replace one message with another—the entire network can be jammed. On computer networks this is easier and seems to be getting easier every day. Consider IP spoofing, router attacks, and so forth, active attacks don't necessarily mean someone down a manhole with a mancope, and they are not limited to three-letter agencies.
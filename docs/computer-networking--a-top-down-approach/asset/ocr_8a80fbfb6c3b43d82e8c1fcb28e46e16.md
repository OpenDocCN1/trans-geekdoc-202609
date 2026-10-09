+   R11. Consider a variation of the MAC algorithm (Figure 8.9) where the sender sends $(m, H(m)+s)$, where $H(m)+s$ is the concatenation of $H(m)$ and $s$. Is this variation flawed? Why or why not?

+   R12. What does it mean for a signed document to be verifiable and nonforgeable?

+   R13. In what way does the public-key encrypted message hash provide a better digital signature than the public-key encrypted message?

+   R14. Suppose certifier.com creates a certificate for foo.com. Typically, the entire certificate would be encrypted with certifier.com's public key. True or false?

+   R15. Suppose Alice has a message that she is ready to send to anyone who asks. Thousands of people want to obtain Alice's message, but each wants to be sure of the integrity of the message. In this context, do you think a MAC-based or a digital-signature-based integrity scheme is more suitable? Why?

+   R16. What is the purpose of a nonce in an end-point authentication protocol?

+   R17. What does it mean to say that a nonce is a once-in-a-lifetime value? In whose lifetime?

+   R18. Is the message integrity scheme based on HMAC susceptible to playback attacks? If so, how can a nonce be incorporated into the scheme to remove this susceptibility?

# **SECTIONS 8.5–8.8**

+   R19. Suppose that Bob receives a PGP message from Alice. How does Bob know for sure that Alice created the message (rather than, say, Trudy)? Does PGP use a MAC for message integrity?

+   R20. In the TLS record, there is a field for TLS sequence numbers. True or false?

+   R21. What is the purpose of the random nonces in the TLS handshake?

+   R22. Suppose an TLS session employs a block cipher with CBC. True or false: The server sends to the client the IV in the clear.

+   R23. Suppose Bob initiates a TCP connection to Trudy who is pretending to be Alice. During the handshake, Trudy sends Bob Alice's certificate. In what step of the TLS handshake algorithm will Bob discover that he is not communicating with Alice?

+   R24. Consider sending a stream of packets from Host A to Host B using IPsec. Typically, a new SA will be established for each packet sent in the stream. True or false?

+   R25. Suppose that TCP is being run over IPsec between headquarters and the branch office in Figure 8.28. If TCP retransmits the same packet, then the two corresponding packets sent by R1 packets will have the same sequence number in the ESP header. True or false?
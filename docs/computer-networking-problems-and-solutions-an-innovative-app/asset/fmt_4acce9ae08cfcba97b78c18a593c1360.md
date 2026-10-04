
Any kind of security should not only examine how you can protect information, but also consider the different ways in which you can cause the protection of data to fail. Given no system is perfect, there will always be some way you can attack the system successfully. If you know the kinds of attacks that can be successfully launched against a transport security system, you can try to design the network and environment in a way that prevents these attacks from being used. Man-in-the-middle (`MitM`) attacks are common enough that they are worth considering in some detail. [Figure 10-5](#ch10.xhtml#ch10fig05) illustrates.

![Image](graphics/10fig05.jpg)

**Figure 10-5** *A Man-in-the-Middle Attack*

[Figure 10-5](#ch10.xhtml#ch10fig05) is similar to [Figure 10-3](#ch10.xhtml#ch10fig03) with one addition: there is a host, B, situated between the host A and the server C that would like to start an encrypted session. By some means, either spoofing C’s IP address, or modifying the Domain Name Service (`DNS`) records so C’s name resolves to B’s address, or perhaps even modifying the routing system so traffic that should be delivered to C is delivered to B instead, the attacker has caused B to receive traffic originating at A and destined to C. In [Figure 10-5](#ch10.xhtml#ch10fig05):

1. Host A sends a semirandom number, called a `nonce`, to C. This information is received by B.
2. Host B, which the attacker is using as the `MitM`, transmits this `nonce` on to C in a way that makes it appear the packet actually originated at A. At this point, the attacker knows the `nonce` encrypted by A; the attacker does not know A’s private key but does have access to anything A sends encrypted with A’s private key.
3. The server, C, sends a response with an encrypted `nonce`, as well. B receives this and records it.
4. Host B passes the `nonce` it received from C on to A. Host A will still believe this packet came directly from C.
5. Host B calculates a private key with A as if it were C.
6. Host B calculates a private key with C as if it were A.

Any traffic A sends to C will be received by B, which will

• Unencrypt the data A has transmitted using the private key calculated at step 5 in [Figure 10-5](#ch10.xhtml#ch10fig05).
• Encrypt the data A has transmitted using the private key calculated at step 6 in [Figure 10-5](#ch10.xhtml#ch10fig05) and transmit it to C.

During this process, the attacker, at B, has access to the entire flow, in plaintext, between A and C. Neither A nor C realizes they have both built an encrypted session to B, rather than to one another. These kinds of `MitM` attacks are very difficult to prevent and detect.

### Transport Layer Security

Transport Layer Security (`TLS`), also known as the *Secure Socket Layer* (`SSL`), is a secure transport layer protocol deployed by default in most web browsers. When users see the small green lock indicating that a website is “safe,” this means the `SSL` certificate is valid, and the traffic between the host (on which the browser runs) and the server (on which the web server runs) is being encrypted. `TLS` is a complex protocol with a lot of different options; this section will provide a rough overview of its operation. [Figure 10-6](#ch10.xhtml#ch10fig06) illustrates the components of the `TLS` suite.

![Image](graphics/10fig06.jpg)

**Figure 10-6** *TLS Components*

In [Figure 10-6](#ch10.xhtml#ch10fig06):

• The **handshake protocol** is responsible for initializing sessions and setting up session parameters, including the initial private key exchange.
• The **alert protocol** is responsible for error handling.
• The **change cipher specification** is responsible for starting the encryption.
• The **record protocol** breaks data blocks presented for transport into fragments, (optionally) compresses the data, adds a Message Authentication Code (`MAC`), encrypts the data using the symmetrical key, adds the original information to the block, and then sends the block to the Transmission Control Protocol (`TCP`) for transport across the network.

Applications running on top of `TLS` use a special port number to access the service through `TLS`. For instance, web services using the Hypertext Transfer Protocol (`HTTP`) are normally accessible over `TCP` port 80; `TLS`-encrypted `HTTP` is normally accessible through port 443. While the service is the same, the change in the port number allows the `TCP` process to direct traffic that needs to be unencrypted for the final application to read it.

The `MAC`, which within this context will mean a Message Authentication Code, is used to ensure the sender is authenticated. While some cryptography systems assume that successfully encrypting data with a key the receiver knows proves the sender is truly who he claims to be, `TLS` does not. Instead, `TLS` includes a `MAC` that validates the sender separately from the keys used to encrypt messages on the wire. This helps prevent `MitM` attacks against `TLS`-encrypted data streams.

[Figure 10-7](#ch10.xhtml#ch10fig07) shows the `TLS` startup handshake, which is managed by the handshake protocol.

![Image](graphics/10fig07.jpg)

**Figure 10-7** *TLS Secure Session Startup Process (Handshake)*

In [Figure 10-7](#ch10.xhtml#ch10fig07):

1. The `client hello` is sent in plaintext, and contains information about the version of `TLS` the client is running, 32 random octets (the `nonce`), a `session identifier` (which allows a previous session to be recovered or restored), a list of the encryption algorithms (`cipher suites`) the client supports, and a list of the data compression algorithms the client supports.
2. The `server hello` is sent in plaintext, as well, and contains the same information as above, from the server’s perspective. In the `server hello`, the encryption algorithm field indicates the kind of encryption that will be used for this session. This is normally the “best” encryption algorithm available at both the client and the server (although it is not always the “best”).
3. The server sends its public key (a certificate), along with the `nonce` that the client sent to the server, where the `nonce` is now encrypted using the server’s private key.
4. The `server hello done` message indicates the client now has the information it needs to complete the session setup.
5. The client generates a private key and uses the server’s public key to encrypt it. This is transmitted in the `client key exchange` message toward the server.
6. Once this has been transmitted, the client must sign *something* known to both the server and the client in order to verify the sender is the correct device. Usually, the signature is across all the messages in the exchange up to this point; generally, a cryptographic hash is used to generate a verification.
7. The `change cipher specification` message essentially acknowledges the session is up and running.
8. The `finished` message once again authenticates all the previous handshake messages to this point.
9. The server then acknowledges the encryption session is set up by sending a `change cipher specification` message.
10. The server then sends a `finished` message, which authenticates the prior messages sent in the handshake in the same way as above.

**Note**

Optional steps in the `TLS` handshake have been left out of this explanation for clarity.

Once the session is up and running, applications can send information toward the receiving host on the correct port number. This data will be encrypted using the previously negotiated private key and then handed off to `TCP` for delivery.

### Final Thoughts on Transport Security

connection do anything else, they must negotiate a specific cipher suite for the communication session. (Other cryptographic system standards use different names for combinations of methods and options.)

> A cipher suite is a specific set of options for a particular cryptographic system standard.

**INITIAL AUTHENTICATION**  The second handshaking stage is **initial authentication**. Messages can be sent by **impostors**, so before two parties begin communication, they need to **authenticate** each other, that is, test the identity of their communication partner. This is called initial authentication because it is done before communication begins. As noted later in this section, there may also be subsequent message-by-message authentication for each message the two parties send.

When both parties authenticate themselves, this is **mutual authentication**. Sometimes, however, authentication is only done by one party. When you log into a server, for instance, you must authenticate yourself to the server, but the server usually does not authenticate itself to you.

> In authentication, communication partners prove their identities to each other.

Note that initial authentication takes place *after* the negotiation stage. The reason for this is very simple. Until the two parties negotiate authentication methods and options within these methods, they cannot begin authentication.

**KEYING**  The third stage is keying. As noted earlier, confidentiality ciphers require keys. As we will see later, authentication requires **secrets**. Both keys and secrets are simply long strings of bits that must be kept secret between the two parties. In most cases, keys and secrets must be sent securely. Sending keys or secrets securely is generally called **keying**. We will see two keying methods later in this chapter.

Note that keying comes *after* authentication. This is necessary because a number of keying methods are vulnerable to key stealing by third parties unless authentication is done first.

# Ongoing Communication

After the two sides have authenticated each other and keys have been exchanged, the handshaking stages are over. The ongoing communication begins and the two parties send many messages back and forth. The two parties usually apply several cryptographic protections during ongoing communication on a message-by-message basis.

+   - First, the sender adds an **electronic signature** to each message. This allows the receiver to authenticate each message. **Message-by-message authentication** thwarts efforts by impostors to insert messages into the dialogue stream.
+   - Second, all good electronic signature technologies also provide **message integrity**, which means that if an attacker captures and alters a message (e.g., changing a customer’s bank balance amount), the authentication process will reject the message.
+   - Third, the sender encrypts the combined message and electronic signature for confidentiality.
3. The second part of the message is encrypted using $K_b$, that is, master key shared between the KDC and “B.” It includes the following data items, intended to be delivered to “B.” Since it is encrypted $K_b$, “A” cannot tamper with it.

+   - One-Time Session Key $K_s$, to be used for the session

+   - An identifier of W (network address of “A”, i.e., $ID_A$)

These data items are used by “B” to establish connection with “A.”

+   4. “A” decrypts the portion of the message encrypted with $K_s$, recovers the session key $K_s$, and saves it for use in the upcoming session. Since this portion of the message is encrypted using $K_s$, it is also verified that this message has originated at KDC.

+   5. Also, “A” forwards $E_{K_b}[K_s || ID_A]$ to “B.” Because it is encrypted with $K_b$, only “B” can read it. “B” decrypts the message, recovers $K_s$, and saves it for use in next session with “A.” Now, “B” has the session key $K_s$, and also knows the identity of the other party $ID_A$.

+   6. Encrypted with session key $K_s$, “B” sends a Nonce $N_2$ to “A.”

+   7. “A” responds to “B” $f(N_2)$ encrypted using $K_s$.

The last two steps are meant to provide mutual authentication between “A” and “B.”

# Limitations of Centralized Key Control using KDC:

+   1. The scheme is based on the trust placed by all users in the KDC. The trust may be betrayed.

+   2. If KDC fails, then the scheme will be rendered non-functional. It is an “all eggs in one basket” situation.

# 6.10.2.2 Decentralized Key Distribution

The Decentralized Key Control Scheme attempts to obviate the limitations of the Centralized KDC-based Key Distribution Scheme. The Decentralized Scheme is based on the concept that each end-user must be able to establish secure connection with any other end-user independently. Figure 6.27 illustrates the Decentralized Key distribution schemes.
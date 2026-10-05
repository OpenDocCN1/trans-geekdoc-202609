# 3.3 Authentication and Key Exchange

[644]. If the sender's clock is ahead of the receiver's clock, Mallory can intercept a message from the sender and reply it later when the timestamp becomes current at the receiver's site. This attack is called suppress-replay and can have irritating consequences.

This protocol, first presented in [820] and corrected in [1162] attempts to counter the suppress-replay attack. It is an enhancement to Yahalom and is an excellent protocol.

+   (1) Alice concatenates her name and a random number and sends it to Bob.
$A_A,R_A$

+   (2) Bob concatenates Alice's name, random number, and a timestamp, and encrypts with the key he shares with Trent. He sends it to Trent along with his name and a random number.
$B_B,E_B(A,R_A,T_B)$

+   (3) Trent generates a random session key. Then he creates two messages. The first is Bob's name, Alice's random number, a random session key, and the timestamp, all encrypted with the key he shares with Alice. The second is Alice's name, the session key, and the timestamp, all encrypted with the key he shares with Bob. He sends both to Alice, along with Bob's random number.
$E_A(E_B(A,K,T_B),E_A(A,K,T_B),R_B$

+   (4) Alice decrypts the message encrypted with her key, extracts $K$, and confirms that $R_A$ has the same value as it did in step [1]. Alice sends Bob messages. The first is the message received from Trent, encrypted with Bob's key. The second is $R_B$, encrypted with the session key.
$E_B(E_A(A,K,T_B),E_A(R_B)$

+   (5) Bob decrypts the message encrypted with his key, extracts $K$, and confirms that $T_B$ and $R_B$ have the same value they did in step [2].

Assuming both random numbers and the timestamp match, Alice and Bob are convinced of one another identity and a secret key. Synchronized clocks are not required because the timestamp is only relative to Bob's clock; Bob only checks the timestamp he generated.

One thing about this protocol is that Alice can use the message she received from Trent for subsequent authentication with Bob, within some predetermined time limit. Assume that Alice and Bob completed the above protocol, communicated, and then terminated the connection. Alice and Bob reauthenticate in three steps, without to rely on Trent.

+   (1) Alice sends Bob the message Trent sent in step [3] and a new random number.
$E_B(A,K,T_B),R'_A$
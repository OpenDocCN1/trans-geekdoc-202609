# 520 CHAPTER 22 Key-Exchange Algorithms

[2] Bob picks a random number, $r_B$, and calculates
K = g^A \cdot r_B \pmod n$

He generates a string $R_B$, then calculates and sends to Alice:
$E_K(g^B \pmod n), E_K(R_B)$

[3] Alice decrypts the first half of Bob's message to obtain $g^B \pmod n$. Then she calculates $K$ and uses $K$ to decrypt $R_B$. She generates another random string, $R_A$, encrypts both strings with $K$, and sends Bob the result.
$E_K(R_A, R_B)$

[4] Bob decrypts the message to obtain $R_A$ and $R_B$. Assuming the $R_B$ he received from Alice is the same as the one he sent to Alice in step (2), he encrypts $R_A$ with $K$ and sends it to Alice.
$E_K(R_A)$

[5] Alice decrypts the message to maintain $R_A$. Assuming the $R_A$ she received from Bob is the same as the one she sent to Bob in step (3), the protocol is complete. Both parties now communicate using $K$ as the session key.

# Strengthening EKE

Bellovin and Merritt suggest an enhancement of the challenge-response portion of the protocol—to prevent a possible attack if a cryptanalyst recovers an old K value.
Look at the basic EKE protocol. In step (3), Alice generates another random number, $S_A$, and sends Bob
$E_K(R_A, S_A)$

In step (4), Bob generates another random number, $S_B$, and sends Bob
$E_K(R_A, R_B, S_B)$

Alice and Bob now both calculate the true session key, $S_A \oplus S_B$. This key is used for all future messages between Alice and Bob, Bob is just as a key-exchange key.
Look at the levels of protection EKE provides. A recovered value of S gives Eve information about $P$, because $P$ is never used to encrypt anything that leads directly to a cryptographic attack. Attack on K is also not possible; K is used just to encrypt random data, and $S$ is never encrypted alone.

# Augmented EKE

The EKE protocol suffers from one serious disadvantage: It requires that both parties possess the $P$. Most password-based authentication systems store a one-way hash of the user's password, not the password itself (see Section 3.2). The Augmented EKE [A-EKE] protocol uses a one-way hash of the user's password as the
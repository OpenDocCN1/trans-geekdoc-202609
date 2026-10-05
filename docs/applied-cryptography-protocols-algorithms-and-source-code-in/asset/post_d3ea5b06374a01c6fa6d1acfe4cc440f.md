
# 520 CHAPTER 22 Key-Exchange Algorithms

[2] Bob picks a random number, $r_B$, and calculates
$K = g^A \cdot r_B \pmod n$

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
Look at the levels of protection EKE provides. A recovered value of $S$ gives Eve information about $P$, because $P$ is never used to encrypt anything that leads directly to a cryptographic attack. Attack on K is also not possible; K is used just to encrypt random data, and $S$ is never encrypted alone.

# Augmented EKE

The EKE protocol suffers from one serious disadvantage: It requires that both parties possess the $P$. Most password-based authentication systems store a one-way hash of the user's password, not the password itself (see Section 3.2). The Augmented EKE [A-EKE] protocol uses a one-way hash of the user's password as the

# 22.5 Encrypted Key Exchange 521

superencryption key in the Diffie-Hellman variant of EKE. The user then sends an extra message based on the original password, this message authenticates the newly chosen key.

Here's how it works. As usual, Alice and Bob want to authenticate each other and generate a common key. They agree on some digital signature scheme where any number can serve as the private key, and the public key is derived from the private key, rather than being generated along with it. The ElGamal and DSA algorithms work with the private key. Alice's password $P$ (or perhaps some simple hash of it) will serve as the private key and as $P'$.

- (1) Alice picks her random exponent $R_b$ and transmits
$E_P^{R_b} \mod n$

- (2) Bob, who knows only $P'$ and cannot derive $P$ from it, chooses $R_b$ and sends
$E_P^{R_b} \mod n$

- (3) Alice and Bob calculate the shared session key $K = g^{A' \cdot b} \mod n$.
Finally, Alice proves that she knows $P$ itself, and not just $P'$, by sending $E_K(S(K))$

Bob, who knows $K$ and $P'$, can decrypt and validate the signature. Only Alice could have sent this message, since she knows $P$; an intruder who obtains a copy of Bob's password file by trying at $P$, but cannot otherwise see the session key.

The A-EKE scheme does not work with the public-key variant of EKE, since in it one party chooses the session key and imposes it on the other. This permits a man-in-the- attack by an attacker who has captured $P'$.

# Applications of EKE

Bellovin and Merritt suggest using this protocol for secure telephones.
Let us assume one of these phones, some sorting of key information must be provided. Conventional solutions require that the caller possess a physical key. This is undesirable in many situations. EKE permits use of a keypad, but uses a much longer key for the call.

EKE would also be useful with cellular phones. Fraud has been a problem in the cellular industry, EKE can defend against and ensure the privacy of the call by rendering phone useless if PIN has not been entered. Since the PIN is not stored within the phone, it is not possible to retrieve one from stolen unit.

EKE's primary strength is that both symmetric and public-key work together in a manner that strengthens them: From a general perspective, EKE functions as a privacy amplifier. That is, it can be used to strengthen comparatively weak symmetric and asymmetric systems.

544 CHAPTER 22 Key-Exchange Algorithms

Consider, for example, the key size needed to maintain security when using exponential key exchange. As Odlycko have shown, even modulus sizes once believed to be safe (192 bits) are vulnerable to attack requiring only a few minutes of computer time. But their attack is not feasible if one must first guess password before applying it. Conversely, the difficulty of cracking exponential key exchange increases dramatically.

# 22.6 FORTIFIED KEY NEGOTATION

This scheme also protects negotiation from poorly chosen passwords and man-in-the- attacks. It uses a hash function of two variables that has a very special property: it has many collisions on the first variable while having no collisions on the second.

$H'(x, y) = H(k, x) \bmod 2^y$, where $H(k, x)$ is an ordinary hash function on $k$ and $x$.

Here's the protocol. Alice and Bob share a secret password, $P$, and have just exchanged a secret key, $K$, using Diffie-Hellman key exchange. They use $P$ to check that their two session keys are the same (and that Eve is not attempting man-in-the- attack), without giving $P$ away to Eve.

- Alice sends Bob $H'(P, K)$

- Bob computes $H'(P, K)$ and compares his result with what he received from Alice.

- He sends Alice $H'(P, K)$

- Alice computes $H'(P, K)$ and compares her result with what she received from Bob.

If Eve is trying man-in-the- attack, she shares one key, $K_1$, with Alice, and another key, $K_2$, with Bob. To fool Bob in step (2), she has to figure out the shared password and then send $H'[P, K_2]$. With a normal hash function she can try common passwords until she guesses the correct one, and then infiltrate the protocol. But with this hash function, many passwords are likely to produce the same value when hashed with $K_1$. So when she finds a match, she will probably have the wrong password, and hence Bob will not be fooled.

545 22.7 Conference Key Distribution and Secret BROADCASTING

Alice wants to broadcast a message, $M$, from a single transmitter. However, she doesn't want it to be intelligible by every listener. In fact, she only wants a select subset of listeners to be able to recover $M$. Everyone else should get nonsense.

Alice can share a different key (secret or public) with each listener. She encrypts the message in some random key, $K$. She then encrypts a copy of $K$ with each of her intended recipients. Finally, she decrypts the encrypted message and all of the encrypted keys with her secret key, looking for the correct one, or, if Alice doesn't mind knowing whose message was, he looks for his name followed by an encrypted multiple-key cryptography, previously discussed works.

Another method is suggested in [35]. First, each listener shares a secret key with Alice, that is larger than any possible encrypted message. All of those keys should be pairwise prime. She encrypts the message in a random key, $K$. Then she computes a single integer, $R$, such that $R$ modulo secret key is congruent to $K$ when secret key is supposed to decrypt the message, and $R$ modulo secret key is otherwise congruent to zero.

For example, if Alice wants the secret to be received by Bob, Carol, and Ellen, but not by Dave and Frank, she encrypts the message with $K$ and computes R such that:

$R = K \pmod{K_B}$
$R = K \pmod{K_C}$
$R = 0 \pmod{K_D}$
$R = K \pmod{K_E}$
$R = 0 \pmod{K_F}$

This is a straightforward algebra problem, one that Alice can solve easily. When listeners receive the broadcast, they compute the received key modulo their secret key. If they were intended to receive the message, they recover it. Otherwise, they recover nothing.

Yet another way, using a threshold scheme (see Section 3.7), is suggested in [141]. Like the others, every potential receiver gets a secret key. This key is a shadow in a yet-uncreated threshold scheme. Alice saves some secret keys for herself, adding some randomness to the system. Let's say there are $k$ people out there.

Then, to broadcast $M$, Alice encrypts $M$ with key $K$ and does the following:

- (1) Alice chooses a random number, $j$. This number serves to hide the number of recipients of the message. It doesn't have to be very large; it can be as small as 0.

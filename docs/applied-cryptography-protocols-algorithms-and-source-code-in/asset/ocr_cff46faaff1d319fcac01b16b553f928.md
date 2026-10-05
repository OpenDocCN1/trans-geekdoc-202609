# 3.3 Authentication and Key Exchange 59

Trent's message is legitimate and not a replay of a response from a previous execution of the protocol. When Alice successfully decrypts $R_b$ and sends Bob $R_b - 1$ in step [5], Bob is ensured that Alice's messages are not replays from an earlier execution of the protocol.

The major security hole in this protocol is that old keys are valuable. Mallory gets access to an old K, he can launch a successful attack [461]. All he has to is record Alice's messages to Bob in step [3]. Then, once he has K, he can pretend to be Alice:

+   1) Mallory sends Bob the following message:
$E_b[K,A]$
2) Bob extracts K, generates $R_b$, and sends Alice:
3) Mallory intercepts the message, decrypts it with K, and sends Bob:
$E_b[R_b - 1]$
4) Bob verifies “Alice's” message is $R_b - 1$.

Now, Mallory has Bob convinced that he is Alice.
A stronger protocol, using timestamps, can defeat this attack [461,456]. A timestamp is added to Trent's message in step [2] encrypted with Bob's key: $E_b[K,A,T]$. Timestamps require a secure and accurate system clock—not a trivial problem itself.

If the key shares with Alice is ever compromised, the consequences are drastic. Mallory can use it to send session keys to talk Bob (or anyone else he wishes to talk to). Even worse, Mallory can continue to do this even after Alice changes her key [90].

Needham and Schroeder attempted to correct these problems in a modified version of their protocol [1160]. Their new protocol is essentially the same as the Otway-Rees protocol, published in the same issue of the journal.

# Outway-Rees

This protocol uses symmetric cryptography [1224].

+   1) Alice generates a message consisting of an index number, her name, Bob's name, and a random number, all encrypted in the key she shares with Trent. She sends this message to Bob along with the index number, her name and his name:
$I,A,B,E_a(R_a,I,A,B)$
2) Bob generates a message consisting of a new random number, the index number, Alice's name, and Bob's name, encrypted in the key he shares with Trent. He sends this to Alice, along with Alice's encrypted message, the index number, her name, and his name:
$I,A,B,E_a(R_a,I,A,B),E_b(R_b,I,A,B)$
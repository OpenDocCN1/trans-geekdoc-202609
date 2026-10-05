# 4.12 One-Way Accumulators

+   (4) The KDC sends the encrypted keys, one by one, onto the network.
(5) Alice chooses a key at random.
(6) Alice encrypts the key with her public key.
(7) Alice waits a while (long enough so the server has no idea what key she has chosen) and sends the double-encrypted key back to the KDC.
(8) The KDC decrypts the double-encrypted key with its private key, leaving a key encrypted with Alice's public key.
(9) The server sends the encrypted key back to Alice.
(10) Alice decrypts the key with her private key.

Eve, sitting in the middle of this protocol, has no idea what Alice chose. She sees a continuous stream of keys go by in step [4]. When Alice sends the key back to the server in step [7], it is encrypted with her public key, which is also secret in this protocol. Eve has no way of correlating it with the stream of keys. When the server sends the key back to Alice in step [9], it is encrypted with Alice's public key. When Alice decrypts the key in step [10] is the key revealed.
If you use RSA, this protocol leaks information at the rate of one per message. It's quadratic residues again. If you're going to distribute keys in this manner, make sure this leak isn't enough to matter. Also, the stream of keys from the KDC must be great enough to preclude a brute-force attack. Of course, if Alice can't trust the KDC, then she shouldn't getting keys from it. A malicious KDC could presumably keep records of every key it generates. Then, it could search them all to determine which is Alice's.
This protocol also assumes that Alice is going to act fairly. There are things she can do, using RSA, to get more information than might otherwise. This is not a problem in our scenario, but it can be in other circumstances.

# 4.12 ONE-SCENARIO ACCUMULATORS

Alice is a member of Cabal. Occasionally she has to meet with other members in dimly lit restaurants and whispers secrets back and forth. The problem is that the restaurants are so dimly that she has trouble knowing if the person across the table is from Alice.

Cabal can choose from several solutions. Every member can carry a member-ship list. This has two problems. Everyone now has to carry a large database, and they have to guard their membership list perfectly carefully. Alternatively, a trusted secretary could issue digitally signed ID cards. This has added the advantage of allowing others to verify members (for discounts at the local grocery store, for example), but it requires a trusted secretary. Not by Cabal, Alice can be trusted to that degree.

A novel solution is to use something called a one-way accumulator [116]. This is sort like a one-way hash function, except that it is commutative. In this, it is possible to hash the database of members in any order and get the same value. More-
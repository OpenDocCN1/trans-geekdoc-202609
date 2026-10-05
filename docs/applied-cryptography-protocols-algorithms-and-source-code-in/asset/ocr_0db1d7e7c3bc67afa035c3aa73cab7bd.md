# CHAPTER 4 Intermediate Protocols

This protocol isn’t secure against collusion among malicious players. Alice and another player can effectively gang up on the third and throwable player out of everything without raising suspicion. Therefore, it is important to check all the keys and random strings every time the players reveal their hands. And if you're sitting around the virtual table with two people who never reveal their hands when one of them is the dealer (Alice, in the below), stop playing.

Understand that this is all an interesting theory, actually implementing it on a computer is an arduous task. A Sparc implementation with three players on separate workstations takes eight hours to shuffle a deck of cards, let alone play an actual game [513].

# Attacks against Poker Protocols

Cryptographers have shown that a small amount of information is leaked by poker protocols if the RSA public-key algorithm is used [453,573]. Specifically, if the binary representation of the card is a quadratic residue [see Section 11.3], then the encryption of the card is also a quadratic residue. This property can be used to mark cards all the aces, for example. This does not reveal much about the hands, but in a game such as poker even a tiny bit of information can be an advantage in the long run.

Shafi Goldwasser and Silvio Micali [624] developed a two-player mental-poker protocol that fixes the problem, although complexity makes it far more theoretical than practical. A general n-player poker protocol that eliminates the problem of information leakage was developed in later [389].

Other research on poker protocols can be found in [573,1634,389]. A complicated protocol that allows players to not reveal their hands can be found in [390]. Coppersmith discusses two ways to cheat at mental poker using the RSA algorithm [370].

# Anonymous Key Distribution

While it is unlikely that anyone is going to use this protocol to play poker via modem, Charles Pleeeger discusses a situation in which this type of protocol would come in handy [1244].

Consider the problem of key distribution. If we assume that players cannot generate their keys (they might have to of a certain form, or have to be signed by some organization, or something similar), we set up a Key Distribution Center to generate and distribute keys. The problem is that we have to figure out some way of distributing keys such that no one, including the server, can figure out who got which key.

This protocol solves the problem:

+   - Alice generates a public-key/private-key key pair. For this protocol, he keeps both keys secret.
- The KDC generates a continuous stream of keys.
- The KDC encrypts the keys, one by one, with its own public key.

## Flipping Coins into a Well

It is interesting to note that in all these protocols, Alice and Bob don't learn the result of the coin flip at the same time. Each protocol has a point where one of the parties (Alice in the first two protocols and Bob in the last) knows the result of the coin flip but cannot change it. That party can, however, delaying the result to the other party. This is known as flipping coins into a well. Imagine Alice is next to the well and Bob is far away. Bob throws the coin and it lands in the well. Alice can now look into and see the result, but she cannot reach down to change it. Bob cannot see the result until Alice lets him close enough to look.

## Key Generation Using Coin Flipping

A real application of this protocol is session-key generation. Coin-flipping protocols allow Alice and Bob to generate a random session key that neither can influence the session key will be. And assuming Alice and Bob encrypt their exchanges, this key generation is secure from eavesdropping as well.

## 4.11 Mental Poker

A protocol similar to the public-key fair coin protocol allows Alice and Bob to play poker with each other via electronic mail. Instead of Alice making and encrypting two messages, one for heads and one for tails, she makes 52 messages, $M_{1...52}$, for each card in the deck. Bob chooses five messages at random, encrypts them with his public key, and sends them back to Alice. Alice cannot see the result until Alice lets him close enough to look. (Wait, the text is scrambled here) ... Bob encrypts them with his public key, and sends them back to Alice. Alice decrypts the messages and sends them to Bob, who decrypts them to determine his hand. He then chooses five messages at random and sends them back to Alice as he received them; she decrypts them and become her hand. During the game, additional cards can be dealt to each player by repeating the procedure. At the end of the game, Alice and Bob both reveal their cards and keys so that each can assured the other did not cheat.

Poker is more fun with more players. The basic mental poker protocol can easily be extended to three more players. In this case, too, the algorithm must be commutative. Alice, Bob, and Carol generate a public-key/private-key pair.
- Alice generates 52 messages, for each card in the deck. These messages should contain some unique random string, so that they can verify their authenticity later. Alice encrypts all messages with her public key and sends them to Bob: $E_{A}(M_{i})$.
- Bob, who cannot read any of the messages, chooses five at random. He encrypts them with his public key and sends them back to Alice: $E_{B}(E_{A}(M_{i}))$.
- Bob sends the other messages to Carol: $E_{A}(M_{i})$.
- Carol, who cannot read any of the messages, chooses five at random. She encrypts them with her public key and sends them to Alice: $E_{C}(E_{A}(M_{i}))$.
- Alice, who cannot read any of the messages sent back to her, decrypts them with her private key and sends them back to Bob or Carol depending on where they came from: $D_{A}(E_{B}(E_{A}(M_{i}))) = E_{B}(M_{i})$ and $D_{A}(E_{C}(E_{A}(M_{i}))) = E_{C}(M_{i})$.
- Bob and Carol decrypt the messages with their keys to reveal their hand: $D_{B}(E_{B}(M_{i})) = M_{i}$ and $D_{C}(E_{C}(M_{i})) = M_{i}$.
- Carol chooses five more choices at random from the remaining. She sends them to Alice: $E_{A}(M_{i})$.
- Alice decrypts the messages with her private key to reveal her hand: $D_{C}(E_{A}(M_{i})) = M_{i}$.
- At the end of the game, Alice, Bob, and Carol reveal their hand and all of their keys so that everyone can make sure no one has cheated.

Additional cards can be dealt in the same manner. If Bob or Carol wants a card, whoever has the deck sends a random card. Ideally, step (10) would not be necessary. All players should be required to reveal the hands at the end of the protocol unless those who haven't folded. Since step (10) is part of the protocol only to catch cheaters, perhaps there are improvements in style.

This protocol isn’t secure against collusion among malicious players. Alice and another player can effectively gang up on the third and throw player out of everything without raising suspicion. Therefore, it is important to check all the keys and random strings every time the players reveal their hands. And if you're sitting around the virtual table with two people who never reveal their hands when one of them is the dealer (Alice, in the below), stop playing.

Understand that this is all an interesting theory, actually implementing it on a computer is an arduous task. A practical implementation with three players on separate workstations takes eight hours to shuffle a deck of cards, let alone play an actual game.

## Attacks against Poker Protocols

Cryptographers have shown that a small amount of information is leaked by poker protocols if the RSA public-key algorithm is used [453,573]. Specifically, if the binary representation of the card is a quadratic residue [see Section 11.3], then the encryption of the card is also a quadratic residue. This property can be used to mark cards all the aces, for example. This does not reveal much about the hands, but in a game such as poker even a tiny bit of information can be an advantage in the long run.

Shafi Goldwasser and Silvio Micali [624] developed a two-player mental-poker protocol that fixes the problem, although complexity makes it far more theoretical than practical. A general n-player poker protocol that eliminates the problem of information leakage was developed in later [389].

Other research on poker protocols can be found in [573,1634,389]. A complicated protocol that allows players to not reveal their hands can be found in [390]. Coppersmith discusses two ways to cheat at mental poker using.

## Anonymous Distribution

If you use RSA, this protocol leaks information at the rate of one per message. It's quadratic residues again. If you're going to distribute keys in this manner, make sure this leak isn't enough to matter. Also, if Alice can't trust the KDC, then she shouldn't getting keys from it. A malicious KDC could presumably keep records of every key it generates. Then, it could search them all to determine which is Alice's.

## 4.12 ONE-SCENARIO ACCUMULATORS

Alice is a member of Cabal. Occasionally she has to meet with other members in dimly lit restaurants and whispers secrets back and forth. The problem is that the restaurants are so dimly that she has trouble knowing if the person across the table is from Alice.

Cabal can choose from several solutions. Every member can carry a membership-ship list. This has two problems. Everyone now has to carry a large database, and they have to guard their membership list perfectly carefully. Alternatively, a trusted secretary could issue digitally signed ID cards. This has added the advantage of allowing others to verify members (for discounts at the local grocery store, for example), but it requires a trusted secretary. Not by Cabal, Alice can be trusted to that degree.

A novel solution is to use something called a one-way accumulator [116]. This is sort like a one-way hash function, except that it is commutative. In this, it is possible to hash the database of members in any order and get the same value.

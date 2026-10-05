
## 4.6 GROUP SIGNATURES

David Chaum introduces this problem in [330]:

A company has several computers, each connected to the local network. Each department of company has its own printer (also connected to the network) and only persons of that department are allowed to use their department's printer. Before printing, therefore, the printer must be convinced that the user is working in that department. At the same time, the company wants privacy; the user's name may not be revealed. If, someone discovers at the end of the day that a printer has been used too often, the director must be able to discover who misused printer, and send him a bill.

The solution to this problem is called a **group signature**. Group signatures have the following properties:

- Only members of the group can sign messages.
- The receiver of the signature can verify that it is a valid signature from the group.
- The receiver of the signature cannot determine which member of the group is the signer.
- In the case of a dispute, the signature can be “opened” to reveal the identity of the signer.

### Group Signatures with a Trusted Arbitrator

This protocol uses a trusted arbitrator:

- (1) Trent generates a large pile of public-key/private-key key pairs and gives every member of the group a different list of unique keys. No keys on any list [If there are *n* members of the group, and each member gets *m* keys, then there are *n-m* total keys].
- (2) Trent publishes the master list of all public keys for the group, in random order. Trent keeps a record of which keys belong to him.
- (3) When group members want to sign a document, he chooses a key random from his personal list.
- (4) When someone wants to verify that a signature belongs to the group, he looks on the master list for the corresponding public key and verifies the signature.
- (5) In the event of a dispute, Trent knows which public key corresponds to which group member. Trent knows everyone's private keys and can forge signatures.

The problem with this protocol is that it requires a trusted party. Trent knows everyone's private keys and can forge signatures. Also, *m* must be long enough to preclude attempts to analyze which keys each member uses.

## 4.7 Fail-Stop Digital SIGNATURES

Let's say Eve is a very powerful adversary. She has vast computer networks and rooms full of Cray computers—orders of magnitude more computing power than Alice. All of these computers churn day and night, to break Alice's private key. Finally—success. Eve can impersonate Alice, forging her signature on documents at will.

Fail-stop digital signatures, introduced by Birgit Platzmann and Michael Weigner [1240], prevent this kind of cheating. If Eve forges Alice's signatures after a brute-force attack, Alice can prove they are forgeries. If Alice signs a document and then denounces it, claiming forgery, a court can verify that it is not a forgery.

The basic idea behind fail-stop signatures is that for every public key, many possible private keys work with it. After seeing different signatures, Alice has only one private key and can compute just one signature. Alice doesn't know any of the other private keys.

Eve wants to break Alice's private key. (Eve could be Alice, trying to compute a second private key for herself.) She collects signed messages and, using her array of Cray computers, tries to recover Alice's private key. If she manages to recover a valid private key, there are so many possible private keys that it is far more likely that she has a different one. The probability of Eve recovering the proper key can be made so small as be negligible.

Now, when Eve forges a signed document using the private key she generated, it will have a different signature than Alice forges the document. If Alice is hauled to court, she can produce two signatures for the same message and public key [corresponding to her private key and to the key Eve created] to prove forgery. On the other hand, Alice cannot produce the two different signatures, there is no forgery and Alice is still bound by her signature.

This signature scheme protects Alice from breaking Alice's signature scheme by sheer computational power. It does nothing against Mallory's much more likely attack of breaking into Alice's house and stealing her private key or Alice's attack of signing a document and conveniently losing her private key. To protect the former, Alice should buy herself a good dog, that kind of thinking is beyond the scope of cryptography.

Additional theory and applications of fail-stop signatures can be found in [1239, 1241, 731].

## 4.8 COMPUTING WITH ENCRYPTED DATA

Alice wants to know the solution to function f(x), for some particular value of x. Unfortunately, her computer is broken. Bob is willing to compute f(x) for her, but...

Alice isn't keen on letting Bob know her x. How can Alice let Bob compute f(x) for without telling him x?

This is the general problem of computing with encrypted data, also called hiding information from an oracle. [Bob is the oracle, he answers questions.] There are ways to do this for certain functions; which are discussed in Section 23.6.

## 4.9 Bit Commitment

The Amazing Alice, magician extraordinaire, will now perform a mystifying feat of mental prowess. She will guess the card Bob will choose before he chooses it! Watch as Alice writes her prediction on a piece of paper. Marvel as Alice puts pieces of paper in an envelope and seals it. Thrill as Alice hands sealed envelope to a random member of the audience. "Pick a card, Bob, any." He looks at it and shows it to Alice and the audience. It's the seven of diamonds. Alice now takes the envelope from the audience. She rips it open. The prediction, written before Bob chose his card, said "seven of diamonds" Applause.

To make this work, Alice had to switch envelopes at the end of the trick. However, even cryptographic protocols can provide a method immune from any slight of hand. Why is this useful? Here's a more mundane story:
Stockbroker Alice wants to convince investor Bob by her method of picking winning stocks.

> "Pick five stocks for me. If they are all ones, I'll give you my business."
ALICE: "If I pick five stocks, you could invest in them without paying me. Why don't you show me the stocks I picked last month?"
BOB: "How do I know you didn't change them after I picked them? Show me the commitment first."
ALICE: "If I pick five stocks, you could invest in them without paying me. Why don't you show me the stocks I picked last month?"
BOB: "How do I know you didn't change them after I picked them? Show me the commitment first."
ALICE: "If I pick five stocks, you could invest in them without paying me. Why don't you show me the stocks I picked last month?"
BOB: "How do I know you didn't change them after I picked them? Show me the commitment first."
ALICE: "If I pick five stocks, you could invest in them without paying me. Why don't you show me the stocks I picked last month?"
BOB: "How do I know you didn't change them after I picked them? Show me the commitment first."
ALICE: "If I pick five stocks, you could invest in them without paying me. Why don't you show me the stocks I picked last month?"
BOB: "How do I know you didn't change them after I picked them? Show me the commitment first."
ALICE: "If I pick five stocks, you could invest in them without paying me. Why don't you show me the stocks I picked last month?"
BOB: "How do I know you didn't change them after I picked them? Show me the commitment first."

(Wait, let me fix the dialogue flow)

Chaum [330] lists a number of other protocols, some in which Trent is unable to fake signatures and others in which Trent is not even required. Another protocol [348] not only hides the identity of the signer, but also allows new members to join the group. Yet another protocol is [1230].

### Bit Commitment Using Symmetric Cryptography

This bit-commitment protocol uses symmetric cryptography:

- 1 Bob generates a random string, $R$, and sends it to Alice.
- 2 Alice creates a message consisting of the bit she wishes to commit to (it can be several bits), and encrypts it with some random key, $K$, and sends the result back to Bob. $E_K(R,b)$

That is the commitment portion of the protocol. Bob cannot decrypt the message. When it comes to reveal her bit, the protocol continues:

- 3 Alice sends the key.
- 4 Bob decrypts the message to reveal her bit.

If the message did not contain Bob's random string, Alice could secretly decrypt it with a variety of keys until she found one other than the one she committed to. Since the bit has only two values, she is certain to find one after a few tries. Bob's random string prevents her from using this attack; she has to find a new message that not only has her bit inverted but also has Bob's random string exactly reproduced. If the encryption algorithm is good, the chance of her finding this is minuscule.

### Bit Commitment Using One-Way Functions

This protocol uses one-way functions:

- 1 Alice generates two random- strings, $R_1$ and $R_2$. $R_1, R_2$
- 2 Alice creates a message consisting of random strings and the bit she wishes to commit to (it can be several bits). $R_1, R_2, b$
- 3 Alice computes the one-way function on the message and sends the result, as well as one of the random strings, to Bob. $H(R_1, R_2, b), R_1$

This transmission from Alice is evidence of commitment. Alice's one-way function in [3] prevents Bob from inverting and determining the bit. When it comes time for Alice to reveal her bit, the protocol continues:

- 4 Alice sends the original message. $R_1, R_2, b$
- 5 Bob computes the one-way function on the message and compares it and $R_1$, with the value and random string he received in [3]. If they match, the bit is valid.

The benefit of this protocol over the previous one is that Bob does not have to send any messages. Alice sends Bob message to commit to a bit and another message to reveal the bit.

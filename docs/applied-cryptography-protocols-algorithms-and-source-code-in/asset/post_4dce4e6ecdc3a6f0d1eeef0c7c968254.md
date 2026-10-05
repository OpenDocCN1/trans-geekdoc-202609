
## 4.3 Undeniable DIGITAL SIGNATURES

Normal digital signatures can be copied exactly. Sometimes this property is useful, as in the dissemination of public announcements. Other times it could be a problem. Imagine a digitally signed person or business letter. If many copies of that document were floating around, each of which could be verified by anyone, this could lead to embarrassment or blackmail. The best solution is a digital signature that can be proven valid, but that the recipient cannot choose to show to a third party without the signer's consent.

The Alice Software Company distributes DEW (Do-Everything-World). To ensure that their software is virus-free, they include a digital signature with each copy. However, only legitimate buyers of the software, not pirates, are able to verify the signature. At the same time, if copies of DEW are found to contain a virus, the Alice Software Company should be unable to deny a valid signature. Undeniable signatures [343,327] are suited to these sorts of tasks. Like a normal digital signature, an undeniable signature depends on the signed document and the signer's private key. Unlike normal digital signatures, an undeniable signature cannot be verified without the signer's consent. Although a better name for these signatures might be something like "noninterferable signatures," the name comes from the fact that if Alice is forced to either acknowledge or deny a signature—perhaps in court—she cannot falsely deny her real signature. The mathematics are complicated, but the basic idea is:

- (1) Alice presents Bob with a signature.
- (2) Bob generates a random number and sends it to Alice.
- (3) Alice does a calculation using the random number and her private key and sends Bob the result. Alice could only do this calculation if the signature is valid.
- (4) Bob confirms this.

There is also an additional protocol so that Alice can prove she did not sign a document, and cannot falsely deny a signature. Bob can't turn around and convince Carol that Alice's signature is valid, because Carol doesn't know Bob's numbers are random. He could have easily worked the protocol without paper, without any help from Alice, and then showed Carol result. Carol can be convinced that Alice's signature is valid only if she completes the protocol with Alice herself. This might not make sense now, but it will once she sees the mathematics in Section 23.4.

This solution is not perfect. You Desmond and Monty show that it is possible, in some applications, for Bob to convince Carol Alice's signature is valid [489]. For instance, Bob buys a legal copy of DEW. He can validate the signature on the software package whenever he wants. Then, Bob convinces Carol that he's a salesman from the Alice Software Company. He sells her a pirated copy of DEW. When Carol tries to validate the signature with Bob, he simultaneously denies the signature with Alice. When Carol sends him the random number, then he sends it on Alice. When Alice replies, he then sends the reply on Carol. Carol is convinced that she is a legitimate buyer of the software, even though she isn't. This attack is an instance of the chess grandmaster problem and is discussed in detail in Section 5.2.

Even so, undeniable signatures have a lot of applications; in many instances Alice doesn't want to be able to verify her signature. She might not want personal correspondence to be verifiable by the press, be shown and verified out of context, or even to be verified after things have changed. If she signs a piece of information she sold, she won't want anyone who hasn't paid for the information to be able to verify its authenticity. Controlling who verifies her signature is a way for Alice to protect her privacy.

A variant of undeniable signatures separates the relation between signer and message from the relation between signer and signature [910]. In one signature scheme, anyone can verify that the signer created the signature, but the cooperation of the signer is required to verify that the signature is valid for the message.

A related notion is an undeniable signature [1229]. Imagine that Alice works for Toxins, Inc., and sends incriminating documents to a newspaper using an undeniable signature protocol. Alice can verify her signature to the newspaper reporter, but not to anyone else. However CEO Bob suspects Alice is the source of the documents. He demands Alice run the disavowal protocol to clear her name, and Alice refuses. Bob maintains that the only reason Alice refuses to is that she is guilty, and fires her.

Entrusted undeniable are like undeniable signatures, except that the disavowal protocol can only be run by Trent. Bob cannot demand Alice run the disavowal protocol; only Trent can. And if Trent is in the court system, then he will only run the protocol to resolve a formal dispute.

## 4.4 Designated Confirmer Signatures

The Alice Software Company is doing a booming business selling DEW—so good, in fact, Alice is spending more time verifying undeniable signatures without writing new features.

Alice would like a way to designate one particular person in the company to be in charge of signature verification for the whole company. Alice, or any other programmer, would be able to sign documents with an undeniable protocol but the verifications would all be handled by Carol.

As it turns out, this is possible with designated confirmer signatures [333,1213]. Alice can sign a document that Bob is convinced the signature is valid, but cannot involve a third party; at the same time Alice can designate Carol as the confirmer for future of her signature. Alice doesn't even need to ask Carol's permission beforehand; she just to use Carol's public key. And Carol can still verify Alice's signature if Alice is out of town, has left the company, or just jumped and died.

Designated confirmer signatures are kind of compromise between normal digital signatures and undeniable signatures. There are certainly instances where Alice might want to limit who can verify her signature. On the other hand, giving Alice complete control determines the enforceability of signatures: Alice might refuse to cooperate in either confirming or denying, she might claim the loss of keys for forming or denying, or she might be unavailable. Designated confirmer can give Alice the protection of an undeniable signature while letting her abuse that protection. Alice might even prefer that way: Designated signatures can help prevent false applications, if she also loses her key, and step in if she is on vacation, in the hospital, or even dead.

This idea has all sorts of purposes. Carol can publish her public key in some directory somewhere, and people can designate her as a confirmer for her signatures. She can charge a small fee for confirming signatures for the masses and make a nice living.

Carol can be a copyright office, a government agency, or a host of other things. This protocol allows organizations to separate the proxy who signs documents from the people who help verify signatures.

## 4.5 PROXY SIGNATURES

Designated confirmer signatures allows a signer to designate someone else to verify his signature. Alice, for instance, needs to go on a business trip to somewhere she doesn't have very good computer network access—to the jungles of Africa, for example. Or she may be incapacitated after surgery. She expects to receive some important e-mail, and has instructed her secretary Bob to respond accordingly. How can Alice give Bob the power to sign messages for her, without giving him her private key?

Proxy signatures is a solution [101]. Alice can give Bob a proxy, such that the following properties hold:

- Distinguishability. Proxy signatures are distinguishable from normal signatures by anyone.
- Unforgeability. Only the original signer and the designated proxy signer can create a valid proxy signature.
- Proxy signer's deviation. A proxy signer cannot create a valid proxy signature not detected as a proxy signature.
- Verifiability. From a proxy signature, a verifier can be convinced of the original signer's agreement on the signed message.
- Identifiability. An original signer can determine the proxy signer's identity from a proxy signature.
- Undeniability. A proxy signer cannot disavow an accepted signature he created.

In some cases, a stronger form of identifiability is required—that anyone can determine the proxy signer's identity from the proxy signature. Proxy signature schemes, based on different digital signature schemes, are in [101].

knowledge in a scalable manner. For example, a PGP commercial product based on the OpenPGP standard has features for splitting public keys that are not part of the OpenPGP standard.134 These features use Blakely–Shamir secret sharing. This is an algorithm that allows the user to take a piece of data and break it into N shares, of which K of them are needed to retrieve the original data. Using a simple version of this approach, the user could break the data into three shares, two of which are needed to get the data back. In a more complex version, the user could require 3 of 6 or even 5 of 12 shares to retrieve the original data, with each key share protected with a unique passphrase known only to the key holder.

Such a solution uses the basic form of secret sharing and shares the private key. This process permits a key pair to be controlled by a group of people, with some subgroup required to reconstitute and use the key. Other systems are based on key holders answering a series of questions in order to recover passwords needed to unlock a protected plaintext key.

To recreate the key under protection, a user can create a set of questions that contain some information only the user would know. The key is split to those questions, with some set of them being required to synthesize the key. Not only does the user provide individualized security questions that are unique to each key holder but also decides how many of the questions need to be answered correctly to retrieve the key under protection, by having it reconstructed from the split parts.

# Creation and Distribution of Keys

# Creation of Keys

The details of key creation using various algorithms were discussed earlier in this chapter. However, from a key management perspective, there are a number of issues that pertain to scalability and cryptographic key integrity.

# Automated Key Generation

Mechanisms used to automatically generate strong cryptographic keys can be used to deploy keys as part of key lifecycle management. Effective automated key generation systems are designed for user transparency as well as complete cryptographic key policy enforcement.

# Truly Random

For a key to be truly effective, it must have an appropriately high work factor. That is to say, the amount of time and effort (work by an attacker) needed to break the key must
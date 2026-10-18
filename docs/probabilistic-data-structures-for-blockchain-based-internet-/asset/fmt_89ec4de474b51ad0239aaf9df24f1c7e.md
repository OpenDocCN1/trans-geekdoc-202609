
Digital signatures are realized with the concept of asymmetric key cryptography (Public-key cryptography). Asymmetric key cryptography uses two different keys, i.e., a public key and a private key. The public key is known to the user only whereas the private key is known to everyone in the universe. For preserving the confidentiality of data, the data to be transferred is encrypted using the public key of the receiver whereas the private key is used at the destination node to decrypt the message.

### [5.4.1 Model of digital signature](#contents.xhtml#rsec5_4_1)

To generate digital signatures, the message is signed using the private key of the sender and at the destination side, signatures are verified using the public key of the sender. However, by integrating the concept of cryptographic hash with digital signatures, the size of digital signatures can be reduced. So, rather than signing the original message, the message digest is signed. The following steps are taken in generating the digital signatures:

*   First, hash the message (`M`) to obtain message digest `h(M)`. Next, the generated hash is signed using the private key of the sender which results in digital signatures.

*   Next, the message and the digital signature are transferred over the channel.

*   Receiver after receiving the particular digital signatures, decrypt it using the public key of the sender (This assures the `authenticity` of the sender). After applying the decryption algorithm, the receiver will get the message digest `h(M)`.

*   Simultaneously, from the original message received receiver, will compute the hash of it. Let's call this value `h’(M)`.

*   If `h(M)`=`h’(M)`, the `integrity` of the original document is preserved.

*   As it is assumed that only signer of the document knows the private key, so no other can generate the signature of the signer. Hence, it ensures `non-repudiation` attribute.

The whole process of generating hash function has been depicted in [Fig. 5.6](#07chap_05.xhtml#fig5_6). Therefore, by applying the hash function, the size of the signature can be reduced.

![FIGURE 5.6 Digital signatures.](images/fig5_6.jpg)

**FIGURE 5.6**  

Digital signatures.

Key points

*   A cryptographic key should be prevented from being guessed by others. However, it is assumed that the cryptographic algorithm is known to everyone.

*   The key should have sufficient length as a key with long length is difficult to guess as compared to short length key.

*   The key should be truly randomly generated with sufficient entropy.

## [5.5 Zero-Knowledge Proof](#contents.xhtml#rsec5_5)

Another concept that is associated with blockchain is zero-knowledge proof. It is a cryptographic method to prove to the verifier that prover knows a value without actually revealing any data except revealing the fact that prover knows the value. By simply, generating the final output, the prover is supposed to prove that they can compute something without telling the computational process whereas the verifier only knows the output.

For example, A wants to prove B that he/she knows the key without disclosing secret key to B, and B verifies that A is actually having the key. Hence, they have the capability to revolutionize the way of data handling, collection, and the way data is transacted with. Zero-knowledge proof has 3 important properties:

*   Completeness: If the fact is true, the prover should convince the verifier for this fact and zero knowledge proof should return true.

*   Soundness: If the fact/statement is false, the prover can't convince the verifier that prover's statement is true.

*   Zero-knowledge/Privacy: If the information provided by prover is true, no verifier learns any other information expect the fact that information is true. In other words, the provider information should not reveal anything else to the verifier.

To better understand zero knowledge proof, let's take the popular and classic example of zero knowledge proof that is of `two balls and colour-blind friend`

Suppose A has two identical balls having different colours (say one red and one green) and your friend B is colour blind which means B can't differentiate between the balls based on their colour. However, A has to prove to B that two balls are of different colours. Nevertheless, A doesn't want to reveal which is red and which is green. This is how proof system for this problem will work:

*   A will give both balls to B and puts both balls behind his back.

*   B then takes out one of the two balls from behind his/her back and shows it.

*   B then puts back the ball behind his/her back again and then reveal just one of the two balls, simply by picking one of the two balls at random with equal chances.

*   Next, B asks A ”Did I switch the ball?”.

Third and fourth steps are repeated till B assures that there are two different colored balls. Obviously, by balls color A can certainly tell whether or not B switched them. Moreover, A could guess right with probability not higher than 50% that whether the ball his switched or not if balls are having same color and therefore indistinguishable. If A and B repeats this process multiple times A will be caught if he/she lies.

Clearly, the above proof system is zero knowledge as B will never learn which is green and which is red ball.

Over and above, zero-knowledge proof has two variants: interactive and non-interactive zero-knowledge proof. In interactive proofs, the prover and the verifier exchange more than one message to prove or verify the information. It demands verifier to constantly ask questions about the knowledge the prover possesses. Unfortunately, the interactive zero knowledge proof has limited transferability. In contrast, non-interactive proof system demands no interaction between prover and verifier except a common reference string between both parties.

Keypoint

`Zero knowledge proof application in blockchain:` Both of the popular blockchain use cases, i.e., Bitcoin and Ethereum are based on public addresses to depict the true identity of the user which maintains anonymity in the network. Notably, due to the distributed nature of the blockchain, interactive zero knowledge proof is not an efficient solution. Moreover, a real world use case of zero knowledge proof is Zcash that enables native transactions to be fully encrypted while being verified by network consensus rule and Zcash is a non-interactive zero knowledge proof system.

## [5.6 Hash Tables](#contents.xhtml#rsec5_6)

It is a popular data structure that supports fast insertion and search operation irrespective of the size of the data. It is basically a method to identify a specific object from a group of similar objects. In particular, hash tables (also called hash map) store data in a format of array and each data value is associated with a unique index value. Hash tables make use of hash function to generate an index, i.e., location where a data element is to be inserted. The information in data structure has two main components, i.e., a unique key and a value. For instance, a key could be unique ID (key doesn't have to be an integer every time) and value is the phone number. The hash function will decide where to map the key and where to store corresponding value with it. The efficiency of mapping is dependent on the efficiency of hash function. Basically, the set from which we use input element is much larger than capacity of the hash table, so that collision can be avoided. Clearly, if the number of items in the table grows, collision rises as well. To measure how full the hash table is, the concept of load factor (`α`) is used which is defined as the fraction of number of used keys (`n`) and the total capacity of the table (`m`).

$$
\begin{array}{l}
{\alpha = \frac{n}{m}}
\end{array}
$$

(5.2)

Notably, `n` can't exceed the total capacity of the table. If `α` approaches to maximum value, the chances of collision rises significantly.

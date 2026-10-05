
## CHAPTER 24 Example Implementations

Here is the communications protocol between customer Alice and Bob. (Actually, Alice and Bob just plug their cards into a machine and wait for it to complete the transaction.) When Alice gets her card, she is given a key pair, $K_1$ and $K_2$, the bank calculates from her name and some secret function. Only the merchant cards have the secrets necessary to work out these customer keys.

- 1) Alice sends Bob her name, $A$, his name, $B$, and a random number, $R_A$, encrypted using DES: first with $K_2$ and then with $K_1$. She also sends her name in the clear.
  $E_{K_1}(E_{K_2}(A, B, R_A))$

- 2) Bob calculates $K_1$ and $K_3$ from Alice's name. He decrypts the message, confirms that $A$ and $B$ are correct, encrypts Alice's unencrypted message with $K_3$.
  $E_{K_3}(A, B, R_A)$
  Bob does not send this message to Alice; 56 bits of the ciphertext become $K_3$. Bob then sends Alice his name, and another random number, $R_B$, encrypted using DES: first with $K_3$ and then with $K_1$.
  $E_{K_1}(E_{K_3}(B, R_B))$

- 3) Alice computes $K_2$ in the same manner. She decrypts the message, confirms that $A$ and $B$ are correct, encrypts Bob's unencrypted message with $K_2$.
  $E_{K_2}(E_{K_1}(A, R_B))$
  Alice does not send this message to Bob; 56 bits of the ciphertext become $K_2$. Alice then sends Bob her name, and the digital check, $C$, encrypted using DES: first with $K_2$ and then with $K_1$.
  $E_{K_1}(E_{K_2}(A, C))$

- 4) Bob computes $K_4$ in the same manner. Assuming all the names match and the check is correctly formed, he accepts it for payment.

A clever thing about this protocol is that the encryption key for each message depends on the previous message. Each message depends as an authenticator for all previous messages. This means that someone cannot replay an old message; the receiver could never decrypt it. Another clever thing about this protocol is that if the application developer not implement this protocol correctly, it won't work.

### 24.1 Clipper

Both cards store records of every transaction. When the cards go online to communicate with the bank—the bank uploads these records for auditing purposes. Tamperproof hardware prevents either participant from messing with the data; Alice cannot change the value of her account. Extensive audit trails provide data to identify and prosecute fraudulent transactions. There are universal secrets in the cards—$K_i$ in customer cards and $K_j$ in the merchant cards—but these are assumed to be difficult to reverse-engineer. This scheme is not meant to be perfect, only more secure than either paper checks or traditional debit cards. The threat of fraud is not from rivals, but from opportunistic customers and protects against that kind of abuse.

### 24.2 Clipper

The Clipper (also known as the Clipper-78) is an NSA-designed, tamper-resistant VLSI chip for encrypting voice conversations. It is one of two chips that implement the U.S. government's Escrow Encryption Standard (EES); VLSI Technologies Inc. manufactures the chip, and Mykotron Inc. programs it. Initially, the Clipper will be available in the AT&T Model 3600 Telephone Security Device. The chip implements the Skipjack encryption algorithm in OFB only. The most controversial aspect of the Clipper and the EES is the key escrow—each chip has a special key, not needed for messages, used to encrypt a copy of each user's message. As part of the synchronization process, the sending Clipper chip generates and sends a Law Access Field (LEAF) to the receiving Clipper chip. The LEAF contains a copy of the session key, encrypted with a special key (called the unit key). This allows a government eavesdropper to recover the session key, and then recover the plaintext of the conversation. According to the director of NIST the key-escrow system is established to ensure that the Clipper Chip is used to protect the privacy of law-abiding Americans. Each device will have unique “keys” that will be needed by authorized government agencies to decode messages encoded by the device. When the device is manufactured, the two keys would be deposited separately in two “key-escrow” databases established by the attorney general. Access to these keys would be limited to government officials with legal authorization to conduct a wiretap.

The government also wants to encourage the sale of telephones with these devices abroad; no one knows what might happen to those key-escrow databases. Politics aside, the internal structure of the LEAF is worth discussing. The LEAF is a 128-bit string containing enough information to allow law enforcement to recover the session key $K_s$, assuming the escrow agencies in those key-escrow databases cooperate. The LEAF contains a 32-bit unit identifier $U$, unlike the Clipper chip. It also contains the 80-bit session key encrypted with the Clipper's unique unit key $K_u$, and a 16-bit checksum, called an escrow identifier. This checksum is a function of the session key, the IV, and possibly other information. These three fields are encrypted with a family key $K_f$, shared by interoperable Clipper chips. The family key, the encryption modes, the details of the checksum, and the exact structure of the LEAF are all secret. It probably looks like this:

```
$E_{K_f}[E_{K_u}(C)]$
```

$K_u$ is programmed into Clipper chips. The key is then split (Section 3.6) and stored in two different-escrow-databases guarded by two different escrow agencies. For Eve to recover $K_s$, she first has to decrypt the LEAF with $K_f$ and recover $U$. Then she has to court an order to each escrow agency, Eve XORs the two halves together to recover $K_u$, then she uses $K_u$ to recover $K_s$ and $K_f$ to eavesdrop on the conversation.

The checksum is designed to prevent someone from circumventing this scheme; the receiving Clipper chip will not decrypt the LEAF if the checksum doesn't check. However, there are only $2^{16}$ possible checksum values, and a bogus LEAF with the right checksum but the key can be found in about 42 minutes. This isn't much help for voice conversations. Because the encryption protocol is not part of the Clipper chip, the 42-minute brute-force attack must occur after the key is exchanged, it cannot be done before making the phone call.

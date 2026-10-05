# 24.16 Clipper

Both cards store records of every transaction. When the cards eventually go online to communicate with the bank—the merchant deposit its money—the bank uploads these records for auditing purposes.
Tamperproof hardware prevents either participant from messing with the data; Alice cannot change the value of her card. Extensive audit trails provide data to identify and prosecute fraudulent transactions. There are universal secrets in the cards—MAC keys in the merchant cards, functions to convert customer names to $K_i$ and $K_j$ in the merchant cards—but these are assumed to be difficult to reverse-engineer.

This scheme is not meant to be perfect, only more secure than either paper checks or traditional debit cards. The threat of fraud is not from rival militaries, but from opportunistic customers and merchants. UEPS protects against that kind of abuse.
The exchange is an excellent example of a robust protocol: Every message spans both parties, includes information to ensure freshness and depends entirely on all the messages that came before.

# 24.16 Clipper

The Clipper (also known as the MYK-78T) is an NSA-designed, tamperresistant VLSI chip for encrypting voice conversations, it is one of the two chips that implement the U.S. government's Escrowed Encryption Standard (EES) [1153]; VLSI Technologies, Inc. manufactures the chip, and Mykotron, Inc. programs it. Initially, the Clipper will be available in the AT&T Model 3600 Telephone Security Device (Section 24.18). The chip implements the Skipjack encryption algorithm (Section 13.12), an NSA-designed secret-key encryption algorithm, in OFB only.

The most controversial aspect of the Clipper, and the EES, is the key escrow—each chip has a special key, not needed for messages. This key is used to encrypt a copy of each user's message. As part of the synchronization process, the sending Clipper chip generates and sends a Law Access Field (LEAF) to the receiving Clipper chip. The LEAF contains a copy of the current session key, encrypted with a special key (called the unit key). This allows a government eavesdropper to recover the session key, and then recover the plaintext of the conversation.

According to the director of NIST [812]:

“key-escrow” system is established to ensure that the “Clipper Chip” is used to protect the privacy of law-abiding Americans. Each device will have unique “keys,” that will be needed by authorized government agencies to decode messages encoded by the device. When the device is manufactured, the two keys would be deposited separately in two “key-escrow” databases established by the attorney general. Access to these keys would be limited to government officials with legal authorization to conduct a wiretap.
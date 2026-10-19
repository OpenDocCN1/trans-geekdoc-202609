# 15.3.4 Spoofing Attack

A fog platform where fog devices collaboratively work is more prone to data tampering and spoofing attacks [19]. Stojmenovic et al. suggested prevention methods could be built in using a public key infrastructure (PKI), Diffie-Hellman key exchange, intrusion detection techniques and monitoring for modified input values. In a health fog platform both security, performance and latency are the important factors to be considered, and mechanisms like encryption methodologies, known as fully homomorphic [20] and somewhat homomorphic [21] can be used to preserve data security during data transmission. These methods constituted by a hybrid of symmetric and public-key encryption algorithms, as well as other variants of attribute-based encryption. The homomorphic encryption schemes allow doing normal operations without decrypting the data, thereby reducing the key distribution which helps to maintain data privacy.

The algorithm for homomorphic encryption is given below:

```
Algorithm Homomorphic encryption
Input: Encrypted data from individual fog nodes.
Output: Secured private data at receiver end
BEGIN
Step 1. Let PT₁ and PT₂ be encrypted data collected from sensor and fog nodes from edge devices.
Step 2. Apply either additive or multiplicative homomorphic (EH) on PT₁ and PT₂ given by equation 15.1 and 15.2 respectively.
EH(PT₁)⊕EH(PT₂) = EH(PT₁ + PT₂) (15.1)
EH(PT₁)⊕EH(PT₂) = EH(PT₁ × PT₂) (15.2)
Where, ⊕ is a mathematical operator.
Step 3. Receive data at in a double encrypted mode.
END
```

Processing should be done on the data in fog node without decrypting the original message, thus preserving data confidentiality.

# 15.3.5 Man-in-the-Middle Attack

In fog computing, there is high chance of going through man-in-the-middle (MITM) attack [22]. During this attack, fog devices serving as gateways might be compromised or substituted by forged ones [23]. Traditionally these attacks can be prevented by using encryption and decryption algorithm methods [22]. But it is difficult to protect communication between fog node and IoT devices using the encryption method. Encryption and decryption methods devour a considerable amount of time and battery on a mobile device. It is often a risk factor against the QoS (quality of service) requirement of the healthcare monitoring system in fog environment.

Kulkarni et al. [24] suggested a method to handle an MITM attack. On the extracted data, they insert Gaussian noise in some part of data to reduce the chance of eavesdropping. They split the data into blocks and shuffled their order. Koo and Hur [25] have proposed a data deduplication scheme based on a proper key management principle. This scheme is suitable for the deduplication of encrypted data in fog storage by efficient ownership
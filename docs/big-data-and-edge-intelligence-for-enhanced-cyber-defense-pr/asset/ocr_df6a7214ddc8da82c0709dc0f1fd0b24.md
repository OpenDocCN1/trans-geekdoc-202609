# Advancing Digital Forensic Intelligence

Encryption techniques add another degree of security by converting data into an unreadable format, guaranteeing that only authorized parties may access and comprehend the data [44]. Sensitive data can be securely transported and stored by employing encryption methods within the EdgeAI framework, reducing the risk of unauthorized access and data breaches. This improves the privacy and integrity of digital forensic processes, allowing investigators to work confidently knowing that the data is secure.

Given a dataset D containing sensitive attributes, the objective is to achieve data anonymization (k-anonymity) by ensuring that each individual's record is indistinguishable from at k–1 other records, while also encrypting the data to provide confidentiality.

Let D = (x₁, x₂, ..., x_n) represent the dataset with sensitive attributes. Define QID as the set of quasi-identifiers (attributes that can potentially identify individuals) in D. The form of the k-anonymity objective function is represented as (3.5):

```
min f(D) = |D| - k
```

where |ID| denotes the size of the dataset D, and k is the desired level of anonymity. The goal is to minimize the number of unique records in D subject to achieving k-anonymity.

For encryption, RSA (Rivest-Shamir-Adleman) is a widely used asymmetric encryption algorithm.

Let M represent the message to be encrypted and C denote the ciphertext obtained after encryption using RSA. The encryption process involves the following steps:

Choose two distinct prime numbers, p and q
Compute n = p * q, which represents the totient function

Now, we calculate the Euler's totient function (3.6):

```
φ(n) = (p-1)*(q-1)
```

Then, we select an integer e that 1 < e < gcd(e, φ(n)) = 1. This serves as the public key exponent.

Compute the modular multiplicative inverse of d modulo φ(n) to obtain the private key exponent (3.7). To encrypt a message M, we use the recipient's public key (n, e):

```
C ≡ M^e (mod n)
```

To decrypt (3.8) the ciphertext C, use the private key (n, d):

```
M ≡ C^d (mod n)
```
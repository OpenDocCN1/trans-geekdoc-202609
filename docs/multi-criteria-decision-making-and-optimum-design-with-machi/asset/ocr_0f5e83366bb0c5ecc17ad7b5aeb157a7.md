# Multi-Criteria Decision-Making with Machine Learning

maintain secure encryption while adding fuzziness or unpredictability to key generation considering uncertainties in prime number selection or exponent choices. Through mathematical formulations and algorithmic procedures, integrating these methodologies improved the computational efficiency and security in encrypting sensitive data.

# 17.2 KEY GENERATION

+   1. Choose two distinct prime numbers.
   Select two large prime numbers, denoted as $p$ and $q$. These numbers should be randomly chosen and keep secret. Their multiplication will be part of the RSA algorithm.
2. Calculate the modulus.
   Compute modulus $n$ by multiplying the two primes: $n = p 	imes q$. The modulus is a part of both the public and the private keys.
3. Compute Euler's totient function.
   Calculate Euler's totient function $\phi(n)$, which is the number of positive integers less than $n$ that are coprime with $n$. For two distinct primes $p$ and $q$, $\phi(n) = (p-1) \times (q-1).
4. Choose an exponent.
   Select an integer $e$ that is relatively prime to $\phi(n)$. This will be part of the public key.
5. Calculate the private exponent.
   Compute private $d$ as the modular multiplicative inverse of $\phi(n)$. In other words, find a value $d$ such that $(d \times e) \mod \phi(n) = 1$. The value of $d$ is a part of the private key.
6. Create the public key.
   The public key consists of the modulus $(n)$ and the exponent $(e)$. This is the key that will be distributed to others for encryption.
7. Create the private key.
   The private key consists of the modulus $(n)$ and the private exponent $(d)$. This key must keep secret and not be shared.
8. Transform the message into cipher text.
   To enable encryption, the message must be transformed into a numerical representation. This is commonly referred to as “padding” and entails numeric value conversion from the plaintext message.

# 17.2.1 ENCRYPTION

The sender uses the recipient's public key to encrypt the message (m). The following is how the encryption works:

+   a. Acquire the public key of the receiver, which consists of the encryption exponent $e$ and modulus $n$.
b. Using the selected encoding scheme, represent the message as a number $m$.
c. Utilize modular exponentiation to determine the cipher text $C$ by applying the formula.

```
$c = m^e \mod m$
```
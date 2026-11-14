- Asymmetric algorithms are slower compared to symmetric algorithms. They are typically used in cases of low-volume encryption, such as digital signatures and key exchange.

NOTE.— A more detailed account of asymmetric encryption is provided later in this chapter (see section 8.6).

# 8.3. Key management

# 8.3.1. Introduction

The objectives of cryptography rely to a great extent on the protection of encryption keys. It is very important to put in place an efficient and reliable management for securely storing and distributing encryption keys. This management is vital for the success of any encryption project.

There are two approaches to key management to help address this problem:

+   - manual management: consists of manually configuring, on each device, all the parameters of a secured link including encryption keys. This approach has proven to be relatively practical in a static and small environment. However, it is not appropriate for a large network;

+   - automatic management: this consists of using a protocol (e.g. ISAKMP) to dynamically configure all parameters of a secured link.

# 8.3.2. Diffie-Hellman key exchange

Diffie-Hellman (DH) is a method that allows two network elements to put in place a system by which they can exchange their secret keys in a protected manner. This method makes it possible to create a new, common secret key based on the two initial secret keys, without using a secure channel to exchange them.

# Functioning

| Step | U1 | U2 |
| :--- | :--- | :--- |
| 1 | The two users choose together:
- a prime number _p_;
- an integer _g_, such that 1 ≤ g ≤ p–1.
Note: this exchange does not need to be secure. | |
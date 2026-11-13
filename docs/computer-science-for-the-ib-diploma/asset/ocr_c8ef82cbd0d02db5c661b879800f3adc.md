# Step 1: Generate your public and private key

Start by selecting two prime numbers. These are generally very large: up to 2048 bits is typical. We will use 61 and 53 for our walkthrough.

p = 61 q = 53

Find n, the product of the two primes, and λ(n) (known as “Carmichael’s totient function”). To follow the maths, all you need to appreciate is that it is the least common multiple of (p – 1) (q – 1). n = pq = 61 x 53 = 3233 and λ(n) = lcm[(p – 1)(q – 1)] = lcm(60,52) = 780

Select an integer, e, that is a prime number, less than λ(n), and not a factor of λ(n). A common choice is 2^16 + 1, being 65537. e = 17

Solve d, where (d x e) mod λ(n) = 1. This is known as the “modular multiplicative inverse”. That is, (17 d) mod (780) = 1. One valid answer in this case is d = 413. The public key will be the two numbers n = 3233, d = 413.

# Step 2: Encrypt your secret message

The cipher text, c, for a secret message, m, is given by the following equation: c(m) = m^mod n So, if the message is A, which is ASCII 65: c(65) = 65^17 mod 3233 = 2790

# Step 3: Decrypt your secret message

The message, m, for cipher text c is given by the following equation: m(c) = c^d mod n So, when given cipher text 2790, this would be decrypted as follows: m(2790) = 2790^413 mod 3233 = 65^17

The security of the algorithm rests in the size of the prime numbers and that factorizing a number into its two constituent primes is still not possible except by brute force of trying every possible set of values. The original prime number factors are required to be able to calculate λ(n). In this case, it would be trivial to find the factors of 3233, but finding the factors of a 4096-bit number would take hundreds or thousands of years. One area of active computing research that may threaten the security of RSA-encrypted data is quantum computing. Shor’s algorithm, specifically, is a quantum algorithm for the factorization of integers that could work very quickly and render modern cryptography obsolete.

# Role of digital certificates

Digital certificates are used as a way of certifying identity on the internet. For HTTPS traffic, they are issued by a mutually trusted third party known as a “certificate authority (CA)”. When a digital certificate is presented in a network transaction, it helps the recipient verify that the public key belongs to the sender and not an imposter. Digital certificates form a key part of the network of trust on the internet. It’s not enough to know that your communication
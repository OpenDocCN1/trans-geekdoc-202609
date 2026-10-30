To create the key, you start by generating two large random primes, p and q, of approximately equal size. You need to pick two numbers so that when multiplied together the product will be the size you want (2048 bits, 4096 bits, and so on).

Now multiply p and q to get n.

Let n = pq

The next step is to multiply the Euler's totient for each of these primes. Basically, the Euler's totient is the total number of co-prime numbers. Two numbers are considered co-prime if they have no common factors. For example, if the original number is 7, then 5 and 7 would be co-prime. Remember that it just so happens that for prime numbers, this is always the number minus 1. For example, 7 has 6 numbers that are co-prime to it. (If you think about this a bit you will see that 1, 2, 3, 4, 5, and 6 are all co-prime with 7.)

Let m = (p - 1)(q - 1)

Now we are going to select another number. We will call this number e. We want to pick e so that it is co-prime to m.

Choose a small number e, co-prime to m.

We are almost done generating a key. Now we just find a number d that when multiplied by e and modulo m would yield a 1. (Remember: Modulo means to divide two numbers and return the remainder. For example, 8 modulo 3 would be 2.)

Find d, such that de mod m = 1

Now you will publish e and n as the public key. Keep d as the secret key. To encrypt, you simply take your message raised to the e power and modulo n.

= m^e % n

To decrypt, you take the ciphertext and raise it to the d power modulo n.

P = C^d % n

The letter e is for encrypt and d is for decrypt. If all this seems a bit complex to you, first you must realize that many people work in network security without being familiar with the actual algorithm for RSA (or any other cryptography, for that matter). However, if you wish to go deeper into cryptography, then this is a very good start. It involves some fundamental number theory, particularly regarding prime numbers. There are other asymmetric algorithms that work in a different manner. For example, elliptic curve cryptography is one such example.

Let's look at an example that might help you understand. Of course, RSA would be done with very large integers. To make the math easy to follow, we will use small integers in this example. (Note that this example is from Wikipedia.)

Choose two distinct prime numbers, such as p = 61 and q = 53.

Compute n = pq giving n = 61 * 53 = 3233.
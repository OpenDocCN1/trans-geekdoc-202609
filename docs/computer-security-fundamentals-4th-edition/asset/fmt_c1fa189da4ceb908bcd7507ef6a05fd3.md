
It has become standard in cryptography to use the fictitious Alice and Bob to illustrate asymmetric cryptography. If Alice wants to send Bob a message, she will use Bob’s public key to encrypt that message. It does not matter if every other person on the planet also has Bob’s public key. That key cannot decrypt the message. Only Bob’s private key can do that. This is shown in [Figure 8.5](#ch08.xhtml#ch08fig05).

![Figure 8.5 Public key cryptography. ¶  ¶ A step-wise analysis of public-key cryptography between Alice, Bob, and Eve is shown. In the first step, Alice gets Bob's public key. In the second step, Alice encrypts the message with Bob's public key. In the third step, Alice sends the message to Bob. In the fourth step, Bob decrypts the message with his private key. Even if Eve intercepts the message, she does not have Bob’s private key and cannot decrypt the message. ¶ ](Images/08fig05.jpg)

`**Figure 8.5**` Public key cryptography. ¶ 

Public key encryption is important because there are no issues to deal with concerning distribution of the keys. With symmetric key encryption, you must get a copy of the key to every person to whom you wish to send your encrypted messages. If that key were lost or copied, someone else might be able to decrypt all of your messages. With public key encryption, you can freely distribute your public key to the entire world, yet only you can decrypt messages encrypted with that public key.

#### RSA

It isn’t possible to discuss cryptography without at least some discussion of RSA, which is a very widely used encryption algorithm. This public key method was developed in 1977 by three mathematicians: Ron Rivest, Adi Shamir, and Len Adleman. The name RSA is derived from the first letter of each mathematician’s last name Let us take a look at the math involved in RSA. (It should be pointed out that knowing the math behind this, or any other algorithm, is not critical for most security professionals. But some readers will have an interest in going deeper into cryptography, and this will be a good place to start.)

There are a few basic math concepts you need to know about in order to understand RSA. Some (or even all) of this material may be a review:

*   **Prime numbers:** A prime number is divisible by itself and by 1. So 2, 3, 5, 7, 11, 13, 17, and 23 are all prime numbers. (Note that 1 itself is considered a special case and is not prime.)

*   **Co-prime:** This actually does not mean prime; it means two numbers have no common factors. So, for example, the factors of 8 (excluding the special case of 1) are 2 and 4, and the factor of 9 are 3. The numbers 8 and 9 have no common factors, so they are co-prime.

*   **Euler’s Totient:** Pronounced “oilers” totient, or called just *the totient*, this is the number of integers smaller than *n* that are co-prime with *n*. So let us consider the number 10. Since 2 is a factor of 10, it is not co-prime with 10. But 3 is co-prime with 10. The number 4 is not co-prime since both 4 and 10 have 2 as a factor. The number 5 is not since it is a factor of 10. Neither is 6 since both 6 and 10 have 2 as a cofactor. The number 7 is prime, so it is co-prime with 10. The number 8 is not because both 8 and 10 have 2 as a factor. The number 9 is co-prime with 10. So the numbers 3, 7, and 9 are co-prime with 10. We add in 1 as a special case, the Euler’s totient of 10 is 4. Now it just so happens that Leonhard Euler also proved that if the number *n* is a prime number, then its totient is always *n* − 1. So the totient of 7 is 6. The totient of 13 is 12.

*   **Multiplying and co-prime:** Now we can easily compute the totient of any number. And we know automatically that the totient of any prime number *n* is just *n* − 1. But what if we multiply two primes? For example, we can multiply 5 and 7 to get 35. Well, we can go through all the numbers up to 35 and tally up the numbers that are co-prime with 35. But the larger the numbers get, the more tedious this process becomes. For example, if you have a 20-digit number, manually calculating the totient is almost impossible. Fortunately, Leonhard Euler also proved that if you have a number that is the product of two primes (let’s call them *p* and *q*), such as 5 and 7, then the totient of the product of those two numbers (in this case 35) is equal to *p* − 1 × *q* − 1 (in this case 4 × 6, or 24).

*   **Modulus:** This is the last concept you need for RSA. There are a few approaches to explaining this concept. We will actually use two of them. First, from a programmer’s perspective, the modulus operation is to divide two numbers but only give the remainder. Programmers often use the symbol % to denote modulo operations. So 10 % 3 is 1. The remainder of 10 divided by 3 is 1. Now, this is not really a mathematical explanation of modulo operations.

Basically, modulo operations take addition and subtraction and limit them by some value. You have actually done this all your life without realizing it. Consider a clock. When you say *2 p.m.*, what you really mean is 14 mod 12 (or 14 divided by 12; just give me the remainder). Or if it is 2 p.m. now (14 actually) and you tell me you will call me in 36 hours, what I do is 14 + 36 mod 12, or 50 mod 12, which is 2 a.m. ( a bit early for a phone call, but it illustrates our point).

Now if you understand these basic operations, then you are ready to learn RSA. If needed, reread the preceding section (perhaps even more than once) before proceeding.

To create the key, you start by generating two large random primes, *p* and *q*, of approximately equal size. You need to pick two numbers so that when multiplied together, the product will be the size you want (2048 bits, 4096 bits, and so on).

Now multiply *p* and *q* to get *n*. Let *n* = *pq*.

The next step is to multiply Euler’s totient for each of these primes. Basically, Euler’s totient is the total number of co-prime numbers. Two numbers are considered co-prime if they have no common factors. For example, if the original number is 7, then 5 and 7 would be co-prime. Remember that it just so happens that for prime numbers, this is always the number minus 1. For example, 7 has 6 numbers that are co-prime to it. (If you think about this a bit, you will see that 1, 2, 3, 4, 5, and 6 are all co-prime with 7.)

Let *m* = (*p* − 1)(*q* − 1).

Now we are going to select another number. We will call this number *e*. We want to pick *e* so that it is co-prime to *m*. Choose a small number *e*, co-prime to *m*.

We are almost done generating a key. Now we just find a number *d* that, when multiplied by *e* and modulo *m*, would yield 1. (Remember: *Modulo* means dividing two numbers and returning the remainder. For example, 8 modulo 3 would be 2.)

Find *d*, such that *de* % *m* = 1.

Now you will publish *e* and *n* as the public key. Keep *d* as the secret key. To encrypt, you simply take your message raised to the *e* power and modulo *n*:

\= *me* % *n*

To decrypt, you take the cipher text and raise it to the *d* power modulo *n*:

P = *Cd* % *n*

The letter *e* is for *encrypt* and *d* is for *decrypt*. If all this seems a bit complex to you, you must realize that many people work in network security without being familiar with the actual algorithm for RSA (or any other cryptography for that matter). However, if you wish to go deeper into cryptography, then this is a very good start. It involves some fundamental number theory, particularly regarding prime numbers. There are other asymmetric algorithms that work in a different manner. For example, elliptic curve cryptography is one such example.

Let’s look at an example that might help you understand. Of course, RSA would be done with very large integers. To make the math easy to follow, we will use small integers in this example.

Choose two distinct prime numbers, such as *p* = 61 and *q* = 53. Compute *n* = *pq*:

*n* = 61 × 53 = 3233

Compute the totient of the product as φ(*n*) = (*p* − 1)(*q* − 1):

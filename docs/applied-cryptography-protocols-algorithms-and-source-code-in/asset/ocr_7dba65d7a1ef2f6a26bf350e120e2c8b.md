# CHAPTER 20 Public-Digital Signature Algorithms

[14] If $C = 4096$, then go to step (1). Otherwise, go to step (7).

[15] Save the value of $S$ and the value of $C$ used to generate $p$ and $q$.

In [1154], the variable $S$ is called the “seed,” $C$ is called the “counter,” and $N$ the “offset.”

The point of this exercise is that there is a public means of generating $p$ and $q$. For all practical purposes, this method prevents cooked values of $p$ and $q$. If someone hands you a $p$ and $q$, you might wonder where that person got them. However, if someone have a value for $S$ and $C$ that generated the $p$ and $q$, you can go through this routine yourself. Using a one-way hash function, SHA in the standard, prevents someone from working backwards from $p$ and $q$ to generate an $S$ and $C$.

This security is better than what you get with RSA. In RSA, the prime numbers are kept secret. Someone could generate a fake prime or one of a special format that makes factoring easier. Unless you know the private key, you won't know that. Even if you don't know a person's private key, you can confirm that $p$ and $q$ have been generated randomly.

# ElGamal Encryption with DSA

There have been allegations that the government likes the DSA because it is only a digital signature algorithm and can't be used for encryption. It is, however, possible to use the DSA function to do ElGamal encryption.

Assume the DSA algorithm is implemented with a single function call:

```
DSAssign(p,q,g,k,x,r,s)
```

You supply the numbers $p, q, g, x$ and $h$, and the function returns the signature parameters: $r$ and $s$.

To ElGamal encryption of message $m$ with public key $y$, choose a random number, $k$, and call

```
DSAssign(p,p,g,k,0,r,s)
```

The value of $r$ returned is $a$ in the ElGamal scheme. Throw $away$. Then, call

```
DSAssign(p,p,y,k,0,r,s)
```

Rename the value of $r$ to be $u$; throw $away$.

```
DSAssign(p,p,m,u,0,r,s)
```

Throw $away$. The value of $s$ returned is $b$ in the ElGamal scheme. You now have the ciphertext, $a$ and $b$.

Decryption is just as easy. Using secret key $x$, and ciphertext messages $a$ and $b$, call

```
DSAssign(p,p,a,x,0,0,r)
```
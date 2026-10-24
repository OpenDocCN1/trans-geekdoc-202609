```
❶ kphi = d*e - 1
   t = kphi

❷ while t % 2 == 0:
       t = divmod(t, 2)[0]

❸ a = 2
   while a < 100:
       ❹ k = t
           while k < kphi:
               x = pow(a, k, n)
               ❺ if x != 1 and x != (n - 1) and pow(x, 2, n) == 1:
                   ❻ p = gcd(x - 1, n)
                       break
               k = k*2
       a = a + 2

   q = n//p
❼ assert (p*q) == n
   print('p = ', p)
   print('q = ', q)
```

*Listing 10-7: A Python program that computes the prime factors p and q from the private exponent d*

This program determines kφ(n) from e and d ❶ by finding the number t such that kφ(n) = 2ˢt, for some s ❷. Then it looks for a and k such that (aᵏ)² = 1 mod n ❸, using t as a starting point for k ❹. When this condition is satisfied ❺, you’ve found a solution. It then determines the factor p ❻ and verifies ❼ that the value of pq equals the value of n. It then prints the resulting values of p and q:

```
p = 2046223079
q = 17870599
```

The program correctly returns the two factors.

# Further Reading

RSA deserves a book by itself. I had to omit many important and interesting topics, such as Daniel Bleichenbacher’s padding oracle attack on OAEP’s predecessor (the standard PKCS#1 v1.5) or Manger’s padding oracle attack on OAEP, both attacks being similar in spirit to the padding oracle attack on block ciphers in Chapter 4. There’s also Michael Wiener’s attack on RSA with low private exponents, and attacks using Coppersmith’s method on RSA with small exponents that potentially also have insecure padding.

To see research results related to side-channel attacks and defenses, view the CHES workshop proceedings that have run since 1999 at *https://ches.iacr.org*. One of the most useful references while writing this chapter was
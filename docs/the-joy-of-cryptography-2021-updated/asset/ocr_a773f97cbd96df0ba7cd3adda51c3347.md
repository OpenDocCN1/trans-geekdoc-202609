Example Let's take the example r = 3359 and s = 2953, which are relatively prime (so the CRT applies). Suppose we want to compute 3141592 + 6535897 % rs. Doing it the usual way in Sage looks like this:

```
sage: r = 3359
sage: s = 2953
sage: (3141592 + 6535897) % (r*s)
9677489
```

Doing it in the CRT way looks like this.

```
sage: u = (3141592 + 6535897) % r
sage: v = (3141592 + 6535897) % s
sage: crt( u,v, r,s )
9677489
```

Both methods give the same answer!

# Application to RSA

You might be wondering what the point of all of this is.7 The CRT method seems like a very indirect and wasteful way to compute anything. This impression might be true for simple operations like addition and single multiplications. However, the CRT method is faster for exponentiation mod N, which is the main operation in RSA!

Example In Sage, we can do basic exponentiation mod n as follows:

```
sage: def modexp(x,e,n): # x^e mod n
....:     return Mod(x,n)^e
```

If we are working over an RSA modulus and know its factorization p x q, then we use the CRT method for exponentiation mod pq as follows. We simply do the exponentiation mod p and (separately) mod q, then use the crt function to convert back to Z_pq.

```
sage: def crtmodexp(x,e,p,q): # x^e mod pq, using CRT speedup
....:     u = Mod(x,p)^e
....:     v = Mod(x,q)^e
....:     return crt(u.lift(),v.lift(),p,q)
```

We need to use u.lift() and v.lift() to convert u and v from Mod-objects into integers, because that is what crt expects.

We can use both methods to perform an exponentiation, and measure how long it takes with the timeit function. In this example, N is about 2000 bits long, and the difference in speed is noticeable:

7 I'm talking about the CRT method for arithmetic mod rs, not life in general.
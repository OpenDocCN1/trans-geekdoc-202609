The values of $a$, $m$, and $q$ have to be carefully chosen to get a good random number sequence.

One good choice of values is: $a=0, m=75, q=2^{31}-1$.

**Weakness:** If an adversary is able to capture a sequence of four consecutive random numbers $X_0, X_1, X_2$, and $X_3$, then the adversary can determine the values of $a, m$, and $q$ by solving the following equations:

```
$X_1 = (mX_0 + a) \bmod q$
$X_2 = (mX_1 + a) \bmod q$
$X_3 = (mX_2 + a) \bmod q$
```

Once these values are known, all future random numbers can be determined.

# ii. Cryptographically Generated Random Numbers

# A. Cyclic Encryption

This algorithm makes use of a counter which is initialized to $C_0$ and incremented after generation of each random number.

+   - If a 56-bit key is to be produced (for DES), a counter period of $2^{56}$ will need to be used.

+   - After a random number is produced, the counter is incremented by one. So, the counter value used for each random number generation will be different.

+   - The counter value is encrypted using a secret master key $K$. The encrypted value of the counter forms the next Random Number: $X_i = E_i(c+i)$.

+   - It is not possible for a cryptanalyst to determine the next random number from the knowledge of the previous random number.

Figure 6.28 illustrates the Cryptographically Generated Pseudo-Random Numbers.
# 7.4.1.2 Encryption Algorithm

If any user in the cryptosystem (say User “B”) intends to send a message M ($0 \le M < n$) to use “A,” then “B” encrypts the message using As Public Key ($e, n$) and sends the cipher-text C to user “A”:

```
$C = M^e \pmod n$
```

# 7.4.1.3 Decryption Algorithm

User “A” receives the cipher-text C and recovers the message M by decrypting it using its own Private Key ($d, n$):

```
$M = C^d \pmod n$
```

Prove that the Decrypted Value of a cipher-text at the recipient end is an exact copy of the plaintext encrypted at the sender end.

# Proof

```
$Decrypted Value = C^d \pmod n$
$= (M^e)^d \pmod n$
$= M^{ed} \pmod n$
```

Since, $d = e^{-1} \pmod \Phi(n)$
$. $ed = k \Phi(n) + 1$; for some integer $k$
$. $Decrypted Value at the recipient end $= M^{ed} \pmod n$
$= (M^{\Phi(n)+1}) \pmod n$

Now, we need to prove that $MK\Phi(n) + 1 \pmod n = M$\nThe value of $M$ has two possibilities:

+   - Case 1: $M$ relatively prime to $n$, that is, $GCD(M, n) = 1$
- Case 2: $M$ not relatively prime to ton, that is, $GCD(M, n) \neq 1$

**Case 1:**

$GCD(M, n) = 1$, that is, $M$ is relatively prime to $n$.
Then, $M^{\Phi(n)} = 1 \pmod n$ (by Euler’s Theorem)
Raising both sides of the congruence to power $k$
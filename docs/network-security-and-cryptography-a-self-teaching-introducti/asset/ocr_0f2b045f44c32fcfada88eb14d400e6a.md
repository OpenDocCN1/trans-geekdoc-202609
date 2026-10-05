# PUBLIC-KEY CRYPTOGRAPHY FOR DATA CONFIDENTIALITY • 321

+   Then “A” determines its Public Key $P_A = n_A G$ and makes it available to all other users in the cryptosystem.

**3. Encryption of Plaintext by Sender:** Supposing any user in the cryptosystem intends to send a message $M$ over “A,” then it proceeds as follows:

+   - First message $M$ is encoded in $E_p$ for mapping it to one of the points (say $P_p$ in $(a, b)$) is reversible, that for each possible value of plaintext $M$, there will be a unique point from $E_p$ $(a, b)$.

+   - Encryption of $P_m$ by Sender

+   - Sender selects a random integer $k$ such that $1 < k < n$

+   - Using the public key $P_A$ of intended recipient “A,” the sender encrypts the plain text $P_m$ and creates a cipher-text $C_m$:

```
$C_m = \{kG, P_m + kP_A\}$
```

The cipher-text $C_m$ comprises two components. Both components are the points from $E_p(a, b)$. the first component “kG” is called “clue,” since it provides a clue about parameter “k” to the recipient, since “k” is known only to the sender.

+   - The Cipher-text $C_m$ by recipient is transmitted to the intended recipient “A.”

**4. Decryption of $C_m$ by recipient “A”:** “A” receives the cipher-text $C_m$ and decrypts it follows using its private key $n_A$, which is known only to “A.”

+   - Multiplies $k G$ by $n_A$

+   - Subtracts the result of step (i) from $P_m + kP_A$

i.e., $P_m + kP_A - n_A kG = P_m + kP_A - kP_A$ (since $P_A = n_A G$) = p
Thus, the recipient “A” is able to extract the encoded plaintext $P_m$.

+   - Then “A” decodes $P_m$ to extract the message $m$, without having any knowledge of parameter $k$, which is known only to the sender of the cipher-text.
![](bbox=[0.12, 0.12, 0.9, 0.37])

# Figure 8.10 $\diamondsuit$ Creating a digital signature for a document

$K_B^-(m)$. At first, it might seem odd that Bob is using his private key (which, as we saw in Section 8.2, was used to decrypt a message that had been encrypted with his public key) to sign a document. But recall that encryption and decryption are nothing more than mathematical operations (exponentiation to the power of $e$ or $d$ in RSA; see Section 8.2) and recall that Bob's goal is not to scramble or obscure the contents of the document, but rather to sign the document in a manner that is verifiable and nonforgeable. Bob's digital signature of the document is $K_B^-(m)$.

Does the digital signature $K_B^-(m)$ meet our requirements of being verifiable and nonforgeable? Suppose Alice has $m$ and $K_B^-(m)$. She wants to prove in court (being litigious) that Bob had indeed signed the document and was the only person who could have possibly signed the document. Alice takes Bob's public key, $K_B^+$, and applies it to the digital signature, $K_B^-(m)$, associated with the document, $m$. That is, she computes $K_B^+(K_B^-(m))$, and voilà, with a dramatic flurry, she produces $m$, which exactly matches the original document! Alice then argues that only Bob could have signed the document, for the following reasons:

+   - Whoever signed the message must have used the private key, $K_B$, in computing the signature $K_B^-(m)$, such that $K_B^+(K_B^-(m)) = m$.
- The only person who could have known the private key, $K_B^-$, is Bob. Recall from our discussion of RSA in Section 8.2 that knowing the public key, $K_B^+$, is of no help in learning the private key, $K_B^-$. Therefore, the only person who could know $K_B^-$ is the person who generated the pair of keys, $(K_B^-, K_B^+)$, in the first place, Bob. (Note that this assumes, though, that Bob has not given $K_B^-$ to anyone, nor has anyone stolen $K_B^-$ from Bob.)

It is also important to note that if the original document, $m$, is ever modified to some alternate form, $m'$, the signature that Bob created for $m$ will not be valid for $m'$.
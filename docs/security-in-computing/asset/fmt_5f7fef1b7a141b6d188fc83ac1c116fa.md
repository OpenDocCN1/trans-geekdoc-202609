
The same DES algorithm is used both for encryption and decryption. This result is true because cycle `j` derives from cycle (`j-1`) in the following manner:

```
![Image](graphics/12equ01.jpg)![Image](graphics/12equ02.jpg)
```

where ⊕ is the exclusive OR operation and `f` is the function computed in an expand-shift-substitute-permute cycle. These two equations show that the result of each cycle depends only on the previous cycle.

By rewriting these equations in terms of `R[j-1]` and `L[j-1]`, we get

```
![Image](graphics/12equ03.jpg)
```

and

```
![Image](graphics/12equ04.jpg)
```

Substituting (3) into (4) gives

```
![Image](graphics/12equ05.jpg)
```

Equations ([3](#ch12.html#ch12equ03)) and ([5](#ch12.html#ch12equ05)) show that these same values could be obtained from the results of later cycles. This property makes DES a reversible procedure; we can encrypt a string and also decrypt the result to derive the plaintext again.

With DES, the same function `f` is used forward to encrypt or backwards to decrypt. The only change is that the keys must be taken in reverse order (`k[16]`, `k[15]`, ..., `k[1]`) for decryption. Using one algorithm either to encrypt or to decrypt is convenient for a hardware or software implementation of DES.

### Chaining

You may have noticed a weakness in description of the previous section. DES uses the same process for each 64-bit block. That means that any identical data blocks encrypted with the same key will have the same output. Of course, you might say, the process has to be regular and consistent for decryption to be possible, and that is certainly true.

Now think like an attacker. A bank uses DES to encrypt a network stream of data containing instructions to transfer money from one account to another. The bank chooses a key to use for some period of time, for example, a day, because changing keys is cumbersome. Just to make this argument simple, assume the amount and account number are both exactly 64 bits long and happen to appear on 64-bit boundaries within the transfer message. (A similar argument will work regardless of the lengths and positions of the fields.) In [Figure 12-4](#ch12.html#ch12fig04) we depict the general form of these messages. The figure also shows four examples, to transfer (1) $100 from Annie to Brian, (2) $500 from Carole to Drew, (3) $0.01 from Evin to our malicious agent Zelda, and (4) the same amount from Feng to Zelda. (Note: the encrypted values in these four example figures are fictitious, created just for these explanations; no real cryptography was applied.)

```
![Image](graphics/12fig04.jpg)
```

**FIGURE 12-4** Transfer Messages

Because these are networked communications, Zelda can see them in ciphertext form. Although she cannot interpret the content, she can look for similarities. Let us assume she knows where to look for the different fields. She will see two messages with the same encrypted destination account numbers and infer that those are probably the two transfers to her account. With that knowledge, she can create new messages, as shown in [Figure 12-5](#ch12.html#ch12fig05), to transfer money from Annie and Carole to her account.

```
![Image](graphics/12fig05.jpg)
```

**FIGURE 12-5** Fabricated Transfer Messages

Without ever accessing the underlying plaintext, Zelda has fabricated two encrypted messages that might pass. (She still has a little more work to do to cover for her reuse of a previous transaction number.) The problem described here occurs because each plaintext block is encrypted independently from all other blocks, so an attacker can reorder and substitute blocks undetected.

The solution to this problem is called **chaining**. If the encryption of each block depends not only on the direct ciphertext of its distinct content but also on previous content, the order and position of each block in the chain is fixed. That change would prevent Zelda from reusing blocks from previous encryptions.

In [Figure 12-6](#ch12.html#ch12fig06) you can see the effect of chaining. In the previous figure Annie’s account number encrypted twice as w2z%pr. But in this figure Annie’s account number is first combined with the encryption of the date block using the exclusive OR (⊕) function, producing the result C4UI6H. That C4UI6H is then encrypted, producing the result bl3tfr. Comparing the top and bottom of the figure, you can see that the first field, the date, encrypts the same in both halves, but the next fields differ, so all subsequent blocks are influenced by this difference. The encrypted value of each block feeds into the plaintext of the next block, and so each encrypted block depends on the values of all preceding blocks. Thus, no attacker can reorder or substitute encrypted blocks without destroying this chain of encryption. If we had shown results for the last two lines from the original figure, you would see that the two Zelda blocks would be different, because each depends on different preceding data.

```
![Image](graphics/12fig06.jpg)
```

**FIGURE 12-6** Chained Encryption

### Initialization Vector

You may have detected one final difficulty with the chaining example. Although data blocks along the chain are distinct, the first block (the date) has no prior context on which to depend, and thus it would always encrypt the same. The solution to this difficulty is a slight extension to the chaining approach.

To start the encryption of a data stream, you first create one extra block containing any value. The exact value is insignificant as long as it changes for each encryption; a random number generator is useful. Then, as shown in [Figure 12-7](#ch12.html#ch12fig07) you apply chained encryption, starting with the first block (the random number), and linking subsequent blocks together as in the previous example. In this way, the first real data block (actually the second block encrypted) is different from one time to the next because the random initialization vector is different.

```
![Image](graphics/12fig07.jpg)
```

**FIGURE 12-7** Chained Encryption with an Initialization Vector

These two chaining techniques are similarly applicable with most symmetric ciphers.

### Questions About the Security of DES

Since its first announcement, there has been controversy concerning the security provided by DES. Although much of this controversy has appeared in the open literature, certain features of DES have neither been revealed by the designers nor inferred by outside analysts.

#### Design of the Algorithm

Initially, there was concern with the basic algorithm itself. During development of the algorithm, the National Security Agency (NSA) indicated that key elements of the algorithm design were “sensitive” and would not be made public. These elements include the rationale behind transformations by the S-boxes, the P-boxes, and the key changes. There are many possibilities for the S-box substitutions, but one particular set was chosen for DES.

Two issues arose about the design’s secrecy. The first involved a fear that certain “trapdoors” had been imbedded in the DES algorithm so that a covert, easy means was available to decrypt any DES-encrypted message. For instance, such trapdoors would give the NSA the ability to inspect private communications.

After a Congressional inquiry, the results of which are classified, an unclassified summary exonerated the NSA from any improper involvement in the DES design. (For a good discussion on the design of DES, see [SMI88a].)

The second issue addressed the possibility that a design flaw would be (or perhaps has been) discovered by a cryptanalyst, this time giving an interceptor the ability to access private communications.

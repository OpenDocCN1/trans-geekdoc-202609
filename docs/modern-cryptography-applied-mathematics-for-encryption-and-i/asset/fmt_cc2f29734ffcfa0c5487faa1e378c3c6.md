
In their study of SSL using RSA, Aciiçmez and Schindler examined the timing for modular arithmetic operations used in that specific implementation of RSA. This ultimately led to a method for factoring the public key, thus yielding the private key used in that RSA implementation. This methodology is important because normal approaches to factoring the public key are entirely too time consuming to be of practical use (Swenson, 2008). It is important to derive some additional information about the implementation of RSA in order to attempt a more practical approach to factoring. By using number theory, specifically with respect to the functionality of modular arithmetic, the researchers significantly decreased the time required for factoring the public key. Clearly these findings are significant and show an important problem with some implementations of RSA.

These studies are simply a sample of known attack vectors against RSA. Many of these attacks depend on a small modulus. And you have seen that many RSA implementations use the same small modulus (e = 2^(16) + 1 = 65537). It is also true that increases in computing power will make these attacks, as well as brute-force attempts to crack RSA, even more practical. So far, the cryptography community has reacted by simply using ever larger key sizes for RSA. It seems likely that an entirely new asymmetric algorithm will be needed. But in the meantime, when you implement RSA, make sure that you not only use a large key size, but that you be wary of using too small a modulus value.

#### General Rules for Cryptanalysis

Regardless of the technique used, three resources are required for all cryptanalysis:

   ![image](Images/image00484.jpeg)   **Time**    The number of “primitive operations” that must be performed. This is quite loose; primitive operations could be basic computer instructions, such as addition, XOR, shift, and so forth, or entire encryption methods.

   ![image](Images/image00484.jpeg)   **Memory**    The amount of storage required to perform the attack.

   ![image](Images/image00484.jpeg)   **Data**    The *quantity* of plain texts and cipher texts required.

With infinite time, memory, and data, any cipher can be broken. Of course, nobody has infinite resources, and, in fact, resources are generally quite limited—particularly time. It would do no good to break the encryption of military communications and learn of an attack, if that break occurred several weeks *after* the attack. The information is useful only if it is timely.

**Note**

In general, the primary advantage that a government entity has in cryptanalysis is the resource of memory. A supercomputer, or even a cluster of high-end servers, can put far more resources to breaking a cipher than an individual with a single computer can. Even with those resources, however, breaking a modern cipher is far from trivial. It is still an onerous, resource-intensive task with no guarantee of success. And breaking a modern cipher with a PC is simply not feasible.

With any cryptanalysis attack, varying degrees of success are possible:

   ![image](Images/image00484.jpeg)   **Total break**    The attacker deduces the secret key.

   ![image](Images/image00484.jpeg)   **Global deduction**    The attacker discovers a functionally equivalent algorithm for encryption and decryption, but without learning the key.

   ![image](Images/image00484.jpeg)   **Instance (local) deduction**    The attacker discovers additional plain texts (or cipher texts) not previously known.

   ![image](Images/image00484.jpeg)   **Information deduction**    The attacker gains some Shannon information about plain texts (or cipher texts) not previously known.

   ![image](Images/image00484.jpeg)   **Distinguishing algorithm**    The attacker can distinguish the cipher from a random permutation.

Consider this list carefully. A total break may be the only type of cryptanalysis success you’ve considered. However, that is only one possible definition of a successful cryptanalysis—and, in fact, it is the least likely outcome. In general, if your cryptanalysis produces more information about the key than was previously known, it is considered a success.

#### Rainbow Tables

Many passwords are stored with a cryptographic hash, which prevents the network or database administrator from reading the password. Recall from [Chapter 9](#part0018.xhtml#ch09) that cryptographic hashes are not reversible—it is not merely computationally difficult, or impractical, to “unhash” something; it is mathematically impossible. It would seem, then, that breaking passwords protected by cryptographic hashes is impossible. However, that is not actually the case.

A *rainbow table* is a precomputed table of hashes. The most primitive way to create such a table would be to precompute hashes of all possible passwords of a given size. Assuming a standard English keyboard, there are 26 characters in uppercase and 26 in lowercase (52 possibilities), 10 digits, and about 8 special characters (#, !, $, and so on)—or about 70 possible values available for each character (the value 70 is just a rough estimate to illustrate this concept). A single character password could have 70 possible values, whereas a two-character password could have 70², or 4900 possible values. Even an 8-character password could have up to 576,480,100,000,000 possible values! So calculating tables that account for all passwords of any length from 5 to 10 characters would be computationally intensive and would require a great deal of storage.

Because this method for composing precomputed tables of hashes is very primitive, hash chains can be used instead to make this process efficient and to reduce the space needed to store the precomputed hashes. To create a hash chain, you use a reduction function, we will call R, that maps hash values back to plain-text values. This is not unhashing or reversing a hash; it is merely a method to precompute hashes more quickly.

Another, even more advanced, method is to replace the reduction function with a sequence of related reduction functions R[1]…R[k]. The issue then becomes how to implement this process. For example, Microsoft Windows stores password hashes in the Security Account Manager (SAM) file. To find a password, you would first obtain the SAM file for a target machine, and then search the contents through rainbow tables for a match.

The Windows password-cracker tool Ophcrack can automate this process for you. After loading a CD/DVD containing rainbow tables, Ophcrack boots to a live version of Linux. Then it launches a tool that copies the SAM file from the Windows machine and searches the rainbow tables on the CD/DVD for a match. [Figure 17-3](#part0028.xhtml#ch17fig03) shows the Ophcrack interface taken from an actual system, so some information has been redacted for security purposes.

![Images](Images/image00751.jpeg)

* * *

**FIGURE 17-3    Ophcrack interface**

**Note**

Rainbow tables get very large. As of this writing, no portable rainbow tables can return passwords that are more than 12 to 14 characters in length. Therefore, longer passwords are useful for thwarting this attack.

#### The Birthday Paradox

If none of the previous methods works, and you are forced to rely on brute force, finding the key may not take as much time as you think. Consider DES, for example, with its 56-bit key. This means 2^(56) possible keys, or in decimal notation, 72,057,594,037,927,936 possible keys. Even if you could try 1 million keys per second, this would take 72,057,594,037 seconds, or about 2285 years—much too long. You should realize that you probably won’t have to try every single key; you might get the right key just by chance in the first 100 you try, though the odds against that are beyond astronomical! Once you pass the first half the possible keys (at about the 1142-year mark) it gets increasingly likely that you will hit the key with your next attempt. That still is not helpful.

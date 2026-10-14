
Of course, the easiest way to breach encryption is to see the password as the user types it in. This is often accomplished via spyware. For intelligence-gathering agencies, this is a viable option. For law enforcement, this can be done only with a warrant, and for civilians this is simply not an option.

### Side-Channel Attack

Side-channel attacks are more difficult to accomplish. They are based on studying the physical components of a cryptographic system, seeking clues as to the cryptographic keys. For example, a gateway router that implements a virtual private network might be examined to study its power consumption or timing, or to see if there are electromagnetic leaks that provide cryptographic clues that can be used in cryptanalysis.

There are variations of this attack, including the following:

![image](Images/image00484.jpeg) `Timing attacks` Attacks that measure how much time various computations take to perform.

![image](Images/image00484.jpeg) `Data remanence` Attacks that gather sensitive data or portions thereof that remain in memory after having been deleted.

![image](Images/image00484.jpeg) `Electromagnetic attacks` Attacks based on leaked electromagnetic radiation.

Electromagnetic emanations are particularly interesting with respect to the most common sort of network cable, unshielded twisted pair (UTP). You can attempt to detect the signal passing through UTP cable and derive information from it. As you might suspect, this is a nontrivial task. In fact, in response to this issue, the U.S. National Security Agency established the TEMPEST standard, which prohibits cables used to transmit classified data from being within a certain distance of cables transmitting unclassified data to prevent information “leakage.”

### Resources

As stated at the beginning of this chapter, the goal of this chapter is to get you familiar with the concepts of cryptanalysis. If you are seeking more specific information, perhaps even tutorials on cryptanalysis, I suggest you first master the information in this chapter, and then consider the following resources:

![image](Images/image00484.jpeg) “A Tutorial on Linear and Differential Cryptanalysis,” by Howard M. Heys, Memorial University of Newfoundland, [www.engr.mun.ca/~howard/PAPERS/ldc_tutorial.pdf](http://www.engr.mun.ca/~howard/PAPERS/ldc_tutorial.pdf).

![image](Images/image00484.jpeg) “Differential Cryptanalysis Tutorial,” The Amazing King web site, [www.theamazingking.com/crypto-diff.php](http://www.theamazingking.com/crypto-diff.php). This source is not a typical scholarly resource and provides information in a way that is easy to understand.

![image](Images/image00484.jpeg) “Linear Cryptanalysis Tutorial,” The Amazing King web site, [www.theamazingking.com/crypto-linear.php](http://www.theamazingking.com/crypto-linear.php).

![image](Images/image00484.jpeg) “A Self-Study Course in Block-Cipher Cryptanalysis,” by Bruce Schneier, [www.schneier.com/paper-self-study.pdf](http://www.schneier.com/paper-self-study.pdf).

![image](Images/image00484.jpeg) “A Tutorial on Linear and Differential Cryptanalysis,” by Howard M. Heys. *Cryptologia* 26, 3 (July 2002), 189–221, [http://dx.doi.org/10.1080/0161-110291890885](http://dx.doi.org/10.1080/0161-110291890885).

![image](Images/image00484.jpeg) “Cryptography and Network Security” video, by Prof. D. Mukhopadhyay, [www.youtube.com/watch?v=xcBqraHhcJU](http://www.youtube.com/watch?v=xcBqraHhcJU).

### Conclusions

This chapter provided a broad general introduction to cryptanalysis. You should be very familiar with classic techniques such as frequency analysis, and you should understand the concept of the birthday paradox, as well as how it is applied to cryptographic problems.

For modern methods such as linear cryptanalysis and differential cryptanalysis, you should have a general understanding of the concepts and some grasp of the applications. It is not critical that you be able to apply these techniques. You should, however, have a working knowledge of rainbow tables.

### Test Your Knowledge

[1](#part0028.xhtml#ch17qu1). What is brute-force cracking?

[2](#part0028.xhtml#ch17qu2). Applying the birthday paradox, how many keys would you need to try out of *n* possible keys to have a 50 percent chance of finding a match?

[3](#part0028.xhtml#ch17qu3). In the English language, _______ is the most common first letter of a word.

[4](#part0028.xhtml#ch17qu4). ______ is the most common word in the English language.

[5](#part0028.xhtml#ch17qu5). With a ______, the attacker obtains a number of plain-text/cipher-text pairs.

[6](#part0028.xhtml#ch17qu6). ______ is based on finding affine approximations to the action of a cipher.

[7](#part0028.xhtml#ch17qu7). Using ______, the attacker discovers additional plain texts (or cipher text) not previously known.

[8](#part0028.xhtml#ch17qu8). In ______, the attacker discovers a functionally equivalent algorithm for encryption and decryption, but without learning the key.

[9](#part0028.xhtml#ch17qu9). A _____ is essentially a precomputed table of hashes.

[10](#part0028.xhtml#ch17qu10). The concept of a hash-chain is to use a _____, we will call R, that ____.

### Answers

[1](#part0028.xhtml#ch17qu1a). Trying every possible key to guess the right one

[2](#part0028.xhtml#ch17qu2a). 774√*n*

[3](#part0028.xhtml#ch17qu3a). T

[4](#part0028.xhtml#ch17qu4a). the

[5](#part0028.xhtml#ch17qu5a). known plain-text attack

[6](#part0028.xhtml#ch17qu6a). Linear cryptanalysis

[7](#part0028.xhtml#ch17qu7a). instance (local) deduction

[8](#part0028.xhtml#ch17qu8a). global deduction

[9](#part0028.xhtml#ch17qu9a). rainbow table

[10](#part0028.xhtml#ch17qu10a). reduction function, maps hash values back to plain-text values

### Endnotes

[1](#part0028.xhtml#ch17note1). For a list of Mitsuru Matsui’s publications, see [www.cryptographersworld.com/a.php?a=64](http://www.cryptographersworld.com/a.php?a=64).

[2](#part0028.xhtml#ch17note2). M. Matsui, “Linear Cryptanalysis Method for DES Cipher,” 1999, [www.cs.bgu.ac.il/~beimel/Courses/crypto2001/Matsui.pdf](http://www.cs.bgu.ac.il/~beimel/Courses/crypto2001/Matsui.pdf).

[3](#part0028.xhtml#ch17note3). C. Swenson, *Modern Cryptanalysis: Techniques for Advanced Code Breaking* (Wiley, 2008).

[4](#part0028.xhtml#ch17note4). J. Kelsey, B. Schneier, and D. Wagner, “Mod *n* Cryptanalysis, with Applications Against RC5P and M6,” 1999, [www.schneier.com/paper-mod3.pdf](http://www.schneier.com/paper-mod3.pdf).

[5](#part0028.xhtml#ch17note5). N. Heninger and H. Shacham, “Reconstructing RSA Private Keys from Random Key Bits,” *Advances in Cryptology Lecture Notes in Computer Science*, 1 (1) (2009).

[6](#part0028.xhtml#ch17note6). B. Su, W. Wu, and W. Zhang, “Security of the SMS4 Block Cipher Against Differential Cryptanalysis,” *Journal of Computer Science and Technology*, 26(1), 130–138 (2011).

[7](#part0028.xhtml#ch17note7). A. Alekseychuk, L. Kovalchuk, and S. Pal’chenko, “Cryptographic Parameters of s-Boxes that Characterize the Security of GOST-like Block Ciphers Against Linear and Differential Cryptanalysis,” *Zakhist Inform*, 2, 12–23 (2007).

[8](#part0028.xhtml#ch17note8). Y. Zhao and W. Qi, “Small Private-Exponent Attack on RSA with Primes Sharing Bits,” *Lecture Notes in Computer Science*, 4779, 221–229 (2007).

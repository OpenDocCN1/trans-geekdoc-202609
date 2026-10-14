
As you can see, the `a` in the plain text is shifted to the right three letters to become a `d` in the cipher text. Then the `t` in the plain text is shifted three letters to the right to become a `w` in the cipher text. This process continues for all the letters in the plain text. In our example, none of the shifts went beyond the letter `z`. What would happen if we shifted the letter `y` to the right three? The process would wrap around the alphabet, starting back at letter `a`. So the letter `y` would be shifted to a letter `b` in the cipher text.

**Note**

Decryption is trivial if the recipient knows the shift that was used and reverses it. For example, if the sender shifts three to the right to encrypt the message, the recipient can shift three to the left to decrypt the message.

Although Caesar was reputed to have used a shift of three to the right, any shifting pattern will work with this method, shifting either to the right or left by any number of spaces. Because this is a very simple method to understand, it’s a good place to start our study of encryption. It is, however, extremely easy to crack. You see, any language has a certain letter and word *frequency*, meaning that some letters are used more frequently than others. In the English language, the most common single-letter word is `a`, followed closely by the word `I`. The most common three-letter word is `the`, followed closely by the word `and.` Those two facts alone could help you decrypt a Caesar cipher. However, you can apply additional rules. For example, in the English language, the most common two letter sequences are `oo` and `ee`.^([4](#part0009.xhtml#ch01note4a)) Examining the frequency of letter and letter combination occurrences is called *frequency analysis*.

It is claimed that other Caesars, such as Augustus, used variations of the Caesar cipher, such as one shift to the right. It should be obvious that any shift, left or right, of more than 26 (at least in English) would simply loop around the alphabet. So a shift to the right of 27 is really just a shift of one.

Although the Caesar cipher is certainly not appropriate for modern cryptographic needs, it does contain all the items needed for a cryptography algorithm. First, we have the plain text message—in our current example, `Attack at dawn`. Then we have an algorithm—shift every letter. And then a key, in this case +`3`, or three to the right (–`3` would be three to the left). And finally we have cipher text, `Dwwdfn dw gdzq`. This is, essentially, the same structure used by all modern symmetric algorithms. The only differences between the Caesar cipher and modern symmetric ciphers are the complexity of the algorithm and the size of the key.

The size of the key brings us to one significant problem with the Caesar cipher—its small key space. Recall that key space is the total number of possible keys. Because there are only 26 letters in the English alphabet, the key space is `26` (that is, +–`26`). It would be relatively easy for a person working with pen and paper to check all possible keys, and it would be ridiculously trivial for a computer to do so. In the cyber security world, a malicious person who checks all possible keys to decipher an encrypted message is conducting what is called a *brute-force attack*. The smaller the key space, the easier a brute-force attack will be. Compare the Caesar cipher, with a key space of 26, to AES 128-bit, with a key space of 2^(128), or about 3.4 × 10^(38). Clearly, the larger key space makes a cipher more resistant to brute-force attacks. Note, however, that simply having a long key is not sufficient for security. You will learn more about this when we discuss cryptanalysis in [Chapter 17](#part0028.xhtml#ch17).

###### Mathematical Notation of the Caesar Cipher

With the various ancient ciphers we will be using, the math is trivial. However, it is a good idea for you to become accustomed to mathematical notation, at least with those algorithms where such notation is appropriate. It is common to use a capital letter `P` to represent plain text and a capital letter `C` to represent cipher text. We can also use a capital letter `K` to represent the key. This gives us the following mathematical representation of a Caesar cipher:

C ≡ P + K (mod 26)

Don’t be overly concerned about the mod 26. We will explore modulus operations in detail in [Chapter 4](#part0012.xhtml#ch04). For now, I just use the modulus operation to denote dividing by a given number (in this case, 26, because there are 26 letters in the alphabet) and listing only the remainder.

Decryption can also be represented via mathematical symbols:

P ≡ C – K (mod 26)

The mathematical representation of Caesar’s method of shifting three to the right is

C ≡ P + 3 (mod 26)

According to the book *The Lives of the Caesars*, written by Suetonius, Julius Caesar used this cipher extensively:

              There are also the letters of his to Cicero, as well as to his intimates on private affairs, and in the latter, if he had anything confidential to say, he wrote it in cipher, that is by so changing the order of the letters of the alphabet, that not a word could be made out. If anyone wishes to decipher these, and get at their meaning, he must substitute the fourth letter of the alphabet, namely D, for A, and so with the others.^([5](#part0009.xhtml#ch01note5a))

If the plain text is the 24th letter of the alphabet (which is the letter `X`), then the cipher text is (24 + 3)/26, listing only the remainder. Thus, 27/26 = 1, or the letter `A`.

**Note**

We cannot know how effective the Caesar cipher was at concealing messages. However, at the time of Julius Caesar, illiteracy was widespread and cryptography was not widely known. So what may seem a trivial cipher today—in fact, child’s play—may well have been effective enough more than 2000 years ago.

The Caesar cipher is probably the most widely known substitution cipher, but it is not the only one. All substitution ciphers operate the same way: by substituting each letter in the plain text for some letter in the cipher text, with a one-to-one relationship between the plain text and cipher text. Let’s look at a few other substitution ciphers.

##### Atbash Cipher

Hebrew scribes copying the biblical book of Jeremiah used the `Atbash substitution cipher.` Applying the Atbash cipher is fairly simple: just reverse the order of the letters of the alphabet. This is, by modern standards, a very primitive cipher that is easy to break. For example, in English, `a` becomes `z`, `b` becomes `y`, `c` becomes `x`, and so on. Of course, the Hebrews used the Hebrew alphabet, with `aleph` being the first letter and `tav` the last letter. However, I will use English examples to demonstrate the cipher:

![Images](Images/image00487.jpeg)

becomes

![Images](Images/image00488.jpeg)

As you can see, the `A` (the first letter in the alphabet) is switched with `Z` (the last letter), and the `t` is the 19th letter (or 7th from the end) and gets swapped with `g`, the 7th letter from the beginning. This process is continued until the entire message is enciphered.

To decrypt the message, you simply reverse the process so that `z` becomes `a`, `b` becomes `y`, and so on. This is obviously a simple cipher and is not used in modern times. However, like the Caesar cipher example, it illustrates the basic concept of cryptography—to perform some permutation on the plain text to render it difficult to read by those who don’t have the key to “unscramble” the cipher text. The Atbash cipher, like the Caesar cipher, is a single-substitution cipher (each letter in the plain text has a direct, one-to-one relationship with each letter in the cipher text). The same letter and word frequency issues that can be used to crack the Caesar cipher can be used to crack the Atbash cipher.

##### Affine Ciphers

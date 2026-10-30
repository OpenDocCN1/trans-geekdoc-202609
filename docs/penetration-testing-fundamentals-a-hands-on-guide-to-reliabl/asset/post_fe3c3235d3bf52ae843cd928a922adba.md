
## PROJECTS
### PROJECT 1
Choose one of the standards discussed in this chapter and write a brief one-page description of not only the standard, but also how you would apply that standard to your own penetration testing.

## Chapter 3
### Cryptography
### Chapter Objectives
After reading this chapter and completing the exercises, you will be able to do the following:
- Understand the basics of cryptography
- Understand how cryptography affects your penetration testing
- Use standard methods to attempt to circumvent cryptography

You may be asking yourself, why a chapter on cryptography in a book about penetration testing? Cryptography is used to secure data, to store password hashes, and to achieve a variety of other security processes. Unfortunately, the view of cryptography presented in movies and television is almost entirely wrong. As a penetration tester, you will need a working knowledge of cryptography. This will guide you as to what can be circumvented, and what cannot. It will help you understand the capabilities and limitations a pen tester, or an attacker, faces when dealing with cryptography.

Of course, a single chapter cannot make one an expert in cryptography. Even an entire book cannot do that. But what I can do in this chapter is provide you with a working knowledge of cryptography, enough to function effectively as a penetration tester. And hopefully you will also gain enough of a foundation in cryptography to support further study if you decide to pursue that. At the end of this chapter, you will be given some recommended resources to continue your study of cryptography.

Because this is a text on penetration testing, as we discuss modern cryptographic algorithms, there will be an emphasis on the algorithms’ relevance to system security.

### Cryptography Basics
The entire purpose of cryptography is to secure messages. In modern times, cryptography has expanded to include cryptographic hashes and digital signatures. All of these tasks are about information security.

And penetration testing is about testing security. Therefore, a penetration tester must be able to at least perform some basic testing of the implementation of security.

## History of Encryption
One of the most common approaches to learning a new topic is to begin with the history of that topic. This works for cryptography as well. In this section I will provide you a general introduction to historical ciphers. Now, these won’t be used in modern penetration testing, but they will help you conceptually understand cryptography so that we can move on to more relevant topics in modern cryptography.

### The Caesar Cipher
One of the oldest encryption methods is the Caesar cipher. This method is purported to have been used by the ancient Roman Caesars—thus, the name. It is actually quite simple to do. You choose some number by which to shift each letter of a text. For example, if the text is

```
A cat
```

and you choose to shift by two letters, then the message becomes

```
C ecv
```

Or, if you choose to shift by three letters, it becomes

```
D f dw
```

Julius Caesar was reputed to have used a shift of three to the right. However, you can choose any shifting pattern you wish. You can shift either to the right or to the left by any number of spaces you like. Because this is a very simple method to understand, it makes a good place to start our study of encryption. It is, however, extremely easy to crack. You see, any language has a certain letter and word frequency, meaning that some letters are used more frequently than others. In the English language, the most common single-letter word is a. The most common three-letter word is the. Those two rules alone could help you decrypt a Caesar cipher. For example, if you saw a string of seemingly nonsense letters and noticed that a three-letter word was frequently repeated in the message, you might easily surmise that this word was the—and the odds are highly in favor of this being correct. Furthermore, if you frequently noticed a single-letter word in the text, it is most likely the letter a. You now have found the substitution scheme for A, T, H, and E. You can now either translate all of those letters in the message and attempt to surmise the rest or simply analyze the substitute letters used for A, T, H, and E and derive the substitution cipher that was used for this message. Decrypting a message of this type does not even require a computer. It could be done in less than ten minutes using pen and paper by someone with no background in cryptography. There are other rules that will help make cracking this code even easier. For example, in the English language the two most common two-letter combinations are ee and oo. That gives you even more to work on.

Another reason this algorithm can be easily cracked is an issue known as key space. The *key space* is the number of possible keys that could be used. In this case, when applied to the English alphabet, there are only 26 possible keys since there are only 26 letters in the English alphabet. That means that you could simply try each possible key (+1, +2, +3....+26) until one works. Trying all possible keys is referred to as a *brute force attack*.

The substitution scheme you choose (for example, +2, +1) is referred to as a *substitution alphabet* (that is, *B* substitutes for *A*, *U* substitutes for *T*). Thus, the Caesar cipher is also referred to as a *mono-alphabet substitution* method, meaning that it uses a single substitution for the encryption. There are other mono-alphabet algorithms, but the Caesar cipher is the most widely known.

### Atbash
In ancient times, Hebrew scribes used this substitution cipher to encrypt religious works such as the Book of Jeremiah. Applying the Atbash cipher is fairly simple; just reverse the order of the letters of the alphabet. This is, by modern standards, a very primitive and easy-to-break cipher.

The Atbash cipher is a Hebrew code that substitutes the first letter of the alphabet for the last and the second letter for the second to the last, and so on. It simply reverses the alphabet. For example, in English:

A becomes Z, B becomes Y, C becomes X, and so on

Of course, the Hebrews used a different alphabet, with *aleph* being the first letter and *tav* being the last letter. However, I will use English examples to demonstrate this:

Attack at dawn

becomes

Zggzxp zg wz dm

As you can see, the *A* is the first letter in the alphabet and is switched with *Z*, the last letter in the alphabet. Then the *T* is the nineteenth letter (seventh from the end) and gets swapped with *G*, the seventh letter from the beginning. This process is continued until the entire message is enciphered.

To decrypt the message, you simply reverse the process and *Z* becomes *A*, *B* becomes *Y*, and so on. This is obviously a rather simple cipher and not used in modern times. However, it illustrates the basic concept of cryptography: to perform some permutation on the plaintext to render it difficult to read by those who don’t have the key to unscramble the ciphertext. The Atbash cipher, like the Caesar cipher, is a single substitution cipher. That means each letter in the plaintext has a direct, one-to-one relationship with each letter in the ciphertext. This also means that the same letter and word frequency issues that can be used to crack a Caesar cipher can be used to crack the Atbash cipher.

### Multi-Alphabet Substitution
Eventually, a slight improvement on the Caesar cipher was developed, called *multi-alphabet substitution*. In this scheme, you select multiple numbers by which to shift letters (that is, multiple substitution alphabets). For example, if you select three substitution alphabets (+2, −2, +3), then

```
A CAT
```

becomes

```
C ADV
```

Notice that the fourth letter starts over with another +2, and you can see that the first A was transformed to C and the second A was transformed to D. This makes it more difficult to decipher the underlying text. While this is harder to decrypt than a Caesar cipher, it is not overly difficult. It can be done with simple pen and paper and a bit of effort. It can be cracked very quickly with a computer. In fact, no one would use such a method today to send any truly secure message, for this type of encryption is considered very weak.

At one time, multi-alphabet substitution was considered quite secure. In fact, a special version of this, called a Vigenère cipher, was used in the 1800s and early 1900s. The Vigenère cipher was invented in 1553 by Giovan Battista Bellaso. This is a polyalphabetic cipher that uses a lookup table. Figure 3-1 shows the table used in the Vigenère cipher.

|   | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z |
| B | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A |
| C | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B |
| D | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C |
| E | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D |
| F | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E |
| G | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F |
| H | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G |
| I | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H |
| J | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I |
| K | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J |
| L | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K |
| M | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L |
| N | N | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M |
| O | O | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N |
| P | P | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O |
| Q | Q | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P |
| R | R | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q |
| S | S | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R |
| T | T | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S |
| U | U | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T |
| V | V | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U |
| W | W | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V |
| X | X | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W |
| Y | Y | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X |
| Z | Z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y |

Match the letter of your keyword on the top with the letter of your plaintext on the left to find the ciphertext. For example, if you are encrypting the word cat and your key is horse, then the ciphertext is jok.

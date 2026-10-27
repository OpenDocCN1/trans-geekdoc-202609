
Below this, the key GAUSS is written vertically down the left hand side to provide the first letters of our five cipher alphabets. Each of these cipher alphabets is continued from its first letter in the same order as our initial mixed alphabet. Now to encipher, the five alphabets are used in order, as many times as necessary, until the message is at an end. We get:

```
MATHEMATICS IS THE QUEEN OF THE SCIENCES plaintext
GAUSSGAUSSG AU SSG AUSSG AU SSG AUSSG AUS key
OHZQLOHZUIN VR DQX RJLLS FA DQX GTULSJSF ciphertext
```

This sort of cipher is referred to as a Quagmire III by members of the American Cryptogram Association (ACA), such as James J. Gillogly. The entire plaintext of Kryptos has not yet been recovered, but Gillogly, using computer programs of his own design, deciphered the majority of it in 1999. Several factors served to make his work more difficult:

- 1. There’s no obvious indication that the left side contained four ciphers instead of just one.
- 2. The mixing of the alphabets was done with a keyword, but not KRYPTOS, as in the clue on the right side.
- 3. Sanborn intentionally introduced some errors in the ciphers.
- 4. Only the first two ciphers are Quagmire IIIs. Ciphers 3 and 4 arose from other systems.

Determining the correct keys and recovering the first two messages is left as a challenge to the reader. The solutions can easily be found online. Can you use the techniques detailed in this chapter to meet this challenge? The second part should be easier than the first, since there is more ciphertext to work with.

The third cipher made use of transposition (see Chapter 3) and was also solved by Gillogly. With only a little more than three lines of ciphertext left, Gillogly got stuck. He was unable to break the fourth and final cipher.

After Gillogly’s success, the CIA revealed that one of its employees, David Stein, had already deciphered the portions Gillogly recovered back in 1998. Stein’s results appeared in a classified publication, which James had no opportunity to see. Not to be bested by CIA, the National Security Agency (NSA) revealed that some of their employees had solved it in 1992, but initially NSA wouldn’t provide their names! In 2005, the information was released that it was actually a team at NSA (Ken Miller, Dennis McDaniels, and two others whose identities are still not publicly known).17 Despite intense attention, the last portion of Kryptos has resisted decipherment, at least as far as the general public knows! “People call me an agent of Satan,” says artist Sanborn, “because I won’t tell my secret.”18

Sanborn (Figure 2.14) has, at least, revealed valuable clues. On November 20, 2010, he indicated that the letters starting at position 64 of the undeciphered portion, namely NYPVTT, decipher to BERLIN.19 Surprisingly, this didn’t help! No solution came forth! Exactly four years later, on November 20, 2014, Sanborn released another clue. It represented an expansion of his previous clue. He said that NYPVTTMZFPK deciphered to BERLIN CLOCK. Still no solution appeared,

17 http://cn.wikipedia.org/wiki/Kryptos.
18 Levy, Steven, “Mission Impossible: The Code Even the CIA Can’t Crack,” Wired, Vol. 17, No. 5, April 20, 2009.
19 Scryer, “Kryptos Clue,” The Cryptogram, Vol. 77, No. 1, January–February 2011, p. 11. Scryer is the American Cryptogram Association (ACA) pen-name used by James J. Gillogly.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_105_0.png)

**Figure 2.14**  James Sanborn (1945–) ([http://www.pbs.org/wgbh/nova/sciencenow/3411/images/ate-bio-03.jpg](http://www.pbs.org/wgbh/nova/sciencenow/3411/images/ate-bio-03.jpg))

and now we have another mini-mystery—why were both clues released on November 20? Does this date have some special significance for Sanborn or *Kryptos*? In 2020, Sanborn provided a third clue: the letters in positions 26 through 34 decipher to NORTHEAST. This clue broke the previous pattern of dates, being given on January 29.[^20]

Although matrix encryption is not presented until [Chapter 6], I should point out now that some researchers believe that a form of matrix encryption was used to create the still unsolved portion of *Kryptos*. Greg Link, Dante Molle, and I investigated this possibility, but were unable to offer definitive proof one way or the other.[^21] There are many ways in which matrices can be used to encipher text and we were only able to use Sanborn’s clues to rule out some of the simpler methods.

## 2.5 Autokeys

Now that we’ve examined the cryptography, cryptanalysis, and historical uses of the basic Vigenère cipher, let’s examine the real contribution that Blaise de Vigenère made to this system, which,

[^20] Schwartz, John, and Jonathan Corum, “This Sculpture Holds a Decades-Old Mystery. And Now, Another Clue,” *The New York Times*, January 29, 2020, available online at [https://www.nytimes.com/interactive/2020/01/29/climate/kryptos-sculpture-final-clue.html](https://www.nytimes.com/interactive/2020/01/29/climate/kryptos-sculpture-final-clue.html).

[^21] Our investigation appeared as Bauer, Craig, Gregory Link, and Dante Molle, “James Sanborn’s *Kryptos* and the Matrix Encryption Conjecture,” *Cryptologia*, Vol. 40, No. 6, 2016, pp. 541–552. The results were later summarized in a broader survey of *Kryptos* as part of chapter 9 (pp. 386–407) of Bauer, Craig P., *Unsolved! The History and Mystery of the World’s Greatest Ciphers from Ancient Egypt to Online Secret Societies*, Princeton University Press, Princeton, New Jersey, 2017.

recall, already existed. Vigenère’s autokey only used the given key (COMET in the examples below) once. After that single application, the original message (or the ciphertext generated) is used as the key for the rest of the message.

```
S E N D S U P P L I E S ...    message
C O M E T S E N D S U P ...    key
U S Z H L M T C O A Y H ...    ciphertext
```

The ciphertext used as “key”:

```
S E N D S U P P L I E S ...    message
C O M E T U S Z H L O H ...    key
U S Z H L O H O S T S Z ...    ciphertext
```

This particular example was presented by Claude Shannon in his classic paper “Communication Theory of Secrecy Systems.”22

Since the encipherment of each letter depends on previous message or cipher letters, we have a sort of chaining in use here. This idea was applied again when matrix encryption was discovered and is still in use in modern block ciphers. It’s examined in greater detail in this book in Section 14.6, which covers various modes of encryption. Using the ciphertext as the key, although sounding like a complication, yields an easily broken cipher!

One risk associated with various autokey methods is that an error in a single position can propagate through the rest of the ciphertext. Observe what happens in our earlier example if the third character is mistakenly enciphered as N instead of Z. An error-free encipherment is reproduced below for comparison.

```
S E N D S U P P L I E S ...    message
C O M E T U S N H L O H ...    key
U S N H L O H C S T S Z ...    ciphertext obtained
U S Z H L O H O S T S Z ...    ciphertext desired
```

Continuing on we would find that every fifth ciphertext character after our initial error is also incorrect.

The Vigenère cipher was introduced in this chapter, then broken, and we’re about to go on to patch it, creating a stronger system. However, it should be noted that the Vigenère cipher did not get disposed of so quickly in the real world. It had an extremely successful run. We may never again see a system that survives for hundreds of years before successful attacks are discovered.

## 2.6 The Running Key Cipher and Its Cryptanalysis

Because the major weakness in the Vigenère cipher is the fact that the key repeats at regular intervals, allowing the attacks described above, a natural improvement is to encipher in a similar manner, but with a key that does not repeat. One way to do this is by using the text of a book as the key. This approach is often called a running key (Vigenère) cipher. An example is provided below.

```
BEGIN THE ATTACK AT DAWN    plaintext
IT WAS THE BEST OF TIMES I    key
JXCIF MOI BXKTQP TB PEOV    ciphertext
```


of the involvement of early cryptographers in alchemy and magic, let it be known that *Traicté des Chiffres* contains a recipe for making gold.

The Vigenère cipher was one of the best at the time, especially when using mixed alphabets; nevertheless, there are still various cases of its being cracked. One amusing anecdote involves such a cipher being broken by Casanova (Figure 2.7), who then used his accomplishment as a means to a seduction.⁶ He wrote:

Five or six weeks later, she asked me if I had deciphered the manuscript which had the transmutation procedure. I told her that I had.

> > “Without the key, sir, excuse me if I believe the thing impossible.”
> > “Do you wish me to name your key, madame?”
> > “If you please.”

I then told her the word, which belonged to no language, and I saw her surprise. She told me that it was impossible, for she believed herself the only possessor of that word which she kept in her memory and which she had never written down.

I could have told her the truth – that the same calculation which had served me for deciphering the manuscript had enabled me to learn the word – but on a caprice it struck me to tell her that a genie had revealed it to me. This false disclosure fettered Madame d’Urfé to me. That day I became the master of her soul, and I abused my power. Every time I think of it, I am distressed and ashamed, and I do penance now in the obligation under which I place myself of telling the truth in writing my memoirs. [I took my leave] bearing with me her soul, her heart, her wits and all the good sense that she had left.

Sadly, Casanova didn’t reveal his method of cryptanalysis.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_91_0.png)

Figure 2.7 Casanova, studly codebreaker.

## 2.3 Cryptanalysis of the Vigenère Cipher

So, how can we be like Casanova and break a Vigenère cipher? Knowing the length of the key usually makes breaking this system easy. For example, if the length of the key was 2, then the first, third, fifth, etc., letters would all be enciphered with the same alphabet, as would the second, fourth, sixth, etc., albeit using a different alphabet. Grouping these letters together and looking at the frequencies, one letter usually stands out, namely E. A difficulty may arise; if the message is short, the most frequent letter in a specific group won’t always be E. This problem is addressed in the example coming up. For now, let’s assume that we can identify E. Because a straight alphabet is used, all the other letters would also be known. Thus, the message is easily broken. If mixed alphabets are used, the decipherment is slower, but still possible with patience, using a frequency table. Making the key longer requires separating the ciphertext into more groups. For example, if the key is of length 5, we would group the letters as follows:

| | |
|---|---|
|1, 6, 11, 16, ...|alphabet 1|
|2, 7, 12, 17, ...|alphabet 2|
|3, 8, 13, 18, ...|alphabet 3|
|4, 9, 14, 19, ...|alphabet 4|
|5, 10, 15, 20, ...|alphabet 5|

Notice that each group will be part of an equivalence class mod 5.

So how can we determine the length of the key? Several methods are available. The simplest is to assume that some plaintext portions of the message are repeated in the same alignment with the key. For example, if two computer science professors are communicating, the word COMPUTER may appear repeatedly in the message. If the key is ORANGE, we may have various alignments:

```
COMPUTER      COMPUTER      COMPUTER
ORANGEOR      RANGEORA      ANGEORAN

COMPUTER      COMPUTER      COMPUTER
NGEORANG      GEORANGE      EORANGEO
```

It is easy to calculate the probability that one of these alignments will be repeated for various numbers of appearances of the word COMPUTER. Of course, if COMPUTER appears seven or more times in the message, a repeated alignment is guaranteed. This results in eight letters of ciphertext being repeated. The distance between the first letters of these repetitions must be a multiple of the keylength. Many other words may be repeated in the same alignment with the keyword, such as common words like THE and AND. Taking all repeats of say, three letters or more, and looking at the distances between them will suggest a keylength of which all of these distances should be multiples. There may be some repetition arising from different words combining with different alignments of the keyword, but this will usually appear as background noise and the true keylength will be clear. This process is known as the Kasiski test.7 (It might be known as the Babbage test, as Charles Babbage discovered it before Kasiski, but, as was typical for Babbage, he didn’t follow through. He never published this particular result.)8 The Kasiski test will be demonstrated shortly, but first another method of determining the keylength is examined.

7 Friedrich W. Kasiski (1805–1881) was a retired Prussian infantry major, who published his method in Die Geheimschriften und die Dechiffrir-kunst in 1863.

8 For a bit more on this see Singh, Simon, The Code Book, Doubleday, New York, 1999, p. 78. For a tremendous amount more see Franksen, Ole Immanuel, Mr. Babbage’s Secret, The Tale of a Cypher and APL, Prentice-Hall, Englewood Cliffs, New Jersey, 1984.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_93_0.png)

Figure 2.8 William Friedman (1891–1969). (Courtesy of National Cryptologic Museum, Fort Meade, Maryland.)

A wonderful attack, published in 1920 by William Friedman (Figure 2.8),² arises from a calculation called the index of coincidence (IC). Simply stated, this is the probability that two randomly chosen letters from a text of length N will be the same.

For both to be A, we take

$P(\text{first letter is A}) \cdot P(\text{second letter is A}) = \frac{F_A}{N} \cdot \frac{F_A - 1}{N - 1}$

where $F_A$ denotes the frequency of A.

Because both letters could have been B, or both letters could have been C, etc., we must sum these probabilities over each letter in the alphabet, which then gives

$\text{IC} = \frac{\sum_{i=A}^{Z} F_i(F_i - 1)}{N(N - 1)}$

The use of multiple substitution alphabets in a cipher flattens the frequency distribution for the letters and therefore decreases the chance of two randomly selected ciphertext letters being the same, as compared to the chance for letters in the original plaintext message. Thus, the value of the index of coincidence can be said to measure the flatness of the frequency distribution or, in other words, estimate the number of alphabets in use.

⁹ Friedman, William F., The Index of Coincidence and Its Applications in Cryptography, Publication No. 22, Riverbank Laboratories, Geneva, Illinois, 1920.

Due to the variation of letter frequencies in normal plaintext, we will not get exactly the same value from the IC every time a keyword of a given length is used; however, the expected value may be calculated for each size keyword. It is provided in the following table. The values depend in part on the length of the text. Separate tables can be constructed for various message lengths. The table below gives values for long messages.

| Number of Alphabets (Keyword Length) | Expected Value for Index of Coincidence |
|---|---|
| 1 | 0.0660 |
| 2 | 0.0520 |
| 3 | 0.0473 |
| 4 | 0.0449 |
| 5 | 0.0435 |
| 6 | 0.0426 |
| 7 | 0.0419 |
| 8 | 0.0414 |
| 9 | 0.0410 |
| 10 | 0.0407 |

As N gets large, we approach a limiting value of approximately 0.0388. This is the value we’d get for purely random text—that is, text where all letters are equally frequent and thus share a probability of 1/26.

Notice that the difference between expected values is largest when the number of alphabets used is small. We can easily distinguish between one alphabet (a monoalphabetic substitution cipher) and two alphabets, but distinguishing between nine and ten alphabets is difficult.

Suppose the index of coincidence is 0.04085, indicating that nine or ten alphabets have been used. We can investigate further by assuming that the correct keylength is 9 and splitting the ciphertext into nine groups of letters, each of which would have been enciphered by the same alphabet, if our assumption is correct. The first group would contain the letters in positions 1, 10, 19, 28,…, because a key of length 9 forces us to start over with the first alphabet at position 10, and again at positions 19, 28, etc. The second group would contain all letters enciphered with the second alphabet, positions 2, 11, 20, 29, etc. Now applying the IC to group one should indicate (by resulting in a value close to 0.066) if those letters truly did arise from encipherment with the same alphabet. If the value of the IC is closer to 0.038, we lose confidence in a keylength of 9. But the first group is not the only one we should consider. The IC value for this group could be a misleading fluke! Testing all nine groups of letters separately gives a much firmer statistical base upon which to decide if a keylength of 9 is correct. If the nine IC values, considered as a group, are

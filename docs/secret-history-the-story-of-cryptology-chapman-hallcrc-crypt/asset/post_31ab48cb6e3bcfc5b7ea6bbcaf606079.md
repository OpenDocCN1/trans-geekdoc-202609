
There are many possible ways to proceed from here. We have a 12-letter word, ZBGUSHMSGZSU, so let’s consider its pattern. It has the form ABCDEFGECAED. At one of the websites referenced earlier, you can type in this pattern and you’ll see that there’s only one word that fits, namely CONSEQUENCES. Substituting for all of the letters now revealed gives

```
THE  N UST     E  UT ON  N  TS CONSEQUENCES H E  EEN
JDS CGWMUJNCQV NSIBVMJC BG QGW CJU ZBGUSHMSGZSU DQIS ASSG Q
  S STE  O  THE HU  N  CE .
WCUQUJSN XBN JDS DMTQG NQZS .
```

The fifth word cannot be anything other than ITS. Placing I above every C quickly leads to more letters and the message is revealed to be:

```
THE INDUSTRIAL REVOLUTION AND ITS CONSEQUENCES HAVE BEEN A
DISASTER FOR THE HUMAN RACE .
```

This is a quote from former mathematician Theodore Kaczynski. The substitutions used to encipher it follow.

A B C D E F G H I J K L M N O P Q R S T U V W X Y Z plaintext
Q A Z W S X E D C R F V T G B Y H N U J M I K O L P ciphertext

Do you see the pattern in the substitutions now that it is entirely revealed?40 Notice that the statistics given in this chapter helped, but they don’t match our message perfectly. T was the second most frequent letter in our table, but it’s tied for fourth place in the sample cipher. Nevertheless, the frequency was high enough to make it seem like a reasonable substitution. In general, we may make some incorrect guesses in trying to break a cipher. When this happens, simply backtrack and try other guesses!

Now that we’ve achieved some skill in breaking MASCs, it’s time to laugh at those who are not so well informed; may they forever wallow in their ignorance! One fellow, whose name has been lost to history, unwittingly displayed his ignorance when he proudly explained how he had deciphered a message of the type we’ve been examining.41

> From the moment when the note fell into my hands, I never stopped studying from time to time the signs which it bore.... About 15 years more or less passed, until the moment when God (Glory to Him!) did me the favor of permitting me to comprehend these signs, although no one taught them to me...

On a more serious note, Chevalier de Rohan’s death was a direct consequence of his inability to decipher such a message.42 The original message was in French and the ciphertext read

```
mg dulhxcc lgu ghj yxuj lm ct ulgc alj
```

## 1.15 Ciphers by a Killer and a Composer

The paragraph above ended on a serious note, but on an even *more* serious note, there have been instances of serial killers using ciphers. In some cases, the purpose was to hide incriminating evidence such as details of murders recorded in a journal (e.g. Unabomber and Joseph Edward Duncan), and sometimes simply to taunt the police and the public (e.g. Zodiac, Scorpion, and B.T.K.). Some such ciphers are still unsolved and the killers themselves not yet identified.

The first set of three ciphers that the Zodiac killer sent out were made available to the National Security Agency (NSA), Central Intelligence Agency (CIA), and Federal Bureau of Investigation (FBI), but it was a pair of amateurs that broke them. Donald Harden, a high school history and economics teacher, began working on the ciphers and was later joined by his wife, Bettye Harden, who had no previous experience with cryptology. Nevertheless, she came up with the idea of a probable word search and together they recovered the messages. It took the pair 20 hours. Complications included the presence of five errors. Part one of this cipher is shown in Figure 1.18. How can you tell that it is more complicated than a MASC?

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_57_0.png)

Figure 1.18 A Zodiac killer cipher.

The decipherment for this portion is:

I like killing people because it is so much fun it is more fun than killing wild game in the forest because man is the most dangerous animal of all to kill something gi

I ended up having a lot to say about another cipher created by the Zodiac killer. It’s reproduced in Figure 1.19, but I won’t be giving any spoilers here. If you wish to learn more, I encourage you to pursue the references at the end of this chapter.

It seems like a good time to lighten things up again. “Pomp and Circumstance,” played at virtually every graduation ceremony, was composed by Edward Elgar (Figure 1.20). Although this is certainly his best known composition, he also composed a cipher message in 1897 that no one has been able to break. It’s shown in Figure 1.21.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_58_0.png)

Figure 1.19 Another Zodiac Killer Cipher.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_58_1.png)

Figure 1.20 Edward Elgar (https://en.wikipedia.org/wiki/Edward_Elgar).

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_59_0.png)

**Figure 1.21**  An open problem—what does this say? ([https://en.wikipedia.org/wiki/File:Dorabella-cipher-image.gif](https://en.wikipedia.org/wiki/File:Dorabella-cipher-image.gif)).

## 1.16 Affine Ciphers

When we introduced the mixed alphabets, the mathematical view of encrypting (via modular arithmetic) seemed to disappear! It appeared again on the other side, cryptanalysis, where we’ve been using some simple statistics. Returning to Caesar’s cipher, we can generalize to bring the mathematical perspective back to enciphering again. Caesar used $C=M+3\pmod{26}$. We made the key arbitrary, giving $C=M+K\pmod{26}$. But why not generalize further? We do this by introducing a multiplier, $a$.

Consider $C=aM+b\pmod{26}$. Here our key is $K=(a,b)$, an ordered pair. Using $K=(0,b)$ is not allowed, because every letter would get sent to $b$ and the message would be impossible to decipher—only its length would be known. $K=(1,3)$ gives a Caesar shift. What about other values? We only get a 1:1 map between plaintext and ciphertext letters when the greatest common divisor of $a$ and 26 is 1. That is, $a$ and 26 must be relatively prime (also called *coprime*).

The various values of $a$ may be investigated individually. All odd values between 1 and 25 inclusive work, with the exception of 13. Euler’s totient function, $\varphi(n)$ gives the number of positive integers less than $n$ and relatively prime to $n$. So we may write $\varphi(26)=12$. This function is very useful in public key cryptography, as will be seen in [Section 14.3](#). Now, $b$ can take any value in the range 0 to 25, so the keyspace for this cipher is $(12)(26)=312$. Decipherment is done via the equation $M=a^{-1}(C-b)$, where $a^{-1}$ is the multiplicative inverse of $a$, that is, the number that gives 1 when multiplied by $a\pmod{26}$.

The keyspace for an affine cipher is too small to serve as protection against a brute force attack. Although we are using some mathematics here, the set of possible keys is just a tiny subset of that for the general MASC. Recall that the keyspace for this is $26!=403,291,461,126,605,635,584,000,000$. A mod 26 multiplication table ([Table 1.5](#)) is provided for your convenience in using an affine cipher.

Let’s encipher a short message using the key $(11, 8)$ to get the hang of this system:

```
HOW ARE YOU? I’M AFFINE.
```

We convert the message to numbers (ignoring punctuation) to get:

```
7, 14, 22, 0, 17, 4, 24, 14, 20, 8, 12, 0, 5, 5, 8, 13, 4
```

### Table 1.5 Mod 26 Multiplication Table

| |25|24|23|22|21|20|19|18|17|16|15|14|13|12|11|10|9|8|7|6|5|4|3|2|1|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|1|25|24|23|22|21|20|19|18|17|16|15|14|13|12|11|10|9|8|7|6|5|4|3|2|1|
|2|24|22|20|18|16|14|12|10|8|6|4|2|0|24|22|20|18|16|14|12|10|8|6|4|2|
|3|23|20|17|14|11|8|5|2|25|22|19|16|13|10|7|4|1|24|21|18|15|12|9|6|3|
|4|22|18|14|10|6|2|24|20|16|12|8|4|0|22|18|14|10|6|2|24|20|16|12|8|4|
|5|21|16|11|6|1|22|17|12|7|2|23|18|13|8|3|24|19|14|9|4|25|20|15|10|5|
|6|20|14|8|2|22|16|10|4|24|18|12|6|0|20|14|8|2|22|16|10|4|24|18|12|6|
|7|19|12|5|24|17|10|3|22|15|8|1|20|13|6|25|18|11|4|23|16|9|2|21|14|7|
|8|18|10|2|20|12|4|22|14|6|24|16|8|0|18|10|2|20|12|4|22|14|6|24|16|8|
|9|17|8|25|16|7|24|15|6|23|14|5|22|13|4|21|12|3|20|11|2|19|10|1|18|9|
|10|16|6|22|12|2|18|8|24|14|4|20|10|0|16|6|22|12|2|18|8|24|14|4|20|10|
|11|15|4|19|8|23|12|1|16|5|20|9|24|13|2|17|6|21|10|25|14|3|18|7|22|11|
|12|14|2|16|4|18|6|20|8|22|10|24|12|0|14|2|16|4|18|6|20|8|22|10|24|12|
|13|13|0|13|0|13|0|13|0|13|0|13|0|13|0|13|0|13|0|13|0|13|0|13|0|13|
|14|12|24|10|22|8|20|6|18|4|16|2|14|0|12|24|10|22|8|20|6|18|4|16|2|14|
|15|11|22|7|18|3|14|25|10|21|6|17|2|13|24|9|20|5|16|1|12|23|8|19|4|15|
|16|10|20|4|14|24|8|18|2|12|22|6|16|0|10|20|4|14|24|8|18|2|12|22|6|16|
|17|9|18|1|10|19|2|11|20|3|12|21|4|13|22|5|14|23|6|15|24|7|16|25|8|17|
|18|8|16|24|6|14|22|4|12|20|2|10|18|0|8|16|24|6|14|22|4|12|20|2|10|18|
|19|7|14|21|2|9|16|23|4|11|18|25|6|13|20|1|8|15|22|3|10|17|24|5|12|19|
|20|6|12|18|24|4|10|16|22|2|8|14|20|0|6|12|18|24|4|10|16|22|2|8|14|20|
|21|5|10|15|20|25|4|9|14|19|24|3|8|13|18|23|2|7|12|17|22|1|6|11|16|21|
|22|4|8|12|16|20|24|2|6|10|14|18|22|0|4|8|12|16|20|24|2|6|10|14|18|22|
|23|3|6|9|12|15|18|21|24|1|4|7|10|13|16|19|22|25|2|5|8|11|14|17|20|23|
|24|2|4|6|8|10|12|14|16|18|20|22|24|0|2|4|6|8|10|12|14|16|18|20|22|24|
|25|1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|16|17|18|19|20|21|22|23|24|25|

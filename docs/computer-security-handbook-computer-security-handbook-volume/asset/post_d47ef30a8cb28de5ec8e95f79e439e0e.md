
![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_228_0.png)

## EXHIBIT 7.3 Scytale in Use
Source: Copyright © 2008 M. E. Kabay. Used with permission.

to be broken into up to six rows of eight letters to be written across the rolled-up strip, in this way:

- athenian
- troopswi
- thinoned
- aysmarch
- ofromebe
- readynow

The message might appear on the scytale as shown schematically in Exhibit 7.3. Reading the unwrapped strip without the stick would produce this ciphertext (shown in uppercase):

```
ATTAORTRHYFEHOISREEONMODNPOAMYISNRENAWECBONIDHEW
```

“The first attested use of [a substitution cipher] in military affairs comes from the Romans.”10 During that time, Julius Caesar encoded all his messages by simply replacing every letter with the letter three positions away. For example, the letter a would become the letter d, the letter b would become the letter e, and so on. Now called the Caesar cipher, this scheme is best-known of all the monoalphabetic algorithms (see Section 7.2.5).11 Consider the Caesar cipher illustrated in the next comparison using the modern English alphabet, with the letters of the alphabet simply shifted three places.

```
Plaintext: abcdefghijklmnopqrstuvwxyz
Ciphertext: DEFGHIJKLMNOPQRSTUVWXYZABC
```

To encrypt a message, the sender finds each letter of the message in the plaintext alphabet and uses the letter below it in the ciphertext alphabet. Thus, the clear message:

```
Plaintext: beware the ides of march
```

is transformed into the encrypted message:

```
Ciphertext: EHZDUH WKH LGHV RI PDUFK
```

Byzantine Emperor.13 In 1492, a man known as al-Kalka-shandi described this technique in an encyclopedia. He also described several cryptographic techniques, including substitution and transposition ciphers.14

Returning to the Caesar cipher, consider how this code could be broken using the science of cryptanalysis. When examined for a length of time, this particular code is fairly transparent. As soon as several letters are identified correctly, the rest fall into place. For example, because “the” is the most common three-letter word in the English language, testing “XLI” against “the” reveals that each letter of plaintext has a fixed relationship to the ciphertext: a shift of three to the right.

If that difference is applied to the rest of the message, the result is a piece of plaintext that is intelligible and thus assumed to be the correct solution to the problem. However, even in this simple example several sophisticated processes and assumptions are at work; they deserve closer attention before looking at more complex codes. First, the test of “the” against “XLI” assumes that the plaintext is English and that the attacker has some detailed knowledge of that language, such as the frequency of certain words. Second, it is assumed that the ciphertext follows the plaintext in terms of word breaks. Typically, this is not the case. Ciphertext usually is written in blocks of letters of equal length to further disguise it, as in:

```
Ciphertext: EHZDU HWKHL GHVRI PDUFK
```

When the recipient of the message decrypts it, the result, while not exactly easy reading, is nevertheless entirely intelligible:

```
Plaintext: bewar ethei desof march
```

Also note the convention of ignoring the case of individual letters and placing all plaintext in lowercase while all ciphertext is in capitals.

## 7.2.4 Brute Force Cryptanalysis.

The next thing to note about the Caesar cipher is that, using the English alphabet, there are 26 possible keys. This means that someone intercepting the encrypted message could mount a standard form of attack known as brute force cryptanalysis. This method runs possible keys through the decryption algorithm until a solution is discovered. Statistically speaking, the correct key is reached after testing only half of all possible keys. In Exhibit 7.5, a spreadsheet table details a brute force attack on the Caesar ciphertext. In the example, the plaintext appears in line 6, Key #3.

Note that three items of information are required for this attack, and all three of them are relevant to encryption on personal computers:

- 1. A knowledge of the encryption algorithm used
- 2. The number of possible keys
- 3. The language of the plaintext

Using a computer in an office is somewhat different from sending messages on the field of battle (at least on a good day). Unlike an enemy spy, someone who is attempting to gain unauthorized access to data already has a fairly good idea of which algorithm is being used. (There are relatively few in use, and they often are directly associated with particular applications). This takes care of the first item. The primary obstacle to a brute force attack is the second item, number of keys. In the case of the Caesar

Functionally, brute force attacks depend on knowing which encryption algorithm is behind the ciphertext. Practically, they depend on the feasibility of successes within an appropriate time frame. They also depend on the third item of information in the list above: knowledge of the language of the plaintext. The solution to the Caesar cipher in Exhibit 7.5 tends to jump out because it is closer to plain English than any of the other solutions. However, without knowing what constitutes plaintext, a brute force attack will, at best, be inefficient, and, at worst, unsuccessful. This part of cryptanalysis, recognizing a positive result, is less amenable to automation than any other. The difficulty is compounded by encryption of purely numerical results where the correct cleartext can be impossible to determine without extensive additional knowledge.

## 7.2.5 Monoalphabetic Substitution Ciphers.

Both the Caesar cipher and the random substitution cipher shown are examples of monoalphabetic ciphers. This means that one letter of ciphertext stands for one letter of plaintext. This renders such codes susceptible to an attack quite different from brute force. Suppose a customs officer attempts to discover when and how an illegal weapons shipment will be entering the country. The following message is intercepted:

```
YZYGJ KZORZ OYXZR RKZRK XUXRJ XRZXU YKQQQ
```

The person who encoded this text clearly substituted new letters for the original letters of the message. To the experienced code breaker or cryptanalyst, the task of deciphering this message is quite a simple one. First count how many times each letter occurs in the text. This produces a list like this:

```
Ciphertext: R Z X Y K J U O G
Frequency: 6 6 5 4 4 2 2 2 1
```

Note that the last three letters are discounted as they are merely filling out the five-letter grouping. Next refer to a table of frequencies, which shows the relative frequency with which the letters of the alphabet occur in a specific language or dialect of that language. One such list is shown in Exhibit 7.6. This list was created for this example and proposes that the most commonly used letters in English in descending order of frequency are e, t, r, and so on. The actual order is more likely to be e, t, a, i, o, n, s, h, r, d, l, u, the order of keys on the English Linotype machine from the nineteenth century, although the precise order of frequencies can vary according to the region of origin or subject matter of the text.

Assuming that the original message is in English, a list that matches code letters to plaintext letters is easily derived.

```
Ciphertext: R Z X Y K J U O G
Frequency: 6 6 5 4 4 2 2 2 1
Plaintext: e t r i n o a h s
```

The result is:

```
Ciphertext: YZYGJ KZORZ OYXZR RKZRK XUXRJ XRZXU YKQQQ
Plaintext: itiso nthet hirte enten rareo retra inqqq
```

This is readable as "it is on the thirteen ten rare ore train." Although this example obviously was contrived to make a point, it clearly illustrates an important cryptographic

## Exhibit 7.6 Frequency Lists for English

| | English by Letter | | | English by Frequency | | | |
|---|---|---|---|---|---|---|---|
| A | 7.25 | N | 7.75 | E | 12.75 | U | 3.00 |
| B | 1.25 | O | 7.50 | T | 9.25 | R | 8.50 |
| C | 3.50 | P | 2.75 | I | 7.75 | N | 7.75 |
| D | 4.25 | Q | 0.50 | I | 7.75 | N | 7.75 |
| E | 12.75 | R | 8.50 | I | 7.75 | N | 7.75 |
| F | 3.00 | S | 6.00 | O | 7.50 | A | 7.25 |
| G | 2.00 | T | 9.25 | A | 7.25 | S | 6.00 |
| H | 3.50 | U | 3.00 | S | 6.00 | D | 4.25 |
| I | 7.75 | V | 1.50 | D | 4.25 | L | 3.75 |
| J | 0.25 | W | 1.50 | L | 3.75 | C | 3.50 |
| K | 0.50 | X | 0.50 | C | 3.50 | H | 3.50 |
| L | 3.75 | Y | 2.25 | H | 3.50 | F | 3.00 |
| M | 2.75 | Z | 0.25 | F | 3.00 | M | 2.75 |

tool that can quickly decipher something that at first seems to be very forbidding. The encryption in the previous example could have been based on a simple substitution cipher. For example, after using the password “TRICK” followed by the regular alphabet minus the letters in the password for the plaintext, the ciphertext is the alphabet written backward:

```
Plaintext:  TRICKABDEFGHJLMNOPQSUVWXYZ
Ciphertext: ZYXWVUTSRQPONMLKJIHGFEDCBA
```

Frequency analysis also works if the substitution is entirely random, as in the example shown earlier, the key for which is entirely random. The specialized tools, such as frequency tables, that are required to break codes point out a basic trade-off: If a basic level of protection is needed, it is easy to get but also easy to break, at least for an expert. The qualification “for an expert” is important because users of encryption need to keep its role in perspective. The salient questions are: Who can gain from decrypting the data, and what means do they have at their disposal? There is no point investing in powerful encryption hardware or software if those likely to attempt to read your files are not particularly sophisticated, dedicated, or well equipped. For example, a person who mails a postcard knows it can be read by anyone who sees it. Envelopes can be used to prevent this, hardly the ultimate in confidentiality, but widely used and relatively successful nonetheless.

## 7.2.6 Polyalphabetical Substitution Ciphers.

Even when the plaintext uses a wider range of letters than the contrived example, substitution ciphers can be cracked by frequency analysis. A powerful technique is to concentrate on the frequency of two-letter combinations, which are known as digraphs, the most common of which in English is “TH.” One way to counter frequency analysis is to use multiple substitutes for the more frequent letters. This cannot be done with a straightforward alphabetic coding. However, if using numbers for letters, it is possible to assign multiple numbers to some letters, such as 13 17 19 23 for E, which would help dilute the natural frequency of this letter. It would appear that supplying multiple substitutions, known as homophones, in proportion to the frequency of each letter would effectively

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

# 7.2.4 Brute Force Cryptanalysis.

The next thing to note about the Caesar cipher is that, using the English alphabet, there are 26 possible keys. This means that someone intercepting the encrypted message could mount a standard form of attack known as brute force cryptanalysis. This method runs possible keys through the decryption algorithm until a solution is discovered. Statistically speaking, the correct key is reached after testing only half of all possible keys. In Exhibit 7.5, a spreadsheet table details a brute force attack on the Caesar ciphertext. In the example, the plaintext appears in line 6, Key #3.

Note that three items of information are required for this attack, and all three of them are relevant to encryption on personal computers:

+   1. A knowledge of the encryption algorithm used
+   2. The number of possible keys
+   3. The language of the plaintext

Using a computer in an office is somewhat different from sending messages on the field of battle (at least on a good day). Unlike an enemy spy, someone who is attempting to gain unauthorized access to data already has a fairly good idea of which algorithm is being used. (There are relatively few in use, and they often are directly associated with particular applications). This takes care of the first item. The primary obstacle to a brute force attack is the second item, number of keys. In the case of the Caesar
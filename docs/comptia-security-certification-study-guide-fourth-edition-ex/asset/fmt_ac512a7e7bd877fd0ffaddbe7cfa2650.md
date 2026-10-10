
## 2. Start the CrypTool program and click Close if a startup tip displays.

## 3. Choose File | Close to close the sample document that appears.

## 4. To create a new document, choose File | New.

## 5. Type the following text into the new document:

![Images](p0515-01.jpg)

## 6. Choose Crypt/Decrypt | Symmetric (classic) | Caesar/Rot-13.

## 7. The Key Entry dialog box appears. This is where you can specify how many characters to increment with the substitution cipher. Choose Number Value and then type `3`. Notice that the sample in the dialog box shows what the new values of every letter in the alphabet will become.

## 8. Click Encrypt. You should see that your message was encrypted.

## 9. To decrypt the information, choose Crypt/Decrypt | Symmetric (classic) | Caesar/Rot-13.

## 10. Choose Number Value and type `3`.

## 11. Click Decrypt and notice that the original text is back.

## 12. Close CrypTool.

### Repeating Key

Most keys you input into software to do the encryption are words or phrases rather than simple numbers, so let’s look at an example of a mathematical operation involving a word as the key.

For this example, let’s assume that the key is “bad.” When a message is encrypted, the key is repeated for the duration of the message. The algorithm in this example will do the following:

1. Convert the characters in the message to a number based on the position in the alphabet.
2. Convert the characters in the key to a number based on its position in the alphabet.
3. Add the two numbers together to get a new value.
4. Convert the new value to its corresponding letter in the alphabet (for example, 3 becomes `C`).

Let’s walk through an example of this encryption process, using the message “com security.” We remove the space and write the message. Then we repeat the key of “bad” for the duration of the message:

![Images](p0516-01.jpg)

We then convert the message and key to numeric values (based on the values shown in [Figure 12-3](#ch12.xhtml#ch12fig3)) that represent the place in the alphabet where each character resides.

![Image](t0516-01.jpg)

**FIGURE 12-3**  

A conversion table

For example, `A` becomes 1, `B` becomes 2, and so on, as follows (I put in spaces to separate the numbers to help you visualize the process):

![Images](p0516-02.jpg)

Once the characters have been converted to their numbers, we can add the message numbers to their corresponding key numbers. After the numbers have been added together, we convert the new numbers to characters to create the cipher text of the message:

![Images](p0517-01.jpg)

As a final result, the text “com security” is encrypted to become “epq ufgwsmvz.” Again, this is an oversimplified example of how an algorithm is used with a key, but it demonstrates how the key is repeated for the duration of the message.

To decrypt the message, you perform the reverse: take the cipher text and convert it to numeric values. Then subtract the values associated with the key from the cipher values to come up with the plain text values. Finally, convert the plain text values back to their associated characters.

### Vigenère Cipher

Another common cipher used many years ago was the Vigenère cipher. This type of cipher involves creating a Vigenère table to determine which cipher character to substitute for the plain text character when a key is used. [Figure 12-4](#ch12.xhtml#ch12fig4) shows an example of a Vigenère table.

![Image](f0517-01.jpg)

**FIGURE 12-4**  

Using a Vigenère table to encrypt a message

When encrypting information using the Vigenère cipher, you write your message and then repeat the key below the message for the duration of the message, just as in the previous example:

![Images](p0518-01.jpg)

To encrypt the message, you work with one character at a time. For example, to encrypt the letter `h` in the message, locate the `h` row in the Vigenère table and intersect it with the column that represents the character in the key (the `b` column in this example). The intersecting value becomes your cipher character, which is `i` in this case.

The following is the resulting cipher text using the Vigenère table:

![Images](p0518-02.jpg)

Note that using a short key such as “bad” is not a good practice, as it is easier to crack than a longer key. I use a short key in these examples just so the key can repeat for the duration of the message.

### Other Cryptography Terms

Several other cryptography concepts are important to understand for the Security+ certification exam. The following sections introduce these cryptography terms and concepts.

#### Key Strength/Key Length

`Key strength`, also known as `key space` or `key length`, refers to how many bits are in the encryption key. The larger the key space, the better the encryption. This is because a larger key space has more possible values that need to be calculated if someone is trying to crack the key. For example, a 2-bit key space allows for only four values: 00, 01, 10, and 11. It would take no time at all to calculate all possible keys a 2-bit key could have. If you increase the key space and go to 3 bits, then there are eight possible values: 000, 001, 010, 011, 100, 101, 110, and 111.

Common key spaces today are 64-bit, 128-bit, 256-bit, and sometimes 512-bit.

#### Work Factor

The term `work factor` refers to a value indicating the time it would take to break the encryption. The work factor is normally measured in time, and it is usually a higher value with a larger key space.

For example, to crack a 64-bit key would take less time than cracking a 128-bit key, so the work factor is lower to crack a 64-bit key.

#### One-Time Pads

A `one-time pad (OTP)` is a very secure method of encrypting information that involves using a key only once. The key is a randomly generated value that is used to encrypt the data and then never used again.

The benefit of using different keys is that hackers are cracking encryption based on working with different pieces of data that have been encrypted with the same key in order to reverse-engineer the process and crack the key.

#### Cipher Suites

The different types of cipher suites are stream ciphers and block ciphers. `Stream cipher` algorithms encrypt data one bit at a time. Plain text bits are converted into encrypted cipher text. This method is usually not as secure as block cipher techniques, discussed next, but it generally executes faster. In addition, the cipher text is always the same size as the original plain text and is less prone to errors. If an error occurs during the encryption process, usually this affects only a single bit instead of the whole string. In contrast, when block ciphers contain errors, the entire block becomes unintelligible. The plain text bits are typically encrypted with the bits of a key by using an exclusive OR (XOR) function (described shortly).

Instead of encrypting a bit at a time, `block cipher` algorithms encrypt data in blocks. Block ciphers have more overhead than stream ciphers. This overhead is provided separately, depending on the implementation and the block size that can be modified (the most common size is 64 bits). Because a block cipher handles encryption at a higher level, it is generally more secure. The downside is that the execution takes longer.

#### Modes of Operation

Block ciphers are offered in different modes, such as Electronic Code Book (ECB), Cipher Block Chaining (CBC), Counter mode, and Output Feedback (OFB). [Table 12-1](#ch12.xhtml#ch12tab1) lists some of the block cipher modes currently available.

**TABLE 12-1**  

Block Cipher Modes

![Image](t0520-01.jpg)

#### Authenticated vs. Unauthenticated

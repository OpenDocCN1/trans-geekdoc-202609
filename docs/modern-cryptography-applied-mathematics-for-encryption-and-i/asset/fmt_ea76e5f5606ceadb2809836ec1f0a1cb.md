
4. Repeat this, except this time use the next letter of the keyword, `a`. Locate the second letter of the plain text `t` in the top row.

5. Move down that column until you find an `a`, and then we select the letter on the far left of that row, which would be `h`.

6. When you reach the last letter of the keyword, you start over at the first letter of the keyword, so that

![Images](Images/image00496.jpeg)

becomes

![Images](Images/image00497.jpeg)

##### Devices

In modern times, devices are almost always used with cryptography. For example, computers are used to encrypt e-mail, web traffic, and so on. In ancient times, there were also ciphers based on the use of specific devices to encrypt and decrypt messages.

###### Scytale Cipher

The `Scytale cipher` is one such ancient cipher. Often mispronounced (it actually rhymes with “Italy”), this cipher used a cylinder with a strip of parchment wrapped around it. If you had the correct diameter cylinder, then when the parchment was wrapped around it, the message could be read. You can see the concept shown in [Figure 1-2](#part0009.xhtml#ch01fig02).

![Images](Images/image00498.jpeg)

* * *

**FIGURE 1-2    Scytale**

If you did not have the correct size of cylinder, however, or if you simply found the parchment and no cylinder, the message would appear to be a random string of letters. This method was first used by the Spartans and later throughout Greece. The earliest mention of Scytale was by the Greek poet Archilochus in the seventh century B.C.E. However, the first mention of how it actually worked was by Plutarch in the first century B.C.E., in his work *Parallel Lives*:

              The dispatch-scroll is of the following character. When the ephors send out an admiral or a general, they make two round pieces of wood exactly alike in length and thickness, so that each corresponds to the other in its dimensions, and keep one themselves, while they give the other to their envoy. These pieces of wood they call “scytalae.” Whenever, then, they wish to send some secret and important message, they make a scroll of parchment long and narrow, like a leathern strap, and wind it round their “scytale,” leaving no vacant space thereon, but covering its surface all round with the parchment. After doing this, they write what they wish on the parchment, just as it lies wrapped about the “scytale”; and when they have written their message, they take the parchment off, and send it, without the piece of wood, to the commander. He, when he has received it, cannot other get any meaning of it—since the letters have no connection, but are disarranged—unless he takes his own “scytale” and winds the strip of parchment about it, so that, when its spiral course is restored perfectly, and that which follows is joined to that which precedes, he reads around the staff, and so discovers the continuity of the message. And the parchment, like the staff, is called “scytale,” as the thing measured bears the name of the measure.^([9](#part0009.xhtml#ch01note9a))

###### Alberti Cipher Disk

The Alberti `cipher disk`, created by Leon Battista Alberti, is an example of a multi-alphabet substitution. Alberti wrote about this cipher in 1467 in his book *De Cifris*. It is said to be the first multi-alphabet cipher. It consists of two disks attached in the center with a common pin. Each disk had 24 equal cells. The larger, outer disk, called the `stabilis`, displayed an uppercase Latin alphabet used for the plain text. The smaller, inner disk, called the `mobilis`, displayed a lowercase alphabet for the cipher text.

To encrypt a message, a letter on the inner disk was lined up with a letter on the outer disk as a key. If you knew what letter to line up with, you would know which key to use. This has the effect of offering multiple substitution alphabets. You can see an example of the cipher disk, with the English alphabet, in [Figure 1-3](#part0009.xhtml#ch01fig03).

![Images](Images/image00499.jpeg)

* * *

**FIGURE 1-3    Cipher disk**

In Alberti’s original cipher disk, he used the Latin alphabet. So the outer disk had the Latin alphabet minus a few English letters, as well as numbers 1 through 4 for use with a codebook that had phrases and words assigned four-digit values.

###### The Jefferson Disk

The `Jefferson disk`, which was called a “wheel cipher” by its inventor, Thomas Jefferson, is a rather complex device, at least for its time. Invented in 1795, the disk is a set of wheels or disks, each displaying the 26 letters of the English alphabet. The disks are all on a central axle and can be rotated about the axle. The order of the disks is the key, and both sender and receiver had to order their disks according to the key. An example of the Jefferson disk is shown in [Figure 1-4](#part0009.xhtml#ch01fig04).

![Images](Images/image00500.jpeg)

* * *

**FIGURE 1-4    Jefferson disk**

When using the Jefferson disk, the sender would rotate the letters on the disks until the message was spelled out in a single row. The sender would then copy down any row of text on the disks other than the one that contained the plain text message. That enciphered message would then be sent to the recipient. The recipient then arranged the disk letters according to the predefined order and then rotated the disk until the message was displayed.

**Note**

This device was independently invented by Étienne Bazeries (1846–1931), a French cryptographer, although Jefferson improved on the disk in his version. Bazeries was known for being a very skilled cryptographer and cryptanalyst. After he broke several transposition systems used by the French military, the French government hired him to work for the Ministry of Foreign Affairs. During World War I, he worked on breaking German ciphers.

Stories such as this are not uncommon in cryptography. Two different parties may independently invent the same or remarkably similar ciphers. This often occurs from time to time in modern times, when at least some work in cryptography is classified by various governments. You will see other examples of this in later chapters on modern ciphers.

##### Book Ciphers

*Book ciphers* have probably been around for as long as books have been available. Essentially, the sender and receiver agree to use a particular book as its basis. The simplest implementation is to send coordinates for words. So, for example, `3 3 10` means “go to page 3, line 3, tenth word.” In this way, the sender can specify words with coordinates and write out entire sentences. There are numerous variations of this cipher. For example you could combine book ciphers with Vigenère and use the book coordinates to denote the keyword for Vigenère.

* * *

**Beale Ciphers**

In 1885, a pamphlet was published describing treasure buried in the 1820s by one Thomas J. Beale in Virginia. The `Beale ciphers` are three cipher texts that allegedly give the location, contents, and names of the owners of the buried treasure. The first Beale cipher, which has not been solved, provides the location. The second cipher provides details of the contents of the treasure and has been solved. The second cipher was a book cipher that used the US Declaration of Independence as the book. Each number in the cipher represents a word in the document. They are presented here simply as an example of a book cipher.

* * *

#### Transposition Ciphers

So far, we have looked at ciphers in which some sort of substitution is performed. However, this is not the only way to encrypt a message. It is also possible to transpose parts of a message. Transposition ciphers provide yet another avenue for encryption.

##### Reverse Order

The simplest implementation of a transposition cipher is to reverse the plain text. In this way

![Images](Images/image00501.jpeg)

becomes

![Images](Images/image00502.jpeg)

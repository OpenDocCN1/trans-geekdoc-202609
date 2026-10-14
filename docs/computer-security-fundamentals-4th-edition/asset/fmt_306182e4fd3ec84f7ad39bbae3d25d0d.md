
0111100001 0110100011 0111100111 0111100111 0011100001 0011100001 0011100011

If you convert that to text, you would get:

xZ7![Question mark symbol.](Images/233in01.jpg)![Question mark symbol.](Images/233in01.jpg)#

All this is transparent to the end user, who doesn’t even know that salting is happening or what it is. However, an attacker using a rainbow table to get passwords would get the wrong password.

### Steganography

*Steganography* is the art and science of writing hidden messages in such a way that no one, apart from the sender and intended recipient, suspects the existence of the message. It is a form of security through obscurity. Often the message is hidden in some other file, such as a digital picture or an audio file, to defy detection.

The advantage of steganography over cryptography alone is that messages do not attract attention to themselves. If someone is aware that a message is even there, she won’t try to decipher it. In many cases, messages are encrypted and hidden via steganography.

The most common implementation of steganography utilizes the least significant bits in a file in order to store data. By altering the least significant bit, you can hide additional data without altering the original file in any noticeable way.

There are some basic steganography terms you should know:

*   *Payload* is the data to be covertly communicated. In other words, it is the message you wish to hide.

*   The *carrier* is the signal, stream, or data file into which the payload is hidden.

*   The *channel* is the medium used. This may be still photos, video, or sound files.

The most common way steganography is accomplished today is via least significant bits. Every file has a certain number of bits per unit of the file. For example, an image file in Windows is 24 bits per pixel. If you change the least significant of those bits, then the change is not noticeable with the naked eye. And you can hide information in the least significant bits of an image file. With least significant bit (lsb) replacement, certain bits in the carrier file are replaced.

#### Historical Steganography

In modern times, steganography involves digital manipulation of files to hide messages. However, the concept of hiding messages is not new. There have been many methods used throughout history.

*   The ancient Chinese wrapped notes in wax and swallowed them for transport. This was a crude but effective method of hiding messages.

*   In ancient Greece, a messenger’s head would be shaved, a message was written on his head, and then his hair was allowed to grow back. Obviously, this method required some time.

*   In 1518 Johannes Trithemius wrote a book on cryptography and described a technique in which a message was hidden by having each letter taken as a word from a specific column.

*   During World War II the French Resistance sent messages written on the backs of couriers using invisible ink.

*   Microdots are images/undeveloped film the size of a typewriter period that are embedded in innocuous documents. These were said to be used by spies during the Cold War.

*   Also during the Cold War, the U.S. Central Intelligence Agency used various devices to hide messages. For example, they developed a tobacco pipe that had a small space to hide microfilm but could still be smoked.

In more recent times, but before the advent of computers, other methods were used to hide messages.

#### Steganography Methods and Tools

There are a number of tools available for implementing steganography. Many are free or at least have free trial versions. A few of these tools are listed here:

*   `QuickStego`: Easy to use but very limited

*   `Invisible Secrets`: Much more robust, with both a free version and a commercial version available

*   `MP3Stego`: Specifically for hiding payload in MP3 files

*   `Stealth Files 4`: Works with sound files, video files, and image files

*   `Snow`: Hides data in whitespace

*   `StegVideo`: Hides data in a video sequence

*   `Invisible Secrets`: A very versatile steganography tool that has several options

### Cryptanalysis

Cryptanalysis is a daunting task. It essentially involves searching for some means to break through encryption of some sort. And, unlike what you see in the movies, it is a very time-consuming task that frequently leads to only partial success. Cryptanalysis involves using any method to decrypt the message that is more efficient than simple brute-force attempts. (Remember that brute forcing means simply trying every possible key.)

A cryptanalysis success is not necessarily breaking the target cipher. In fact, finding any information about the target cipher or key is considered a success. There are several types of cryptographic success:

*   **Total break:** The attacker deduces the secret key.

*   **Global deduction:** The attacker discovers a functionally equivalent algorithm for encryption and decryption but without learning the key.

*   **Instance (local) deduction:** The attacker discovers additional plain texts (or cipher texts) not previously known.

*   **Information deduction:** The attacker gains some Shannon information about plain texts (or cipher texts) not previously known.

*   **Distinguishing algorithm:** The attacker can distinguish the cipher from a random permutation.

Entire books have been written on cryptanalysis. The purpose of this section is just to give you some basic concepts from the field so that you have a basic understanding. There are certainly other methods not discussed in this section.

##### Known Plain Text Attack

The known plain text attack method is based on having a sample of known plain texts and their resulting cipher texts and then using this information to try to ascertain something about the key used. It is easier to obtain known plain text samples than you might think. Consider email. Many people, myself included, use a standard signature block. If you have ever received an email from me, you know what my signature block is. Then if you intercept encrypted emails I send, you can compare the known signature block to the end of the encrypted email. You would then have a known plain text and the matching cipher text to work with. Success with this method requires many thousands of known plain text samples.

##### Chosen Plain Text Attack

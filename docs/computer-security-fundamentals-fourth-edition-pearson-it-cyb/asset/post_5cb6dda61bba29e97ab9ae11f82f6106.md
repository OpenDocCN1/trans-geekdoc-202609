...[/content].

Let's construct final content.

We'll start with the digital signature paragraph (no heading). Then image line. Then Figure caption. Then "## Hashing". Then paragraph. Then "## MD5". Then paragraph. Then "## SHA". Then combined paragraph (including SHA-1, SHA-256, rainbow table). Then steganography terms list (payload, carrier, channel). Then paragraph about steganography (the long paragraph). Then list of historical methods (converted). Then paragraph about modern times (maybe keep as separate paragraph). Then heading "## Steganography Methods and Tools". Then paragraph about tools. Then list of tools. Then heading "## Cryptanalysis". Then paragraph about cryptanalysis. Then list of cryptographic success items.

Now ensure that there are blank lines between paragraphs. Also ensure that list items are separated by line breaks.

Now check for any OCR errors that need correction beyond headings and list markers.

Potential issues:

- In the steganography terms list, there is a stray "+   -" before "The ancient Chinese...". That's two hyphens. We'll convert to "-". Also there may be extra spaces.

- In the list of tools, there is duplicate "Invisible Secrets". That's okay.

- In the paragraph about steganography terms, there is "The most common way steganography is accomplished today is via least significant bits." That's fine.

- In the paragraph about steganography, there is "Every file has a certain number of bits per unit of the file. For example, an image file in Windows is 24 bits per pixel." That's fine.

- In the paragraph about steganography, "If you change the least significant of those bits, then the change is not noticeable with the naked eye." fine.

- In the paragraph about steganography, "And you can hide information in the least significant bits of an image file." fine.

- In the paragraph about steganography, "With least significant bit (lsb) replacement, certain bits in the carrier file are replaced." fine.

Now check for any other OCR errors:

- In the paragraph about hashing: "Third, there are no collisions." Might be okay.

- In the paragraph about hashing: "Second, you get a fixed-length output no matter what input is given." fine.

- In the paragraph about hashing: "First and foremost, it is one way." maybe "one-way" but okay.

- In the paragraph about hashing: "Ideally we would like to have no collisions." fine.

- In the paragraph about hashing: "But the reality is that with fixed-length output, collisions are possible." fine.

- In the paragraph about hashing: "So the goal is to make collisions so unlikely as to be something we need not think about." fine.

- In the paragraph about MD5: "It has been found to be not as collision resistant as SHA." fine.

- In the paragraph about SHA: "It was SHA-1, but since then later versions, like SHA-256, have become more common." fine.

- In the paragraph about SHA: "SHA has a very large number of possible combinations." fine.

- In the paragraph about SHA: "This means there is a limit to how large a rainbow table can be, and this is why longer passwords are more secure than shorter passwords." fine.

- In the paragraph about SHA: "Since the development of rainbow tables, there have been methods designed to thwart such attacks." fine.

- In the paragraph about SHA: "The most common is salting, in which random bits are added to further secure encryption or hashing." fine.

- In the paragraph about SHA: "This is most often encountered with hashing to prevent rainbow table attacks." fine.

- In the paragraph about SHA: "Essentially, the salt is intermixed with the message that is to be hashed." fine.

- In the example binary: "01110000 01100001 01110011 01110011 00110000 00110000 00110001". That's fine.

- In the example after inserting bits: "01111100001 0110100011 0111100111 0111100111 0011100001 0011100001 00111000011". Might be okay.

- In the conversion to text: "xZ7". fine.

Now check for any missing punctuation or spacing.

Now ensure that the code block for hash is correct.

Now we need to ensure that there is a blank line between paragraphs. Also ensure that list items are preceded by "- " (dash space). Also ensure that headings are "## " (two #). Also ensure that there is a blank line before and after headings? Typically a heading is its own line, but we can have a blank line before and after.

Now let's write the final content.

We'll start:

[content]
A digital signature is not used to ensure the confidentiality of a message but rather to guarantee who sent the message. This is referred to as *nonrepudiation*. Essentially, nonrepudiation means proving who the sender is. Digital signatures are actually rather simple, but they are clever. They simply reverse the asymmetric encryption process. Recall that in asymmetric encryption, the public key (which anyone can have access to) is used to encrypt a message to the recipient, and the private key (which is kept secure and private) can decrypt it. With a digital signature, the sender encrypts something with his private key. If the recipient is able to decrypt that with the sender’s public key, then it must have been sent by the person purported to have sent the message. This process is shown in Figure 8.6.

![](img/c3d42b1644a6441bc36fb604e6c73b21_278_0.png)

Figure 8.6 Digital signatures.

## Hashing

A *hashing* is a type of cryptographic algorithm that has some specific characteristics. First and foremost, it is one way. That means you cannot unhash something. Second, you get a fixed-length output no matter what input is given. Third, there are no collisions. A collision occurs when two different inputs to the same hashing algorithm produce the same output (called a *hash* or *digest*). Ideally we would like to have no collisions. But the reality is that with fixed-length output, collisions are possible. So the goal is to make collisions so unlikely as to be something we need not think about.

## MD5

*MD5* is a 128-bit hash that is specified in RFC 1321. It was designed by Ron Rivest in 1991 to replace an earlier hash function, MD4. MD5 produces a 128-bit hash or digest. It has been found to be not as collision resistant as SHA.

## SHA

It was SHA-1, but since then later versions, like SHA-256, have become more common. SHA has a very large number of possible combinations. This means there is a limit to how large a rainbow table can be, and this is why longer passwords are more secure than shorter passwords. Since the development of rainbow tables, there have been methods designed to thwart such attacks. The most common is salting, in which random bits are added to further secure encryption or hashing. This is most often encountered with hashing to prevent rainbow table attacks. Essentially, the salt is intermixed with the message that is to be hashed. Consider an example. Say that you have a password that is:

In binary that is:

01110000 01100001 01110011 01110011 00110000 00110000 00110001

A salt algorithm would insert bits periodically. Let's assume for our example that we insert bits every fourth bit, giving us:

01111100001 0110100011 0111100111 0111100111 0011100001 0011100001 00111000011

If you convert that to text, you would get:

xZ7

All this is transparent to the end user, who doesn't even know that salting is happening or what it is. However, an attacker using a rainbow table to get passwords would get the wrong password.

Steganography is the art and science of writing hidden messages in such a way that no one, apart from the sender and intended recipient, suspects the existence of the message. It is a form of security through obscurity. Often the message is hidden in some other file, such as a digital picture or an audio file, to defy detection. The advantage of steganography over cryptography alone is that messages do not attract attention to themselves. If someone is aware that a message is even there, she won't try to decipher it. In many cases, messages are encrypted and hidden via steganography. The most common implementation of steganography utilizes the least significant bits in a file in order to store data. By altering the least significant bit, you can hide additional data without altering the original file in any noticeable way.

- Payload is the data to be covertly communicated. In other words, it is the message you wish to hide.

- The carrier is the signal, stream, or data file into which the payload is hidden.

- The channel is the medium used. This may be still photos, video, or sound files.

In modern times, steganography involves digital manipulation of files to hide messages. However, the concept of hiding messages is not new. There have been many methods used throughout history.

- The ancient Chinese wrapped notes in wax and swallowed them for transport. This was a crude but effective method of hiding messages.

- In ancient Greece, a messenger’s head would be shaved, a message was written on his head, and then his hair was allowed to grow back. Obviously, this method required some time.

- In 1518 Johannes Trithemius wrote a book on cryptography and described a technique in which a message was hidden by having each letter taken as a word from a specific column.

- During World War II the French Resistance sent messages written on the backs of couriers using invisible ink.

- Microdots are images/undeveloped film the size of a typewriter period that are embedded in innocuous documents. These were said to be used by spies during the Cold War.

- Also during the Cold War, the U.S. Central Intelligence Agency used various devices to hide messages. For example, they developed a tobacco pipe that had a small space to hide microfilm but could still be smoked.

## Steganography Methods and Tools

There are a number of tools available for implementing steganography. Many are free or at least have free trial versions. A few of these tools are listed here:

- **QuickStego:** Easy to use but very limited

- **Invisible Secrets:** Much more robust, with both a free version and a commercial version available

- **MP3Stego:** Specifically for hiding payload in MP3 files

- **Stealth Files 4:** Works with sound files, video files, and image files

- **Snow:** Hides data in whitespace

- **StegVideo:** Hides data in a video sequence

- **Invisible Secrets:** A very versatile steganography tool that has several options

## Cryptanalysis

Cryptanalysis is a daunting task. It essentially involves searching for some means to break through encryption of some sort. And, unlike what you see in the movies, it is a very time-consuming task that frequently leads to only partial success. Cryptanalysis involves using any method to decrypt the message that is more efficient than simple brute-force attempts. (Remember that brute forcing means simply trying every possible key.)

- **Total break:** The attacker deduces the secret key.

- **Global deduction:** The attacker discovers a functionally equivalent algorithm for encryption and decryption but without learning the key.

- **Instance (local) deduction:** The attacker discovers additional plain texts (or cipher texts) not previously known.

- **Information deduction:** The attacker gains some Shannon information about plain texts (or cipher texts) not previously known.

- **Distinguishing algorithm:** The attacker can distinguish the cipher from a random permutation.


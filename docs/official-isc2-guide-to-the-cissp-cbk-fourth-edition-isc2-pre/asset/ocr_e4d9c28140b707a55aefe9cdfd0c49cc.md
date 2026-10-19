rule set that will alert or block data streams it cannot decrypt can prove to be a strong addition to malware defenses.

# Steganography and Watermarking

Steganography is the science of hiding information. Whereas the goal of cryptography is to make data unreadable by a third party, the goal of steganography is to hide the data from a third party. With computers and networks, there are many ways of hiding information, such as:

+   - Covert channels
+   - Hidden text within webpages
+   - Hiding files in "plain sight" (what better place to hide a file than with an important sounding name in the c:\winnt\system32 directory?)
+   - Null ciphers (e.g., using the first letter of each word to form a hidden message in an otherwise innocuous text)

Steganography is significantly more sophisticated than the examples above suggest, allowing a user to hide large amounts of information within image and audio files. These forms of steganography often are used in conjunction with cryptography so that the information is doubly protected; first it is encrypted and then hidden so that an adversary has to first find the information (an often difficult task in and of itself) and then decrypt it.

There are a number of uses for steganography. One of the most widely used applications is for so-called digital watermarking. A watermark, historically, is the replication of an image, logo, or text on paper stock so that the source of the document can be at least partially authenticated. A digital watermark can accomplish the same function; graphic artists, for example, might post sample images on their website complete with an embedded signature so that they can later prove their ownership in case others attempt to portray the work as their own.

# Steganographic Methods

The following formula provides a very generic description of the pieces of the steganographic process: 8

```
cover_medium + hidden_data + stego_key = stego_medium
```

In this context, the cover_medium is the file in which you will hide the hidden_data, which may also be encrypted using the stego_key. The resultant file is the stego_medium (which will, of course. be the same type of file as the cover_medium). The cover_medium